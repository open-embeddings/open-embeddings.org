---
layout: home
title: Home
---

# The Spice Must Flow: Open Embeddings

**Open Embeddings creates a standardized way for AI-native content discovery.**

Embeddings can make it easier to find relevant content for humans, agents and scripts without access to the original material. Today, keyword searches into content providers leave context on the table. Similarity searches are great, but we have to download the content to generate the embeddings. This wastes time and bandwidth, and it can lead to data capture behind walled gardens.

## The Problem

**What problem is Open Embedding solving?**
Humans / Agents / Scripts want to find maximally relevant content without needing to consume unrelated content in a publisher agnostic way.

## Our Solution

**How do Open Embeddings solve this problem?**
- Create a standardized way for content providers to expose their content in an AI-native format
- Create a standardized way for indexers to provide embeddings and metadata for content discovery  
- Create a standardized way for agents and scripts to query embeddings by URI

## Practical Example

I wanted to build a script to build up a collection of youtube/vimeo/tiktok self-improvement videos to build a pipeline "the path to my best self". Embedding all possible videos about self-improvement would overwhelm my janky laptop. Better instead if I had a way to gather embeddings on aspects of the video, encode my query, and pop out the most relevant videos for further screening.

## Community Benefits

**What are the expected community benefits of Open Embeddings?**

1. **Content Providers** pay less in publishing costs (bandwidth, compute, storage) to expose their content to AI systems.
2. **Developers** can easily access high-quality embeddings for content without the need to download the content themselves.
3. **End Users** can "collect" embeddings without worrying about which model or platform they are using, allowing for a more seamless experience.

## Target Audience

**Developers, Content Creators, AI platforms**

## Value Proposition

- **Developers**: Easier access to high-quality embeddings for content without re-embedding costs.
- **Content Creators**: Greater control over how their content is interpreted and used by AI, with the ability to expose multiple sets of embeddings.
- **AI Platforms**: A standardized way to ingest and understand web content, reducing the need for re-embedding and allowing for more efficient content discovery and delivery.

## Hard Implementation Problems to Solve at Scale

- **Model sprawl** - Can we build on recent academic work to generalize on a framework to transform between embedding spaces for multi-modal models?
- **Cache-Invalidation**: Trusting the embeddings and metadata

## Our Vision

When you understand our thesis, we hope you will help us:

* Define a great Open Format / Spec for content-providers to leverage multiple models
* Update commonly used content publishing tools to support the format securely  
* Generate a corpus of distributed cross-space materials to allow transitions between closed models and open model encoded data

Our goal is to find a sustainable way to lower the barrier to entry for new AI agents/scripts and services, while taking pressure off the indexers pounding content providers to effectively perform the same operation across multiple models.

## Get Involved

We encourage community participation through multiple channels:

- **[Read the Draft RFC](rfc.html)** - Review and comment on the technical specification
- **[See Examples](examples.html)** - Explore sample implementations and use cases
- **[Provide Feedback](feedback.html)** - Share your thoughts and suggestions
- **[View our Roadmap](roadmap.html)** - See what's planned for the future
- **Contribute to the project** - Join our open-source development efforts

---

*This project is run as a non-profit, funded through donations and open-source grants with the goal of creating an open and accessible internet for AI.*