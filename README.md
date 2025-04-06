# Agribot
from flask import Flask, request
from twilio.twiml.messaging_response import MessagingResponse

app = Flask(__name__)

@app.route("/whatsapp", methods=['POST'])
def whatsapp_reply():
    incoming_msg = request.values.get('Body', '').lower()
    resp = MessagingResponse()
    msg = resp.message()
    if "hello" in incoming_msg:
        msg.body("Hi! How can I assist you today?")
    elif "help" in incoming_msg:
        msg.body("Sure! I can help you with information, updates, and more.")
    else:
        msg.body("I'm a simple bot. Try saying 'Hello' or 'Help'.")
    return str(resp)  
if __name__ == "__main__":
    app.run(debug=True)
