# 🎮 Astrocade Mini

A chat-based 3D scene builder powered by AI. Describe what you want to see and watch it appear in a live Three.js scene.

![Astrocade Mini](screenshots/demo.png)

## Features

- **Chat-based 3D scene editing** — Describe objects, modifications, and interactions in natural language
- **Persistent scene state** — Objects are tracked by name and can be referenced and modified in follow-up messages
- **Animations** — Ask for objects to rotate, bounce, orbit, or any other animation
- **Play/Stop mode** — Toggle animations on and off
- **Orbit controls** — Click and drag to rotate the camera, scroll to zoom
- **Conversation memory** — The AI remembers what's in your scene and can modify existing objects
- **One-click suggestions** — Quick-start prompts to get building immediately

## Quick Start

### Prerequisites
- [Node.js](https://nodejs.org/) (v18 or higher)
- A free [Gemini API key](https://aistudio.google.com/apikey)

### Setup

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/astrocade-mini.git
cd astrocade-mini

# Install dependencies
npm install

# Create your .env file
cp .env.example .env
# Edit .env and add your Gemini API key

# Start the server
npm start
```

Then open **http://localhost:3000** in your browser.

## How It Works

1. You type a description in the chat (e.g., "add a red sphere that bounces")
2. The message is sent to the Gemini API with a system prompt that instructs it to generate Three.js code
3. The generated code is executed in the browser, modifying the live 3D scene
4. Objects are tracked in a named registry so you can reference and modify them later

### Architecture

```
astrocade-mini/
├── server/
│   └── index.js          # Express server + Gemini API integration
├── public/
│   └── index.html         # Three.js scene + chat UI (single-file frontend)
├── .env.example           # Environment variable template
├── package.json
└── README.md
```

- **Backend**: Express.js server that proxies chat messages to the Gemini API and manages conversation history
- **Frontend**: Single HTML file with Three.js for 3D rendering and a custom chat interface
- **AI**: Gemini 2.0 Flash generates Three.js code snippets that are executed in the browser context

## Example Prompts

- "Create a blue cube in the center"
- "Make the cube rotate slowly"
- "Add a ring of trees around the cube"
- "Build a little house with a red roof and a chimney"
- "Create a solar system with orbiting planets"
- "Add a particle fountain that shoots colored spheres upward"
- "Make a snowman with a carrot nose"

## Tech Stack

- **Three.js** (r128) — 3D rendering
- **Express.js** — Backend server
- **Google Gemini 2.0 Flash** — AI code generation
- **Vanilla JS** — Frontend (no build step needed)

## License

MIT
