# 🚀 TrendingYTUploader

API Layer for Automated Trending Content Generation & Distribution

TrendingYTUploader is a high-performance API backend built with FastAPI. It leverages Google's state-of-the-art Gemini Veo 3.1 model to programmatically generate high-fidelity videos (with native audio) and automatically pushes them to YouTube to capture trending traffic.

## ✨ Key Features

- **Video Synthesis**: Generates cinematic 1080p videos with audio using the veo-3.1-generate model
- **Automated Uploads**: Seamlessly pushes generated assets to YouTube with optimized metadata (Title, Tags, Description)
- **Async Operations**: Handles long-running video generation tasks asynchronously with polling mechanisms
- **Vibe Coding Support**: Optimized for rapid iteration and deployment using the latest Google Gen AI SDK

## 🛠️ Tech Stack

- **Framework**: FastAPI (Python 3.10+)
- **AI Engine**: Gemini Veo 3.1 API
- **Upload Layer**: YouTube Data API v3
- **Task Management**: Python asyncio & google-genai SDK

## 📂 Project Structure

```
TrendingYTUploader/
├── app/
│   ├── main.py              # FastAPI Entry Point
│   ├── services/
│   │   ├── gemini_service.py # Veo 3.1 Video Generation Logic
│   │   └── youtube_service.py # YouTube Data API Integration
│   └── utils/
│       └── auth.py          # OAuth2 & API Key Management
├── client_secrets.json      # YouTube API Credentials
├── .env                     # Environment Variables
├── requirements.txt
└── README.md
```

## 🚀 Getting Started

### 1. Prerequisites

- **Google AI Studio API Key**: Get it from [AI Studio](https://aistudio.google.com/)
- **YouTube Data API**: Enable in Google Cloud Console and download `client_secrets.json`

### 2. Installation

```bash
git clone https://github.com/yourusername/TrendingYTUploader.git
cd TrendingYTUploader
pip install -r requirements.txt
```

### 3. Environment Setup

Create a `.env` file in the root:

```env
GEMINI_API_KEY=your_gemini_key_here
YOUTUBE_CATEGORY_ID=22
```

### 4. Running the API

```bash
uvicorn app.main:app --reload
```

## 📡 API Endpoints

### POST /generate-and-upload

Triggers the full pipeline: Generate → Poll → Download → Upload.

**Request Body:**

```json
{
  "prompt": "A futuristic neon city at night, cinematic drone shot, 4k",
  "title": "The Future is Here",
  "description": "Trending AI generated video using Gemini Veo 3.1"
}
```

**Workflow Logic:**

1. **Request**: FastAPI receives the prompt
2. **Generation**: Calls `client.models.generate_videos()` using `veo-3.1-generate-preview`
3. **Wait**: Polls the operation status until `done == True`
4. **Transfer**: Downloads the video bytes and passes them to the YouTube `videos().insert()` method

## 📝 License

This project is licensed under the MIT License.

## 🎥 Resources

- [How to Upload Videos to YouTube Using Python (YouTube API v3 Tutorial)](https://www.youtube.com/watch?v=IqA1J374VTQ) - Step-by-step guide on setting up the YouTube Data API and the Python code required for the upload portion of your project.

---

**Need the implementation code?** Check out `gemini_service.py` for the Veo 3.1 polling logic!
