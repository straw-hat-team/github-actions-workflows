# Elixir Credo

Runs [Dialyxir](https://github.com/jeremyjh/dialyxir) in your project.

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Ensure that [Credo](https://github.com/rrrene/credo) dependency is present in your project. Check your `mix.exs`
   file.
    
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
           {:credo, ">= 0.0.0", only: [:dev, :test], runtime: false},
         ]
       end
     end
    ```

3. Make sure `actions/checkout` action is used before this action.
4. Add this action to your job in your workflow, here is an example:

    ```yaml
    #...
    jobs:
      publish:
        name: Run Credo
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2 # checkout the repository first
          - uses: straw-hat-team/github-actions-workflows/elixir/credo@master
            with:
              elixir-version: '1.11'
              otp-version: '22.3'
    ```

### Fix credo could not be found error

If you see the following error:

```log
** (Mix) The task "credo" could not be found
```

1. Verify that `credo` dependency was added correctly as a dependency.
