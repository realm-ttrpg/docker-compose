# docker-compose quickstart

The included `docker-compose.yml` manifest builds the Discord bot, API server,
and web interface container images from a set of subdirectories populated by
a utility script.

```
realm/
├─ docker-compose.yml
├─ scripts/    <-- helper scripts
├─ rpgbot/     <-- discord-bot repo
├─ rpgserver/  <-- api-server repo
└─ rpgweb/     <-- web-interface repo
```

## Setup

Before building the service images, you will need the following configuration
files. There are example versions of each in the same directory.

- `rpgbot/config.toml` - Bot configuration file
- `rpgserver/config.toml` - API server configuration file
- `rpgweb/src/.env` - Web interface build environment file

You must also have a `$HOME/.npmrc` file with credentials for
`npm.pkg.github.com` in order to build the `web` image in the stack. (See:
[Authenticating with a personal access token][])

Clone the repositories:

```shell
scripts/clone
```

Build the service images:

```shell
docker compose build
```

Start the services:

```shell
# remove -d flag to run in foreground
docker compose up -d
```

## Update

Pull repository updates:

```shell
scripts/update
```

Build updated service images:

```shell
docker compose build
```

Restart affected containers:

```shell
docker compose up -d
```

[authenticating with a personal access token]: https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-npm-registry#authenticating-with-a-personal-access-token
