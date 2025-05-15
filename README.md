# Flask app to handle incoming calls
from flask import Flask, request, abort
from twilio.twiml.voice_response import VoiceResponse
import time

app = Flask(__name__)

# Simple in-memory call tracker (use Redis or DB in production)
call_log = {}

@app.route("/voice", methods=['POST'])
def voice():
    from_number = request.form.get('From')
    now = time.time()
    
    if from_number not in call_log:
        call_log[from_number] = []
    
    # Keep only calls from the last 60 seconds
    call_log[from_number] = [t for t in call_log[from_number] if now - t < 60]
    
    if len(call_log[from_number]) >= 3:
        abort(403)  # Block excessive calls

    call_log[from_number].append(now)

    response = VoiceResponse()
    response.say("Hello, this is your secure service.")
    return str(response)

if __name__ == "__main__":
    app.run(debug=True)

