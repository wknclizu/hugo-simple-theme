+++
author = "Hugo Authors"
title = "Test Post with Comments Enabled"
date = "2024-01-02"
description = "This post demonstrates Cusdis comments integration."
tags = ["test", "comments"]
+++

This is a test post to demonstrate the Cusdis comment functionality.

## Comment System

This post should show the Cusdis comment section below the content (when properly configured with an app_id).

## Configuration

To enable comments on your site:

1. Sign up for Cusdis at https://cusdis.com
2. Create an app and get your app ID
3. Add the configuration to your `hugo.toml`:

```toml
[params.cusdis]
app_id = "your-app-id-here"
# Optional settings:
# host = "https://cusdis.com"
# lang = "en"
```

## Per-Post Control

To disable comments on specific posts, add `disableComments = true` to the post's front matter.