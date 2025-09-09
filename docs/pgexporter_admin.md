---
outline: deep
---

# `pgexporter-admin`

`pgexporter-admin` exists to manage list of admins/users allowed to access `pgexporter`. It is the administration utility of `pgexporter`.

Usage:
```
pgexporter-admin -f <user-file> [options] <command>
pgexporter-admin -?
pgexporter-admin -V
```

:::tip NOTE
The notation standard used for describing usage can be found [here](http://docopt.org).
:::

## Meta Options

### Help

Usage
```sh
$ pgexporter-admin -?
# or
$ pgexporter-admin --help
```

Output:
```
pgexporter-admin 0.7.0
  Administration utility for pgexporter

USAGE:
  pgexporter-admin -f <user-file> [options] [command]
  pgexporter-admin -?
  pgexporter-admin -V

OPTIONS:

  -f, --file FILE         Set the path to a user file\n");
  -U, --user USER         Set the user name\n");
  -P, --password PASSWORD Set the password for the user\n");
  -g, --generate          Generate a password\n");
  -l, --length            Password length\n");
  -V, --version           Display version information\n");
  -F, --format text|json  Set the output format\n");
  -?, --help              Display help\n");

COMMANDS:
  master-key              Create or update the master key
  user <subcommand>       Manage a specific user, where <subcommand> can be
                          - add  to add a new user
                          - del  to remove an existing user
                          - edit to change the password for an existing user
                          - ls   to list all available users

pgexporter: https://pgexporter.github.io/
Report bugs: https://github.com/pgexporter/pgexporter/issues
```

### Version

Usage:
```sh
$ pgexporter-admin -V
# or
$ pgexporter-admin --version
```

Output:
```
pgexporter-admin 0.7.0
```

## Commands:

### `master-key`

_Description_: Set master key.

:::code-group
```sh [Usage]
$ pgexporter-admin add-user # -f <users-file> [options]
# or
$ pgexporter-admin add-user # -f <users-file> [options]
```
:::

### `user add`

_Description_: Add a user.

:::code-group
```sh [Usage]
$ pgexporter-admin user add # -f <users-file> [options]
```
:::

### `user edit`

_Description_: Update password of a user.

:::code-group
```sh [Usage]
$ pgexporter-admin user edit # -f <users-file> [options]
```
:::

### `user del`

_Description_: Remove a user.

:::code-group
```sh [Usage]
$ pgexporter-admin user del # -f <users-file> [options]
```
:::

### `user ls`

_Description_: Provides list of users configured for `pgexporter`.

:::code-group
```sh [Usage]
$ pgexporter-admin user ls # -f <users-file> [options]
```

:::
