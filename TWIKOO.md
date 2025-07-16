# Twikoo Comments Integration

This Hugo Simple theme includes built-in support for [Twikoo](https://twikoo.js.org), a simple, safe, and free comment system.

## Priority

**Note: Twikoo has higher priority than Cusdis. If both Twikoo and Cusdis are configured, the system will only use Twikoo.**

## Vercel Cloud Function Deployment

### 1. Apply for MongoDB

1. Go to [MongoDB official website](https://www.mongodb.com/cloud/atlas/register) to register
2. Create a free MongoDB database
3. On the Clusters page, click CONNECT and follow the steps to set up connections allowing all IP addresses (create users on the Database Access page, add IP address 0.0.0.0/0 on the Network Access page)
4. After completion, click "Choose a connection method", select "Connect your application", and copy the connection string

### 2. Vercel Deployment

1. Apply for a [Vercel](https://vercel.com) account
2. Click the following button to deploy Twikoo to Vercel with one click:

   [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/twikoojs/twikoo/tree/main/src/server/vercel-min)

3. Go to Settings -> Environment Variables, add environment variable `MONGODB_URI`, with the value being the MongoDB connection string from step 1
4. Go to Overview, click the link under Domains. If the environment is configured correctly, you will see the prompt "Twikoo cloud function is running normally"
5. The Vercel address is your environment ID

## Hugo Theme Configuration

Add the following configuration to your `hugo.toml`:

```toml
[params.twikoo]
env_id = "https://your-twikoo-app.vercel.app"  # Required: Your Vercel deployment address
lang = "zh-CN"                                 # Optional: Language setting
# region = ""                                  # Optional: Environment region (not needed for Vercel deployment)
# path = ""                                    # Optional: Custom path (defaults to current page path)
```

## Configuration Description

### Required Parameters

- `env_id`: Complete URL address of Vercel deployment (e.g., `https://your-twikoo-app.vercel.app`)

### Optional Parameters

- `lang`: Comment area language setting
  - `zh-CN`: Simplified Chinese (default)
  - `zh-TW`: Traditional Chinese
  - `en`: English
  - `ja`: Japanese
  - For more language support, please refer to: [Language list](https://github.com/twikoojs/twikoo/blob/main/src/client/utils/i18n/index.js)

- `region`: Environment region (**Not needed for Vercel deployment**)
  - Only needed for Tencent Cloud environment: `ap-shanghai` or `ap-guangzhou`

- `path`: Custom path (usually not needed)
  - Defaults to using `location.pathname` to distinguish different articles

## Usage

### Global Settings

After configuration, comments will automatically appear below all blog posts. The comment system only displays in articles within the main content section (usually "blog").

### Individual Article Control

To disable comments on specific articles, add the following to the article's front matter:

```yaml
---
title: "Article without comments"
disableComments: true
---
```

## Features

- ✅ Supports Markdown
- ✅ Supports dark mode
- ✅ No registration required for commenting
- ✅ Supports email notifications
- ✅ Supports WeChat notifications
- ✅ Supports QQ notifications
- ✅ Supports admin panel
- ✅ Supports anti-spam comments
- ✅ Supports import/export

## Management

Visit your Twikoo address + `/admin` (e.g., `https://your-twikoo-app.vercel.app/admin`) to enter the admin panel for comment management.

## Implementation Details

Comments are rendered only under the following conditions:
1. Valid `env_id` is configured
2. Article is in the main section (usually blog)
3. Article does not have `disableComments: true` set
4. If both Cusdis and Twikoo are configured, Twikoo has higher priority

Integration includes:
- `/layouts/_partials/twikoo.html` - Comment component template
- Updated `/layouts/single.html` - Includes comments in blog posts
- Configuration options in `hugo.toml` 