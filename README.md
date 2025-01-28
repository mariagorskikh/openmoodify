# Moodify

Moodify is a web-based application that transforms YouTube videos into customized audio clips with various vibes. Users can paste a YouTube link, select an emoji representing the desired vibe, and generate an audio clip with effects like reverb and tempo adjustments.

---

## Features
- 🎵 Paste YouTube links and choose from 10 unique vibes using emojis.
- ⚙️ Real-time audio processing with visual feedback and loading animations.
- 💾 Download or play the transformed audio directly in the browser.

---

## Prerequisites
Before you begin, ensure you have the following installed on your system:
- **Python 3.8+**
- **Node.js 14+** (optional for static file serving)
- **pip** (Python package manager)
- **FFmpeg** (for audio processing)

---

## Installation

### 1. Clone the Repository

git clone https://github.com/mariagorskikh/moodify.git
cd moodify

### 2. Install Python Dependencies
bash
Copy
Edit
pip install -r requirements.txt

### 3. Install FFmpeg
Ensure FFmpeg is installed and accessible from your system's PATH:

Windows: Download FFmpeg and add it to your PATH.
Mac/Linux:
bash
Copy
Edit
brew install ffmpeg  # macOS (using Homebrew)
sudo apt install ffmpeg  # Ubuntu/Linux

### 4. Optional: Install Node.js Dependencies
If you want to serve the frontend files using Node.js:

bash
Copy
Edit
npm install
Configuration

## 1. Set Up Environment Variables
Create a .env file in the project directory to store environment variables. This ensures sensitive information isn't hardcoded in the app.

makefile
Copy
Edit
FLASK_ENV=production
API_KEY=your_optional_api_key  # Add if using an external service

## 2. Update the Frontend API URL
Ensure the API URL in script.js points to your backend server:

javascript
Copy
Edit
const BASE_URL = 'http://localhost:5005';  // Update if deploying to a live server
Usage

## 1. Start the Backend Server
Run the Flask app:

bash
Copy
Edit
python app.py
The backend will be available at http://localhost:5005.

## 2. Open the Frontend
### Option 1: Open the index.html file directly in your browser:
Navigate to the project folder and double-click index.html.
### Option 2: Serve the frontend using a static server (Node.js):
bash
Copy
Edit
npx http-server . -p 8080
Visit http://localhost:8080 in your browser.

## How to Use

Paste a YouTube link into the input box.
Select a vibe by clicking an emoji.
Press Enter or wait for the audio to process.
Play the audio, download it, or try another vibe.
API Endpoints

### 1. /api/transform
Method: POST
Payload:
json
Copy
Edit
{
    "url": "YouTube video URL",
    "effect_type": "vibe type (e.g., 'slow_reverb')"
}
Response: Transformed audio file (MP3 format).

### 2. /api/health
Method: GET
Response:
json
Copy
Edit
{
    "status": "healthy"
}
Troubleshooting

### Common Issues
CORS Errors:
Ensure the Flask app allows cross-origin requests (managed using Flask-CORS).
FFmpeg Not Found:
Verify FFmpeg is installed and accessible in your system’s PATH.
YouTube Download Errors:
Update the yt-dlp library:
bash
Copy
Edit
pip install -U yt-dlp
Deployment

Local Deployment
Run the backend server:
bash
Copy
Edit
python app.py
Open index.html in your browser or serve it using Node.js:
bash
Copy
Edit
npx http-server . -p 8080
Production Deployment
Use a production-ready web server like Gunicorn for the backend:
bash
Copy
Edit
pip install gunicorn
gunicorn -w 4 -b 0.0.0.0:5005 app:app
Deploy to a hosting service like Heroku, AWS, or Vercel.
Update the API URL in script.js to point to the live backend.

### License

This project is licensed under the MIT License. See the LICENSE file for details.

### Acknowledgements

yt-dlp for YouTube downloading.
FFmpeg for audio processing.
Flask for the backend framework.

