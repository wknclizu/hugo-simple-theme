# Comment System Configuration Guide

Hugo Simple theme supports two comment systems: **Twikoo** and **Cusdis**.

## Priority

**Important: Twikoo has higher priority than Cusdis. If both systems are configured, the theme will only use Twikoo.**

## Quick Selection

### Recommended: Twikoo
- ✅ **Supports Markdown** (Important advantage)
- ✅ Feature-rich (email notifications, WeChat notifications, QQ notifications)
- ✅ Complete admin panel
- ✅ Anti-spam comments
- ✅ Supports import/export
- ✅ Dark mode
- ❌ Requires cloud function deployment

### Alternative: Cusdis
- ✅ Lightweight (~5kb)
- ✅ Privacy-friendly
- ✅ Simple and easy to use
- ✅ No cloud function required
- ❌ **Does not support Markdown**
- ❌ Relatively simple features

## Configuration Methods

### Twikoo Configuration (Recommended)

1. **Deploy cloud function to Vercel**: See [TWIKOO.md](./TWIKOO.md)
2. **Configure in hugo.toml**:
   ```toml
   [params.twikoo]
   env_id = "https://your-twikoo-app.vercel.app"  # Required
   lang = "zh-CN"                                 # Optional
   ```

### Cusdis Configuration (Alternative)

1. **Register Cusdis account**: See [CUSDIS.md](./CUSDIS.md)
2. **Configure in hugo.toml**:
   ```toml
   [params.cusdis]
   app_id = "your-app-id-here"  # Required
   lang = "en"                  # Optional
   ```

## Disable Comments

Add to any article's front matter:
```yaml
---
disableComments: true
---
```

## Complete Configuration Example

```toml
# Complete configuration in hugo.toml
[params]
# Other configurations...

# Twikoo comment system (higher priority)
[params.twikoo]
env_id = "https://your-twikoo-app.vercel.app"
lang = "zh-CN"

# Cusdis comment system (alternative, only effective when Twikoo is not configured)
[params.cusdis]
app_id = "your-cusdis-app-id"
host = "https://cusdis.com"
lang = "en"
```

## Detailed Documentation

- [Twikoo Detailed Configuration Documentation](./TWIKOO.md)
- [Cusdis Detailed Configuration Documentation](./CUSDIS.md)

## Recommendations

If you need **Markdown support** and **rich features**, it is recommended to use **Twikoo**.
If you prefer **simple and lightweight**, you can choose **Cusdis**. 