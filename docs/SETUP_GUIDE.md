# 🚀 Complete Setup Guide for ClarityAI

This guide will walk you through setting up ClarityAI from scratch.

## 📋 Prerequisites Checklist

Before you begin, make sure you have:

- [ ] **Flutter SDK** (3.6.0 or higher)
- [ ] **Python** (3.9 or higher)
- [ ] **Git** (for cloning the repository)
- [ ] **Code Editor** (VS Code recommended)
- [ ] **Tavily API Key** ([Get it here](https://tavily.com))
- [ ] **Google Gemini API Key** ([Get it here](https://makersuite.google.com/app/apikey))

---

## 🔧 Step 1: Install Prerequisites

### Install Flutter

#### Windows
1. Download Flutter SDK from [flutter.dev](https://flutter.dev/docs/get-started/install/windows)
2. Extract to `C:\src\flutter`
3. Add to PATH: `C:\src\flutter\bin`
4. Verify: `flutter --version`

#### macOS
```bash
brew install flutter
flutter --version
```

#### Linux
```bash
sudo snap install flutter --classic
flutter --version
```

### Install Python

#### Windows
1. Download from [python.org](https://www.python.org/downloads/)
2. Run installer and check "Add Python to PATH"
3. Verify: `python --version`

#### macOS
```bash
brew install python@3.11
python3 --version
```

#### Linux
```bash
sudo apt update
sudo apt install python3.11 python3-pip
python3 --version
```

---

## 📥 Step 2: Clone the Repository

```bash
# Clone the repository
git clone https://github.com/yourusername/ClarityAI.git

# Navigate to the project directory
cd ClarityAI
```

---

## 🐍 Step 3: Backend Setup

### 1. Navigate to Server Directory
```bash
cd server
```

### 2. Create Virtual Environment

**Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

You should see `(venv)` in your terminal prompt.

### 3. Install Python Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

This will install:
- FastAPI
- Uvicorn
- Google Generative AI (Gemini)
- Tavily Python SDK
- Sentence Transformers
- And more...

### 4. Configure Environment Variables

Create a `.env` file in the `server` directory:

```bash
# Windows
copy .env.example .env
notepad .env

# macOS/Linux
cp .env.example .env
nano .env
```

Add your API keys:
```env
TAVILY_API_KEY=tvly-xxxxxxxxxxxxxxxxxxxxxxxxxx
GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

#### Getting API Keys

**Tavily API Key:**
1. Go to [tavily.com](https://tavily.com)
2. Sign up for a free account
3. Navigate to API Keys section
4. Copy your API key

**Gemini API Key:**
1. Go to [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Sign in with your Google account
3. Click "Create API Key"
4. Copy your API key

### 5. Test the Backend

```bash
# Start the server
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

You should see:
```
INFO:     Uvicorn running on http://0.0.0.0:8000
INFO:     Application startup complete.
```

Visit `http://localhost:8000/docs` to see the API documentation.

**Keep this terminal open!** The server needs to run while using the app.

---

## 📱 Step 4: Frontend Setup

### 1. Open a New Terminal

**Keep the backend server running** and open a new terminal window.

### 2. Navigate to Project Root

```bash
cd ClarityAI  # or wherever you cloned the repo
```

### 3. Install Flutter Dependencies

```bash
flutter pub get
```

This will install:
- Google Fonts
- WebSocket Client
- Flutter Markdown
- Skeletonizer
- And more...

### 4. Verify Flutter Setup

```bash
flutter doctor
```

Fix any issues shown (you may need to install platform-specific tools).

### 5. Configure API Endpoint (if needed)

If your backend runs on a different host/port, edit `lib/services/chat_web_service.dart`:

```dart
final url = Uri.parse('ws://YOUR_HOST:YOUR_PORT/ws/chat');
```

### 6. Run the App

Choose your platform:

**Web (Recommended for development):**
```bash
flutter run -d chrome
```

**Windows:**
```bash
flutter run -d windows
```

**macOS:**
```bash
flutter run -d macos
```

**iOS (requires Xcode on macOS):**
```bash
flutter run -d ios
```

**Android (requires Android Studio):**
```bash
flutter run -d android
```

---

## ✅ Step 5: Verify Everything Works

1. **Backend Check**: Visit `http://localhost:8000/docs` - you should see the FastAPI documentation

2. **Frontend Check**: The Flutter app should open and show the home page

3. **Integration Test**: 
   - Type a question like "What is quantum computing?"
   - Press Enter
   - You should see:
     - Loading animation
     - Search results with sources
     - AI-generated answer streaming in

---

## 🐛 Troubleshooting

### Backend Issues

**Problem: `ModuleNotFoundError`**
```bash
# Solution: Make sure virtual environment is activated
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows
pip install -r requirements.txt
```

**Problem: `API key not found`**
```bash
# Solution: Check your .env file
cat .env  # Should show your API keys
```

**Problem: Port 8000 already in use**
```bash
# Solution: Use a different port
uvicorn main:app --reload --port 8001
# Update Flutter app to use ws://localhost:8001/ws/chat
```

### Frontend Issues

**Problem: `Package not found`**
```bash
# Solution: Run pub get again
flutter pub get
flutter clean
flutter pub get
```

**Problem: WebSocket connection failed**
```bash
# Solution: Make sure backend is running
# Check the URL in chat_web_service.dart matches your backend
```

**Problem: `No device found`**
```bash
# Solution: Check available devices
flutter devices
# Run on Chrome if available
flutter run -d chrome
```

### Common Issues

**Problem: Slow first query**
- **Reason**: Sentence Transformers model downloads on first use (~100MB)
- **Solution**: Wait for the model to download, then it'll be cached

**Problem: No search results**
- **Reason**: Tavily API might be down or rate limited
- **Solution**: Check your API quota at [tavily.com](https://tavily.com)

**Problem: AI not responding**
- **Reason**: Gemini API might be down or rate limited
- **Solution**: Check [Google API status](https://status.cloud.google.com/)

---

## 🎯 Next Steps

Now that you're set up:

1. ✅ Try asking different questions
2. ✅ Explore the codebase
3. ✅ Customize the UI (see `lib/theme/colors.dart`)
4. ✅ Modify the AI prompt (see `server/services/llm_service.py`)
5. ✅ Read [CONTRIBUTING.md](../CONTRIBUTING.md) to contribute

---

## 📚 Additional Resources

- [Flutter Documentation](https://flutter.dev/docs)
- [FastAPI Documentation](https://fastapi.tiangolo.com)
- [Gemini API Guide](https://ai.google.dev/docs)
- [Tavily API Docs](https://docs.tavily.com)

---

## 💡 Tips

- **Development Workflow**: Keep backend terminal and frontend terminal open side-by-side
- **Hot Reload**: Flutter supports hot reload - press `r` in the terminal to reload
- **Backend Changes**: Uvicorn auto-reloads when you save Python files
- **Debugging**: Use `print()` statements or IDE debuggers
- **VS Code Extensions**: Install Flutter, Python, and FastAPI extensions

---

## 🆘 Still Having Issues?

- 📖 Check the [main README](../README.md)
- 🐛 [Open an issue](https://github.com/yourusername/ClarityAI/issues)
- 💬 [Start a discussion](https://github.com/yourusername/ClarityAI/discussions)

---

Happy coding! 🚀

