<div align="center">

# 🎵 Song Identification, Mood Detection & Music Recommendation Website

### A beginner-friendly web application where users can **upload a short audio clip**, and the system will:

1. **Identify the song**
2. **Detect the mood of the song using Machine Learning**
3. **Recommend similar songs**

</div>



## 🚀 Project Overview

Music platforms like **Shazam** and **Spotify** analyze audio signals to recognize songs and suggest similar music.  

## 🤝 Contributers
- ![Ruvaifa](https://github.com/Ruvaifa)

## 🧠 System Workflow

1. User uploads an audio clip (5–15 seconds)
2. Backend saves and processes the audio
3. Song is identified using a music recognition API
4. Audio features are extracted
5. ML model predicts the mood
6. Similar songs are recommended
7. Results are displayed on the website



## 🏗️ Tech Stack

### 🌐 Frontend
- ⚛️ **React 18.3** - Modern UI framework
- 📘 **TypeScript 5.5** - Type-safe development
- 🎨 **Tailwind CSS** - Utility-first styling
- 🎭 **Framer Motion** - Smooth animations

### ⚙️ Backend
- 🚀 **FastAPI** - High-performance Python framework
- 🐘 **PostgreSQL** - Robust relational database
- 🔥 **Supabase** - Real-time database & auth

### 🎧 Audio Processing
- 🎼 **Librosa** – audio feature extraction
- 📊 **NumPy** – numerical operations

### 🧠 Machine Learning
- 🎲 **Scikit-learn**
- 🤖 Pre-trained classical ML models

### 🎶 Music APIs
- 🎙️ **ACRCloud / Shazam API** – song identification
- 🎧 **Spotify Web API** – recommendations

---

## 🧠 Machine Learning Models Used

This project **intentionally avoids deep learning** to keep it beginner-friendly.



### 🎼 1️⃣ Audio Feature Extraction (Input to ML Models)

Using **Librosa**, we extract numerical features from the audio clip:

- Tempo (BPM)
- Zero Crossing Rate
- Spectral Centroid
- Spectral Bandwidth
- RMS Energy
- MFCCs (Mel-Frequency Cepstral Coefficients)

These features convert audio into a **numerical vector**, which ML models can understand.

---

### 😊 2️⃣ Mood Detection Model (Core ML Part)

#### 🎯 Goal
Classify a song into one of the moods:
- Happy
- Sad
- Calm
- Energetic

---

### 🔹 ML Models

You can start with **any one** of these:

#### ✅ Logistic Regression
- Easy to understand
- Fast to train
- Good baseline model

---

### 📊 Training the ML Model

- Dataset: Pre-labeled music datasets (e.g., GTZAN, Free Music Archive)
- Labels: Mood category
- Train-test split: 80/20
- Evaluation metrics:
  - Accuracy
  - Confusion matrix

The trained model is saved using `joblib` or `pickle`.

---

### 🔮 Prediction Flow

1. Audio uploaded by user
2. Features extracted
3. Features passed to trained ML model
4. Model outputs predicted mood
5. Mood shown on frontend



## 🎧 3️⃣ Recommendation Logic (ML + API Based)

### 🔹 Option 1: API-Based Recommendation
- Use Spotify Audio Features:
  - Valence
  - Energy
  - Tempo
- Recommend songs with similar values

### 🔹 Option 2: ML-Based Similarity
- Use **Cosine Similarity**
- Compare feature vectors of songs
- Recommend top N similar songs

📌 Beginners can start with **API-based recommendations**.



## 📁 Project Structure
```
tune-trace/                          # (or whatever name you choose)
│
├── frontend/                        # React + TypeScript app
│   ├── public/
│   │   └── index.html
│   │
│   ├── src/
│   │   ├── assets/                  # Images, icons, static files
│   │   ├── components/              # Reusable UI components
│   │   │   ├── AudioUpload.tsx
│   │   │   ├── SongResult.tsx
│   │   │   ├── MoodBadge.tsx
│   │   │   └── RecommendationCard.tsx
│   │   │
│   │   ├── pages/                   # Page-level components
│   │   │   ├── Home.tsx
│   │   │   └── Result.tsx
│   │   │
│   │   ├── services/                # API calls (FastAPI / Supabase)
│   │   │   ├── api.ts
│   │   │   ├── audioService.ts
│   │   │   └── authService.ts
│   │   │
│   │   ├── hooks/                   # Custom React hooks
│   │   │   └── useAudioUpload.ts
│   │   │
│   │   ├── types/                   # TypeScript interfaces
│   │   │   ├── song.ts
│   │   │   └── mood.ts
│   │   │
│   │   ├── utils/                   # Helper functions
│   │   │   └── formatDuration.ts
│   │   │
│   │   ├── App.tsx
│   │   ├── main.tsx
│   │   └── index.css
│   │
│   ├── tailwind.config.ts
│   ├── tsconfig.json
│   └── vite.config.ts
│
├── backend/                         # FastAPI backend
│   ├── app/
│   │   ├── main.py                  # FastAPI entry point
│   │   │
│   │   ├── api/                     # Route definitions
│   │   │   ├── audio.py             # Audio upload endpoint
│   │   │   ├── song.py              # Song identification API
│   │   │   ├── mood.py              # Mood prediction endpoint
│   │   │   └── recommend.py         # Song recommendations
│   │   │
│   │   ├── core/                    # App configuration
│   │   │   ├── config.py            # Environment variables
│   │   │   └── security.py
│   │   │
│   │   ├── services/                # Business logic
│   │   │   ├── acrcloud_service.py
│   │   │   ├── spotify_service.py
│   │   │   └── audio_service.py
│   │   │
│   │   ├── ml/                      # Machine Learning logic
│   │   │   ├── feature_extraction.py
│   │   │   ├── mood_classifier.py
│   │   │   └── model/
│   │   │       └── mood_model.pkl
│   │   │
│   │   ├── db/                      # Database layer
│   │   │   ├── supabase.py
│   │   │   └── schemas.py
│   │   │
│   │   ├── utils/
│   │   │   └── file_handler.py
│   │   │
│   │   └── __init__.py
│   │
│   ├── uploads/                     # Temporary audio storage
│   ├── requirements.txt
│   └── .env.example
│
├── ml-training/                     # Offline ML training (important)
│   ├── datasets/
│   ├── notebooks/
│   │   └── mood_training.ipynb
│   ├── train_model.py
│   └── evaluate.py
│
├── docs/                            # Documentation
│   ├── api.md
│   ├── ml.md
│   └── architecture.md
│
├── .gitignore
├── README.md
└── docker-compose.yml (optional)
```
---
## 🧪 Future Improvements
- CNN-based audio classification
- Spectrogram-based deep learning
- User-personalized recommendations
- Multi-label mood prediction

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---