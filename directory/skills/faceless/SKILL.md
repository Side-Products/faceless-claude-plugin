---
name: faceless
description: Work with the videos in a Faceless.so account through the Faceless connector. Use when the user asks about their Faceless videos or series episodes, wants to render a finished video, write per-platform titles and captions, publish or schedule to YouTube, TikTok, Instagram, X, Facebook, LinkedIn or Threads, cancel a scheduled post, or see their posting calendar and analytics.
---

# Faceless

Faceless.so runs faceless short-form video channels. This skill works with videos that already exist in the user's Faceless account: finding them, getting them ready to post, publishing or scheduling them, and reading how they performed. New videos are made in the Faceless app at https://faceless.so, not here.

## Orient first

1. `faceless_get_me` shows the connected team and plan.
2. `faceless_list_accounts` lists the social accounts connected in Faceless. Use the ids it returns; never guess one. If the platform the user wants is missing, tell them to connect it in the Faceless app.

## Find a video

- `faceless_list_videos` (newest first, paginated) or, for a series, `faceless_list_series` then `faceless_list_series_episodes`.
- `faceless_get_video` returns the script, per-platform post metadata, thumbnails and the rendered MP4 URL. `faceless_get_video_status` must read `completed` before the video can be rendered or posted.

## Get it ready to post

1. No `renderedVideoUrl` yet: call `faceless_render_video`, then poll `faceless_get_render` every 5 to 15 seconds until it reports `done`.
2. Write each platform's title, caption or description with `faceless_update_video`. Scheduling rejects any platform whose metadata is missing.
3. Optionally pick a thumbnail variant with `faceless_select_video_thumbnail`.

## Publish or schedule

- `faceless_schedule_post` takes the platforms and an ISO 8601 time. Check `faceless_get_calendar` first so posts do not collide.
- `faceless_publish_post` posts to one platform immediately. Posting is public, so confirm the video, platform, account and copy with the user before calling it or `faceless_schedule_post`.
- `faceless_cancel_post` cancels a scheduled post that has not gone out yet.

## Performance

`faceless_get_analytics` returns views, likes, comments and posting volume across platforms for a trailing window; `faceless_get_calendar` shows what was posted, what is queued and what failed.

## Errors

- `forbidden_scope`: the permission was unticked when the user connected Faceless; they can reconnect and keep it ticked.
- `invalid_input` on scheduling: usually missing post metadata for a platform; set it with `faceless_update_video`.
- `rate_limited`: wait and retry.

## Tools

- `faceless_get_me`: Identify the caller
- `faceless_list_videos`: List the team's videos
- `faceless_get_video`: Get one video
- `faceless_update_video`: Update a video's name or post metadata
- `faceless_select_video_thumbnail`: Choose which thumbnail a video uses
- `faceless_get_video_status`: Poll video generation progress
- `faceless_render_video`: Render a video to MP4
- `faceless_get_render`: Poll render progress
- `faceless_list_series`: List the team's series
- `faceless_get_series`: Get one series
- `faceless_list_series_episodes`: List a series' episodes
- `faceless_publish_post`: Publish a rendered video to a platform now
- `faceless_schedule_post`: Schedule a video to one or more platforms
- `faceless_cancel_post`: Cancel a scheduled post
- `faceless_get_calendar`: Posting calendar
- `faceless_list_accounts`: List connected social accounts
- `faceless_get_analytics`: Cross-platform posting analytics
