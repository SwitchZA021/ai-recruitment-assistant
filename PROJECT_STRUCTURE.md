# Project Structure

This project follows a structure that combines Electron with React/TypeScript for the frontend and Python for the backend AI processing.

```
ai-recruitment-assistant/
├── .github/                     # GitHub configuration
├── public/                      # Static assets for the Electron app
├── src/                         # Frontend source code
│   ├── main/                    # Electron main process
│   │   ├── main.ts              # Main entry point for Electron
│   │   ├── with-python.ts       # Handles Python process management
│   │   └── preload.ts           # Preload script for renderer process
│   │
│   ├── renderer/                # Frontend React code (renderer process)
│   │   ├── components/          # Reusable React components
│   │   │   ├── LeftPanel/       # Job spec input panel
│   │   │   ├── MiddlePanel/     # Generated content panel
│   │   │   ├── RightPanel/      # AI assistant chat panel
│   │   │   └── Layout/          # Layout components
│   │   │
│   │   ├── contexts/            # React context providers
│   │   ├── hooks/               # Custom React hooks
│   │   ├── services/            # Frontend services
│   │   ├── types/               # TypeScript type definitions
│   │   ├── utils/               # Utility functions
│   │   ├── App.tsx              # Main App component
│   │   └── index.tsx            # Renderer entry point
│   │
│   └── shared/                  # Shared code between main and renderer
│
├── python/                      # Python backend code
│   ├── ai/                      # AI processing modules
│   │   ├── models/              # AI model integrations
│   │   │   ├── openai.py        # OpenAI integration
│   │   │   ├── gemini.py        # Gemini integration
│   │   │   └── deepseek.py      # DeepSeek integration
│   │   │
│   │   ├── prompts/             # AI prompt templates
│   │   └── utils/               # AI utility functions
│   │
│   ├── api/                     # API endpoints for frontend communication
│   │   ├── api.py               # Main API entry point
│   │   ├── routes/              # API route handlers
│   │   └── models/              # API data models
│   │
│   ├── services/                # Backend services
│   │   ├── content_generator.py # Content generation service
│   │   ├── job_restructurer.py  # Job restructuring service
│   │   └── template_manager.py  # Template management service
│   │
│   └── utils/                   # Utility functions
│       ├── logger.py            # Logging utilities
│       └── file_manager.py      # File management utilities
│
├── logs/                        # Application logs directory
├── templates/                   # Template files for generated content
├── electron-builder.config.js   # Electron builder configuration
├── package.json                 # Node dependencies and scripts
├── tsconfig.json                # TypeScript configuration
├── webpack.config.js            # Webpack configuration
├── requirements.txt             # Python dependencies
└── README.md                    # Project documentation
```

## Technology Stack

- **Electron**: Cross-platform desktop framework
- **React + TypeScript**: Frontend UI with static typing
- **Python**: Backend processing with AI capabilities
- **Flask**: API server for frontend-backend communication
- **react-resizable-panels**: For the three-panel layout
- **AI Libraries**: 
  - OpenAI API
  - Gemini API
  - DeepSeek API

## Development Workflow

1. The Electron main process spawns the Python Flask server on app startup
2. The React frontend communicates with the Python backend via API calls
3. The Python backend processes requests using AI models and returns results
4. The frontend displays the results in the appropriate panel

## Building and Packaging

The application uses:
- Webpack for bundling the frontend
- PyInstaller for packaging the Python backend
- electron-builder for creating the final desktop application

This structure creates a standalone executable that bundles all necessary components for Windows, macOS and Linux.