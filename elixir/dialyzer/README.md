# Elixir Dialyzer

Runs [Dialyxir](https://github.com/jeremyjh/dialyxir) in your project.

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Complete [Setup Dialyxir in your project](#setup-dialyxir-in-your-project).
2. Make sure `actions/checkout` action is used before this action.
3. Add this action to your job in your workflow, here is an example:

    ```yaml
    #...
    jobs:
      dialyzer:
        name: Run Dialyzer
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2 # checkout the repository first
          - uses: straw-hat-team/github-actions-workflows/elixir/dialyzer@master
            with:
              elixir-version: '1.11' # optional, fallback to use .tool-versions
              otp-version: '22.3' # optional, fallback to use .tool-versions
              version-type: 'loose' # optional, fallback to strict
    ```

### Setup Dialyxir in your project

1. Ensure that [Dialyxir](https://github.com/jeremyjh/dialyxir) dependency is present in your project. Check
   your `mix.exs` file.

    ```elixir
    defmodule MyLibrary.MixProject do
      use Mix.Project
    
      def project do
        [
          # ...
          deps: deps()
        ]
      end
    
      defp deps do
        [
          # ... here, is an example of how to add it
          {:dialyxir, ">= 0.0.0", only: [:dev], runtime: false}
        ]
      end
    end
    ```

2. In your `mix.exs`, you must configure Dialyzer with the following settings:

    ```elixir
    defmodule MyLibrary.MixProject do
      use Mix.Project
    
      def project do
        [
          # ...
          dialyzer: [
            # ... other dialyzer settings
            plt_core_path: "priv/plts", # must be this
            plt_file: {:no_warn, "priv/plts/dialyzer.plt"}
            # must be this
          ]
        ]
      end
    end
    ```

3. Make sure that `priv/plts` directory exists before running Dialyzer. Create a file called `priv/plts/.gitkeep` and
   commit the file as part of your repository to make sure the directory exists at all time.

    ```shell
    # Creates priv/plts directory if it doesn't exists
    mkdir -p priv/plts
    # Create an empty file
    touch priv/plts/.gitkeep
    ```

4. You probably do not want to commit the `plts` files therefore add the following content to your `.gitignore` file:

    ```.gitignore
    /priv/plts/*.plt
    /priv/plts/*.plt.hash
    ```

### Fix No such file, directory or application error

If you see the following error:

```log
:dialyzer.run error: No such file, directory or application: ".../_build/dev/dialyxir_erlang-..._elixir-..._deps-dev.plt"
```

1. Verify the Dialyzer configuration. Follow [Setup Dialyxir in your project](#setup-dialyxir-in-your-project) guide.

### Fix The task "dialyzer" could not be found error

If you see the following error:

```log
** (Mix) The task "dialyzer" could not be found
```

1. Verify that `dialyxir` dependency was added correctly.
   Follow [Setup Dialyxir in your project](#setup-dialyxir-in-your-project) guide.
