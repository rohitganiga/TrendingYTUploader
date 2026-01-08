🚀 TrendingYTUploaderAPI Layer for Automated Trending Content Generation & DistributionTrendingYTUploader is a high-performance API backend built with FastAPI. It leverages Google's state-of-the-art Gemini Veo 3.1 model to programmatically generate high-fidelity videos (with native audio) and automatically pushes them to YouTube to capture trending traffic.✨ Key FeaturesVideo Synthesis: Generates cinematic 1080p videos with audio using the veo-3.1-generate model.Automated Uploads: Seamlessly pushes generated assets to YouTube with optimized metadata (Title, Tags, Description).Async Operations: Handles long-running video generation tasks asynchronously with polling mechanisms.Vibe Coding Support: Optimized for rapid iteration and deployment using the latest Google Gen AI SDK.🛠️ Tech StackFramework: FastAPI (Python 3.10+)AI Engine: Gemini Veo 3.1 APIUpload Layer: YouTube Data API v3Task Management: Python asyncio & google-genai SDK📂 Project StructurePlaintextTrendingYTUploader/
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
🚀 Getting Started1. PrerequisitesGoogle AI Studio API Key: Get it from AI Studio.YouTube Data API: Enable in Google Cloud Console and download client_secrets.json.2. InstallationBashgit clone https://github.com/yourusername/TrendingYTUploader.git
cd TrendingYTUploader
pip install -r requirements.txt
3. Environment SetupCreate a .env file in the root:Code snippetGEMINI_API_KEY=your_gemini_key_here
YOUTUBE_CATEGORY_ID=22
4. Running the APIBashuvicorn app.main:app --reload
📡 API EndpointsPOST /generate-and-uploadTriggers the full pipeline: Generate $\rightarrow$ Poll $\rightarrow$ Download $\rightarrow$ Upload.Request Body:JSON{
  "prompt": "A futuristic neon city at night, cinematic drone shot, 4k",
  "title": "The Future is Here",
  "description": "Trending AI generated video using Gemini Veo 3.1"
}
Workflow Logic:Request: FastAPI receives the prompt.Generation: Calls client.models.generate_videos() using veo-3.1-generate-preview.Wait: Polls the operation status until done == True.Transfer: Downloads the video bytes and passes them to the YouTube videos().insert() method.📝 LicenseThis project is licensed under the MIT License.Would you like me to generate the Python code for the gemini_service.py to handle the Veo 3.1 polling logic?How to Upload Videos to YouTube Using Python (YouTube API v3 Tutorial)This video provides a step-by-step guide on setting up the YouTube Data API and the Python code required for the upload portion of your project.