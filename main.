from flask import Flask, request
from twilio.twiml.messaging_response import MessagingResponse

app = Flask(__name__)

valid_codes = {
    "G7X2W9L": "Batch A01 - Verified Genuine",
    "G4PQ8MZ": "Batch A02 - Verified Genuine",
    "G9RT3NY": "Batch A03 - Verified Genuine",
    "G1AB5KL": "Batch A04 - Verified Genuine",
    "G5DE8CU": "Batch A05 - Verified Genuine",
    "G3ZM7XQ": "Batch A06 - Verified Genuine",
}

@app.route("/whatsapp", methods=["POST"])
def whatsapp():
    incoming_msg = request.values.get("Body", "").strip().upper()
    print("📨 Message received:", incoming_msg)
    resp = MessagingResponse()
    msg = resp.message()

    if incoming_msg in valid_codes:
        msg.body(f"✅ AUTHENTIC: {valid_codes[incoming_msg]}")
    else:
        msg.body("⚠️ WARNING: This product code is not recognised. It may be counterfeit or mistyped.")

    return str(resp)
