# KOALA RAG SYSTEM

This project is a Retrieval-Augmented Generation (RAG) chatbot built with a LLaMA model (8-bit quantized using bitsandbytes).
The backend runs on Flask inside Google Colab, exposed via ngrok, and the frontend is a simple HTML page that interacts with the API.

📂 Project Files

notebook.ipynb → Google Colab notebook for running the model + Flask API.

index.html → Frontend UI to interact with the chatbot API.

# 🚀 How to Run the Project
1. Open Notebook on Colab

Upload or open the notebook.ipynb in Google Colab.

Make sure you select GPU runtime (Runtime > Change runtime type > GPU).

2. Install Requirements

In the first notebook cells, install dependencies (Transformers, Bitsandbytes, Flask, Ngrok).

!pip install transformers bitsandbytes flask flask-cors pyngrok

3. Start Flask API

Example snippet:

from flask import Flask, request, jsonify
from pyngrok import ngrok

app = Flask(__name__)


@app.route("/chat", methods=["POST"])
def chat():
    user_input = request.json["query"]
    response = generate_answer(user_input)
    return jsonify({"answer": response}
    
public_url = ngrok.connect(5000)
print("Public URL:", public_url)
app.run(port=5000)


When you run this, Colab will print a Public URL (from ngrok) that exposes your API.

4. Connect Frontend (index.html)

  Open the index.html file in your browser.
  
  Inside the HTML/JS, replace the API_URL with the ngrok link printed by Colab (something like https://xxxx.ngrok.io/chat).

Example in JS:

  const API_URL = "https://xxxx.ngrok.io/chat";

5. Chat with the Bot

  Enter a query in the frontend.
  
  The request is sent to the Flask API running on Colab.
  
  The model generates a response and sends it back to the browser.

🔑 Notes

  The model runs in Colab, not locally (unless you set it up with a GPU machine).
  
  Each Colab run will generate a new ngrok URL, so update the HTML file accordingly.
  
  This setup is for testing and demo purposes; for production, deploy on a proper server.
