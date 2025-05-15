- 👋 Hi, I’m @LOngxing342
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
LOngxing342/LOngxing342 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
from twilio.rest import Client

account_sid = 'your_account_sid'
auth_token = 'your_auth_token'
client = Client(account_sid, auth_token)

client.incoming_phone_numbers('PNXXXX').update(voice_url='http://example.com/block')


from twilio.rest import Client

# Your Twilio credentials (use environment variables in production!)
account_sid = 'your_account_sid'
auth_token = 'your_auth_token'

# Initialize the Twilio client
client = Client(account_sid, auth_token)

# Update the voice URL of a specific Twilio phone number
phone_number_sid = 'PNXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'  # Replace with your PhoneNumber SID
new_voice_url = 'https://example.com/your-voice-handler'  # Must be a public HTTPS URL

client.incoming_phone_numbers(phone_number_sid).update(voice_url=new_voice_url)

print(f"Voice URL updated for {phone_number_sid}")
