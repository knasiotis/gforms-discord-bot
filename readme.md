# Personal changes for specific usage
My fork includes the following differences/improvements

Bot does not require !start to begin (it is possible start the script on system boot)

- Bot now sorts the form so that it definitely posts the latest messages (The bot could be fooled by someone changing the sort order manually)
- Fixed some exceptions and updated dependencies


## gforms-discord-bot

This is a simple Discord bot intended to monitor and report on incoming responses from Google Forms through its Google Sheets integration. It regularly checks for new rows in the responses spreadsheet, and posts them on Discord. It's well commented and minimalistic, so feel free to adapt it to your own needs!

# Usage:

- Use the **!start** command to make the bot start reading the sheet and post regular updates.
- Alternatively, use the **!start N** command where **N** is the row number you want it to start reading from.
- Use the **!stop** command to make the bot stop posting updates. The bot has a cache that remembers the last row it posted, so you don't have to specify a number after the first run if you just want it to continue where it left off.
- *OPTIONAL*: Use the **!random** command to enable users to get a random response.

<img src="https://i.imgur.com/CfbnBt9.png"/>

## Deploying this bot:

**Requirements**: Make sure to have both Python3 and pip3 installed on your computer/wherever you're running this bot from, as well as git.
I recommend using a Linux VM with Ubuntu if using Windows. If you're using Ubuntu and starting from scratch, execute:

~~~sh
$ sudo apt-get install python3 python3-pip git
~~~

### Clone this repository and enter it using a command-line

Execute the following command to clone out this repository:

~~~sh
$ git clone https://github.com/Fireblend/gforms-discord-bot.git
$ cd gforms-discord-bot
~~~

### Install required Python Packages and run the app

It is recommended you use a virtual environment, but it is not required. Virtual Environments are independent groups of Python libraries, one for each project. Packages installed for one project will not affect other projects or the operating system’s packages. If you want to use a Virtual Environment, install the python3-venv package and activate the environment. If not, skip the following commands:

~~~sh
$ sudo apt-get install python3-venv
$ python3 -m venv venv
$ . venv/bin/activate
~~~

Now install the requirements for the app (they should be installed in the venv directory if you're using a virtual env, or on the Python install path if not):

~~~sh
$ pip3 install -r requirements.txt
~~~

## Setup the bot:

You'll need:

- A Google **credentials.json** file you can download from: https://developers.google.com/sheets/api/quickstart/python. Place it in the same directory as the **bot-template.py** file.
- A **Google Sheets ID** and the **name of the sheet** you want to pull data from. The ID is found in the sheet's URL.
- A **Discord bot token**. You can get one by creating an application here: https://discordapp.com/developers/applications/ and then adding a bot to it.

Once you've got those 3 last values, paste them at the top of the **bot-template.py** file.

At this point you can also set up any role/channels restriction for the bot that you'd like or enable random functionality, by editing the values right underneath where those IDs and tokens were placed. Use lowercase letters for both roles and channels you'd like to restrict bot usage to.

You're free to modify the code to fit your needs. Crucially, you probably need to modify the **format_row(...)** and **format_random(...)** near the beginning of the bot script.

## Running the bot:

To run the bot, just execute the script from the command line:

~~~sh
$ python3 app.py
~~~

### Invite to a Discord server and use:

Go to the application dashboard on Discord, and copy the application's **Client ID**, then insert it into this URL:
https://discordapp.com/oauth2/authorize?client_id=INSERT_CLIENT_ID_HERE&scope=bot

Then just enter the URL and invite the bot to your server :)
