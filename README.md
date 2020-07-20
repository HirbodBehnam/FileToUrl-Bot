# File To Url Bot
A Telegram bot to convert files to URL without disk usage

## Why this?
* No disk usage: Only file IDs are saved and files are streamed to client when they request it. Also links are generated as soon as the user gives the file to bot.
* Easy to use: Just give the URL that bot gives you to the download manager and let it download the file.
* Private use (optional): The bot only responds to your commands and not anyone else.
## Why not this?
* ~~No download resume support: I tried to create resume support but I'm a noob and I couldn't create it.~~ Now the it supports resumes but if you resume the download, it will be super slow because I had to reduce the request size to 4KB from 64KB. For some reasons (that I don't know) if I choose a bigger chunk size, in about half of conditions, it gives me an error about ` An invalid limit was provided`.
* High CPU usage: This is not because of bad programming, the Telegram encryption is a bit heavy and if a lot of users start to download some files, your server will suffer from high CPU usage.

## How to install?
I have tested this bot on Python 3.6.9. I'm not sure if it works on older versions or not.

First install some pip packages:
```
pip3 install aiohttp telethon cryptg
```
Now clone this repository and edit `main.py` file. Change `Domain`, `Port`, `api_id`, `api_hash` and `bot_token`.

If you want to make a public bot, remove these two lines from `main.py`:
```python
if event.message.from_id not in admins:
	return
```
If you want to create a private bot, add your id (which is an int) to `admins` set.

If you want to use TLS webserver, add `ssl_context` to `web._run_app(app, port=Port)`. [More Info](https://docs.aiohttp.org/en/stable/web_reference.html#aiohttp.web.run_app)

Now simply run `main.py` with python.
