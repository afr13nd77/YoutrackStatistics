# YouTrack Statistics Bot

A Telegram bot that delivers regular reports on bug tracking activity from YouTrack.

## What it does

Connects to the YouTrack API and sends scheduled reports to a Telegram chat with statistics on new and resolved bugs. Designed for product and engineering teams who want to stay on top of bug trends without logging into YouTrack.

## Features

- **Flexible time periods** — report for today, current/previous week, or current/previous month
- **Filtered reporting** — view all issues or only closed ones for the selected period
- **YouTrack API integration** — pulls issue data directly from your project
- **Telegram delivery** — reports land in a team chat, no context switching needed

## Use case

Product managers and team leads need a quick daily/weekly snapshot of bug dynamics: are we closing more bugs than we're creating? Is the backlog growing? This bot answers those questions automatically, delivered right into the team's Telegram chat.

## Tech stack

- **Python**
- YouTrack REST API
- Telegram Bot API
- Scheduled task execution

## Quick start

```bash
git clone https://github.com/afr13nd77/YoutrackStatistics.git
cd YoutrackStatistics
pip install -r requirements.txt
```

Configure your credentials:

```
YOUTRACK_URL=https://your-instance.youtrack.cloud
YOUTRACK_TOKEN=your_api_token
TELEGRAM_BOT_TOKEN=your_bot_token
TELEGRAM_CHAT_ID=your_chat_id
```

## Usage

```bash
python youtrackstatistics.py <Period> <IssuesState>
```

**Period** — reporting time window:

| Value | Description |
|-------|-------------|
| `day` | Today |
| `week` | Current week |
| `prevweek` | Previous week |
| `month` | Current month |
| `prevmonth` | Previous month |

**IssuesState** — which issues to include:

| Value | Description |
|-------|-------------|
| `all` | All issues (new + open + closed) |
| `closed` | Only resolved issues |

Examples:

```bash
# Daily report — all bugs created/updated today
python youtrackstatistics.py day all

# Previous week — only closed bugs (sprint review)
python youtrackstatistics.py prevweek closed

# Monthly summary — everything
python youtrackstatistics.py month all
```

## How it works

1. Connects to the YouTrack API using a personal access token
2. Queries issues by creation/resolution date within the reporting period
3. Aggregates statistics (new bugs, closed bugs, delta)
4. Formats and sends the report via Telegram Bot API

## Context

Built for an internal product team to automate bug tracking visibility. Replaced manual weekly reports that took 30+ minutes to compile.

## License

MIT
