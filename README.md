[![Setup StackQL](https://github.com/stackql/setup-stackql/actions/workflows/setup-stackql.yml/badge.svg)](https://github.com/stackql/setup-stackql/actions/workflows/setup-stackql.yml)  

# setup-stackql

The `stackql/setup-stackql` action is a JavaScript action that sets up StackQL CLI in your GitHub Actions workflow by:

- Downloading a latest Stackql CLI and adding it to the `PATH`.
- Setup AUTH env var in the Github Action

This action can be run on `ubuntu-latest`, `windows-latest`, and `macos-latest` GitHub Actions runners, and will install and expose the latest version of the `stackql` CLI on the runner environment.  

# Auth
[Learn more](https://stackql.io/docs/getting-started/authenticating) about authentication setup when running stackql

### Basic Example
1. Set Auth variable, for example:
```
{ "github": { "type": "basic", "credentialsenvvar": "STACKQL_GITHUB_CREDS" } }
```
2. create the github token as a secret
3. In the execution step, pass the secret as environment variable with name "STACKQL_GITHUB_CREDS"

Check the "Use GitHub Provider" step in `.github/workflows/setup-stackql.yml` for the working example

### json File Auth example

1. Set Auth variable, for example:
```
{ "google": { "type": "service_account",  "credentialsfilepath": "sa-key.json" }}
```
2. encode the key json file into base64 string
3. in execution step, run `sudo echo ${{ secrets.<name of the secret> }} | base64 -d > sa-key.json`

Check the "Prep Google Creds" step in `.github/workflows/setup-stackql.yml` for the working example