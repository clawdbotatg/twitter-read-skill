---
name: twitter-read
description: Efficient Twitter/X access using web_fetch for reading (notifications, timelines, profiles) and browser only for interactions (replies, likes, retweets). Use when needing to check Twitter notifications, read tweets, or monitor activity without full browser overhead.
---

# Twitter Read

## Core Pattern

**Reading = `web_fetch` | Interaction = `browser`**

Use `web_fetch` for all read operations—it's faster, lighter, and doesn't require browser automation. Only open a browser when you need to interact (reply, like, retweet, post).

## URL Patterns

### Notifications
```
https://x.com/notifications
```
Returns HTML with recent notifications. Parse for mentions, replies, likes, follows.

### User Timeline
```
https://x.com/username
```
Returns the user's profile page with recent tweets.

### Individual Tweet
```
https://x.com/username/status/1234567890
```
Returns a specific tweet and its replies.

### Following / For You Timeline
```
https://x.com/home
```
Returns the main timeline (requires authentication via cookies/session).

## Usage Examples

### Check notifications
```
web_fetch("https://x.com/notifications")
```
Parse the markdown/text for new activity.

### Read a specific user's recent tweets
```
web_fetch("https://x.com/austingriffith")
```
Extract tweet content from the returned text.

### View a tweet thread
```
web_fetch("https://x.com/vitalikbuterin/status/1234567890")
```
Get the tweet and its reply chain.

## When to Use Browser

Only use browser automation when you need to:
- Post a tweet
- Reply to a tweet
- Like or retweet
- Follow/unfollow
- Any other write operation

For everything else, `web_fetch` is faster and preferred.

## Authentication Notes

- **No credentials in this skill** - Authentication happens via browser session or API tokens configured elsewhere
- `web_fetch` will work for public content without auth
- For authenticated content (DMs, protected accounts), you may need cookies/session from a browser
- Never hardcode API keys or secrets—use environment variables or secure config

## Parsing Tips

Twitter HTML is dense. When using `web_fetch`:
- Look for tweet text in `<article>` or `data-testid="tweet"` patterns
- Notification counts often in `aria-label` attributes
- Profile stats (followers, etc.) in labeled elements
- Rely on text extraction—exact selectors change frequently

The `extractMode: "text"` option in `web_fetch` often works better than markdown for Twitter's structure.
