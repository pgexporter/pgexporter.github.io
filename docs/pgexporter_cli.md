# `pgexporter-cli`

`pgexporter-cli` exists to control `pgexporter`, especially when `pgexporter` is [running as a daemon](./pgexporter/command_line_flags.md#run-as-a-daemon).

Usage:
```
pgexporter-cli -c <config-file> [options] [command]
pgexporter-cli -h <host> -p <port> [options] [command]
pgexporter-cli -?
pgexporter-cli -V
```

Commands:
- [`ping`](#ping): Check if `pgexporter` is alive.
- [`shutdown`](#shutdown): Shutdown `pgexporter`.
- [`status`](#status): Status of `pgexporter`.
- [`status details`](#details): Alias for `status`.
- [`reload`](#reload): Reload the configuration.
<!-- - `reset`: Reset the Prometheus statistics. -->

:::tip NOTE
The notation standard used for describing usage can be found [here](http://docopt.org).
:::

## Meta Options

### Help

:::code-group

```sh [Usage]
$ pgexporter-cli --help
```

```txt [Sample Output]
pgexporter-cli 0.6.0
  Command line utility for pgexporter

USAGE:
  pgexporter-cli -c <config-file> [options] <command>
  pgexporter-cli -h <host> -p <port> [options] <command>
  pgexporter-cli -?
  pgexporter-cli -V

OPTIONS:

Usage:
  pgexporter-cli [ -c CONFIG_FILE ] [ COMMAND ]

Options:
  -c, --config CONFIG_FILE                       Set the path to the pgexporter.conf file
  -h, --host HOST                                Set the host name
  -p, --port PORT                                Set the port number
  -U, --user USERNAME                            Set the user name
  -P, --password PASSWORD                        Set the password
  -L, --logfile FILE                             Set the log file
  -v, --verbose                                  Output text string of result
  -V, --version                                  Display version information
  -F, --format text|json|raw                     Set the output format
  -C, --compress none|gz|zstd|lz4|bz2            Compress the wire protocol
  -E, --encrypt none|aes|aes256|aes192|aes128    Encrypt the wire protocol
  -?, --help                                     Display help

COMMANDS:
  ping                     Check if pgexporter is alive
  shutdown                 Shutdown pgexporter
  status [details]         Status of pgexporter, with optional details
  conf <action>            Manage the configuration, with one of subcommands:
                           - 'reload' to reload the configuration
                           - 'ls' to print the configurations used
                           - 'get' to obtain information about a runtime configuration value
                           - 'set' to modify a configuration value;
  clear <what>             Clear data, with:
                           - 'prometheus' to reset the Prometheus statistics
```

:::

### Version

:::code-group

```sh [Usage]
$ pgexporter-cli --version
# or
$ pgexporter-cli -V
```

```txt [Sample Output]
pgexporter-cli 0.6.0
```
:::

## Commands

### `ping`

_Description_: Checks if `pgexporter` is successfully running.

:::tip NOTE
It needs [`verbose`](#verbose) flag to output anything.
:::

:::code-group

```sh [Usage]
$ pgexporter-cli ping # -c <config-file> [options] --verbose
# or
$ pgexporter-cli ping # -h <host> -p port [options] --verbose
```

```txt [Output 1]
pgexporter is running.
```
```txt [Output 2]
pgexporter is not running.
```
:::

### `shutdown`

_Description_: Shutdown `pgexporter`.

:::code-group

```sh [Usage]
$ pgexporter-cli shutdown # -c <config-file> [options]
# or
$ pgexporter-cli shutdown # -h <host> -p port [options]
```

:::

### `status`

_Description_: Provides status of the servers `pgexporter` is listening to for metrics.


:::code-group
```sh [Usage]
$ pgexporter-cli status # -c <config-file> [options]
# or
$ pgexporter-cli status # -h <host> -p port [options]
```

```txt [Sample Output]
Number of servers: 8
Server           : own
  Active         : Yes
Server           : v10
  Active         : No
Server           : v11
  Active         : No
Server           : v12
  Active         : No
Server           : v13
  Active         : Yes
Server           : v14
  Active         : No
Server           : v15
  Active         : Yes
Server           : v16beta2
  Active         : No
```
:::

### `status details`

_Description_: See [status](#status).

:::code-group
```sh [Usage]
$ pgexporter-cli status details # -c <config-file> [options]
# or
$ pgexporter-cli status details # -h <host> -p port [options]
```

```txt [Sample Output]
Number of servers: 8
Server           : own
  Active         : Yes
Server           : v10
  Active         : No
Server           : v11
  Active         : No
Server           : v12
  Active         : No
Server           : v13
  Active         : Yes
Server           : v14
  Active         : No
Server           : v15
  Active         : Yes
Server           : v16beta2
  Active         : No
```
:::


### `conf reload`

_Description_: Reload the configuration of `pgexporter` (in case of changes).

:::code-group
```sh [Usage]
$ pgexporter-cli conf reload # -c <config-file> [options]
```
:::

:::warning
`conf reload` can only be done in local connections.
:::

## Options

### Config File

_Description_:

Specify the [`pgexporter.conf` file](./pgexporter/configuration.md).

:::code-group
```sh [Usage]
$ pgexporter-cli -c <path-of-config-file> # [options] [command]
# or
$ pgexporter-cli --config <path-of-config-file> # [options] [command]
```

```sh [Example Usage]
# Assuming path to config is ./pgexporter.conf
$ pgexporter-cli -c ./pgexporter.conf # [options] [command]
```
:::

### Host

_Description_:

Specify the **host** of `pgexporter`.

:::code-group
```sh [Usage]
$ pgexporter-cli -h <host> # -p <port> [options] [command]
# or
$ pgexporter-cli --host <host> # -p <port> [options] [command]
```

```sh [Example Usage]
# Assuming host is localhost
$ pgexporter-cli -h localhost # -p <port> [options] [command]
# or
# Assuming host is 127.0.0.1
$ pgexporter-cli -h 127.0.0.1 # -p <port> [options] [command]
```
:::

### Port

_Description_:

Speicfy the **port** of `pgexporter`.

:::code-group
```sh [Usage]
$ pgexporter-cli -p <port> # -h <host> [options] [command]
# or
$ pgexporter-cli --port <port> # -h <host> [options] [command]
```

```sh [Example Usage]
# Assuming port is 8080
$ pgexporter-cli -p 8080 # -h <host> [options] [command]
```
:::

:::warning NOTE
The `port` mentioned here is the port at which [**management** is open](./pgexporter/configuration.md).
:::

### Username

_Description_:

Username of the user trying to interact with `pgexporter`.

:::code-group
```sh [Usage]
$ pgexporter-cli -U <username> # -P <password> [options] [command]
# or
$ pgexporter-cli --user <username> # -P <password> [options] [command]
```

```sh [Example Usage]
$ pgexporter-cli -U pgexporter # -P <password> [options] [command]
```
:::

:::warning NOTE
If you do not provide your credentials in the arguments, you will be prompted to provide them later.
:::

:::tip NOTE
Steps for registering a username and password to access `pgexporter` through `pgexporter-cli` can be [viewed here](../guide/pgexporter/configuration.md#user-vault).
:::

### Password

_Description_:

Password of the user trying to interact with `pgexporter`.

:::code-group
```sh [Usage]
$ pgexporter-cli -P <password> # -U <username> [options] [command]
# or
$ pgexporter-cli --password <password> # --user <username> [options] [command]
```
```sh [Example Usage]
$ pgexporter-cli -P pgexporter # -U pgexporter [options] [command]
```
:::

:::warning NOTE
If you do not provide your credentials in the arguments, you will be prompted to provide them later.
:::

:::tip NOTE
Steps for registering a username and password to access `pgexporter` through `pgexporter-cli` can be [viewed here](#(../guide/pgexporter/configuration.md#user-vault)).
:::

### Log File

_Description_:

Specify the log file for `pgexporter_config`.

:::code-group
```sh [Usage]
$ pgexporter-cli -L <path-to-log-file> # -U <username> [options] [command]
# or
$ pgexporter-cli --logfile <path-to-log-file> # -U <username> [options] [command]
```
```sh [Example Usage]
# Assuming wanting a logfile ./log.out
$ pgexporter-cli -L ./log.out # -U <username> [options] [command]
```
:::

### Verbose

_Description_:

Outputs more verbose information.

:::code-group
```sh [Usage]
$ pgexporter-cli -v  # [options] [command]
# or
$ pgexporter-cli --verbose # [options] [command]
```
:::
