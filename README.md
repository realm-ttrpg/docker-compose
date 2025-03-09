# docker-compose quickstart

The included `docker-compose.yml` manifest assumes that you have the API
server, Discord bot, and web interface projects cloned into subdirectories:

```
realm/
├─ docker-compose.yml
├─ scripts/
├─ rpgbot/     <-- discord-bot repo
├─ rpgserver/  <-- api-server repo
└─ rpgweb/     <-- web-interface repo
```

There are two scripts in the `scripts` folder for managing the service
repositories (`clone` and `update`).

Before building the service images, you will need the following configuration
files:

- `rpgbot/config.toml`
- `rpgserver/config.toml`
- `rpgweb/src/.env`

You must have a `$HOME/.npmrc` file with credentials for `npm.pkg.github.com` in
order to build the `web` image in the stack. (See:
[Authenticating with a personal access token][])

Build the service images:

```shell
docker compose build
```

Then spin up the entire stack:

```shell
docker compose up  # add -d flag to daemonize
```

[authenticating with a personal access token]: https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-npm-registry#authenticating-with-a-personal-access-token
