
# OTP-Boss Bot
OTP-Boss Bot is a Telegram bot integrated with Twilio Voice API and ElevenLabs Text-to-Speech API. This bot is designed for managing subscriptions, generating calls with voice messages, and handling OTP-based scenarios for authentication or verification.

---

## Features
1. **Subscription Management**  
   - Check subscription status.
   - Add new subscriptions.
   - Notify users when a subscription expires.

2. **Call Functionality**  
   - Initiate calls using Twilio API.  
   - Generate and play voice scripts with ElevenLabs Text-to-Speech API.  
   - Handle OTP verification through calls.

3. **User Commands**  
   - `/start`: Initiate the bot and create default user settings.  
   - `/check`: Check subscription status.  
   - `/call [Phone Number] [Name] [Code] [Company Name]`: Initiate a custom call.  
   - `/add_subs [User ID] [Number of Days]`: Add subscription days for a user (Admin only).  
   - `/help`: List available commands.

4. **Voice Interaction**  
   - Play custom voice messages during calls.  
   - Support for collecting numeric input (e.g., OTP) from recipients.

---

## Prerequisites
1. **APIs and Libraries**:
   - **Telegram Bot Token** from [Telegram BotFather](https://core.telegram.org/bots#botfather).
   - **Twilio Account SID** and **Auth Token** from [Twilio](https://www.twilio.com/).
   - **ElevenLabs API Key** for Text-to-Speech ([ElevenLabs](https://elevenlabs.io/)).
   - **Ngrok** for exposing localhost to the web.

2. **Environment Setup**:
   - Python 3.8 or above.
   - Required Python packages listed in `requirements.txt`.

3. **Configuration**:
   - Configuration file `conf/settings.txt` should include the following keys:
     ```json
     {
       "bot_token": "<YOUR_BOT_TOKEN>",
       "account_sid": "<YOUR_TWILIO_ACCOUNT_SID>",
       "auth_token": "<YOUR_TWILIO_AUTH_TOKEN>",
       "ngrok_url": "<YOUR_NGROK_URL>",
       "Twilio Phone Number": "<YOUR_TWILIO_PHONE_NUMBER>"
     }
     ```

---

## Installation

1. **Download the Repository**

2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set Up Configuration**:
   - Create the `conf/` directory and add the `settings.txt` configuration file as described above.

4. **Run the Bot**:
   ```bash
   python bot.py
   ```

5. **Run the Flask Server** (for handling Twilio responses):
   ```bash
   python voice_resp.py
   ```

---

## File Structure
```
otp-boss-bot/
├── bot.py                 # Main Telegram bot script.
├── voice_resp.py          # Flask server for Twilio voice responses.
├── requirements.txt       # Python dependencies.
├── conf/                  # Configuration files and user data.
│   ├── settings.txt       # Global settings for APIs.
│   ├── <User ID>/         # User-specific data (e.g., subscriptions, audio files).
└── └── sounds/            # Common audio files for the bot.
```

---

## Commands Overview

### Public Commands
- `/start`: Initialize the bot.
- `/check`: Display the subscription status.
- `/call [Phone Number] [Name] [Code] [Company Name]`: Start a call with specified details.

### Admin Commands
- `/add_subs [User ID] [Number of Days]`: Add subscription days to a user.

### Informational Commands
- `/help`: Display a list of available commands and their descriptions.

---

## Environment Variables
For secure handling of credentials, you can use environment variables. Update your `settings.txt` to read these variables:
```python
import os
bot_token = os.getenv("BOT_TOKEN")
account_sid = os.getenv("TWILIO_SID")
auth_token = os.getenv("TWILIO_AUTH_TOKEN")
ngrok = os.getenv("NGROK_URL")
phone_numz = os.getenv("TWILIO_PHONE_NUMBER")
```

---

## Deployment

### Local Deployment
1. Run the bot script:
   ```bash
   python bot.py
   ```
2. Run the voice response server:
   ```bash
   python voice_resp.py
   ```
3. Use **ngrok** to expose the Flask app:
   ```bash
   ngrok http 5000
   ```

### Server Deployment
- Use a platform like AWS, Heroku, or Google Cloud for hosting.
- Ensure your webhook URLs are properly configured for Telegram and Twilio.

---

## Future Enhancements
1. Multi-language support for voice scripts.
2. Web-based dashboard for admin management.
3. Enhanced security features, such as encrypted configurations.

---

## Contribution

Fork this repository and send pull requests and drop stars to the repo.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for more information.