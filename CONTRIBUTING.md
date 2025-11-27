# Contributing to ClarityAI

First off, thank you for considering contributing to ClarityAI! It's people like you that make this project great.

## 🤝 How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check the existing issues to avoid duplicates. When you create a bug report, include as many details as possible:

- **Use a clear and descriptive title**
- **Describe the exact steps to reproduce the problem**
- **Provide specific examples** (code snippets, screenshots, etc.)
- **Describe the behavior you observed** and what you expected to see
- **Include details about your environment** (OS, Flutter version, Python version)

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion:

- **Use a clear and descriptive title**
- **Provide a detailed description** of the suggested enhancement
- **Explain why this enhancement would be useful**
- **List some examples** of how it would work

### Pull Requests

1. **Fork the repo** and create your branch from `main`
2. **Follow the code style** of the project
3. **Write clear commit messages**
4. **Update documentation** if needed
5. **Test your changes** thoroughly
6. **Submit a pull request** with a clear description

## 💻 Development Setup

### Backend Development

```bash
cd server
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```

### Frontend Development

```bash
flutter pub get
flutter run -d chrome  # or your preferred device
```

## 📝 Code Style

### Python (Backend)

- Follow [PEP 8](https://pep8.org/) style guide
- Use type hints where appropriate
- Write docstrings for functions and classes
- Keep functions focused and small

### Dart (Frontend)

- Follow [Dart style guide](https://dart.dev/guides/language/effective-dart/style)
- Use meaningful variable names
- Keep widgets small and focused
- Add comments for complex logic

## 🧪 Testing

### Backend Tests

```bash
cd server
pytest
```

### Frontend Tests

```bash
flutter test
```

## 📋 Commit Message Guidelines

- Use the present tense ("Add feature" not "Added feature")
- Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit the first line to 72 characters
- Reference issues and pull requests after the first line

Examples:
```
Add voice input feature

- Implement speech-to-text
- Add microphone button to UI
- Update documentation

Fixes #123
```

## 🌟 Areas for Contribution

We especially welcome contributions in these areas:

- 🎨 **UI/UX improvements**: Make the interface more beautiful and intuitive
- 🐛 **Bug fixes**: Help squash those pesky bugs
- 📚 **Documentation**: Improve guides, add tutorials, fix typos
- ✨ **New features**: Implement items from the roadmap
- 🧪 **Testing**: Add unit tests, integration tests, e2e tests
- 🌍 **Internationalization**: Add support for more languages
- ♿ **Accessibility**: Improve accessibility features

## 📜 Code of Conduct

### Our Pledge

We are committed to providing a friendly, safe, and welcoming environment for all contributors.

### Our Standards

- ✅ Be respectful and inclusive
- ✅ Welcome newcomers and help them learn
- ✅ Accept constructive criticism gracefully
- ✅ Focus on what's best for the community

- ❌ No harassment, discrimination, or trolling
- ❌ No personal attacks or insults
- ❌ No spam or self-promotion

## ❓ Questions?

Feel free to:
- Open an issue with the "question" label
- Start a discussion in the Discussions tab
- Reach out to the maintainers

## 📄 License

By contributing to ClarityAI, you agree that your contributions will be licensed under the MIT License.

---

Thank you for contributing! 🎉

