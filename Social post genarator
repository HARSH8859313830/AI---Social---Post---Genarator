import openai
import os
from flask import Flask, render_template, request
from dotenv import load_dotenv

load_dotenv()

openai.api_key = os.getenv("OPENAI_API_KEY")

app = Flask(__name__)

def generate_post(prompt):
    response = openai.Completion.create(
        engine="text-davinci-003",
        prompt=f"Generate a creative and engaging social media caption with emojis and 5 related hashtags for: {prompt}",
        max_tokens=100,
        temperature=0.9
    )
    return response.choices[0].text.strip()

@app.route("/", methods=["GET", "POST"])
def index():
    result = ""
    if request.method == "POST":
        topic = request.form["topic"]
        result = generate_post(topic)
    return render_template("index.html", result=result)

if __name__ == "__main__":
    app.run(debug=True)
