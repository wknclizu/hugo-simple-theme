# Cusdis Comments Integration

This Hugo Simple theme includes built-in support for [Cusdis](https://cusdis.com), a lightweight, privacy-friendly comment system.

## Priority

**Note: If both Twikoo and Cusdis are configured, the system will prioritize Twikoo. To use Cusdis, ensure that Twikoo's `env_id` parameter is not configured.**

## Setup

1. **Sign up for Cusdis**: Visit [cusdis.com](https://cusdis.com) and create an account
2. **Create an app**: Set up a new app in your Cusdis dashboard and get your App ID  
3. **Configure your site**: Add the following to your `hugo.toml`:

```toml
[params.cusdis]
app_id = "your-app-id-here"            # Required: Your Cusdis app ID
host = "https://cusdis.com"            # Optional: Custom Cusdis host (defaults to cusdis.com)
lang = "en"                            # Optional: Language (e.g., "en", "zh-cn", etc.)
```

## Usage

### Global Settings

Comments will automatically appear on all blog posts once you've configured the `app_id`. The comment system only appears on posts in your main section (typically "blog").

### Per-Post Control

To disable comments on specific posts, add the following to the post's front matter:

```yaml
---
title: "My Post Without Comments"
disableComments: true
---
```

### Supported Languages

The theme supports multiple languages through Cusdis's built-in internationalization:
- `en` - English  
- `zh-cn` - Simplified Chinese
- `zh-tw` - Traditional Chinese
- `ja` - Japanese
- And many more...

## Customization

### Custom Host

If you're self-hosting Cusdis, specify your custom host:

```toml
[params.cusdis]
app_id = "your-app-id"
host = "https://your-cusdis-instance.com"
```

## Implementation Details

Comments are only rendered when:
1. A valid `app_id` is configured
2. The post is in the main section (blog)  
3. The post doesn't have `disableComments: true`

The integration consists of:
- `/layouts/_partials/cusdis.html` - Comment widget template
- Updated `/layouts/single.html` - Includes comments on blog posts
- Configuration options in `hugo.toml`