# 🤖 Vity - AI Terminal Assistant

![demo_video](https://github.com/Kaleab-Ayenew/demo_vids/blob/main/loom_720p-_online-video-cutter.com_-_1_.gif)

AI-powered terminal assistant that generates shell commands and provides coding help. Works with OpenAI, Google Gemini, local models (Ollama), and any OpenAI-compatible API.

## ✨ Features

- **🎯 Smart Command Generation**: Describe tasks, get exact commands
- **🤖 Multi-Provider Support**: OpenAI, Google Gemini, Ollama, or any OpenAI-compatible API
- **🏠 Local Model Support**: Run completely offline with Ollama
- **🧠 Context Awareness**: Record terminal sessions for better responses
- **💬 Chat Mode**: Ask questions about errors and commands
- **📹 Session Recording**: Capture terminal output for contextual help

## 🚀 Quick Start

### Install
```bash
curl -LsSf https://raw.githubusercontent.com/kaleab-ayenew/vity/main/install.sh | sh
```

### Configure
```bash
vity config
```
You'll be prompted for:
- **Base URL**: Your LLM provider endpoint
- **API Key**: Your API key (use `NONE` for local models)
- **Model**: Model name to use
- **History Limit**: Lines of terminal history to send (default: 1000)

### Use
```bash
# Generate commands
vity do "find all python files larger than 1MB"
vity do "kill process using port 3000"

# Chat with AI
vity chat "explain this error message"
vity chat "what does chmod 755 do?"

# Use with context
vity record    # Start recording session
# ... work normally ...
vity do "fix this error"  # AI sees your terminal history
exit          # Stop recording
```

## 🔧 Provider Configuration Examples

### OpenAI
```
Base URL: https://api.openai.com/v1
API Key: sk-your-openai-key
Model: gpt-4o-mini
```

### Google Gemini
```
Base URL: https://generativelanguage.googleapis.com/v1beta
API Key: your-gemini-key
Model: gemini-1.5-flash
```

### Ollama (Local)
```
Base URL: http://localhost:11434/v1
API Key: NONE
Model: llama3.2:3b
```

### Other Providers
Works with any OpenAI-compatible API (Anthropic, Together AI, etc.)

## 📋 Requirements

- **Python**: 3.9+
- **OS**: Linux or macOS
- **LLM Provider**: OpenAI, Gemini, Ollama, or compatible API

## 🎯 Commands

| Command | Description |
|---------|-------------|
| `vity do "<task>"` | Generate shell command |
| `vity chat "<question>"` | Chat with AI |
| `vity record` | Start recording session |
| `vity status` | Show recording status |
| `vity config` | Manage configuration |
| `vity config --reset` | Reset configuration |
| `vity install` | Install shell integration |
| `vity reinstall` | Reinstall shell integration |
| `vity uninstall` | Completely remove vity |

## 🔄 Context Recording

For the best experience, use recording to give Vity context:

```bash
vity record          # Start recording
# ... work normally, encounter errors ...
vity do "fix this"   # AI sees your terminal history and errors
exit                 # Stop recording
```

## 🗑️ Uninstalling

```bash
# Remove everything (shell integration, config, logs, chat history)
vity uninstall

# Or force without confirmation
vity uninstall --force
```

Then remove the package:
```bash
pipx uninstall vity  # if installed with pipx
# or
pip uninstall vity   # if installed with pip
```

## 🛠️ Troubleshooting

**Command not found**: Restart terminal or run `source ~/.bashrc`

**API errors**: Check your configuration with `vity config --show`

**Reset everything**: `vity config --reset`

## 🔒 Privacy

- Configuration stored locally in `~/.config/vity/`
- Terminal history only sent during recording or with `-f` flag
- No data stored on external servers (except API calls)

## 🛠️ Development

Want to contribute or work on Vity? Here's how to get started:

### Clone the Repository

```bash
# Clone the repository
git clone https://github.com/kaleab-ayenew/vity.git
cd vity
```

### Setup Development Environment

```bash
# Install uv (fast Python package installer)
curl -LsSf https://astral.sh/uv/install.sh | sh

# Create a virtual environment and install dependencies
uv venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install the package in editable mode with dev dependencies
uv pip install -e ".[dev]"
```

### Build the Package

```bash
# Install build tools
pip install build

# Build the package
python -m build
```

This creates distribution files in the `dist/` directory.

### Running Tests

```bash
# Install test dependencies
uv pip install -e ".[dev]"

# Run tests (if available)
pytest
```

### Code Quality

```bash
# Format code with black
black src/

# Lint with ruff
ruff check src/

# Type checking with mypy
mypy src/
```

### Making Changes

1. Create a new branch for your feature/fix
2. Make your changes
3. Test your changes locally
4. Submit a pull request

## 📄 License

MIT License - see [LICENSE](LICENSE) file.

---

**Need help?** Run `vity help` or open an issue on [GitHub](https://github.com/kaleab-ayenew/vity/issues).
