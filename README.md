# FairMeeting-Timer
FairMeeting Timer 

# 📌 Overview

FairMeeting Timer is a Python-based tool designed to track and visualize speaking times during meetings. It helps ensure equitable participation by measuring and displaying how much each participant speaks.

# 🎯 Objectives

- Transcribe audio from a given file.
- Track speaking times of different participants.
- Generate a bar chart to visualize speaking distribution.

# 🛠️ Tech Stack

- Programming Language: Python
- Data Processing: Pandas, NumPy
- Visualization: Matplotlib
- Speech Recognition: SpeechRecognition

# 📂 Project Structure

FairMeeting_Timer/
│── data/                  # Audio files and processed data
│── notebooks/             # Jupyter Notebooks for exploration
│── src/
│   ├── transcribe.py      # Speech recognition logic
│   ├── analyze.py         # Data analysis functions
│   ├── visualize.py       # Data visualization scripts
│── fair_meeting_timer.py  # Main script
│── requirements.txt       # Required dependencies
│── README.md              # Project documentation

# 🚀 Installation & Usage

- Clone Repository
git clone https://github.com/yourusername/FairMeeting_Timer.git
cd FairMeeting_Timer

- Install Dependencies
pip install -r requirements.txt

- Run the Script
python fair_meeting_timer.py

# 📈 Example Code

import speech_recognition as sr
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# Function to transcribe audio and track speaking times
def transcribe_audio(audio_file):
    recognizer = sr.Recognizer()
    with sr.AudioFile(audio_file) as source:
        audio = recognizer.record(source)
    
    try:
        transcript = recognizer.recognize_google(audio)
        return transcript
    except sr.UnknownValueError:
        return "[Unrecognized speech]"
    except sr.RequestError:
        return "[Could not request results]"

# Function to plot speaking times
def plot_speaking_times(speaking_times):
    speakers = list(speaking_times.keys())
    times = list(speaking_times.values())
    
    plt.figure(figsize=(8, 6))
    plt.bar(speakers, times, color=['blue', 'green', 'red'])
    plt.xlabel("Speakers")
    plt.ylabel("Speaking Time (seconds)")
    plt.title("FairMeeting Timer - Speaking Distribution")
    plt.show()

# Example speaking time data
speaking_times = {"Ilaria": 45, "Matteo": 32, "Chiara": 23}
plot_speaking_times(speaking_times)

# 📜 License

MIT License

# 🤝 Contributing

Contributions are welcome! Please open an issue or submit a pull request.

