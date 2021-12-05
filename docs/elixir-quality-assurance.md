# Elixir Quality Assurance

Enables Quality Assurance tools:

- Testing (mix test)
- Formatter (mix format)
- Linter (mix credo)
- Typespec (mix dialyzer)

## Usage

Create a new GitHub Workflow (ex: `.github/workflows/ci.yml`) with the following content:

```yaml
name: Elixir Quality Assurance

on:
  push:
    branches:
      - master
  pull_request:
    branches:
      - master

jobs:
  quality-assurance:
    uses: straw-hat-team/github-actions-workflows/.github/workflows/elixir-quality-assurance.yml@master
    with:
      elixir-version: '1.11'
      otp-version: '22.3'
      testing-enabled: true
      formatter-enabled: true
      credo-enabled: true
      dialyzer-enabled: true
```

## Dialyzer setup

Add the [Dialyxir](https://github.com/jeremyjh/dialyxir) dependency:

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
      # ...
      {:dialyxir, ">= 0.0.0", only: [:dev], runtime: false}
    ]
  end
end
```

In your `mix.exs`, you must configure Dialyzer with the following settings:

```elixir
defmodule MyLibrary.MixProject do
  use Mix.Project

  def project do
    [
      # ...
      dialyzer: [
        # ... other dialyzer settings
        plt_core_path: "priv/plts",
        plt_file: {:no_warn, "priv/plts/dialyzer.plt"}
      ]
    ]
  end
end
```

Make sure that `priv/plts` directory exists before running Dialyzer. Create a file called `priv/plts/.gitkeep` and
commit the file as part of your repository to make sure the directory exists at all time.

```shell
# Creates priv/plts directory if it doesn't exists
mdkir -p priv/plts
# Create an empty file
touch priv/plts/.gitkeep
```

You probably do not want to commit the `plts` files therefore add the following content to your `.gitignore` file:

```.gitignore
/priv/plts/*.plt
/priv/plts/*.plt.hash
```

## Troubleshooting

### Credo

```log
** (Mix) The task "credo" could not be found
```

Verify that `credo` dependency was added correctly.

### Dialyzer

```log
:dialyzer.run error: No such file, directory or application: ".../_build/dev/dialyxir_erlang-..._elixir-..._deps-dev.plt"
```

Verify the Dialyzer configuration follows the guidelines.

```log
** (Mix) The task "dialyzer" could not be found
```

Verify that `dialyzer` dependency was added correctly.
