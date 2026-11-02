# 🎭 Emotion Prediction – NLP Web Application

A deep learning web app that reads a piece of text and predicts the emotion behind it. The model is a **Bidirectional GRU (BiGRU)** built with TensorFlow/Keras, served through a **FastAPI** application and deployed on **Render**.

🔗 **Live Demo:** [emotion-prediction-1-obw4.onrender.com](https://emotion-prediction-1-obw4.onrender.com)
📦 **Repository:** [anubhavtrivedi18/Emotion-Prediction](https://github.com/anubhavtrivedi18/Emotion-Prediction)

> ⏳ The app runs on Render's free tier, so the first request after a period of inactivity may take 30–60 seconds while the service wakes up.

---

## 📌 Overview

The project classifies English text into one of six emotions:

| Emotion | Example |
|---------|---------|
| 😢 Sadness | "I feel so empty and alone today." |
| 😄 Joy | "I just got the job, I'm over the moon!" |
| ❤️ Love | "I care about you more than words can say." |
| 😠 Anger | "I can't believe they ignored me again." |
| 😨 Fear | "I'm terrified of what might happen tomorrow." |
| 😲 Surprise | "I never expected this to happen!" |

---

## ✨ Features

- BiGRU-based text classification model for six emotion classes
- Text preprocessing and tokenization pipeline shared between training and inference
- REST API built with FastAPI, with automatic interactive docs (Swagger UI)
- Simple web interface for entering text and viewing predictions
- Deployed and publicly accessible on Render

---

## 🛠️ Tech Stack

| Area | Tools |
|------|-------|
| Language | Python |
| Deep Learning | TensorFlow, Keras (Embedding + Bidirectional GRU) |
| NLP | Tokenization, sequence padding, text cleaning |
| Backend | FastAPI, Uvicorn |
| Deployment | Render |

---

## 🧠 Model Architecture

```
Input text
   │
   ▼
Text preprocessing (cleaning, lowercasing, stopword/punctuation handling)
   │
   ▼
Tokenizer → integer sequences → padding
   │
   ▼
Embedding layer
   │
   ▼
Bidirectional GRU
   │
   ▼
Dense layer(s) + Dropout
   │
   ▼
Softmax (6 emotion classes)
```

A BiGRU reads the sequence in both directions, so each word is interpreted with context from the words before *and* after it, which helps with emotion cues that depend on phrasing.

---

## 📁 Project Structure

> Adjust this to match your actual repository layout.

```
Emotion-Prediction/
├── app/
│   ├── main.py              # FastAPI application
│   ├── templates/           # HTML templates (if used)
│   └── static/              # CSS / JS assets (if used)
├── model/
│   ├── emotion_model.h5     # Trained BiGRU model
│   └── tokenizer.pkl        # Fitted tokenizer
├── notebooks/
│   └── training.ipynb       # Data exploration, training, evaluation
├── requirements.txt
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/anubhavtrivedi18/Emotion-Prediction.git
cd Emotion-Prediction
```

### 2. Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the app locally

```bash
uvicorn app.main:app --reload
```

Open **http://127.0.0.1:8000** in your browser.
Interactive API docs are available at **http://127.0.0.1:8000/docs**.

---

## 🔌 API Usage

### `POST /predict`

**Request**

```json
{
  "text": "I am so happy to see you again!"
}
```

**Response**

```json
{
  "emotion": "joy",
  "confidence": 0.94
}
```

**cURL example**you again!"}'
```

> Update the endpoint name and response fiel

```bash
curl -X POST "https://emotion-prediction-1-obw4.onrender.com/predict" \
     -H "Content-Type: application/json" \
     -d '{"text": "I am so happy to see ds to match your `main.py`.

---

## 📊 Model Performance

| Metric | Score |
|--------|-------|
| Accuracy | _add your value_ |
| Macro F1-score | _add your value_ |

Add a confusion matrix or training curves here, for example:

```markdown
![Confusion Matrix](assets/confusion_matrix.png)
```

---

## ☁️ Deployment on Render

1. Push the project to GitHub.
2. On [Render](https://render.com), create a new **Web Service** and connect the repository.
3. Set the following:
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `uvicorn app.main:app --host 0.0.0.0 --port $PORT`
4. Deploy. Render will rebuild automatically on every push.

---

## 🔮 Future Improvements

- Fine-tune a transformer model (BERT / DistilBERT) and compare against the BiGRU baseline
- Add multi-label emotion detection for text that expresses more than one emotion
- Show per-class probability scores in the UI
- Containerize with Docker and add CI/CD
- Add unit tests for the preprocessing and API layers

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome. Feel free to open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## 👤 Author

**Anubhav Trivedi**
GitHub: [@anubhavtrivedi18](https://github.com/anubhavtrivedi18)
