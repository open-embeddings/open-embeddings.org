# The Spice Must Flow: Open Embeddings, a Standard for AI-Native Content Discovery

We're working on building a platform to define the specifications for a new file to be included on every website called 'open embeddings'. We want to build an elegant, easy to use website that defines the draft RFC and allows people to comment on the format / iterate on the design until we get something that works.

## Business Plan:
A non-profit that will fund running costs through donations, or look for other open source funding sources for open source projects.

## Elevator Pitch:
Embeddings can make it easier to find relevant content for humans, agents and scripts without access to the original material. Today, keyword searches into content providers leave context on the table. Similarity searches are great, but we have to download the content to generate the embeddings. This wastes time and bandwidth, and it can lead to data capture behind walled gardens.

## What problem is Open Embedding solving?
Humans / Agents / Scripts want to find maximally relevant content without needing to consume unrelated content in a publisher agnostic way.

## How do Open Embeddings solve this problem?
- Create a standardized way for content providers to expose their content in an AI-native format
- Create a standardized way for indexers to provide embeddings and metadata for content discovery
- Create a standardized way for agents and scripts to query embeddings by URI

## Practical Example:
I wanted to build a script to build up a collection of youtube/vimeo/tiktok self-improvement videos to build a pipeline "the path to my best self". Embedding all possible videos about self-improvement would overwhelm my janky laptop. Better instead if I had a way to gather embeddings on aspects of the video, encode my query, and pop out the most relevant videos for further screening.

## What are the expected community benefits of Open Embeddings?
1. Content Providers pay less in publishing costs (bandwidth, compute, storage) to expose their content to AI systems.
2. Developers can easily access high-quality embeddings for content without the need to download the content themselves.
3. End Users can "collect" embeddings without worrying about which model or platform they are using, allowing for a more seamless experience.

## Target End-User:
Developers, Content Creators, AI platforms

## Value Proposition:
- Developers: Easier access to high-quality embeddings for content without re-embedding costs.
- Content Creators: Greater control over how their content is interpreted and used by AI, with the ability to expose multiple sets of embeddings.
- AI Platforms: A standardized way to ingest and understand web content, reducing the need for re-embedding and allowing for more efficient content discovery and delivery.

## Hard Implementation Problems to Solve at Scale:
- Model sprawl - Can we build on recent academic work to generalize on a framework to transform between embedding spaces for multi-modal models?
- Cache-Invalidation: Trusting the embeddings and metadata

## Sustainability:
- The project will be run as a non-profit, funded through donations and open-source grants from individual and donations with best-in-class administrative fee applied for any paid work, with the rest done by community volunteers.
- We will seek partnerships with organizations that share our vision of an open and accessible internet, potentially including tech companies, educational institutions, and non-profits focused on open-source software and AI ethics.

1. Reach out to Mozilla and Google to see if they are interested in helping us build the website and draft RFC.

## Call to Action:
We should have multiple hooks on the site / content encourage community participation, such as:
- Participate on draft spec
- POCs
- Share your use cases
- Contribute to the project

## Competitive Landscape:
There are no other known groups pushing in this direction. We should look to encourage them to join forces.

====

## Technical Vision / Draft RFC Format:
A json file that contains a list of content underneath a URI path, with a set of embeddings, models-used (versions), dates, etc - maybe be broken out to be an index to multiple files per path to keep bandwidth low.

- Should match other IETF RFC documents in structure, allow users to submit PRs for updates
- Should be written in Markdown, with a simple CI/CD pipeline to convert it to HTML and PDF formats for easy reading and sharing.

====

We want to split things into three repositories to allow different levels of participation.

- Open Embeddings Document Format - simply for hosting Pull-requests and comments from the community on the actual technical specification
- Sample Data/Parsers - Python, Javascript, Ruby, Bash-script code for downloading and parsing websites open-embeddings data
- End user website - Look at requirements below

## End User Website Requirements:
Similar aesthetic to Mozilla website, but with a focus on simplicity and ease of use.
- Simple to maintain. It should have a static section and a dynamic section for running interactive demos of the Sample Data/Parsers.
  -- Interactive demos should be able to run in a browser to show how a query for X can be traced through the embeddings to find relevant content but model/language/platform agnostic.
- Aesthetically pleasing. A clean, modern, and minimalist design with a focus on readability and ease of navigation. We will
      use a simple color palette and typography to ensure the content is the primary focus. Simple with a structure of:
1. Main Page
2. Link to RFC
3. Examples
4. Feedback submission
5. Roadmap

## Presentation Goals:
When you leave this presentation, you will hopefully understand the thesis and some of you will further:
* Define a great Open Format / Spec for content-providers to leverage multiple models
* Update commonly used content publishing tools to support the format securely
* Generate a corpus of distributed cross-space materials to allow transitions between closed models and open model encoded data

My hope is we can find a sustainable way to lower the barrier to entry for new AI agents/scripts and services, while taking pressure off the indexers pounding content providers to effectively perform the same operation across multiple models.

# important-instruction-reminders
Do what has been asked; nothing more, nothing less.
NEVER create files unless they're absolutely necessary for achieving your goal.
ALWAYS prefer editing an existing file to creating a new one.
NEVER proactively create documentation files (*.md) or README files. Only create documentation files if explicitly requested by the User.