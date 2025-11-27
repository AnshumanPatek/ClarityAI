# 🔍 ClarityAI

<div align="center">

**An intelligent AI-powered search engine inspired by Perplexity AI**

[![Flutter](https://img.shields.io/badge/Flutter-3.6.0-02569B?logo=flutter)](https://flutter.dev)
[![FastAPI](https://img.shields.io/badge/FastAPI-Latest-009688?logo=fastapi)](https://fastapi.tiangolo.com)
[![Gemini](https://img.shields.io/badge/Gemini-2.0%20Flash-4285F4?logo=google)](https://deepmind.google/technologies/gemini/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

*Ask questions. Get answers. Backed by sources.*

[Features](#-features) • [Architecture](#-architecture) • [Setup](#-getting-started) • [Demo](#-demo)

</div>

---

## 📖 About

ClarityAI is a modern, open-source AI search assistant that combines the power of **real-time web search** with **advanced language models** to provide accurate, well-cited answers to your questions. Built with Flutter for a beautiful cross-platform experience and powered by FastAPI + Google Gemini on the backend.

### Why ClarityAI?

- 🎯 **Source-Backed Answers**: Every response is grounded in real web search results
- ⚡ **Real-Time Streaming**: See answers generate in real-time via WebSocket
- 🧠 **Smart Ranking**: Semantic similarity scoring ensures the most relevant sources
- 🌐 **Cross-Platform**: Works on Web, iOS, Android, Windows, macOS, and Linux
- 🎨 **Modern UI**: Clean, intuitive interface inspired by Perplexity AI

---

## ✨ Features

### 🔎 **Intelligent Search**
- Real-time web search powered by [Tavily API](https://tavily.com)
- Fetches up to 10 relevant sources per query
- Advanced content extraction using Trafilatura

### 🤖 **AI-Powered Responses**
- Powered by Google's **Gemini 2.0 Flash** model
- Streaming responses for instant feedback
- Context-aware answers based on retrieved sources
- Deep reasoning with comprehensive explanations

### 📊 **Smart Source Ranking**
- Semantic similarity using Sentence Transformers (`all-miniLM-L6-v2`)
- Relevance scoring with configurable thresholds
- Sources sorted by relevance to your query

### 💬 **Real-Time Communication**
- WebSocket-based streaming for live updates
- Progressive answer rendering
- Smooth, responsive user experience

### 🎨 **Beautiful Interface**
- Material Design 3 with custom theming
- Google Fonts (Inter) for elegant typography
- Responsive layout for all screen sizes
- Markdown rendering for formatted responses
- Skeleton loading states for better UX

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Flutter Frontend                         │
│  ┌────────────┐  ┌────────────┐  ┌─────────────────────┐   │
│  │  HomePage  │  │  ChatPage  │  │  WebSocket Service  │   │
│  └────────────┘  └────────────┘  └─────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
                           │
                    WebSocket (ws://)
                           │
┌─────────────────────────────────────────────────────────────┐
│                     FastAPI Backend                          │
│  ┌─────────────────────────────────────────────────────┐   │
│  │              WebSocket Endpoint (/ws/chat)           │   │
│  └─────────────────────────────────────────────────────┘   │
│                           │                                  │
│     ┌────────────────────┼────────────────────┐            │
│     ▼                    ▼                     ▼            │
│  ┌──────────┐     ┌──────────────┐     ┌─────────────┐    │
│  │  Search  │     │ Sort Source  │     │  LLM        │    │
│  │  Service │     │ Service      │     │  Service    │    │
│  └──────────┘     └──────────────┘     └─────────────┘    │
│      │                    │                     │           │
│      ▼                    ▼                     ▼           │
│  Tavily API    Sentence Transformers    Gemini 2.0 Flash   │
└─────────────────────────────────────────────────────────────┘
```

### Tech Stack

#### Frontend
- **Framework**: Flutter 3.6.0+ (Dart)
- **UI Components**: Material Design 3
- **Fonts**: Google Fonts (Inter)
- **Markdown**: flutter_markdown
- **WebSocket**: web_socket_client
- **Loading States**: Skeletonizer

#### Backend
- **Framework**: FastAPI (Python)
- **LLM**: Google Gemini 2.0 Flash
- **Search API**: Tavily
- **Content Extraction**: Trafilatura
- **Embeddings**: Sentence Transformers (all-miniLM-L6-v2)
- **Vector Operations**: NumPy

---

## 🚀 Getting Started

### Prerequisites

- **Flutter SDK**: 3.6.0 or higher ([Install Flutter](https://flutter.dev/docs/get-started/install))
- **Python**: 3.9 or higher
- **API Keys**:
  - [Tavily API Key](https://tavily.com) (for web search)
  - [Google Gemini API Key](https://makersuite.google.com/app/apikey) (for AI responses)

### Backend Setup

1. **Navigate to the server directory**
   ```bash
   cd server
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   
   # Activate on Windows
   venv\Scripts\activate
   
   # Activate on macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   
   Create a `.env` file in the `server` directory:
   ```env
   TAVILY_API_KEY=your_tavily_api_key_here
   GEMINI_API_KEY=your_gemini_api_key_here
   ```

5. **Start the server**
   ```bash
   uvicorn main:app --reload --host 0.0.0.0 --port 8000
   ```

   The API will be available at `http://localhost:8000`

### Frontend Setup

1. **Navigate to the project root**
   ```bash
   cd ..
   ```

2. **Install Flutter dependencies**
   ```bash
   flutter pub get
   ```

3. **Configure the API endpoint** (if needed)
   
   Update the WebSocket URL in `lib/services/chat_web_service.dart` if your backend runs on a different host/port.

4. **Run the app**
   
   ```bash
   # For Web
   flutter run -d chrome
   
   # For Windows
   flutter run -d windows
   
   # For iOS (macOS only)
   flutter run -d ios
   
   # For Android
   flutter run -d android
   ```

---

## 📦 Dependencies

### Backend (`server/`)

Create a `requirements.txt` file with:

```txt
fastapi==0.115.0
uvicorn[standard]==0.30.0
python-dotenv==1.0.1
pydantic==2.9.0
pydantic-settings==2.5.0
tavily-python==0.5.0
google-generativeai==0.8.3
trafilatura==1.12.2
sentence-transformers==3.3.1
numpy==2.1.3
websockets==14.1
```

Install with:
```bash
pip install -r requirements.txt
```

### Frontend (Managed by `pubspec.yaml`)

Key dependencies:
- `google_fonts`: Beautiful typography
- `web_socket_client`: Real-time communication
- `flutter_markdown`: Render formatted responses
- `skeletonizer`: Loading animations

---

## 🎯 Usage

1. **Start the backend server** (see Backend Setup)

2. **Launch the Flutter app**

3. **Ask a question**:
   - Type your question in the search bar
   - Press Enter or click the search button

4. **View results**:
   - Sources appear first with relevance scores
   - AI-generated answer streams in real-time
   - Click sources to view original content

---

## 🛠️ Project Structure

```
ClarityAI/
├── lib/                          # Flutter frontend
│   ├── main.dart                 # App entry point
│   ├── pages/
│   │   ├── home_page.dart        # Landing page
│   │   └── chat_page.dart        # Results page
│   ├── services/
│   │   └── chat_web_service.dart # WebSocket client
│   ├── widgets/
│   │   ├── answer_section.dart   # AI response display
│   │   ├── sources_section.dart  # Sources display
│   │   ├── search_bar_button.dart
│   │   ├── search_section.dart
│   │   ├── side_bar.dart
│   │   └── side_bar_button.dart
│   └── theme/
│       └── colors.dart           # App color scheme
│
├── server/                       # FastAPI backend
│   ├── main.py                   # API entry point
│   ├── config.py                 # Environment configuration
│   ├── pydantic_models/
│   │   └── chat_body.py          # Request models
│   └── services/
│       ├── llm_service.py        # Gemini integration
│       ├── search_service.py     # Tavily search
│       └── sort_source_service.py # Relevance ranking
│
├── pubspec.yaml                  # Flutter dependencies
├── requirements.txt              # Python dependencies
└── README.md                     # This file
```

---

## 🔧 Configuration

### Backend Configuration

Edit `server/.env`:

```env
# Required API Keys
TAVILY_API_KEY=tvly-xxxxxxxxxxxxx
GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxx

# Optional: Adjust server settings in main.py
# - Search result count (default: 10)
# - Relevance threshold (default: 0.3)
# - WebSocket delay (default: 0.1s)
```

### Frontend Configuration

Edit `lib/services/chat_web_service.dart` to change the API endpoint:

```dart
final url = Uri.parse('ws://localhost:8000/ws/chat');
```

---

## 🎨 Customization

### Change Color Scheme

Edit `lib/theme/colors.dart`:

```dart
class AppColors {
  static const Color background = Color(0xFF191919);
  static const Color whiteColor = Color(0xFFFFFFFF);
  static const Color submitButton = Color(0xFF20808D);
  // Add more colors...
}
```

### Adjust AI Behavior

Edit `server/services/llm_service.py`:

```python
full_prompt = f"""
Context from web search:
{context_text}

Query: {query}

[Customize your prompt here]
"""
```

### Change Search Results Count

Edit `server/services/search_service.py`:

```python
response = tavily_client.search(query, max_results=10)  # Adjust number
```

---

## 🧪 API Endpoints

### WebSocket Endpoint

**`/ws/chat`** - Real-time chat with streaming responses

**Request** (JSON):
```json
{
  "query": "What is quantum computing?"
}
```

**Response Stream**:
```json
// First message: Search results
{
  "type": "search_result",
  "data": [
    {
      "title": "Quantum Computing Explained",
      "url": "https://example.com",
      "content": "...",
      "relevance_score": 0.87
    }
  ]
}

// Subsequent messages: Content chunks
{
  "type": "content",
  "data": "Quantum computing is..."
}
```

### REST Endpoint

**`POST /chat`** - Traditional chat endpoint (non-streaming)

**Request Body**:
```json
{
  "query": "What is quantum computing?"
}
```

---

## 🌟 Features Roadmap

- [ ] **Chat History**: Save and retrieve previous conversations
- [ ] **Follow-up Questions**: Context-aware follow-up queries
- [ ] **User Accounts**: Authentication and personalization
- [ ] **Source Citations**: Inline citations in responses
- [ ] **Export Answers**: PDF/Markdown export
- [ ] **Dark/Light Theme Toggle**
- [ ] **Multiple AI Models**: Support for different LLMs
- [ ] **Voice Input**: Speech-to-text queries
- [ ] **Mobile Optimization**: Enhanced mobile experience

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b feature/amazing-feature`)
3. **Commit your changes** (`git commit -m 'Add amazing feature'`)
4. **Push to the branch** (`git push origin feature/amazing-feature`)
5. **Open a Pull Request**

---

## 📝 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Perplexity AI** - Inspiration for the concept
- **Google Gemini** - Powerful language model
- **Tavily** - Excellent search API
- **Flutter Team** - Amazing cross-platform framework
- **FastAPI** - Lightning-fast Python web framework

---

## 📧 Contact

Have questions or suggestions? Feel free to:

- 🐛 [Open an issue](../../issues)
- 💬 [Start a discussion](../../discussions)
- ⭐ Star this repo if you find it useful!

---

<div align="center">

**Built with ❤️ using Flutter & FastAPI**

[⬆ Back to Top](#-clarityai)

</div>

