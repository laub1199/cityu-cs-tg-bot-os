# CityU CS Telegram Bot

## Description
An open source Telegram bot project for CityU CS Telegram Group

## Table of Contents
- [File Structure](#file-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
  - [Run with Python](#run-with-python)
  - [Docker Support](#docker-support)
- [Roadmap & Todos](#roadmap-&-todos)
  - [Features](#features)
    - [Contribution Guide](#contribution-guide)
    - [Deployment Announcer](#deployment-announcer)
    - [Polling Feature](#polling-feature)
    - [Instagram Post Fetcher](#instagram-post-fetcher)
    - [Lyrics Guesser](#lyrics-guesser)
  - [Others](#others)
    - [README Refinement](#readme-refinement)
- [Usage](#usage)
  - [Starting](#starting)
  - [New Functionality](#new-functionality)
  - [Code Style and Naming Convention](#code-style-and-naming-convention)
  - [For new source files](#for-new-source-files)
- [Contributing](#contributing)

## File Structure
```
.
├── README.md
├── bot.py
├── app
│  ├── commands                     # Commands folder
│  │  ├── hub.py                    # Single interface for all commands
│  │  └── ...
│  ├── conversations                # Conversation handlers folder
│  │  ├── hub.py                    # Single interface for all conversations
│  │  └── ...
│  ├── message_handlers             # Message handlers folder
│  │  ├── hub.py                    # Single interface for all message handlers
│  │  └── ...
│  ├── modules                      # Modules folder
│  │  ├── hub.py                    # Single interface for all modules
│  │  ├── utils.py                  # Utility functions
│  │  └── ...
│  ├── txts                         # Texts folder for prompt messages
│  │  ├── help.txt                  # Help text shown with /help
│  │  ├── pin.txt                   # Pin text shown with /pin
│  │  ├── start.txt                 # Start text shown with /start
│  │  ├── updaet_log.txt            # Update log text shown with /update_log
│  │  └── ...
│  ├── main.py                      # Start point of the bot
│  └── requirements.txt             # Requirements for python packages
└── ...
```

## Prerequisites
- [Docker](https://www.docker.com/)

## Installation
1. Clone the repository
2. Copy `/app/.env.dev` to `/app/.env`

### Run with Python
1. Run `pip install -r /app/requirements.txt` to install all the required packages in your local environment
2. Run `python /app/main.py` to start the bot for testing

### Docker Support
1. To remove the built image, run:
```shell
docker rmi cityu-cs-tg-bot:latest
```
2. To remove the built container, run:
```shell
docker rm $(docker stop $(docker ps -a -q --filter ancestor=cityu-cs-tg-bot --format="{{.ID}}"))
```
3. To build the docker image, run:
```shell
docker build -t cityu-cs-tg-bot:latest .
```
4. To run the docker container, run:
```shell
docker run -d --name cityu-cs-tg-bot cityu-cs-tg-bot
```

## Roadmap

### Features

#### Contribution Guide

#### Description
Show the contributors of the bot and prompt the Github link of the bot.

#### Possible Commands
- `/contribute` - Prompt the Github link of the bot.
- `/contribution` - Show the contributors of the bot

#### Deployment Announcer

#### Description
Show the version and potentially the latest update log of the bot when the bot is newly deployed.

#### Polling Feature

##### Description
Polling system that allow users to create polls and vote for polls.

##### Possible Commands
- `/poll` - Create a new poll
- `/vote` - Vote for a poll
- `/endpoll` - End a poll
- `/result` - Show the result of a poll

#### Instagram Post Fetcher

##### Description
Fetch the latest post from CityU related Instagram account and send it to the group when there is a new post.

##### Possible Commands
- `/insta` - Fetch the latest post from CityU related Instagram account
- `/insta <account>` - Fetch the latest post from the specified account

##### Accounts
- [cityucss_binary01](https://www.instagram.com/cityucss_binary01/)
- [hkcityu.info](https://www.instagram.com/hkcityu.info/)
- [cityusu](https://www.instagram.com/cityusu/)
- [cityusu.edb](https://www.instagram.com/cityusu.edb/)
- [cityusucouncil](https://www.instagram.com/cityusucouncil/)
- [cityusu.cbc](https://www.instagram.com/cityusu.cbc/)
- [cityusu_welfare](https://www.instagram.com/cityusu_welfare/)

#### Lyrics Guesser

##### Description
Request the lyrics of a song from the bot, allowing users to guess the song by replying the lyrics message.

##### Possible Commands
- `/lyrics` - Request the lyrics of a song from the bot

### Others

#### README Refinement

##### Description
Refine the README.md file sections with better readability and align the text style.

## Usage

### Starting
For developing, a local environment is recommended. A testing bot is available at [@test_citycs_bot](https://t.me/test_citycs_bot) with the token provided. For production, a docker container is recommended.

### New Functionality
Adding new commands, conversations, message handlers, or modules, please always place them in the corresponding folder and import them to the `hub.py` file.
```python
# e.g. in app/commands/hub.py
from .cmd_crypto import *
```
Those file should then be imported to the `main.py` file or other files by importing through the `hub.py` file.
<br/>
When a long paragraph of message is needed to be texts, please place them in the `txts` folder.

### Code Style and Naming Convention

#### Naming Convention for Files
Please also follow the naming convention of the files:
- Commands: `cmd_` + `<command_name>`
```
e.g. app/commands/cmd_crypto.py
```
- Conversations: `conv_` + `<conversation_name>`
```
e.g. app/conversations/conv_source.py
```
- Message Handlers: `msg_` + `<message_handler_name>`
```
e.g. app/message_handlers/msg_source.py
```
- Modules: `module_` + `<module_name>`
```
e.g. app/modules/module_utils.py
```

#### Naming Convention for Functions
Please also follow the naming convention of the functions:
use `snake_case` for functions and variables
```python
def get_crypto_price():
    student_id = 12345678
    pass
```

#### For new source files
Please contact the [author](https://t.me/xiii_xiii_xx) of the project through Telegram to add new source files to the project.

## Contributing

### General Steps
Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a pull request

For any question, please contact the [author](https://t.me/xiii_xiii_xx) through Telegram.
