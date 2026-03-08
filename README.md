# Backend - AI Student Companion

Complete API backend for the AI Student Companion platform with 5 core AI features.

## Features
- 🎓 **AI Tutor** - Concept explanation with leveled learning
- 💼 **Interview Prep Bot** - Mock interviews with evaluation
- 📝 **Notes Generator** - Convert lectures/PDFs to structured notes
- 🐛 **Code Debugger** - AI-powered code analysis and fixing
- 📊 **Quiz Generator** - Dynamic quizzes for revision

## Project Structure

```
backend/
├── src/
│   ├── server.js              # Main server entry point
│   ├── config/
│   │   └── constants.js       # App-wide constants
│   ├── middleware/
│   │   ├── errorHandler.js    # Global error handling
│   │   └── logger.js          # Request logging
│   ├── services/
│   │   └── aiService.js       # OpenAI/Claude API integration
│   ├── routes/
│   │   ├── tutor.js
│   │   ├── interview.js
│   │   ├── notes.js
│   │   ├── debugger.js
│   │   ├── quiz.js
│   │   └── auth.js
│   └── controllers/
│       ├── tutorController.js
│       ├── interviewController.js
│       ├── notesController.js
│       ├── debuggerController.js
│       ├── quizController.js
│       └── authController.js
├── .env.example               # Environment template
├── .gitignore
└── package.json
```

## Setup

### 1. Install Dependencies
```bash
cd backend
npm install
```

### 2. Configure Environment
```bash
cp .env.example .env
```

Edit `.env` with your settings:
```env
OPENAI_API_KEY=your_key_here
PORT=5000
MONGODB_URI=mongodb://localhost:27017/ai-student-companion
JWT_SECRET=your_secret
```

### 3. Run Development Server
```bash
npm run dev
```

Server runs on `http://localhost:5000`

## API Endpoints

### Health Check
- `GET /api/health` - API status

### Authentication
- `POST /api/auth/register` - Register user
- `POST /api/auth/login` - Login user
- `POST /api/auth/logout` - Logout user

### AI Tutor
- `POST /api/tutor/explain` - Get concept explanation
- `GET /api/tutor/history` - Get explanation history

### Interview Prep
- `GET /api/interview/question` - Get interview question
- `POST /api/interview/evaluate` - Evaluate answer
- `GET /api/interview/sessions` - Get session history

### Notes Generator
- `POST /api/notes/generate` - Generate notes from text
- `GET /api/notes/list` - Get all notes
- `GET /api/notes/:id` - Get specific note
- `DELETE /api/notes/:id` - Delete note

### Code Debugger
- `POST /api/debugger/analyze` - Analyze & debug code
- `GET /api/debugger/history` - Get debug history

### Quiz Generator
- `GET /api/quiz/question` - Get quiz question
- `POST /api/quiz/submit` - Submit answer
- `GET /api/quiz/results` - Get results

## Example Requests

### Explain a Concept
```bash
curl -X POST http://localhost:5000/api/tutor/explain \
  -H "Content-Type: application/json" \
  -d '{"topic":"Python decorators","level":"intermediate"}'
```

### Debug Code
```bash
curl -X POST http://localhost:5000/api/debugger/analyze \
  -H "Content-Type: application/json" \
  -d '{"code":"x = 5\nprint(y)","language":"python"}'
```

### Generate Notes
```bash
curl -X POST http://localhost:5000/api/notes/generate \
  -H "Content-Type: application/json" \
  -d '{"text":"Long lecture content here...","format":"bullet"}'
```

## Next Steps
- [ ] Connect MongoDB for persistence
- [ ] Implement JWT authentication middleware
- [ ] Add database models (User, Note, Quiz, etc.)
- [ ] Implement rate limiting
- [ ] Add input validation
- [ ] Deploy to production

## Technology Stack
- **Runtime**: Node.js
- **Framework**: Express.js
- **AI Integration**: OpenAI API
- **Database**: MongoDB (ready to integrate)
- **Auth**: JWT + bcryptjs
- **Validation**: express-validator

## License
MIT
