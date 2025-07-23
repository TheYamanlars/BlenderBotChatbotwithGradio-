BlenderBot Chatbot with Gradio (Dockerized)
An interactive chatbot web app powered by Meta AI's facebook/blenderbot-1B-distill and served through Gradio. Easily deployable using Docker.
Features

- Chatbot powered by Hugging Face Transformers
- Maintains conversation history
- Uses BlenderBot 1B distilled model for conversational AI
- Gradio UI for interactive web interface
- Docker support for reproducible deployment

Project Structure

multi_chatbot/
├── gradio_blenderbot.py       # Main chatbot script
├── requirements.txt           # Dependencies
├── Dockerfile                 # Docker build file
└── ...

Local Usage (Without Docker)

# Step 1: Create and activate a virtual environment
python -m venv venv
venv\Scripts\activate   # Windows
# or
source venv/bin/activate  # macOS/Linux

# Step 2: Install dependencies
pip install -r requirements.txt

# Step 3: Run the app
python gradio_blenderbot.py

Docker Usage

# Step 1: Build the image
docker build -t gradio-blenderbot .

# Step 2: Run the container
docker run -it -p 7860:7860 gradio-blenderbot

Then open your browser at: http://localhost:7860

Requirements

gradio==4.44.1
transformers==4.39.3
torch==2.1.2

Model

- Name: facebook/blenderbot-1B-distill
- Task: Conversational text generation (seq2seq)
- Source: https://huggingface.co/facebook/blenderbot-1B-distill

Dockerfile (included)

FROM python:3.10-slim

WORKDIR /app
COPY . /app

RUN pip install --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt

CMD ["python", "gradio_blenderbot.py"]

Notes

- You can share the Gradio app publicly by setting share=True in demo.launch(...)
- For cloud deployment, consider Hugging Face Spaces, IBM Cloud Code Engine, or Streamlit Sharing.

Contact
Made by Cansu Yamanlar 
Contributions and issues welcome!
