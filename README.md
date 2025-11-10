NAME:DIVYA E
REG NO: 212223230050
CHATBOT
AIM
To develop a scalable AI-enabled chatbot that helps employees of a large public sector organization with HR, IT, and organizational queries using NLP and document processing, while ensuring security (2FA) and filtering inappropriate language.​

ALGORITHM
Step-by-Step Algorithm:

User Authentication:

Implement 2-factor authentication (email + OTP).​

Receive Query:

Accept employee query via web/chat interface.

Filter Language:

Check user input against list of banned words.

Intent Detection:

Use pretrained NLP model (BERT or similar) to classify query (HR, IT, Events, etc.).​

Response Retrieval:

Retrieve or generate response from FAQ/document database.

Document Processing:

If user uploads a document, extract summary/keywords using NLP pipeline.

Output Response:

Return response in under 5 seconds.

Scalability:

Use threading/async code to serve at least 5 users in parallel.

REQUIRED TOOLS
Python 3.8+

Flask (Web server)

transformers (HuggingFace, BERT for NLP)

NLTK or spaCy (language filtering, keyword extraction)

PyOTP (for email-based 2FA)

Threading/asyncio (to handle multiple users)

sqlite3 or TinyDB (for FAQ/document storage)

Simple front-end: HTML/JS/Bootstrap

IMPLEMENTATION CODE (Simplified Example)


```

1. Train Your Model (train_chatbot.py)

import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import LogisticRegression
import pickle

# Sample data: query and intent
data = {
    'question': [
        "How many leave days do I have?",
        "Who do I call for IT support?",
        "When is the next company event?",
        "How do I update my address?",
        "Can I request work from home?",
    ],
    'intent': [
        "leave_balance",
        "it_support",
        "company_event",
        "update_address",
        "work_from_home"
    ]
}
df = pd.DataFrame(data)

# Vectorizer & Model pipeline
vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(df['question'])
y = df['intent']

model = LogisticRegression(max_iter=200)
model.fit(X, y)

# Save artifacts
pickle.dump(model, open("model.pkl", "wb"))
pickle.dump(vectorizer, open("vectorizer.pkl", "wb"))
pickle.dump(list(df['intent']), open("intents.pkl", "wb"))
print("Training complete, model and vectorizer saved.")

2. Simple Chatbot Server (chatbot_server.py)
import pickle
from flask import Flask, request, jsonify

 app = Flask(__name__) 

model = pickle.load(open("model.pkl", "rb"))
vectorizer = pickle.load(open("vectorizer.pkl", "rb"))
intents = pickle.load(open("intents.pkl", "rb"))

response_map = {
    "leave_balance": "You have 15 days of annual leave remaining.",
    "it_support": "Please call the IT helpdesk at extension 1234.",
    "company_event": "The next event is the Annual Team Meet on November 10th.",
    "update_address": "To update your address, visit the HR portal and use the profile section.",
    "work_from_home": "You can request work-from-home via the company HR portal."
}

@app.route("/chat", methods=["POST"])
def chat():
    query = request.json.get("message", "")
    X = vectorizer.transform([query])
    pred_intent = model.predict(X)[0]
    response = response_map.get(pred_intent, "I am sorry, I did not understand your question.")
    return jsonify({"intent": pred_intent, "response": response})

if __name__ == "__main__":
    app.run(debug=True)



```
output:

NAME:SANDHIYA SREE
REG NO: 212223220093
CHATBOT
AIM
To develop a scalable AI-enabled chatbot that helps employees of a large public sector organization with HR, IT, and organizational queries using NLP and document processing, while ensuring security (2FA) and filtering inappropriate language.​

ALGORITHM
Step-by-Step Algorithm:

User Authentication:

Implement 2-factor authentication (email + OTP).​

Receive Query:

Accept employee query via web/chat interface.

Filter Language:

Check user input against list of banned words.

Intent Detection:

Use pretrained NLP model (BERT or similar) to classify query (HR, IT, Events, etc.).​

Response Retrieval:

Retrieve or generate response from FAQ/document database.

Document Processing:

If user uploads a document, extract summary/keywords using NLP pipeline.

Output Response:

Return response in under 5 seconds.

Scalability:

Use threading/async code to serve at least 5 users in parallel.

REQUIRED TOOLS
Python 3.8+

Flask (Web server)

transformers (HuggingFace, BERT for NLP)

NLTK or spaCy (language filtering, keyword extraction)

PyOTP (for email-based 2FA)

Threading/asyncio (to handle multiple users)

sqlite3 or TinyDB (for FAQ/document storage)

Simple front-end: HTML/JS/Bootstrap

IMPLEMENTATION CODE (Simplified Example)


```

1. Train Your Model (train_chatbot.py)

import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import LogisticRegression
import pickle

# Sample data: query and intent
data = {
    'question': [
        "How many leave days do I have?",
        "Who do I call for IT support?",
        "When is the next company event?",
        "How do I update my address?",
        "Can I request work from home?",
    ],
    'intent': [
        "leave_balance",
        "it_support",
        "company_event",
        "update_address",
        "work_from_home"
    ]
}
df = pd.DataFrame(data)

# Vectorizer & Model pipeline
vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(df['question'])
y = df['intent']

model = LogisticRegression(max_iter=200)
model.fit(X, y)

# Save artifacts
pickle.dump(model, open("model.pkl", "wb"))
pickle.dump(vectorizer, open("vectorizer.pkl", "wb"))
pickle.dump(list(df['intent']), open("intents.pkl", "wb"))
print("Training complete, model and vectorizer saved.")

2. Simple Chatbot Server (chatbot_server.py)
import pickle
from flask import Flask, request, jsonify

 app = Flask(__name__) 

model = pickle.load(open("model.pkl", "rb"))
vectorizer = pickle.load(open("vectorizer.pkl", "rb"))
intents = pickle.load(open("intents.pkl", "rb"))

response_map = {
    "leave_balance": "You have 15 days of annual leave remaining.",
    "it_support": "Please call the IT helpdesk at extension 1234.",
    "company_event": "The next event is the Annual Team Meet on November 10th.",
    "update_address": "To update your address, visit the HR portal and use the profile section.",
    "work_from_home": "You can request work-from-home via the company HR portal."
}

@app.route("/chat", methods=["POST"])
def chat():
    query = request.json.get("message", "")
    X = vectorizer.transform([query])
    pred_intent = model.predict(X)[0]
    response = response_map.get(pred_intent, "I am sorry, I did not understand your question.")
    return jsonify({"intent": pred_intent, "response": response})

if __name__ == "__main__":
    app.run(debug=True)



```
output:

<img width="1035" height="555" alt="Screenshot 2025-11-10 134807" src="https://github.com/user-attachments/assets/dbff2b89-0b84-483a-97ff-beb6d1c67477" />
RESULT:
Thus the Chatbot is executed Successfully.


