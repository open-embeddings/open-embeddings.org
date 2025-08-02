---
layout: page
title: "Use Cases & Examples"
permalink: /examples.html
---

# Use Cases - Walk the modality ladder

### Skill Grinding

I wanted to build a script to build up a collection of youtube/vimeo/tiktok self-improvement videos to build a pipeline "the path to my best self". Embedding all possible videos about self-improvement would overwhelm my janky laptop. Better instead if I had a way to gather embeddings on aspects of the video, encode my query, and pop out the most relevant videos for further screening.

What I would rather do is encode my question across n-models and then query multiple indexers or content providers for relevant content. This would allow me to find the most relevant content without needing to download every video or article, saving time and bandwidth.


## Static Content Sites

As I publish content, I want to make searching it easier. This will require adding plugins to docusaurus, jekyll, and other static site generators to generate the `open-embeddings.json` file automatically . We'll also want to provide support for eschewing that work to a remote GPU, as we can't guarantee the local user has the compute power to generate embeddings.

## Images

 Google DeepMind just published the whole earth dataset with embeddings. How these can be queries dynamically has two problems:
 1. Intent - they were intended to be consumed by an engine, but that may not be why I'm asking
 2. Model access - I may not have access to the model that generated the embeddings, so I need a way to transform between embedding spaces.

## Podcasts and Audio Content

Podcast publishers may want to expose both the transcript embeddings and the audio embeddings by major area.

## Youtube, Vimeo, TikTok, and Other Video Platforms

Publisher discretion may want to expose embeddings of the audio transcript, the characters and time-indexes, it is really at the discretion of the publisher. The key is the fileformat (see [RFC](./rfc))
