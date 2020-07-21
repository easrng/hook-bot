# How to make a HookBot Bot

A HookBot bot has two main components: a JSON manifest, and a message handler webhook. Bots are invited with the manifest link.

## The manifest

The bot manifest is a JSON file that describes your bot.
It has the following keys:
 
 - `avatar`: The link to your bot's avatar. The avatar should be square.
 - `name`: The name of your bot.
 - `webhook`: Your URL for your bot's message handler webhook.

For example:
```json
{
  "avatar":
    "https://cdn.glitch.com/b57cb370-c9a0-4310-8ca3-11106d0c9ddc%2Fphoto-1549634377-5831ba549c84.jfif?v=1573580879606",
  "name": "Moth Bot",
  "webhook": "https://moth-bot.glitch.me/message"
}
```

## The message handler webhook

The message handler webhook is how your bot receives messages. HookBot POSTs messages to it when a user sends a message starting with your bot's prefix. Prefixes are managed by HookBot and your bot has no control over them. 
The messages POSTed to you are JSON objects with the following keys:

  - `content`: The message, without the prefix
  - `response`: The response webhook
  - `server`: The server ID
  - `user`: The user ID
  - `manager`: If the user has the "Manage Server" permission.

For example:
```json
{
  "content: "",
  "response: "https://hook-bot-backend.glitch.me/webhook/129fbc4a-baac-4870-958a-bc2213f3fb10",
  "server": "722963069294346352",
  "user": "642358695652753418",
  "manager": true
}
```

## Sending messages

To reply to a message, POST a JSON object to the message's `response` URL.
The POSTed JSON object must have the following keys:

 - `content`: The message
 - `embeds`: An optional array of up to 10 [embed](https://discord.com/developers/docs/resources/channel#embed-object) objects

# Invites
HookBot bots don't have an invite page in quite the same way that normal bots do, but to create a link with instructions to invite your bot, use the form below.

<form action="./invite" method="GET" style="display:grid;grid-gap:0.5rem">
  <input type="text" name="name" placeholder="Bot Name...">
  <input type="url" name="url" placeholder="Bot Manifest URL...">
  <input type="url" name="avatar" placeholder="Bot Avatar URL...">
  <input type="submit" value="Create Invite">
</form>
