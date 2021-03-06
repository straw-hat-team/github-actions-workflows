# GitHub Actions Workflows

A set of GitHub Actions Workflow Templates.

- [References](#references)

## References

### Actions

- [semantic-pull-request](./semantic-pull-request/README.md): ensures that the Pull Request title matches Conventional
  Commits spec.

#### asdf

- [asdf/get-version](./asdf/get-version/README.md): return the version for a given asdf plugin.

#### Elixir-Lang

- [elixir/compilation-warnings](./elixir/compilation-warnings/README.md): compiles the code treating warnings as errors.
- [elixir/credo](./elixir/credo/README.md): runs Credo linter.
- [elixir/dialyzer](./elixir/dialyzer/README.md): runs Dialyzer typespec check.
- [elixir/format](./elixir/format/README.md): runs formatter.
- [elixir/publish](./elixir/publish/README.md): publish a release to Hex.
- [elixir/setup](./elixir/setup/README.md): setup Elixir, use `.tool-versions` file as a fallback for the versions.
- [elixir/test](./elixir/test/README.md): runs tests.
- [elixir/umbrella-publish](./elixir/umbrella-publish/README.md): publish an Elixir package to Hex.pm from an Umbrella
  app setup.

#### Git

- [git/set-sht-bot-user](./git/set-sht-bot-user/README.md): set the Straw Hat Team Bot Git user.

#### NodeJS

- [nodejs/setup](./nodejs/setup/README.md): setup NodeJS, use `.tool-versions` file as a fallback for the version.
- [nodejs/prettier](./nodejs/prettier/README.md): runs prettier check on all files.
- [nodejs/jest](./nodejs/jest/README.md): runs jest runner in the project.

### Workflows Templates

- [Workflows Templates](./.github/workflows/README.md)
