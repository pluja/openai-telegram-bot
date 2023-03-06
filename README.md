# [This project is hosted at Codeberg!](https://codeberg.org/pluja/openai-telegram-bot)

## Readme for [OpenAI API Telegram Bot](https://codeberg.org/pluja/openai-telegram-bot)

A telegram bot to interact with OpenAI API. You can:

- Generate images with DALL-E: `/imagine`
- Chat with ChatGPT: Just chat!
- Transcribe audio to text: Just send a voice message!

Other features include:

- Clear ChatGPT context history (to save tokens).
- Per-user context and usage metrics and spent $.
- No database, data is saved in-memory.
- Lightweight: just a single python file.

## Self-hosting

Self hosting this chatbot is pretty easy. You just need to follow this steps:

1. Get your OPENAI Token from [here](https://platform.openai.com/account/api-keys).
   - You will need to set a payment method.

2. Generate a new bot:
   1. Start a new chat with [@BotFather](https://t.me/BotFather) bot.
   2. Type `/newbot` command. Set a name and a username.
   3. Copy the Token that BotFather will give you.
   
3. Get allowed users' IDs:
   1. Start a new chat with [@RawDataBot](https://t.me/RawDataBot).
   2. Send a message or forward a message from any desired user.
   3. Copy the `message.from.id` field value. Should be an ID like: 1234567890

4. Setup the bot:
   1. Clone the repo: `git clone https://codeberg.org/pluja/openai-telegram-bot`
   2. Rename the `example.docker-compose.yml` file to `docker-compose.yml`.
   3. Edit the environment variables:
      1. Set your OPENAI_TOKEN.
      2. Set your BOT_TOKEN.
      3. Set your ALLOWED_USERS (comma separated user ids).
      4. Set the SYSTEM_PROMPT for ChatGPT. This is always instructed to ChatGPT as the system.
   4. Build and start the bot: `docker compose up --build -d`.
   
5. Enjoy!

## Usage

- By simply sending normal chat messages, you will be interacting with ChatGPT.
  - The last 5 messages (from user and bot) are sent to ChatGPT API as context.
  - Use the command `/clear` to clear your context and start over a completely new chat.

- By using the `/imagine <prompt>` command, you will be getting images generated by DALL-E.
    - Example: `/imagine A cat with a red hat`.

- Sending a voice message to the bot, it will transcribe it to text using Whisper.

- `/info` command allows you to see your usage statistics.
