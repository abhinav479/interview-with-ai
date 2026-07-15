# AI Interviewer

AI Interviewer is a real-time voice-based technical interview platform that analyzes a candidate's GitHub profile, conducts an AI-led interview, stores the conversation transcript, and generates a final score with feedback.

## Features

- Real-time AI interview sessions using OpenAI Realtime API
- Voice-based interaction through WebRTC and WebSocket sideband events
- GitHub profile scraping to personalize interview questions
- Interview transcript storage with user and assistant messages
- Automated interview scoring and feedback using Google Gemini
- PostgreSQL-backed persistence using Prisma ORM
- React-based frontend with route-based interview and result pages

## Tech Stack

### Frontend

- React 19
- TypeScript
- React Router
- Tailwind CSS
- Radix UI
- Lucide React
- Sonner
- Bun

### Backend

- Bun
- Express.js
- TypeScript
- WebSocket
- OpenAI Realtime API
- Google Gemini API
- Zod
- Axios

### Database

- PostgreSQL
- Prisma ORM
- Prisma PostgreSQL adapter

### Tooling

- Turborepo
- Bun workspaces
- Prettier
- Shared TypeScript and ESLint configuration packages

## Project Structure

```text
ai-interviewer/
├── apps/
│   ├── frontend/          # React frontend application
│   └── backend/           # Express/Bun backend API
├── packages/
│   ├── ui/                # Shared React UI package
│   ├── eslint-config/     # Shared ESLint configuration
│   └── typescript-config/ # Shared TypeScript configuration
├── package.json
├── turbo.json
└── bun.lock
```

## How It Works

1. The user submits their GitHub profile URL.
2. The backend extracts GitHub metadata and creates a new interview session.
3. The frontend starts a real-time interview session with OpenAI Realtime API.
4. OpenAI conducts the interview using the candidate's GitHub metadata as context.
5. User and assistant messages are stored in PostgreSQL.
6. Gemini evaluates the transcript and returns a score with feedback.
7. The frontend displays the final interview result.

## Getting Started

### Prerequisites

- Bun 1.3.11 or later
- Node.js 18 or later
- PostgreSQL database
- OpenAI API key
- Google Gemini API key

### Installation

```bash
bun install
```

### Environment Variables

Create an environment file for the backend and add the required variables:

```env
DATABASE_URL="postgresql://USER:PASSWORD@HOST:PORT/DATABASE"
OPENAI_KEY="your_openai_api_key"
GEMINI_API_KEY="your_gemini_api_key"
```

### Database Setup

Run Prisma migrations or push the schema to your PostgreSQL database:

```bash
cd apps/backend
bunx prisma db push
```

### Run the App

From the root directory:

```bash
bun run dev
```

The backend runs on:

```text
http://localhost:3001
```

The frontend runs using Bun's development server.

## API Overview

### Create Pre-Interview Session

```http
POST /api/v1/pre-interview
```

Creates an interview session after processing the candidate's GitHub profile.

### Start Interview Session

```http
POST /api/v1/session/:interviewId
```

Starts a real-time OpenAI interview session.

### Save User Response

```http
POST /api/v1/session/user/response/:interviewId
```

Stores a user response in the interview transcript.

### Get Interview Result

```http
GET /api/v1/result/:interviewId
```

Returns the final score, feedback, transcript, and interview status.

## Resume Highlights

- Built an AI interview platform using React, TypeScript, Bun, and Express, enabling real-time voice-based technical interviews.
- Integrated OpenAI Realtime API, WebRTC, WebSocket sideband events, and Gemini for live conversations and automated evaluation.
- Designed a PostgreSQL and Prisma data layer to persist interview sessions, transcripts, GitHub metadata, scores, and feedback.

## License

This project is for educational and portfolio use.
