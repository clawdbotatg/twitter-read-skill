# Twitter Read Skill

An OpenClaw skill for efficient Twitter/X access using `web_fetch` for reading and browser automation only for interactions.

## What It Does

Teaches OpenClaw agents the optimal pattern for Twitter access:
- **Reading** (notifications, timelines, profiles) → Use `web_fetch` (fast, lightweight)
- **Interactions** (replies, likes, retweets) → Use browser automation (only when needed)

## Installation

```bash
openclaw skill install twitter-read.skill
```

Or from GitHub:

```bash
openclaw skill install https://github.com/clawdbotatg/twitter-read-skill/raw/main/twitter-read.skill
```

## Features

- URL patterns for notifications, timelines, and individual tweets
- Usage examples for common Twitter operations
- Clear guidance on when to use `web_fetch` vs. browser
- Parsing tips for Twitter HTML structure
- Zero credentials required (uses external auth config)

## Security

This skill contains:
- ✅ No API keys
- ✅ No tokens
- ✅ No credentials
- ✅ No secrets

Authentication is handled externally via browser sessions or environment variables.

## Examples

### Check notifications
```javascript
web_fetch("https://x.com/notifications")
```

### Read a user's recent tweets
```javascript
web_fetch("https://x.com/username")
```

### View a specific tweet
```javascript
web_fetch("https://x.com/username/status/1234567890")
```

## Documentation

See [SKILL.md](twitter-read/SKILL.md) for complete documentation.

## License

MIT
