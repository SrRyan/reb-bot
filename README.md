# reb-bot

🤖 Your friendly neighborhood discord bot.

## Development

You'll need the following env vars (either `.env` or however you want to supply):

```sh
DISCORD_TOKEN= # discord bot token
IEX_PUB_TOKEN= # public token for iex cloud
IEX_SECRET_TOKEN= # secret token for iex cloud
REDIS_URL= # redis:// style connection URL
```

Then setup:

```console
rob@local$ script/setup
```

Then run:

```console
rob@local$ script/setup
```

## Creating a new command

Use the generator script:

```console
rob@local$ script/generate-command -n foobar
command file generated: /workspaces/reb-bot/lib/commands/foobar.rb
```

And add your changes to the generated file.

## Registering commands

For bots that use slash commands, they must be [registered with Discord](https://discord.com/developers/docs/interactions/application-commands#registering-a-command). Commands can be registered globally, or to a specific server. During development, it's recommended to register to a specific server since it will update instantly, then register it globally when ready.

Open a debug console with `script/console`:

```ruby
server_id = Rebbot::TEST_SERVER_ID # or nil for global

# clean up old commands
bot.delete_commands!(server_id)

# register new commands
bot.register_commands!(server_id)
```
