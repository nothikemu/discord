<div align="center">

# 🤖 DiscordBot Template

**A fully-featured, production-ready Discord bot starter kit — no fluff, just functions.**

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=flat-square&logo=python)](https://www.python.org/)
[![discord.py](https://img.shields.io/badge/discord.py-2.x-5865F2?style=flat-square&logo=discord)](https://discordpy.readthedocs.io/)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![Commands](https://img.shields.io/badge/Commands-68%2B-orange?style=flat-square)]()

> Stop stitching together tutorials. This template gives you **68+ working commands** out of the box — full moderation suite, utility tools, fun commands, a giveaway system, and clean mod-logging — all in one readable file you can extend in minutes.

[Quick Start](#-quick-start) · [Commands](#-command-reference) · [24/7 Hosting](#-running-247) · [Configuration](#-configuration)

</div>

---

## 📦 What You Get

This is not a bare-bones "ping pong" starter. Drop this into your server and your mods can immediately kick, ban, mute, warn, purge, lock channels, run giveaways, and more — without touching any configuration beyond your token.

- **30 general commands** — polls, reminders, tags, calculators, dice rolls, 8-ball, coin flips, Morse code, and more
- **30 moderation commands** — full kick/ban/mute/warn pipeline with persistent per-user logs, softban, tempban, massban, slowmode, channel lock/hide, voice controls, and auto mod-log
- **8 fun/utility commands** — giveaways with auto-draw, sniping, leaderboards, command usage stats
- **3 owner-only commands** — shutdown, DM a user, set bot status
- **Automatic events** — join/leave messages, AFK detection, command error handling, snipe tracking
- **Zero database required** — everything runs in memory; swap in SQLite or Postgres when you're ready to scale

---

## 🧾 Product Description

> **DiscordBot Template** is an open-source Discord bot starter written in Python, designed for server owners who want a fully functional bot on day one without building from scratch. It ships with a complete moderation toolkit, quality-of-life utilities, and a clean, well-commented codebase that any Python developer can extend. Whether you're running a gaming community, a study server, or a business hub, this template gives your moderators real tools and your members a better experience — immediately.

---

## 📋 Table of Contents

1. [Requirements](#-requirements)
2. [Creating Your Bot on Discord](#-creating-your-bot-on-discord)
3. [Giving the Bot Permissions](#-giving-the-bot-permissions)
4. [Installation](#-installation)
5. [Configuration](#-configuration)
6. [Running the Bot](#-running-the-bot)
7. [Running 24/7](#-running-247)
8. [Command Reference](#-command-reference)
9. [How to Extend the Bot](#-how-to-extend-the-bot)
10. [Troubleshooting](#-troubleshooting)

---

## ✅ Requirements

| Requirement | Version |
|---|---|
| Python | 3.10 or higher |
| discord.py | 2.x |
| Operating System | Windows, macOS, or Linux |

---

## 🏗 Creating Your Bot on Discord

Follow these steps exactly to create a bot account in Discord's developer portal.

**Step 1 — Open the Developer Portal**

Go to [https://discord.com/developers/applications](https://discord.com/developers/applications) and log in with your Discord account.

**Step 2 — Create a New Application**

Click **New Application** in the top-right corner. Give it a name (this becomes the bot's display name), then click **Create**.

**Step 3 — Add a Bot User**

In the left sidebar, click **Bot**. Then click **Add Bot** → **Yes, do it!**

You will now see your bot's username and a **Token** section. This token is your bot's password — keep it private and never share it.

**Step 4 — Copy Your Token**

Click **Reset Token**, confirm, then copy the token that appears. You will paste this into the code shortly.

> ⚠️ **If your token is ever exposed publicly** (e.g. pushed to GitHub), immediately click **Reset Token** to invalidate the old one.

**Step 5 — Enable Privileged Intents**

Still on the Bot page, scroll down to **Privileged Gateway Intents** and enable all three:

- ✅ Presence Intent
- ✅ Server Members Intent
- ✅ Message Content Intent

Click **Save Changes**.

---

## 🔐 Giving the Bot Permissions

**Step 1 — Go to OAuth2 → URL Generator**

In the left sidebar, click **OAuth2**, then **URL Generator**.

**Step 2 — Select Scopes**

Under **Scopes**, check:
- ✅ `bot`
- ✅ `applications.commands`

**Step 3 — Select Bot Permissions**

Under **Bot Permissions**, check everything you want. For full functionality, select:

| Permission | Why |
|---|---|
| Administrator | Grants all permissions at once (easiest for testing) |
| *— OR select individually:* | |
| Kick Members | `!kick` command |
| Ban Members | `!ban`, `!unban`, `!tempban`, `!massban`, `!softban` |
| Manage Roles | `!mute`, `!unmute`, `!role`, `!unrole` |
| Manage Channels | `!slowmode`, `!lock`, `!unlock`, `!hidechannel`, `!showchannel`, `!clonevchan` |
| Manage Messages | `!purge`, `!warn`, `!say`, `!prune` |
| Manage Nicknames | `!nickname` |
| Move Members | `!move` |
| Mute Members | `!servermute`, `!serverunmute` |
| Deafen Members | `!deafen`, `!undeafen` |
| Send Messages | Respond to commands |
| Read Message History | `!snipe`, `!purge` |
| Embed Links | Embed-formatted replies |
| Add Reactions | `!poll`, `!giveaway` |

**Step 4 — Invite the Bot**

Scroll down. Copy the generated URL and paste it into your browser. Select the server you want to add it to, then click **Authorize**.

---

## 💻 Installation

**Step 1 — Clone or download the code**

```bash
git clone https://github.com/yourusername/discordbot-template.git
cd discordbot-template
```

Or just download `discord_bot.py` directly.

**Step 2 — Install Python**

Download Python 3.10+ from [https://www.python.org/downloads/](https://www.python.org/downloads/).

During installation on Windows, check **"Add Python to PATH"**.

Verify your install:
```bash
python --version
# Expected: Python 3.10.x or higher
```

**Step 3 — Install discord.py**

```bash
pip install discord.py
```

For voice support (not required by this bot):
```bash
pip install "discord.py[voice]"
```

**Step 4 — Verify the install**

```bash
python -c "import discord; print(discord.__version__)"
# Expected: 2.x.x
```

---

## ⚙️ Configuration

Open `discord_bot.py` in any text editor. Near the top you will find the config block:

```python
# ─── CONFIG ───────────────────────────────────────────────────────────────────
BOT_TOKEN         = "YOUR_BOT_TOKEN_HERE"   # Paste your token here
PREFIX            = "!"                      # Change the command prefix if you want
MOD_LOG_CHANNEL_ID = 0                       # Replace with your mod-log channel's ID
OWNER_ID           = 0                       # Replace with your own Discord user ID
```

**BOT_TOKEN** — Paste the token you copied from the Developer Portal.

**PREFIX** — The character users type before commands. Default is `!`. You can change it to `?`, `>`, or anything you like.

**MOD_LOG_CHANNEL_ID** — The ID of the channel where moderation actions get logged. To get a channel ID: enable Developer Mode in Discord (Settings → Advanced → Developer Mode), then right-click the channel and click **Copy Channel ID**.

**OWNER_ID** — Your personal Discord user ID. Right-click your own name in Discord and click **Copy User ID**. This unlocks owner-only commands like `!shutdown`.

### Using Environment Variables (Recommended for Security)

Instead of hardcoding your token, use an environment variable:

```python
import os
BOT_TOKEN = os.environ.get("DISCORD_TOKEN", "YOUR_BOT_TOKEN_HERE")
```

Then set the variable in your terminal before running:

```bash
# Linux / macOS
export DISCORD_TOKEN="your_actual_token_here"

# Windows Command Prompt
set DISCORD_TOKEN=your_actual_token_here

# Windows PowerShell
$env:DISCORD_TOKEN="your_actual_token_here"
```

---

## ▶️ Running the Bot

Once configured, run the bot with:

```bash
python discord_bot.py
```

If everything is set up correctly, you will see:

```
✅  Logged in as YourBot#1234 (ID: 123456789012345678)
    Serving 1 guilds | 50 members
```

The bot is now online. Go to your Discord server and type `!ping` to verify.

To stop the bot, press `Ctrl + C` in the terminal.

---

## 🌐 Running 24/7

Running `python discord_bot.py` in a terminal only keeps the bot alive while that terminal is open. For always-on uptime, choose one of the options below.

---

### ✅ Free Options

#### Option A — Railway (Easiest Free Tier)

[Railway](https://railway.app) gives you a free container with enough hours for a small bot.

1. Create a free account at [railway.app](https://railway.app)
2. Click **New Project** → **Deploy from GitHub Repo**
3. Connect your GitHub and select your repo
4. Go to **Variables** and add `DISCORD_TOKEN` = your token
5. Railway auto-detects Python and runs your bot

Make sure your repo includes a `requirements.txt`:
```
discord.py>=2.0.0
```

#### Option B — Render (Free Tier)

1. Create an account at [render.com](https://render.com)
2. Click **New** → **Web Service** → connect your GitHub repo
3. Set **Build Command**: `pip install -r requirements.txt`
4. Set **Start Command**: `python discord_bot.py`
5. Add environment variable `DISCORD_TOKEN`
6. Deploy

> Note: Render's free tier spins down after inactivity. Use a service like [UptimeRobot](https://uptimerobot.com) to ping it every 5 minutes.

#### Option C — Oracle Cloud Free Tier (Always Free VM)

Oracle gives a permanently free ARM VM with 4 CPUs and 24 GB RAM — more than enough for a bot.

1. Sign up at [cloud.oracle.com](https://cloud.oracle.com) (requires a credit card for verification, but the Always Free tier is never charged)
2. Create an **Always Free** VM instance (Ampere A1 shape)
3. SSH into the VM and follow the Linux instructions below

#### Option D — Your Own PC (Free, but PC must stay on)

Use a process manager to keep it running in the background:

```bash
# Linux/macOS — use screen
screen -S discordbot
python discord_bot.py
# Press Ctrl+A then D to detach
# Reattach with: screen -r discordbot
```

---

### 💳 Paid Options

#### Option A — VPS (Best Value, ~$4–$6/month)

A Virtual Private Server gives you full control and reliable uptime.

Recommended providers:
- [DigitalOcean](https://digitalocean.com) — $4/mo Droplet
- [Vultr](https://vultr.com) — $2.50/mo instance
- [Linode (Akamai)](https://linode.com) — $5/mo Nanode

Once you have a Linux VPS, SSH in and run:

```bash
# Install Python
sudo apt update && sudo apt install python3 python3-pip -y

# Upload your bot files (or git clone)
git clone https://github.com/yourusername/discordbot-template.git
cd discordbot-template
pip3 install discord.py

# Run with systemd (auto-restarts on crash/reboot)
sudo nano /etc/systemd/system/discordbot.service
```

Paste this into the file (update paths as needed):

```ini
[Unit]
Description=Discord Bot
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/home/ubuntu/discordbot-template
ExecStart=/usr/bin/python3 /home/ubuntu/discordbot-template/discord_bot.py
Restart=always
RestartSec=10
Environment=DISCORD_TOKEN=your_token_here

[Install]
WantedBy=multi-user.target
```

Then enable it:

```bash
sudo systemctl daemon-reload
sudo systemctl enable discordbot
sudo systemctl start discordbot
sudo systemctl status discordbot  # Check it's running
```

#### Option B — Heroku (~$5/month)

1. Install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
2. Create a `Procfile` in your project folder containing:
   ```
   worker: python discord_bot.py
   ```
3. Deploy:
   ```bash
   heroku login
   heroku create your-bot-name
   heroku config:set DISCORD_TOKEN=your_token_here
   git push heroku main
   heroku ps:scale worker=1
   ```

#### Option C — AWS / Google Cloud / Azure

All three major cloud providers offer compute instances. Google Cloud and AWS both have 12-month free trials with credit included. After the trial, a small instance runs ~$5–$10/month.

---

## 📖 Command Reference

All commands use the `!` prefix by default. Anything in `<angle brackets>` is required; `[square brackets]` are optional.

---

### 🔧 General Commands

| Command | Usage | Description |
|---|---|---|
| `help` | `!help [category]` | Show the help menu or details for a category |
| `ping` | `!ping` | Check bot latency |
| `info` | `!info` | Show bot information |
| `avatar` | `!avatar [@user]` | Display a user's avatar |
| `serverinfo` | `!serverinfo` | Display server details |
| `uptime` | `!uptime` | How long the bot has been running |
| `invite` | `!invite` | Get the bot's invite link |
| `stats` | `!stats` | Runtime stats (guilds, users, latency) |
| `roll` | `!roll [NdS]` | Roll dice — e.g. `!roll 2d20` (default: 1d6) |
| `flip` | `!flip` | Flip a coin |
| `8ball` | `!8ball <question>` | Ask the magic 8-ball |
| `say` | `!say <text>` | Make the bot say something (deletes your message) |
| `embed` | `!embed "Title" <description>` | Send a custom embed |
| `announce` | `!announce <#channel> <message>` | Send an announcement to a channel |
| `poll` | `!poll "Question" opt1 opt2 ...` | Create a reaction poll (up to 10 options) |
| `afk` | `!afk [reason]` | Set your AFK status; auto-clears when you chat |
| `time` | `!time` | Show the current UTC time |
| `remind` | `!remind <N> <s/m/h> <message>` | Set a personal reminder |
| `tag` | `!tag <name> [content]` | Save or retrieve a tag |
| `tags` | `!tags` | List all saved tags |
| `deltag` | `!deltag <name>` | Delete a tag |
| `calc` | `!calc <expression>` | Evaluate a math expression |
| `choose` | `!choose <opt1> <opt2> ...` | Randomly pick from options |
| `reverse` | `!reverse <text>` | Reverse a string |
| `wordcount` | `!wordcount <text>` | Count words and characters |
| `morse` | `!morse <text>` | Convert text to Morse code |
| `ascii` | `!ascii <text>` | Show ASCII values of characters |
| `usercount` | `!usercount` | Show human/bot/total member count |
| `time` | `!time` | Current UTC time |

---

### 🛡 Moderation Commands

All moderation commands require the corresponding Discord permission. Actions are automatically logged to your mod-log channel.

| Command | Usage | Required Permission | Description |
|---|---|---|---|
| `kick` | `!kick <@user> [reason]` | Kick Members | Kick a member from the server |
| `ban` | `!ban <@user> [reason]` | Ban Members | Permanently ban a member |
| `unban` | `!unban <user_id> [reason]` | Ban Members | Unban a user by their ID |
| `softban` | `!softban <@user> [reason]` | Ban Members | Ban + unban to delete 7 days of messages |
| `tempban` | `!tempban <@user> <N> <h/d> [reason]` | Ban Members | Temporarily ban for N hours or days |
| `massban` | `!massban <id1> <id2> ...` | Ban Members | Ban multiple users by ID at once |
| `mute` | `!mute <@user> [reason]` | Manage Roles | Mute a member (creates "Muted" role if missing) |
| `unmute` | `!unmute <@user>` | Manage Roles | Remove the mute from a member |
| `warn` | `!warn <@user> [reason]` | Manage Messages | Issue a warning (tracked per user) |
| `warnings` | `!warnings <@user>` | Manage Messages | View all warnings for a member |
| `clearwarn` | `!clearwarn <@user>` | Manage Messages | Clear all warnings for a member |
| `note` | `!note <@user> <text>` | Manage Messages | Add a private staff note to a member |
| `notes` | `!notes <@user>` | Manage Messages | View all staff notes for a member |
| `purge` | `!purge <amount>` | Manage Messages | Bulk-delete messages from a channel |
| `prune` | `!prune <@user> [amount]` | Manage Messages | Delete a specific user's recent messages |
| `slowmode` | `!slowmode <seconds>` | Manage Channels | Set channel slowmode (0 to disable) |
| `lock` | `!lock [#channel]` | Manage Channels | Prevent members from sending messages |
| `unlock` | `!unlock [#channel]` | Manage Channels | Restore message permissions |
| `hidechannel` | `!hidechannel [#channel]` | Manage Channels | Hide a channel from all members |
| `showchannel` | `!showchannel [#channel]` | Manage Channels | Make a hidden channel visible again |
| `clonevchan` | `!clonevchan <#voicechannel>` | Manage Channels | Clone a voice channel |
| `nickname` | `!nickname <@user> [new nick]` | Manage Nicknames | Change or reset a member's nickname |
| `role` | `!role <@user> <role name>` | Manage Roles | Give a role to a member |
| `unrole` | `!unrole <@user> <role name>` | Manage Roles | Remove a role from a member |
| `move` | `!move <@user> <#voicechannel>` | Move Members | Move a member to a voice channel |
| `deafen` | `!deafen <@user>` | Deafen Members | Server-deafen a member |
| `undeafen` | `!undeafen <@user>` | Deafen Members | Remove server-deafen |
| `servermute` | `!servermute <@user>` | Mute Members | Server-mute a member in voice |
| `serverunmute` | `!serverunmute <@user>` | Mute Members | Remove server-mute |

---

### 🎉 Fun / Utility Commands

| Command | Usage | Description |
|---|---|---|
| `whois` | `!whois [@user]` | Detailed profile: ID, roles, join date, status, warnings |
| `joined` | `!joined [@user]` | When a member joined the server |
| `botinfo` | `!botinfo` | Full bot stats including guild count, latency, command count |
| `userstats` | `!userstats [@user]` | Quick summary: warnings, notes, AFK, mute status |
| `cmdstats` | `!cmdstats` | Top 10 most-used commands |
| `leaderboard` | `!leaderboard` | Top 10 most-warned members |
| `snipe` | `!snipe` | Show the last deleted message in this channel |
| `giveaway` | `!giveaway <N> <m/h/d> <prize>` | Start a timed giveaway with auto-draw |
| `reroll` | `!reroll <message_id>` | Pick a new winner for a completed giveaway |
| `usercount` | `!usercount` | Human / bot / total count for the server |

---

### 👑 Owner-Only Commands

These commands only work for the user whose ID is set as `OWNER_ID` in the config.

| Command | Usage | Description |
|---|---|---|
| `shutdown` | `!shutdown` | Gracefully shut down the bot |
| `setstatus` | `!setstatus <playing/watching/listening> <text>` | Change the bot's activity status |
| `dm` | `!dm <@user> <message>` | Send a direct message from the bot to any user |

---

## 🧩 How to Extend the Bot

The code is organized in clear sections marked with comments. Adding a new command takes about 5 lines.

### Adding a Basic Command

```python
@bot.command()
async def hello(ctx):
    """Say hello."""
    await ctx.send(f"Hello, {ctx.author.mention}!")
```

### Adding a Command with Arguments

```python
@bot.command()
async def greet(ctx, member: discord.Member, *, message: str = "Hello!"):
    """Greet a member with a custom message."""
    await ctx.send(f"{member.mention} — {message}")
```

### Adding a Moderation Command with Permission Check

```python
@bot.command()
@commands.has_permissions(manage_guild=True)
async def mymodcmd(ctx, member: discord.Member, *, reason: str = "No reason given"):
    """My custom mod command."""
    # Do something to member
    await ctx.send(embed=make_embed("✅ Done", f"Applied to {member}.", discord.Color.green()))
    await log_action(ctx.guild, "My Action", ctx.author, member, reason)
```

### Using the `make_embed` Helper

The bot includes a `make_embed(title, description, color)` helper that builds consistent embeds:

```python
await ctx.send(embed=make_embed("Title", "Description", discord.Color.blue()))
```

### Persistent Storage

By default all data (warnings, tags, notes) lives in Python dictionaries and resets when the bot restarts. To make it permanent, swap the dictionaries for a database:

**SQLite (simple, file-based, no server needed):**
```bash
pip install aiosqlite
```

**PostgreSQL (production-grade):**
```bash
pip install asyncpg
```

### Organizing into Cogs

Once you have more than a dozen commands, consider splitting them into **Cogs** (Discord.py's module system):

```python
# cogs/moderation.py
from discord.ext import commands

class Moderation(commands.Cog):
    def __init__(self, bot):
        self.bot = bot

    @commands.command()
    @commands.has_permissions(kick_members=True)
    async def kick(self, ctx, member: discord.Member, *, reason="No reason"):
        await member.kick(reason=reason)
        await ctx.send(f"Kicked {member}.")

async def setup(bot):
    await bot.add_cog(Moderation(bot))
```

```python
# In discord_bot.py, replace the main block with:
async def main():
    async with bot:
        await bot.load_extension("cogs.moderation")
        await bot.start(BOT_TOKEN)

import asyncio
asyncio.run(main())
```

---

## 🔧 Troubleshooting

**Bot is online but doesn't respond to commands**
- Make sure **Message Content Intent** is enabled in the Developer Portal
- Confirm the bot has **Read Messages** and **Send Messages** permissions in the channel
- Check that your prefix in Discord matches `PREFIX` in the config

**`discord.errors.Forbidden` when using moderation commands**
- The bot's role must be *higher* in the role list than the member you're trying to moderate. Go to Server Settings → Roles and drag the bot's role above member roles.

**`!mute` says it created a Muted role but it doesn't work**
- The bot auto-creates the role but must have permission to edit every channel's permission overrides. Give the bot **Manage Channels** permission, then run `!mute` again.

**`!tempban` doesn't unban after the time expires**
- `tempban` uses `asyncio.sleep`, which means the bot must stay running for the duration. For persistent temp-bans across restarts, store the unban time in a database and check it on `on_ready`.

**Token is invalid**
- Go back to the Developer Portal → Bot → Reset Token. Make sure there are no extra spaces when you paste it.

**ImportError: No module named 'discord'**
- Run `pip install discord.py` in the same Python environment you're using to run the bot.

---

## 📄 License

MIT License — free to use, modify, and distribute. Attribution appreciated but not required.

---

<div align="center">
Made with ❤️ and discord.py · <a href="https://discord.com/developers/docs">Discord Developer Docs</a> · <a href="https://discordpy.readthedocs.io/">discord.py Docs</a>
</div>
