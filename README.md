# Seedance 2 API with APIDot

Build with the Seedance 2 API using APIDot: cURL, Node.js, polling, webhooks, pricing, and fal.ai comparison in one production-oriented GitHub repo.

[Get API Key](https://apidot.ai/dashboard/api-key) | [API Docs](https://apidot.ai/docs/seedance-2) | [Model Page](https://apidot.ai/models/seedance-2) | [Main Examples](https://github.com/APIDotAI/apidot-examples)

## Why this repo exists

Teams choose Seedance 2 when they need more than prompt-only video generation, especially for reference-driven scenes, native audio-video output, and short-form clips that need continuity across shots. On APIDot, both `seedance-2` and `seedance-2-fast` use the same async workflow, so you can iterate in Fast mode and move the same setup into standard delivery when quality matters more.

This repository turns that workflow into runnable server-side examples: a verified cURL request, a native Node.js polling example, webhook receiver notes, prompt examples, pricing context, and production integration guardrails.

## Overview

Seedance 2 is ByteDance Seed's advanced multimodal video generation model for clips that need more than prompt-only motion. It is built for video creation where references, camera intent, physical movement, and audio need to work together in the same result.

Its core strengths include native audio-video generation, image/video/audio reference control, multi-shot storytelling, stronger character and style continuity, and more stable motion in complex scenes. That makes Seedance 2 especially useful for product ads, cinematic short-form videos, storyboard previews, music-driven clips, and character-led sequences.

On APIDot, Seedance 2 is available through `seedance-2` and `seedance-2-fast`. Use `seedance-2` when final quality and 1080p output matter, and use `seedance-2-fast` for lower-cost iteration at 480p or 720p. Requests can use first/last frame images or multimodal `reference_*_urls`, but those two control modes should not be mixed in the same request.

## Capabilities

- Using multimodal references to control composition, motion, and sound: Seedance 2 can use text, images, video, and audio references to guide the generated clip. This helps creators control the subject, camera direction, movement style, rhythm, and scene mood instead of relying on a prompt alone.
- Generating native audio with dialogue, ambience, lip-sync, and beat sync: Seedance 2 can generate synchronized audio together with the video, including spoken dialogue, ambient sound, music timing, and lip-sync. The result can feel closer to a finished short-form video rather than a silent draft that needs separate audio production.
- Building multi-shot cinematic stories with consistent characters and style: Seedance 2 can create connected video sequences with multiple shots in a single generation. It helps keep character identity, visual style, transitions, and story flow consistent, which is useful for ads, short films, social clips, and previs work.
- Recreating camera movement, transitions, and action rhythm from references: With reference videos or images, Seedance 2 can follow camera movement, shot rhythm, composition, and visual style more closely. This makes it useful for turning storyboards, product briefs, motion references, or existing creative examples into new video scenes.
- Supporting realistic motion for dance, action, product, and multi-subject scenes: Seedance 2 is valuable when the scene includes fast action, dancing, product movement, or several subjects interacting. It is designed to keep motion smoother and more physically believable, so the final clip feels more connected and less fragmented.
- Extending, restyling, and refining video ideas through iterative control: Seedance 2 can support workflows where teams extend a scene, reshape the visual style, or improve an existing direction. This makes it easier to explore variations and polish a creative idea without restarting the whole video from scratch.

## Common use cases

This repository is for teams that need reference-driven video generation, native audio, and an async workflow they can carry from testing into production.

- Product ads and social-first branded videos
- Storyboard tests, shot planning, and previs
- Localized marketing variants with native lip-sync
- Game cutscenes and character-driven sequences
- Training and explainer videos with consistent presenters
- Music videos, dance clips, and cinematic b-roll

## Pricing on APIDot

Catalog price: Starting at $0.04 / second.
Pricing snapshot: per second | seedance-2 480p: 10 cr/s ($0.05, with video input), 20 cr/s ($0.10, text/image-to-video); 720p: 20 cr/s ($0.10, with video input), 40 cr/s ($0.20, text/image-to-video); 1080p: 45 cr/s ($0.225, with video input), 90 cr/s ($0.45, text/image-to-video)

This README uses the pricing data currently published in the APIDot model catalog. Check the APIDot model page before high-volume production runs.

### Model-specific pricing

- seedance-2: per second | 480p: 10 cr/s ($0.05, with video input), 20 cr/s ($0.10, text/image-to-video); 720p: 20 cr/s ($0.10, with video input), 40 cr/s ($0.20, text/image-to-video); 1080p: 45 cr/s ($0.225, with video input), 90 cr/s ($0.45, text/image-to-video)
- seedance-2-fast: per second | 480p: 8 cr/s ($0.04, with video input), 14 cr/s ($0.07, text/image-to-video); 720p: 16 cr/s ($0.08, with video input), 28 cr/s ($0.14, text/image-to-video)

## APIDot vs fal.ai

For tiers with fal.ai comparison data in the APIDot catalog, APIDot shows up to 45% lower listed price. Treat this as a catalog snapshot and verify current pricing before launch.

| Tier | APIDot listed price | fal.ai listed price | Note |
| --- | ---: | ---: | --- |
| seedance-2 \| 480p \| with video input | $0.05 | $0.0907 | APIDot is 45% lower in this tier |
| seedance-2 \| 480p \| text/image-to-video | $0.1 | $0.1512 | APIDot is 34% lower in this tier |
| seedance-2 \| 720p \| with video input | $0.1 | $0.1814 | APIDot is 45% lower in this tier |
| seedance-2 \| 720p \| text/image-to-video | $0.2 | $0.3024 | APIDot is 34% lower in this tier |
| seedance-2 \| 1080p \| with video input | $0.225 | $0.3425 | APIDot is 34% lower in this tier |
| seedance-2 \| 1080p \| text/image-to-video | $0.45 | $0.685 | APIDot is 34% lower in this tier |
| seedance-2-fast \| 480p \| with video input | $0.04 | $0.0726 | APIDot is 45% lower in this tier |
| seedance-2-fast \| 480p \| text/image-to-video | $0.07 | $0.121 | APIDot is 42% lower in this tier |
| seedance-2-fast \| 720p \| with video input | $0.08 | $0.1452 | APIDot is 45% lower in this tier |
| seedance-2-fast \| 720p \| text/image-to-video | $0.14 | $0.2419 | APIDot is 42% lower in this tier |

## Quick start

    cp .env.example .env
    # Edit .env and set APIDOT_API_KEY
    cd node
    npm start

The same request shape is available as a copy-paste cURL example in curl/generate.md.

## Minimal API request

Submit to APIDot's unified async generation endpoint:

    POST https://api.apidot.ai/api/generate/submit
    Authorization: Bearer <APIDOT_API_KEY>
    Content-Type: application/json

Primary payload:

```json
{
  "model": "seedance-2",
  "callback_url": "https://your-domain.com/callback",
  "input": {
    "prompt": "A slow dolly-in on a ceramic cup of espresso, morning light",
    "duration": 5,
    "aspect_ratio": "16:9",
    "resolution": "720p",
    "generate_audio": true
  }
}
```

Submit Seedance 2 and Seedance 2 Fast video jobs through APIDot's unified async generation endpoint.

Seedance 2 and `seedance-2-fast` share the same APIDot submit contract. Send the model id, optional callback_url, and model-specific parameters inside `input`, then retrieve the final result through the shared task status endpoint or webhook callbacks.

## Model IDs and request variants

### seedance-2

```json
{
  "model": "seedance-2",
  "callback_url": "https://your-domain.com/callback",
  "input": {
    "prompt": "A slow dolly-in on a ceramic cup of espresso, morning light",
    "duration": 5,
    "aspect_ratio": "16:9",
    "resolution": "720p",
    "generate_audio": true
  }
}
```

### seedance-2-fast

```json
{
  "model": "seedance-2-fast",
  "callback_url": "https://your-domain.com/callback",
  "input": {
    "prompt": "A handheld close-up of rain on a taxi window in neon city light",
    "duration": 5,
    "aspect_ratio": "16:9",
    "resolution": "720p",
    "generate_audio": true
  }
}
```

## Request parameters

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| model | string | yes | Target model id. Use `seedance-2` or `seedance-2-fast`. |
| callback_url | string | no | Optional webhook callback URL for terminal task updates. |
| input | object | yes | Container for Seedance 2 generation parameters. |
| input.prompt | string | yes | Primary generation prompt describing scene, motion, pacing, and style. |
| input.duration | number | yes | Video duration in seconds. Current APIDot support is integer values from 4 through 15. |
| input.aspect_ratio | string | no | Supported values include `21:9`, `16:9`, `4:3`, `1:1`, `3:4`, and `9:16`. |
| input.resolution | string | yes | `seedance-2` supports `480p`, `720p`, and `1080p`. `seedance-2-fast` supports `480p` and `720p`. |
| input.generate_audio | boolean | no | Whether to generate synchronized audio together with the video. |
| input.image_urls | string[] | no | Optional first and last frame images. Use up to 2 URLs only. |
| input.reference_image_urls | string[] | no | Optional reference image URLs for multimodal reference-to-video mode. |
| input.reference_video_urls | string[] | no | Optional reference video URLs for multimodal reference-to-video mode. |
| input.reference_audio_urls | string[] | no | Optional reference audio URLs for multimodal reference-to-video mode. |

## Practical integration notes

- Use `seedance-2-fast` for iteration, then move to `seedance-2` when you need the highest final quality or 1080p output.
- Be explicit about camera motion, pacing, subject continuity, and audio intent in the prompt.
- Do not mix `image_urls` with any `reference_*_urls` fields in the same request.

## Polling and webhooks

APIDot media generation is asynchronous. Store data.task_id immediately after submit, poll /api/generate/status/{task_id} for local tests, and use callback_url webhooks for production queues where users may leave the page before completion.

Webhook handlers should verify task ownership, persist callback events, return 2xx quickly, and be idempotent because duplicate deliveries can happen.

## Response and errors

- code: HTTP-style status code. Successful submits return `200`.
- data.task_id: Async task identifier returned immediately after submission.
- data.status: Initial task status, typically `not_started`.
- data.created_time: ISO 8601 timestamp for task creation.

Common error classes:

- 400 invalid_request: Missing fields, unsupported parameter combinations, or invalid reference input combinations.
- 401 authentication_error: Missing, expired, or invalid Bearer API key.
- 402 insufficient_credits: The current prepaid balance cannot cover the video job.
- 429 rate_limited: Submission rate is temporarily above the current allowed limit.

## Production notes

- Keep APIDot API keys in server-side environment variables.
- Persist task_id, selected model, request payload, user ID, and status together.
- Use a moderate polling interval for tests and webhooks for durable production callbacks.
- Validate source media URLs before submitting requests that depend on source files.
- Avoid logging API keys, private prompts, private media URLs, or callback URLs.
- Retry transient network failures with backoff, but do not retry unchanged invalid payloads.

## FAQ

### What is Seedance 2 on APIDot?

Seedance 2 on APIDot is a multimodal video generation workflow built around `seedance-2` and `seedance-2-fast`. It is meant for short-form video work where prompts alone are not enough and the final clip benefits from visual references, native audio, continuity, and tighter shot control.

### What inputs and reference modes does Seedance 2 support?

You start with a text prompt and can optionally add first and last frame images through `image_urls`, or switch to multimodal reference mode with `reference_image_urls`, `reference_video_urls`, and `reference_audio_urls`. Those two reference approaches cannot be used together in the same request.

### What are the duration, resolution, and aspect-ratio limits?

This page supports integer durations from 4 to 15 seconds. `seedance-2` supports `480p`, `720p`, and `1080p`, while `seedance-2-fast` supports `480p` and `720p`. Supported aspect ratios on APIDot are `21:9`, `16:9`, `4:3`, `1:1`, `3:4`, and `9:16`.

### Does Seedance 2 support native audio and lip-sync?

Yes. Native audio-video generation is one of the main reasons to use Seedance 2. It is designed for clips where dialogue, ambience, rhythm, or lip-sync should be generated together with the video instead of being bolted on later.

### How do first/last frame mode and reference mode differ?

First and last frame mode is for guiding the opening and ending visual state of the clip with up to two images. Reference mode is for broader multimodal control through image, video, or audio reference inputs. On APIDot, you choose one approach or the other per request.

### How should I choose `seedance-2` vs `seedance-2-fast`?

Use `seedance-2-fast` when you want cheaper, faster iteration at 480p or 720p. Use `seedance-2` when the clip is closer to delivery quality, when you need the standard model path, or when you need 1080p output.

### How is Seedance 2 billed on APIDot?

Seedance 2 is billed per second on APIDot. The cost depends on the model variant, the selected resolution, and whether your request includes video input, so pricing is not a single flat rate across all Seedance 2 jobs.

### Is Seedance 2 suitable for commercial or production use?

Yes. APIDot exposes Seedance 2 through a production-ready async API with submit, polling, and webhook support. That makes it usable in creative tools, content pipelines, and automation systems, while commercial rights still depend on your platform terms.

### Can I switch between Seedance 2 variants without changing the endpoint?

Yes. Change only the `model` field between `seedance-2` and `seedance-2-fast`. The submit endpoint and the surrounding async workflow remain the same.

### How do first/last frame mode and reference mode differ?

Use `input.image_urls` for first/last frame control with up to two images. Use `reference_image_urls`, `reference_video_urls`, or `reference_audio_urls` for multimodal reference mode. These two approaches cannot be mixed in one request.

### Is APIDot the creator of the underlying model?

No. This is an APIDot integration repository for calling Seedance 2 through APIDot. ByteDance Seed is listed as the model provider in the APIDot catalog. Use the APIDot model page for current availability, pricing, and usage terms.

## Related links

- APIDot: https://apidot.ai
- Seedance 2 model page: https://apidot.ai/models/seedance-2
- Seedance 2 API docs: https://apidot.ai/docs/seedance-2
- APIDot quickstart: https://apidot.ai/docs/quickstart
- APIDot webhooks: https://apidot.ai/docs/webhooks
- Main APIDot examples repo: https://github.com/APIDotAI/apidot-examples

## Related APIDot model API repositories

More video API examples from APIDot:

| Model | Repository |
| --- | --- |
| Sora 2 Official | [sora-2-official-api](https://github.com/APIDotAI/sora-2-official-api) |
| Happy Horse | [happy-horse-api](https://github.com/APIDotAI/happy-horse-api) |
| Veo 3.1 | [veo-3.1-api](https://github.com/APIDotAI/veo-3.1-api) |


