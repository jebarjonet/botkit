# Botkit - Building Blocks for Building Bots

[![npm](https://img.shields.io/npm/v/botkit.svg)](https://www.npmjs.com/package/botkit)
[![David](https://img.shields.io/david/howdyai/botkit.svg)](https://david-dm.org/howdyai/botkit)
[![npm](https://img.shields.io/npm/l/botkit.svg)](https://spdx.org/licenses/MIT)
[![Build Status](https://travis-ci.com/howdyai/botkit.svg?branch=master)](https://travis-ci.com/howdyai/botkit)

**Botkit is the leading developer tool for building chat bots, apps and custom integrations for major messaging platforms.**

## These docs are for the brand new 4.0 branch of Botkit! If you're looking for version 0.7, [look here](https://botkit.ai/docs).

## Install Botkit

The best way to get started locally with Botkit is by installing our Yeoman template, and using it to create a new Botkit project. 
This will install and configure a starter kit for you!

```
npm install -g yo generator-botkit
yo botkit
```

## Platform Support

Botkit applications can be connected to many different messaging channels. [Platform specific documentation can be found on the main docs site.]()

Botkit can connect to multiple messaging channels through the [Microsoft Bot Framework Service](https://dev.botframework.com).
No plugins are necessary to use the Bot Framework service, and bots can be developed locally using the [Bot Framework Emulator](https://aka.ms/botemulator).

The Botkit project includes official adapters for [self-hosted Websocket](), [Slack](), [Webex Teams](), [Facebook Messenger](), [Twilio SMS](), [Google Hangouts](). Using these plugins, your bot can communicate directly with the messaging platforms.

Additional adapters can be found by searching npm for Bot Framework-compatible adapters.

### ** Remix on Glitch**

Want to dive right in? [Remix one of our starter kits on Glitch](https://glitch.com/botkit). You'll start with a fully functioning app that you can edit and run from the browser!

 [![Remix on Glitch](https://botkit.ai/docs/glitch.png)](https://glitch.com/botkit)

## Build Your Bot

The goal of Botkit is to make it easier and more fun to build software that talks and works like a robot! 
Building a bot should feel cool, and not too technically complicated.

Botkit handles all the nitty gritty details like
API calls, session management and authentication,
allowing you to focus on building COOL FEATURES for your
bot using middleware and event handlers.

The toolkit is designed to provide meaningful building blocks for creating conversational user interfaces - with functions like `hears()`, `ask()`, and `reply()` that do what they say they do.

The [full documentation for Botkit's capabilities begins here &raquo;](../docs/index.md)

### Hearing Keywords

Most bots do their thing by listening for keywords, phrases or patterns in messages from users. Botkit has a special event handler called `hears()` that makes it easy to configure your bot to listen for this type of trigger.

```
controller.hears(['string','pattern .*',new RegExp('.*','i')],'message,other_event', async (bot, message) => {

  // do something!
  await bot.reply(message, 'I heard a message.')

});
```

[Read more about hearing things &rsaquo;](../docs/index.md#matching-patterns-and-keywords-with-hears)

### Responding to Events

Bots can respond to non-verbal events as well, like when a new user joins a channel, a file gets uploaded, or a button gets clicked. These events are handled using an event handling pattern that should look familiar. Most events in Botkit can be replied to like normal messages.

```
controller.on('channel_join', async (bot, message) => {

  await bot.reply(message,'Welcome to the channel!');

});
```

[See a full list of events and more information about handling them &rsaquo;](https://botkit.ai/docs/core.html#receiving-messages-and-events)

### Middleware

In addition to taking direct action in response to a certain message or type of event, Botkit can also take passive action on messages as they move through the application using middlewares. Middleware functions work by changing messages, adding new fields, firing alternate events, and modifying or overriding the behavior of Botkit's core features.

Middleware can be used to adjust how Botkit receives, processes, and sends messages. [Here is a list of available middleware endpoints](https://botkit.ai/docs/readme-pipeline.html).

```
// Log every message received
controller.middleware.receive.use(function(bot, message, next) {

  // log it
  console.log('RECEIVED: ', message);

  // modify the message
  message.logged = true;

  // continue processing the message
  next();

});

// Log every message sent
controller.middleware.send.use(function(bot, message, next) {

  // log it
  console.log('SENT: ', message);

  // modify the message
  message.logged = true;

  // continue processing the message
  next();

});
```
## [Change Log](https://github.com/howdyai/botkit/blob/master/changelog.md)