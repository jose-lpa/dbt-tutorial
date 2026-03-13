# dbt-core tutorial

An implementation of the official [dbt-core tutorial](https://docs.getdbt.com/guides/manual-install),
trying to add some little extra good practices.

It uses GCP BigQuery as data engine.

## Requirements

> [!IMPORTANT]
> This project uses [uv](https://docs.astral.sh/uv/) package manager. Please make sure it is
> available in your system before proceeding.

In order to run this tutorial, the next requirements are needed:

### Environment variables

The next envvars are needed in order to run this project. They just define secrets and local data
that should not be shared across the Internet. You can both directly define them in your terminal,
e.g. using the Bash `export`, or set them in a `.env` file and pass the `--env-file .env` flag
every time you run the `uv run dbt ...` command. I.e. `uv run --env-file .env dbt ...`.

- `GOOGLE_APPLICATION_CREDENTIALS`: The path to your GCP service account `.json` credentials file.
- `GOOGLE_PROJECT_ID`: ID of the GCP project to use.
- `DBT_PROJECT_DIR`: Path to your `dbt-tutorial/jaffle_shop/` directory. Optional envvar but, if
  you set it up, you will remove the need of passing the `--project-dir jaffle_shop` flag every
  time you run `dbt` commands.

## Run dbt

In favor of portability, this project uses `uv` manager. Therefore, the `dbt` commands must be run
using `uv run dbt ...`.

Likewise, the dbt project has been placed inside the `jaffle_shop/` directory. This means that you
will need to pass `--project-dir jaffle_shop` flag when you run `dbt` commands or set up the envvar
`DBT_PROJECT_DIR`, whatever you prefer.

### Check up connections

You can check up that the BigQuery connection is properly configured and the project is ready to go
by running this command:

```shell
uv run --env-file .env dbt debug
```