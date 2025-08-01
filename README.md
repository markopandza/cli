# Octomind CLI

![Continuous Integration](https://github.com/octomind-dev/cli/actions/workflows/ts.yml/badge.svg)

A command-line interface for interacting with the Octomind API. 
This CLI allows you to execute tests, retrieve test reports, and manage private locations as well as environments.
See [API documentation](https://octomind.dev/docs/api-reference/)

## Usage / Installation

1. To install the package globally do **NOT** just a `npm i -g @octomind/octomind` but instead 
```bash
mkdir -p ~/.local/packages
cd ~/.local/packages
npm install @octomind/octomind@latest
# either create an alias
alias octomind="node ~/.local/packages/node_modules/@octomind/octomind/dist/index.js"
# or create a symlink
sudo ln -s ~/.local/packages/node_modules/@octomind/octomind/dist/index.js /usr/local/bin/octomind
```

this will install the package to `~/.local/packages` and create symlinks in `/usr/local/bin` or creates an alias. 
This is necessary for the cli to work and avoid dependency conflicts, when installing the package globally.

2. Use the cli through npx e.g. `npx @octomind/octomind -h`

# octomind

Octomind cli tool. Version: 1.1.2. Additional documentation see https://octomind.dev/docs/api-reference/

**Usage:** `octomind [options] [command]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-V, --version` | output the version number | No |  |

# octomind CLI Documentation

Octomind cli tool. Version: 1.1.2. Additional documentation see https://octomind.dev/docs/api-reference/

## Commands

## init

Initialize configuration by setting up API key

**Usage:** `init [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-t, --test-target-id <id>` | Test target ID | Yes |  |
| `-k, --api-key <key>` | the api key for authentication | Yes |  |
| `-f, --force` | Force overwrite existing configuration | No |  |

## switch-test-target

Switch to a different test target

**Usage:** `switch-test-target [options]`

## debug

run test cases against local build

**Usage:** `debug [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-u, --url <url>` | url the tests should run against | Yes |  |
| `-i, --id [uuid]` | id of the test case you want to run, if not provided will run all test cases in the test target | No |  |
| `-e, --environment-id [uuid]` | id of the environment you want to run against, if not provided will run all test cases against the default environment | No |  |
| `-a, --test-target-id [uuid]` | id of the test target of the test case, if not provided will use the test target id from the config | No |  |
| `--headless` | if we should run headless without the UI of playwright and the browser | No |  |
| `--persist` | if we should write playwright config and files to current directory, you can then run 'npx playwright test' to run them again | No |  |
| `--grep [substring]` | filter test cases by substring | No |  |

## execute

Execute test cases

**Usage:** `execute [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-u, --url <url>` | URL to test | Yes |  |
| `-t, --test-target-id [id]` | Test target ID, if not provided will use the test target id from the config | No |  |
| `-e, --environment-name [name]` | Environment name | No | default |
| `-d, --description [text]` | Test description | No |  |
| `-g, --tags [tags]` | comma separated list of tags | No |  |
| `-v, --variables-to-overwrite [variables]` | JSON object of variables to overwrite | No |  |

## test-report

Get test report details

**Usage:** `test-report [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-r, --test-report-id <id>` | Test report ID | Yes |  |
| `-t, --test-target-id [id]` | Test target ID, if not provided will use the test target id from the config | No |  |

## register-location

Register a private location

**Usage:** `register-location [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-n, --name <name>` | Location name | Yes |  |
| `-p, --password <password>` | Proxy password | Yes |  |
| `-u, --username <user>` | Proxy user | Yes |  |
| `-a, --address <address>` | Location address | Yes |  |

## unregister-location

Unregister a private location

**Usage:** `unregister-location [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-n, --name <name>` | Location name | Yes |  |

## list-private-locations

List all private locations

**Usage:** `list-private-locations [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |

## list-environments

List all environments

**Usage:** `list-environments [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-t, --test-target-id [id]` | Test target ID, if not provided will use the test target id from the config | No |  |

## create-environment

Create a new environment

**Usage:** `create-environment [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-n, --name <name>` | Environment name | Yes |  |
| `-d, --discovery-url <url>` | Discovery URL | Yes |  |
| `-t, --test-target-id [id]` | Test target ID, if not provided will use the test target id from the config | No |  |
| `--test-account-username [username]` | Test account username | No |  |
| `--test-account-password [password]` | Test account password | No |  |
| `--test-account-otp-initializer-key [key]` | Test account OTP initializer key | No |  |
| `--basic-auth-username [username]` | Basic auth username | No |  |
| `--basic-auth-password [password]` | Basic auth password | No |  |
| `--private-location-name [name]` | Private location name | No |  |

## update-environment

Update an existing environment

**Usage:** `update-environment [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-e, --environment-id <id>` | Environment ID | Yes |  |
| `-t, --test-target-id [id]` | Test target ID, if not provided will use the test target id from the config | No |  |
| `-n, --name [name]` | Environment name | No |  |
| `-d, --discovery-url [url]` | Discovery URL | No |  |
| `--test-account-username [username]` | Test account username | No |  |
| `--test-account-password [password]` | Test account password | No |  |
| `--test-account-otp-initializer-key [key]` | Test account OTP initializer key | No |  |
| `--basic-auth-username [username]` | Basic auth username | No |  |
| `--basic-auth-password [password]` | Basic auth password | No |  |
| `--private-location-name [name]` | Private location name | No |  |

## delete-environment

Delete an environment

**Usage:** `delete-environment [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-e, --environment-id <id>` | Environment ID | Yes |  |
| `-t, --test-target-id [id]` | Test target ID, if not provided will use the test target id from the config | No |  |

## start-private-location

Start a private location worker, see https://octomind.dev/docs/proxy/private-location

**Usage:** `start-private-location [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-n, --name [name]` | Location name | No |  |
| `-u, --username [username]` | Proxy user | No |  |
| `-p, --password [password]` | Proxy password | No |  |
| `-l, --host-network` | Use host network (default: false). If set you can use localhost directly | No | false |

## stop-private-location

Stop a private location worker, see https://octomind.dev/docs/proxy/private-location

**Usage:** `stop-private-location [options]`

## notifications

Get notifications for a test target

**Usage:** `notifications [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-t, --test-target-id [id]` | Test target ID, if not provided will use the test target id from the config | No |  |

## test-case

Get details of a specific test case

**Usage:** `test-case [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-c, --test-case-id <id>` | Test case ID | Yes |  |
| `-t, --test-target-id [id]` | Test target ID, if not provided will use the test target id from the config | No |  |

## create-discovery

Create a new test case discovery

**Usage:** `create-discovery [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-n, --name <name>` | Discovery name | Yes |  |
| `-p, --prompt <prompt>` | Discovery prompt | Yes |  |
| `-t, --test-target-id [id]` | Test target ID, if not provided will use the test target id from the config | No |  |
| `-e, --entry-point-url-path [path]` | Entry point URL path | No |  |
| `--prerequisite-id [id]` | Prerequisite test case ID | No |  |
| `--external-id [id]` | External identifier | No |  |
| `--assigned-tag-ids [ids]` | Comma-separated list of tag IDs | No |  |
| `--folder-id [id]` | Folder ID | No |  |

## list-test-cases

List all test cases

**Usage:** `list-test-cases [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |
| `-t, --test-target-id [id]` | Test target ID, if not provided will use the test target id from the config | No |  |

## list-test-targets

List all test targets

**Usage:** `list-test-targets [options]`

### Options

| Option | Description | Required | Default |
|--------|-------------|----------|--------|
| `-j, --json` | Output raw JSON response | No |  |



## Output Formats

By default, the CLI provides formatted text output for better readability. Add the `--json` flag to any command to get the raw JSON response instead. This is useful for scripting or when you need to process the output programmatically.

Example of JSON output:
```json
{
  "id": "826c15af-644b-4b28-89b4-f50ff34e46b7",
  "testTargetId": "3435918b-3d29-4ebd-8c68-9a540532f45a",
  "status": "PASSED",
  "executionUrl": "https://example.com",
  "testResults": [
    {
      "id": "abc-123-456",
      "testTargetId": "3435918b-3d29-4ebd-8c68-9a540532f45a",
      "testCaseId": "test-1",
      "status": "PASSED",
      "traceUrl": "https://storage.googleapis.com/automagically-traces/abc-123-trace.zip"
    },
    {
      "id": "def-456-789",
      "testTargetId": "3435918b-3d29-4ebd-8c68-9a540532f45a",
      "testCaseId": "test-2",
      "status": "PASSED",
      "traceUrl": "https://storage.googleapis.com/automagically-traces/def-456-trace.zip"
    }
  ]
}
```

## Development

1. Clone the repository
2. Install dependencies:
```bash
pnpm install
```

The CLI is written in TypeScript and uses the following dependencies:
- [commander](https://github.com/tj/commander.js): For command-line argument parsing
- [openapi-fetch](https://openapi-ts.dev/openapi-fetch/): For making openapi API calls
- [openapi-typescript](https://openapi-ts.dev/introduction): For generating types from openapi spec

To build from source:
```bash
pnpm run build
```
