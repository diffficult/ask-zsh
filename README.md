# 🤖 Ask ZSH

A ZSH function that brings Claude AI directly to your terminal! Get contextually accurate commands for your specific OS without leaving the command line. Inspired by [ask-claude](https://github.com/MugunthKumar/ask-claude) for Fish shell (discovered via this [Reddit thread](https://www.reddit.com/r/commandline/comments/1gli7c3/built_a_claude_ai_helper_function_for_fish_shell/)).

## ✨ Features

- 🎯 Generates commands specific to your OS (macOS/Linux) and version
- 🐚 Native ZSH integration with Prezto support
- 🔍 Automatic system detection (OS version, distribution)
- 🔒 Secure command review before execution
- 🎨 Pretty terminal output with colored feedback
- 📁 Supports Fabric config integration
- 🚀 Interactive command placement

## 🛠️ Prerequisites

- [ZSH](https://www.zsh.org/) with [Prezto](https://github.com/sorin-ionescu/prezto)
- An [Anthropic API key](https://console.anthropic.com/settings/keys)
- `curl` and `jq` installed on your system

## 📦 Installation

1. Create the Prezto module directory:
```bash
mkdir -p ~/.zprezto/modules/ask-zsh/functions
```

2. Download the function file:
```bash
curl -o ~/.zprezto/modules/ask-zsh/functions/ask-zsh https://raw.githubusercontent.com/yourusername/ask-zsh/main/ask-zsh
```

3. Create the module initialization file:
```bash
echo "source \${0:h}/functions/ask-zsh" > ~/.zprezto/modules/ask-zsh/init.zsh
```

4. Add the module to your `.zpreztorc`:
```bash
zstyle ':prezto:load' pmodule \
  ... \
  'ask-zsh' \
  ...
```

5. Configure your API key (choose one method):
   - Add to Fabric config: `~/.config/fabric/.env`
     ```
     ANTHROPIC_API_KEY=sk-ant-your-api-key
     DEFAULT_MODEL=claude-3-opus-20240229
     ```
   - Or add to your `.zshrc`:
     ```bash
     export CLAUDE_API_KEY="sk-ant-your-api-key"
     export CLAUDE_MODEL="claude-3-opus-20240229"
     ```

## 🚀 Usage

Simply describe what you want to do:
```bash
ask-zsh "flush DNS cache"
ask-zsh "find all PDFs modified in the last week"
ask-zsh "create a new Python virtual environment"
```

The function will:
1. Generate the appropriate command for your system
2. Place it on your command line
3. Let you review and edit before execution

## 📝 Examples

macOS example:
```bash
> ask-zsh "restart DNS"
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder
```

Linux example:
```bash
> ask-zsh "update system packages"
sudo apt update && sudo apt upgrade -y  # On Debian/Ubuntu
```

## 🔧 How It Works

1. Detects your operating system and version
   - macOS: Identifies version (Sonoma, Ventura, etc.)
   - Linux: Identifies distribution and version
2. Gets shell environment details
3. Sends a structured prompt to Claude AI
4. Receives and validates the response
5. Places the command on your terminal for review

## 🎯 System Support

### Currently Supported
- macOS (Sonoma, Ventura, Monterey, Big Sur)
- Linux (Debian-based distributions)
- ZSH with Prezto

### 🚀 Future Improvements

1. Additional LLM Support:
   - OpenAI GPT-4 integration
   - Gemini Pro
   - Mistral AI
   - Local LLMs (Ollama)
   
2. Additional Shell Support:
   - Bash integration
   - Oh My ZSH support
   - Fish shell version
   
3. Enhanced Features:
   - Command history integration
   - Command explanation mode
   - Interactive prompting
   - Custom system prompts
   - Auto-completion improvements
   - Command categories and tagging
   
4. Platform Support:
   - Windows (PowerShell)
   - More Linux distributions
   - BSD systems

5. Security Features:
   - Command sandboxing
   - Permission checking
   - Dangerous command warnings

## 🔒 Security Notes

- API keys are stored securely in config files
- All commands require manual review before execution
- No automatic command execution
- Supports environment isolation via Fabric config

## 👥 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create your feature branch
3. Add your improvements
4. Submit a pull request

Areas we'd love help with:
- Additional LLM integrations
- More shell support
- Improved command detection
- Better system compatibility
- Documentation improvements

## 📄 License

MIT License - see LICENSE file for details

## 💡 Acknowledgments

- Original [ask-claude](https://github.com/MugunthKumar/ask-claude) by Mugunth Kumar
- [Anthropic](https://www.anthropic.com/) for the Claude AI API
- [Prezto](https://github.com/sorin-ionescu/prezto) community
- The [Reddit thread](https://www.reddit.com/r/commandline/comments/1gli7c3/built_a_claude_ai_helper_function_for_fish_shell/) that inspired this port

## 🆘 Support

If you encounter any issues:
1. Check the [Issues](../../issues) page
2. Create a new issue with details about your system and the problem
3. Join our discussions for feature requests and ideas

## 📊 Stats

![GitHub stars](https://img.shields.io/github/stars/diffficult/ask-zsh?style=social)
![GitHub forks](https://img.shields.io/github/forks/diffficult/ask-zsh?style=social)
![GitHub issues](https://img.shields.io/github/issues/diffficult/ask-zsh)
![GitHub pull requests](https://img.shields.io/github/issues-pr/diffficult/ask-zsh)

---
Made with ❤️ by the command line community
