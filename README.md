# Humanize Text — Remove AI Writing Patterns

Make AI-generated text sound natural. Supports 9 languages.

Paste any text — blog post, email, essay, report — and get back a clean, human-sounding version with a readability score.

Powered by [Evolink.ai](https://evolink.ai?utm_source=github&utm_medium=skill&utm_campaign=humanize)

## Install

```bash
clawhub install evolink-humanize
```

Or clone this repo directly:

```bash
git clone https://github.com/xiji2646-netizen/evolink-humanize-skill.git
cp -r evolink-humanize-skill ~/.openclaw/workspace/skills/evolink-humanize
```

## Setup

1. Get an API key at [evolink.ai/signup](https://evolink.ai/signup?utm_source=github&utm_medium=skill&utm_campaign=humanize)
2. Set the environment variable:

```bash
export EVOLINK_API_KEY="your-key-here"
```

## Usage

### From the command line

```bash
# Humanize a text file
bash scripts/humanize.sh "draft.txt"

# Humanize with a specific tone
bash scripts/humanize.sh "draft.txt" "casual blog post"

# Pipe text directly
echo "This is a testament to the transformative power of innovation." | bash scripts/humanize.sh -
```

### In OpenClaw

Just ask your agent:
- "Humanize this text"
- "Make this sound more natural"
- "Remove the AI tone from this paragraph"
- "Rewrite this to sound like a real person wrote it"

## What It Does

### Three-layer processing

1. **Scan** — Detects 24 common AI writing patterns and scores the text (0–100, lower is better)
2. **Rewrite** — Replaces robotic phrasing with natural alternatives
3. **Style Match** — Adjusts tone based on context (blog, academic, business email, casual chat)

### Patterns it catches

| Category | Examples |
|---|---|
| Filler phrases | "It is worth noting that", "In order to", "Furthermore" |
| Promotional fluff | "groundbreaking", "nestled", "vibrant", "breathtaking" |
| Fake depth | "-ing" chains: "highlighting... showcasing... reflecting..." |
| Vague attribution | "Experts believe", "Studies show", "Industry reports indicate" |
| Structural tells | Rule of three, uniform sentence length, formulaic conclusions |
| Vocabulary giveaways | "delve", "tapestry", "landscape", "crucial", "robust", "seamless" |
| Chatbot artifacts | "Great question!", "I hope this helps!", "Let me know if..." |

### Output format

Every run produces:

- **Rewritten text** — clean, human-sounding version
- **Change log** — what was modified and why

## Supported Languages

- English
- Chinese (中文)
- Japanese (日本語)
- Korean (한국어)
- Russian (Русский)
- Hindi (हिन्दी)
- German (Deutsch)
- French (Français)
- Italian (Italiano)

Language is auto-detected. No configuration needed.

## How It Works

```
Input Text
    ↓
[Layer 1: Pattern Scanner]
    Checks 24 AI patterns + vocabulary blacklist (500+ words)
    Outputs list of detected patterns
    ↓
[Layer 2: Rewriter]
    Replaces flagged phrases with natural alternatives
    Varies sentence rhythm, removes filler
    ↓
[Layer 3: Style Adapter]
    Matches target tone (blog / academic / email / casual)
    Injects appropriate personality
    ↓
Humanized Output + Score + Changelog
```

## Configuration

| Variable | Default | Description |
|---|---|---|
| `EVOLINK_API_KEY` | (required) | Your Evolink API key |
| `EVOLINK_MODEL` | `claude-opus-4-6` | Model for processing. You can switch to any model supported by the [Evolink API](https://docs.evolink.ai/en/api-manual/language-series/claude/claude-messages-api?utm_source=github&utm_medium=skill&utm_campaign=humanize), such as `claude-sonnet-4-5-20250929`, `gpt-4o`, etc. |
| `HUMANIZE_SAFE_DIR` | `~/.openclaw/workspace` | Allowed file directory |

## Security & Usage Limits

- **File access**: Only files within `HUMANIZE_SAFE_DIR` are readable
- **Sensitive files blocked**: `.env`, `.ssh`, `config.json`, private keys
- **Size limit**: 5MB for text files
- **MIME validation**: Only `text/*` and `application/json` files accepted
- No data is stored. Text is sent to Evolink API for processing and discarded.

## Examples

### Before (AI-heavy)

> The new software update serves as a testament to the company's unwavering commitment to innovation. Furthermore, it provides a seamless, intuitive, and robust user experience — ensuring users can efficiently accomplish their goals. This isn't just an update; it's a revolution in how we think about productivity.

### After

> The new software update includes batch processing, keyboard shortcuts, and an offline mode. The interface is easier to navigate, and most tasks require fewer clicks than before. It's a solid improvement to the workflow.

## Links

- [Evolink.ai](https://evolink.ai?utm_source=github&utm_medium=skill&utm_campaign=humanize) — AI API platform
- [API Docs (EN)](https://docs.evolink.ai/en/api-manual/language-series/claude/claude-messages-api?utm_source=github&utm_medium=skill&utm_campaign=humanize) — API reference
- [API Docs (中文)](https://docs.evolink.ai/cn/api-manual/language-series/claude/claude-messages-api?utm_source=github&utm_medium=skill&utm_campaign=humanize) — API documentation
- [Get API Key](https://evolink.ai/signup?utm_source=github&utm_medium=skill&utm_campaign=humanize) — Free signup

## License

MIT

## Credits

Pattern detection logic informed by [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing).

Powered by [Evolink.ai](https://evolink.ai?utm_source=github&utm_medium=skill&utm_campaign=humanize)
