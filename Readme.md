# PulseBot - Slack Standup Bot

### Feature requests are welcome. If you've one, raise an issue.

PulseBot is a Slack bot that automates daily standups for your team. It collects responses from team members, stores them, and provides a configurable control panel for admins to manage standup settings.

## Features

- **Automated Standup Reminders:** Sends daily standup questions to all team members via DM.
- **Manual Standup Trigger:** Admins can manually trigger standup reminders.
- **Customizable Schedule:** Set the time and days for standup reminders.
- **Response Channel:** Choose a channel to post standup summaries.
- **Response Window:** Configure how long users have to submit their standup.
- **Admin Control Panel:** Slack modal UI for managing all settings.
- **OAuth Installation:** Securely install the bot to your Slack workspace.

## Getting Started

### Prerequisites

- Python 3.8+
- Slack App credentials (Client ID, Client Secret, Signing Secret, Bot Token)
- [ngrok](https://ngrok.com/) (for local development)

### Installation

0. **Create a Virtual environment for development:**
    ```sh
    virtualenv -p python3 slackbot-env
    ```
1. **Activate the virtual environment:**
    ```sh
    source slackbot-env/bin/activate
    ```
2. **Clone the repository:**
    ```sh
    git clone git@github.com:[your_username]/standup-slack-bot.git
    ```
3. **move to the project directory:**
    ```sh
    cd standup-slack-bot
    ```

4. **Install dependencies:**
    ```sh
    pip install -r requirements.txt
    ```

5. **Configure environment variables:**

    Create a `.env` file in the root directory:
    ```
    SLACK_CLIENT_ID=your_client_id
    SLACK_CLIENT_SECRET=your_client_secret
    SLACK_SIGNING_SECRET=your_signing_secret
    SLACK_BOT_TOKEN=your_bot_token
    PUBLIC_URL=https://your-ngrok-url.ngrok-free.app
    ```

5. **Run the bot:**
    ```sh
    PYTHONPATH=. python app/main.py
    ```

6. **Expose your local server (for Slack events):**
    ```sh
    ngrok http 8000
    ```

7. **Install the bot to your Slack workspace:**
    - Visit `https://[your-ngrok-url].ngrok-free.app/slack/install` and follow the prompts.

## Usage

- Use `/pulsecheck` in Slack to open the admin control panel (admins only).
- Use `/trigger-standup` to manually trigger a standup for all team members.
- Team members will receive a DM with a button to start their standup.
- Responses are stored in a local SQLite database (`standup.db`).

## Project Structure

- db.py has the database structure here
- main.py has all the api handlers for slack app requests
