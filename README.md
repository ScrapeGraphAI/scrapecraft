# ScrapeCraft - AI-Powered Web Scraping Editor

ScrapeCraft is a web-based scraping editor similar to Cursor but specialized for web scraping. It uses AI assistance to help users build scraping pipelines with the ScrapeGraphAI API.

https://github.com/user-attachments/assets/defaf7ad-23da-40b7-82cd-3b2a4d1d22c9

[![API Banner](https://raw.githubusercontent.com/ScrapeGraphAI/Scrapegraph-ai/main/docs/assets/api_banner.png)](https://scrapegraphai.com/?utm_source=github&utm_medium=readme&utm_campaign=api_banner&utm_content=api_banner_image)
## Features

- 🤖 AI-powered assistant using OpenRouter (Kimi-k2 model)
- 🔗 Multi-URL bulk scraping support
- 📋 Dynamic schema definition with Pydantic
- 💻 Python code generation with async support
- 🚀 Real-time WebSocket streaming
- 📊 Results visualization (table & JSON views)
- 🔄 Auto-updating deployment with Watchtower

## Tech Stack

- **Backend**: FastAPI, LangGraph, ScrapeGraphAI
- **Frontend**: React, TypeScript, Tailwind CSS
- **Database**: PostgreSQL
- **Cache**: Redis
- **Deployment**: Docker, Docker Compose, Watchtower

## Prerequisites

- Docker and Docker Compose
- OpenRouter API key (Get it from [OpenRouter](https://openrouter.ai/keys))
- ScrapeGraphAI API key (Get it from [ScrapeGraphAI](https://scrapegraphai.com/auth/login))

## Quick Start with Docker

1. **Clone the repository**
   ```bash
   git clone https://github.com/ScrapeGraphAI/scrapecraft.git
   cd scrapecraft
   ```

2. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Edit the `.env` file and add your API keys:
   - `OPENROUTER_API_KEY`: Get from [OpenRouter](https://openrouter.ai/keys)
   - `SCRAPEGRAPH_API_KEY`: Get from [ScrapeGraphAI](https://scrapegraphai.com/auth/login)

3. **Start the application with Docker**
   ```bash
   docker compose up -d
   ```

4. **Access the application**
   - Frontend: http://localhost:3000
   - API: http://localhost:8000
   - API Docs: http://localhost:8000/docs

5. **Stop the application**
   ```bash
   docker compose down
   ```

## Development Mode

If you want to run the application in development mode without Docker:

### Backend Development
```bash
cd backend
pip install -r requirements.txt
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### Frontend Development
```bash
cd frontend
npm install
npm start
```

## Usage

1. **Create a Pipeline**: Click "New Pipeline" to start
2. **Add URLs**: Use the URL Manager to add websites to scrape
3. **Define Schema**: Create fields for data extraction
4. **Generate Code**: Ask the AI to generate scraping code
5. **Execute**: Run the pipeline to scrape data
6. **Export Results**: Download as JSON or CSV

## Remote Updates

The application includes Watchtower for automatic updates:

1. Push new Docker images to your registry
2. Watchtower will automatically detect and update containers
3. No manual intervention required

## API Endpoints

- `POST /api/chat/message` - Send message to AI assistant
- `GET /api/pipelines` - List all pipelines
- `POST /api/pipelines` - Create new pipeline
- `PUT /api/pipelines/{id}` - Update pipeline
- `POST /api/pipelines/{id}/run` - Execute pipeline
- `WS /ws/{pipeline_id}` - WebSocket connection

## Environment Variables

| Variable | Description | How to Get |
|----------|-------------|------------|
| OPENROUTER_API_KEY | Your OpenRouter API key | [Get API Key](https://openrouter.ai/keys) |
| SCRAPEGRAPH_API_KEY | Your ScrapeGraphAI API key | [Get API Key](https://scrapegraphai.com/auth/login) |
| JWT_SECRET | Secret key for JWT tokens | Generate a random string |
| DATABASE_URL | PostgreSQL connection string | Auto-configured with Docker |
| REDIS_URL | Redis connection string | Auto-configured with Docker |

## License

MIT
