---
layout: project
title: DumpBot
description: Discord bot of the Dumppi Ry
date: 2024-08-24
repo: https://github.com/Dumppiry/dumpbot
technologies:
  - Python
  - Discord.py
  - Sanity Webhooks
---

DumpBot is our discord bot that is added to the DumppiRy discord server. Currently the bot has only one functionality and that is to post notifications about new and modified events to our Discord.

## How it works?

The bot is build using [Discord.py](https://discordpy.readthedocs.io/en/stable/). It has been added to Dumppi Ry discord server.

## Features

### Bot Feed

In the discord we have a channel called `bot-feed`. To this channel, we can post json data that the bot will try to parse based on the `type` field. Data to be parsed must be provided in the `data` field. See Discords [documentation](https://discord.com/developers/docs/resources/webhook) for how to format data for Discords webhooks. Our json to bot-feed needs to be provided in the message content and message should not contain anything else.

#### bot-feed json format

|  Key   | Value                                        |
| :----: | :------------------------------------------- |
| `type` | Type of the data. See the Types table below. |
| `data` | Data for the type                            |

Example structure:

```json
{
  "type": "event_feed",
  "data": {
    "modified": "",
    "event": {
      "title": "Test",
      "url": "https://dumppi.fi/tapahtumat/test",
      "image_url": "",
      "description": "Test event",
      "price": 0,
      "start_date": "2024-11-16T11:19:00.000Z",
      "ticket_sale_start_date": "",
      "ticket_link": "",
      "footer": "Powered by Sanity & Engineered by Ben_P"
    },
    "post_to": 1274286712658591766
  }
}
```

#### Types

|     Type     | Description                                                                        |
| :----------: | :--------------------------------------------------------------------------------- |
| `event_feed` | Data will be parsed in to a event notification and posted to `tapahtumat` channel. |

### Event notifications

Event notifications feature is build using Sanitys webhooks, json data posted to `bot-feed` channel. JSON sent with the webhook is formatted in the [Sanity](https://sanity.io/manage). For changes to webhook, please contact current webmaster of Dumppi Ry.

#### Data

Event notifications are parsed from the bot-feed messages that have type of `event_feed`. The `data` field must be like bellow.

```json
{
  "type": "event_feed",
  "data": {
    "modified": "",
    "event": {
      "title": "Test",
      "url": "https://dumppi.fi/tapahtumat/test",
      "image_url": "",
      "description": "Test event",
      "price": 0,
      "start_date": "2024-11-16T11:19:00.000Z",
      "ticket_sale_start_date": "",
      "ticket_link": "",
      "footer": "Powered by Sanity & Engineered by Ben_P"
    },
    "post_to": 1274286712658591766
  }
}
```

|           Type           | Description                                                                                                                                                                                                                                                                                                                                                                        |
| :----------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|          `type`          | Must be `event_feed`.                                                                                                                                                                                                                                                                                                                                                              |
|          `data`          | Must contain all of the fields from the example above.                                                                                                                                                                                                                                                                                                                             |
|        `modified`        | What property of the event was modified. If event was created use empty string. Possible values: {::nomarkdown} </br> {:/}- `""` If event was created.{::nomarkdown} </br> {:/}- `"price"` If price was changed.{::nomarkdown} </br> {:/}- `"ticket_sale"` If ticket price or ticket saleStartDate was changed.{::nomarkdown} </br> {:/}- `"date"` If event startDate was changed. |
|         `event`          | Data containing information about event. See the format above.                                                                                                                                                                                                                                                                                                                     |
|         `title`          | Title of the event                                                                                                                                                                                                                                                                                                                                                                 |
|          `url`           | Url of the event in dumppi.fi                                                                                                                                                                                                                                                                                                                                                      |
|       `image_url`        | Url for image. Use empty string for no image.                                                                                                                                                                                                                                                                                                                                      |
|      `description`       | Description of the event. Keep it short because Discord has 2000 character limit.                                                                                                                                                                                                                                                                                                  |
|         `price`          | Price of the event. 0 if free.                                                                                                                                                                                                                                                                                                                                                     |
|       `start_date`       | Start date of the event in ISO-8601 format.                                                                                                                                                                                                                                                                                                                                        |
| `ticket_sale_start_date` | Start time of the events ticket sales in ISO-8601 format.                                                                                                                                                                                                                                                                                                                          |
|      `ticket_link`       | Link to where tickets are sold.                                                                                                                                                                                                                                                                                                                                                    |
|         `footer`         | Footer for the Discords embed.                                                                                                                                                                                                                                                                                                                                                     |
|        `post_to`         | Channel ID of a discord channel where the bot posts the message.                                                                                                                                                                                                                                                                                                                   |

## Hosting

Currently DumpBot is hosted by webmaster on his servers. This will probably change in the future. When a new version is wanted to be deployed, contact the webmaster.

## Development

Instructions for how to get going on development can be found in the repositorys README.md.
