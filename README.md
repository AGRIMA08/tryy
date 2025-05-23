## tryy
# PROF TO BOT

**PROF TO BOT** is a Streamlit-based application that records audio, transcribes it using Whisper, and summarizes the content using Groq's Mixtral model. It's designed to help turn lectures and spoken content into structured, easy-to-read notes.

---
## Project Status

**This application is fully functional.** Just add your Groq API key to start using it.

**Note on Deployment:**
Due to technical limitations with PyAudio—which requires direct access to system audio devices—this app cannot be deployed on most cloud platforms. However, it works reliably on local machines.

**Development Time:** Built in approximately 2 hours.

---

## Features

* Record audio through your browser
* Transcribe audio using OpenAI's Whisper (runs locally)
* Summarize text using Groq’s Mixtral language model
* Automatically save summaries with timestamps
* Clean and user-friendly Streamlit interface

---

## Prerequisites

* Python 3.7 or higher
* Working microphone
* Groq API key (free tier available)
* Internet connection (for summarization)

---

## Installation
I am adding the steps to run this(got these written down by ai as they are accurately how it runs)

1. **Clone the project:**

   ```bash
   git clone <your-repo-url>
   cd prof-to-bot
   ```

2. **Install dependencies:**

   ```bash
   pip install streamlit pyaudio wave requests openai-whisper
   ```

   **Windows users:**

   ```bash
   pip install pipwin
   pipwin install pyaudio
   ```

   **macOS users:**

   ```bash
   brew install portaudio
   pip install pyaudio
   ```

3. **Obtain your Groq API key:**

   * Sign up at [Groq Console](https://console.groq.com/)
   * Generate an API key from your dashboard

---

## Configuration

1. Open `try1.py`
2. Find this line:

   ```python
   self.api_key = ""  # add the api key
   ```
3. Replace the empty string with your Groq API key:

   ```python
   self.api_key = "your_groq_api_key_here"
   ```

This is the only required configuration step.

---

## Running the App

1. Open your terminal and run:

   ```bash
   streamlit run try1.py
   ```

2. Use the interface to:

   * Start and stop recordings
   * Transcribe and summarize the audio
   * View or save the results

Summaries are saved to `class_notes.txt`.

---

## File Structure

```
prof-to-bot/
├── try1.py               # Main application script
├── recordings/           # Folder for saved audio files
├── class_notes.txt       # Summary log file
└── README.md             # This documentation
```

---

## Limitations

This app must run locally because:

* PyAudio requires direct access to system-level microphone APIs.
* Web-based environments like Streamlit Cloud or Heroku do not support such access.

---

## Quick Start Guide

1. Install dependencies:

   ```bash
   pip install streamlit pyaudio wave requests openai-whisper
   ```
2. Add your Groq API key to `try1.py`
3. Run:

   ```bash
   streamlit run try1.py
   ```
4. Start recording and summarize your lecture content

---

## Customization

### Recording Quality

Adjust in `AudioRecorder`:

```python
self.RATE = 44100     # Sample rate
self.CHANNELS = 1     # Mono (1) or stereo (2)
self.CHUNK = 1024     # Buffer size
```

### Summary Prompt

Edit the system prompt in `summarize_text` for different tone, depth, or format.

### AI Model

You can use other supported models like:

* `llama2-70b-4096`
* `gemma-7b-it`

Replace the model name in the `GroqAPI` class.

---

## Troubleshooting

* **PyAudio errors:** Refer to the platform-specific installation notes above
* **Microphone permissions:** Ensure access is granted in your system settings
* **No transcription:** Check the clarity of your audio; try re-recording
* **Missing API key:** Double-check your `self.api_key` assignment
* **Slow processing:** The first run downloads Whisper; future runs are faster

---

## Performance Tips

* Record in a quiet environment
* Use a quality microphone
* Limit recordings to under 10 minutes for faster processing
* Ensure your internet connection is stable during summarization

---

## API Notes

* **Groq API:** Used for summarization; free tier available
* **Whisper:** Runs locally with no API cost
---

## Security and Privacy

* Audio is saved only to your local machine
* Transcription is done locally
* Only the transcribed text is sent to the Groq API
* No raw audio is transmitted online
