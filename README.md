# anime-character-classifier

Small Flask web app that sends an image URL to a Roboflow-hosted model and shows the predicted anime character.

## Features

- Web page with two forms (One Piece, Naruto), switched with a toggle. Both post to the same endpoint.
- Sends the image URL to a Roboflow model (project version 3) via the `roboflow` SDK and shows the top predicted class next to the image.
- Logs prediction results and misses.

## Tech stack

Python, Flask, Roboflow SDK, python-dotenv, plain HTML, CSS and JavaScript.

## Structure

```
app.py            Flask routes (GET / and POST /)
ml_model.py       Roboflow client and Predictions class
templates/        index.html
static/           style.css, script.js
requirements.txt
```

## Setup

Requires Python 3.9+ and a Roboflow account with a trained model project.

Environment variables (put them in a `.env` file, which is git-ignored):

| Name | Purpose |
|------|---------|
| `ROBOFLOW_API_KEY` | Your Roboflow API key. |
| `ROBOFLOW_PROJECT_NAME` | Roboflow project that holds the model (version 3 is used). |

```
pip install -r requirements.txt
python app.py
```

Open http://localhost:1200.

## Usage

Type a public image URL into either form and press Predict. The result panel shows the image and the predicted character name.

## Limitations

- The file upload inputs in the page are not wired up; only the image URL works.
- The Naruto and One Piece forms call the same model; the toggle changes only the layout.
- No error handling for a failed prediction (a missing result raises an error), and the app runs with Flask debug on.
- Requires your own trained Roboflow project, which is not included.
