# tryy
# PROF TO BOT 📝

A Streamlit-based audio recording and summarization application that converts lectures and audio content into structured notes using AI-powered transcription and summarization.

## ✅ WORKING STATUS

**This application works perfectly fine!** You just need to add your Groq API key to get started.

### Deployment Note
We couldn't deploy this application online due to technical limitations with PyAudio - most cloud platforms don't support PyAudio's system-level audio access requirements. However, the application runs flawlessly on local machines.

**⏰ Development Time: Completed in just 2 hours!**

## Features

- **Real-time Audio Recording**: Record audio directly through your browser interface
- **AI Transcription**: Convert audio to text using OpenAI Whisper
- **Smart Summarization**: Generate concise summaries using Groq's Mixtral model
- **Automatic Note Saving**: Save summaries with timestamps to a text file
- **User-friendly Interface**: Clean, intuitive Streamlit web interface

## Prerequisites

- Python 3.7 or higher
- A working microphone
- Groq API key (free tier available)
- Internet connection for API calls

## Installation

1. **Clone or download the project files**
   ```bash
   git clone <your-repo-url>
   cd prof-to-bot
   ```

2. **Install required dependencies**
   ```bash
   pip install streamlit pyaudio wave requests openai-whisper
   ```

   **Note for Windows users**: If you encounter issues with PyAudio installation, try:
   ```bash
   pip install pipwin
   pipwin install pyaudio
   ```

   **Note for macOS users**: You might need to install PortAudio first:
   ```bash
   brew install portaudio
   pip install pyaudio
   ```

3. **Get your Groq API key**
   - Visit [Groq Console](https://console.groq.com/)
   - Sign up for a free account
   - Generate an API key
   - Keep this key handy for the next step

## Configuration

1. **Set up your API key (REQUIRED)**
   - Open `try1.py`
   - Find line 74: `self.api_key = ""#add the api key`
   - Replace with your actual Groq API key:
     ```python
     self.api_key = "your_groq_api_key_here"
     ```
   - **This is the ONLY step needed to make the app work!**

2. **Verify dependencies**
   - Ensure all required packages are installed
   - Test your microphone permissions

## Usage

1. **Start the application**
   ```bash
   streamlit run try1.py
   ```

2. **Record audio**
   - Click "🎙️ Start Recording" to begin
   - Speak clearly into your microphone
   - Click "⏹️ Stop Recording" when finished

3. **Generate notes**
   - Play back your recording to verify quality
   - Click "🤖 Transcribe and Summarize"
   - Wait for the AI to process your audio

4. **Access your notes**
   - View the transcription and summary on screen
   - Find saved summaries in `class_notes.txt`

## File Structure

```
prof-to-bot/
├── try1.py                 # Main application file
├── recordings/             # Auto-created directory for audio files
├── class_notes.txt         # Auto-created file for saved summaries
└── README.md              # This file
```

## Why No Online Deployment?

**Technical Limitation**: PyAudio requires system-level access to audio hardware, which is not supported by most cloud deployment platforms (Streamlit Cloud, Heroku, etc.). This is a common limitation for audio recording applications.

**Solution**: The app works perfectly when run locally on your machine where it can access your microphone directly.

## Quick Start (Really Quick!)

1. Install dependencies: `pip install streamlit pyaudio wave requests openai-whisper`
2. Add your Groq API key to line 74 in `try1.py`
3. Run: `streamlit run try1.py`
4. Start recording and generating summaries!

## Key Components

### AudioRecorder Class
- Handles PyAudio integration
- Manages recording sessions
- Saves audio as WAV files

### GroqAPI Class
- Interfaces with Groq's API
- Uses Mixtral-8x7b model for summarization
- Handles error management and logging

### Transcription
- Uses OpenAI Whisper for speech-to-text
- Supports multiple languages
- Runs locally for privacy

## Customization Options

### Change Recording Quality
Modify these parameters in the `AudioRecorder` class:
```python
self.RATE = 44100      # Sample rate (higher = better quality)
self.CHANNELS = 1      # Mono (1) or Stereo (2)
self.CHUNK = 1024      # Buffer size
```

### Adjust Summary Style
Modify the prompt in the `summarize_text` method:
```python
{"role": "user", "content": f"""Your custom prompt here: {text}"""}
```

### Change AI Model
Replace `"mixtral-8x7b-32768"` with other Groq-supported models:
- `"llama2-70b-4096"`
- `"gemma-7b-it"`

## Troubleshooting

### Common Issues

**"No module named 'pyaudio'"**
- Install PyAudio using the platform-specific instructions above

**"Permission denied" for microphone**
- Check browser/system microphone permissions
- Restart the application after granting permissions

**"API key not found" error**
- Verify your Groq API key is correctly set in the code
- Check that your API key is active and has remaining credits

**Poor transcription quality**
- Ensure clear audio input
- Check microphone levels
- Record in a quiet environment
- Consider using a better microphone

**Slow processing**
- First run downloads Whisper model (takes time)
- Subsequent runs will be faster
- Consider using smaller Whisper model for speed

### Performance Tips

- Close other audio applications while recording
- Use a good quality microphone for better transcription
- Keep recordings under 10 minutes for optimal processing
- Ensure stable internet connection for API calls

## API Usage and Costs

- **Groq API**: Free tier includes generous usage limits
- **OpenAI Whisper**: Runs locally, no API costs
- Check [Groq pricing](https://groq.com/pricing/) for current rates

## Privacy and Security

- Audio files are stored locally in the `recordings/` folder
- Transcription happens locally using Whisper
- Only transcribed text is sent to Groq API for summarization
- No audio data is transmitted over the internet

## Contributing

Feel free to submit issues, feature requests, or pull requests to improve the application.

## License

This project is open source. Please check the license file for details.

## Support

For technical issues:
1. Check the troubleshooting section above
2. Verify all dependencies are correctly installed
3. Ensure API keys are properly configured
4. Check the console output for detailed error messages

---

**Happy note-taking! 📚✨**
