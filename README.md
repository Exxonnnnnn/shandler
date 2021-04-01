# What is this package about..?

This is a package is a command handler for discord's new **Slash Commands**. Using this package you can send/edit/delete an interaction response. You can ask for help in our [Support server](https://discord.gg/tMWmEJFq4m).

## Table of Contents
* [Installation](#Installation)
* [Basic-usage](#Basic-usage)
* [Interaction object](#Interaction-object)

## Installation

```
npm i shandler
```

## Basic usage
#### Setup
**Free advice:** Please don't copy paste.
```js
//index.js
const Shandler = require('shandler')
const Discord = require('discord.js')

const client = new Discord.Client()

const options = {
    commandsDir: './commands', // commands folder path (required)
    showLogs: 'extra', // "extra"|"normal"|null (default: "extra")
}

const handler = new Shandler(client, options)

```
#### Let's make a command file.
```js
//ping.js
module.exports ={
    name: 'ping',// if (!name) command name == filename.
    description: 'Is this unusual?',//Default: "An awesome command..!"
    options:[]//We will cover this in the next part
    guilds : [] /*This is for guild specific command registration
    if this is empty, this command will be registered globally*/
    async run({interaction, client}){
        interaction.send("My ping is " + client.ws.ping + "ms")
    }
}
```
## Command Options
You might've thought what all we can do with the `options`. Well you can refer [here](https://discord.com/developers/docs/interactions/slash-commands#applicationcommandoption)
## Interaction object
Unlike discord's normal interaction object shandler's interaction object has more properties and disscord.js methods. 
```js
{
    "type": 2,
    "token": "A_UNIQUE_TOKEN",
    "member": [discord.js guildmember object],
    "id": "786008729715212338",
    "guild": [discord.js guild object],
    "data": {
        "options": [{
            "name": "cardname",
            "value": "The Gitrog Monster"
        }],
        "name": "cardsearch",
        "id": "771825006014889984"
    },
    "channel": [discord.js channel object]
}
```

### [Discord.js Guildmember object](https://discord.js.org/#/docs/main/stable/class/GuildMember)

```js
//Guildmember object
{
    bannable:'',
    client:'',
    deleted:'',
    displayColor:'',
    displayHecColor:'',
    displayName:'',
    guild:'',
    id:'',
    joinedAt:'',
    joinedTimestamp:'',
    kickable:'',
    lastMessage:'',
    lastMessageChannelID:'',
    lastMessageID:'',
    manageable:'',
    nickname:'',
    partial:'',
    permissions:'',
    premiumSince:'',
    premiumSinceTimestamp:'',
    presence:'',
    roles:'',
    user:'',
    voice:''
}
```
Methods | Short description
-------- | -----
[ban](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=ban)
[createDM](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=createDM)
[deleteDM](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=deleteDM)
[edit](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=edit)
[fetch](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=fetch)
[hasPermission](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=hasPermission)
[kick](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=kick)
[permissionsIn](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=permissionsIn)
[send](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=send)
[setNickname](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=setNickname)
[toString](https://discord.js.org/#/docs/main/stable/class/GuildMember?scrollTo=toString)
### [Discord.js Guild object](https://discord.js.org/#/docs/main/stable/class/Guild)


```js
//Guild object
{
    "members":[
    "708965864128380960",
    "756393473430519849"
    ],
    "channels":[
        "796551553325989898",
        "804370936118771763"
        ],
        "roles":[
    "786544962451144736",
    "795978550880239626"
    ],
    "deleted":false,
    "id":"786544962451144736",
    "shardID":0,
    "name":"Exim Studio",
    "icon":"ff66b965fe166d8988b231bdc3b41afd",
    "splash":null,
    "discoverySplash":null,
    "region":"india",
    "memberCount":43,
    "large":false,
    "features":[
        "NEWS",
        "WELCOME_SCREEN_ENABLED",
        "COMMUNITY",
        "PREVIEW_ENABLED",
        "MEMBER_VERIFICATION_GATE_ENABLED"
        ],
        "applicationID":null,
        "afkTimeout":300,
        "afkChannelID":null,
        "systemChannelID":"796423068557115392",
        "premiumTier":0,
        "premiumSubscriptionCount":0,
        "verificationLevel":"MEDIUM",
        "explicitContentFilter":"ALL_MEMBERS",
        "mfaLevel":0,
        "joinedTimestamp":1614255169231,
        "defaultMessageNotifications":"MENTIONS",
        "systemChannelFlags":1,
        "maximumMembers":100000,
        "maximumPresences":null,
        "approximateMemberCount":null,
        "approximatePresenceCount":null,
        "vanityURLCode":null,
        "vanityURLUses":null,
        "description":null,
        "banner":null,
        "rulesChannelID":"796246319039381564",
        "publicUpdatesChannelID":"804370936118771763",
        "preferredLocale":"en-US",
        "ownerID":"764288293167693874",
        "emojis":[
            "805398954430562315",
            "805398954976083968"
            ],
            "createdTimestamp":1607597332347,
            "nameAcronym":"ES",
            "iconURL":"https://cdn.discordapp.com/icons/786544962451144736/ff66b965fe166d8988b231bdc3b41afd.webp%22,%22splashURL%22:null,%22discoverySplashURL%22:null,%22bannerURL%22:null%7D"
}
```
