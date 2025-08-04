---
layout: page
title: "Use Cases & Examples"
permalink: /examples.html
---

This page demonstrates practical implementations and use cases for the Open Embeddings specification.

## Real-World Use Case: The Self-Improvement Video Pipeline

**The Challenge**: Building a script to collect youtube/vimeo/tiktok self-improvement videos for "the path to my best self" without overwhelming a laptop with embedding computation.

**The Open Embeddings Solution**:
1. Video platforms expose embeddings via `open-embeddings.json`
2. Your script encodes the query "self-improvement techniques"
3. Calculate similarity against pre-computed embeddings
4. Receive ranked, relevant videos for further screening

**Benefits**:
- No need to download every video to check relevance
- Reduced bandwidth and compute costs
- Publisher-agnostic discovery across platforms


# Use Cases - Walk the modality ladder

## Static Content Sites

As I publish content, I want to make searching it easier. This will require adding plugins to docusaurus, jekyll, and other static site generators to generate the `open-embeddings.json` file automatically . We'll also want to provide support for eschewing that work to a remote GPU, as we can't guarantee the local user has the compute power to generate embeddings.

## Images

 Google DeepMind just published the whole earth dataset with embeddings. How these can be queried dynamically has two problems:
 1. Intent - they were intended to be consumed by an engine, but that may not be why I'm asking
 2. Model access - I may not have access to the model that generated the embeddings, so I need a way to transform between embedding spaces.

## Podcasts and Audio Content

Podcast publishers may want to expose both the transcript embeddings and the audio embeddings by major area.

## Youtube, Vimeo, TikTok, and Other Video Platforms

Publisher discretion may want to expose embeddings of the audio transcript, the characters and time-indexes, it is really at the discretion of the publisher. The key is the fileformat (see [RFC](./rfc))
