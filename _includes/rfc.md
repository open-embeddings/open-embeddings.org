# Open Embeddings RFC - Draft Specification

*This is a living document. We encourage community feedback and contributions through pull requests and issues.*

## Abstract

The Open Embeddings specification defines a standardized JSON format for content providers to expose embeddings of their content, enabling AI-native content discovery without requiring full content download. This specification addresses the growing need for efficient content similarity search while reducing bandwidth costs and preventing data capture behind walled gardens.

## Motivation

### Problem Statement

Current content discovery methods face several challenges:

1. **Bandwidth Waste**: Similarity searches require downloading content to generate embeddings locally
2. **Computational Cost**: Re-embedding content across different models and platforms is expensive
3. **Walled Gardens**: Data capture behind proprietary systems limits open access
4. **Model Sprawl**: Different embedding models create incompatible representations

### Solution Overview

Open Embeddings provides:
- Standardized JSON format for embedding distribution
- Publisher-agnostic content discovery
- Reduced bandwidth and computational requirements
- Support for multiple embedding models per content item

## Technical Specification

### File Format

Open Embeddings uses JSON format with the following structure:

```json
{
  "version": "1.0",
  "metadata": {
    "generated": "2024-01-15T10:30:00Z",
    "generator": "open-embeddings-tool/1.0",
    "license": "CC-BY-4.0"
  },
  "content": [
    {
      "uri": "/path/to/content",
      "content_type": "text/html",
      "last_modified": "2024-01-15T09:00:00Z",
      "title": "Content Title",
      "embeddings": [
        {
          "model": "text-embedding-ada-002",
          "version": "1.0",
          "dimensions": 1536,
          "vector": [0.023, -0.019, 0.041, "..."],
          "metadata": {
            "chunk_size": 512,
            "overlap": 0,
            "language": "en"
          }
        }
      ]
    }
  ]
}
```

### File Locations

Open Embeddings files SHOULD be accessible at:
1. `/.well-known/open-embeddings.json` (preferred)
2. `/open-embeddings.json` (fallback)

### Hard Implementation Problems

**Model Sprawl**: Can we build on recent academic work to generalize on a framework to transform between embedding spaces for multi-modal models?

**Cache-Invalidation**: Trusting the embeddings and metadata - ensuring content freshness and embedding accuracy.

## References

- [RFC 2119 - Key words for use in RFCs](https://tools.ietf.org/html/rfc2119)
- [RFC 8259 - The JavaScript Object Notation (JSON) Data Interchange Format](https://tools.ietf.org/html/rfc8259)
- [Well-Known URIs](https://tools.ietf.org/html/rfc5785)

---

## Contributing

This RFC is open for community input. Please:
- Submit issues for questions or suggestions
- Create pull requests for specific changes
- Join discussions on the project repository

*Last updated: [Current Date]*
# Examples

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

## Sample Implementation

### Basic open-embeddings.json

Here's a simple example of an `open-embeddings.json` file for a blog:

```json
{
  "version": "1.0",
  "metadata": {
    "generated": "2024-01-15T10:30:00Z",
    "generator": "blog-embeddings-tool/1.0",
    "license": "CC-BY-ND-4.0"
  },
  "content": [
    {
      "uri": "/blog/ai-future",
      "content_type": "text/html",
      "last_modified": "2024-01-15T09:00:00Z",
      "embeddings": [
        {
          "model": "text-embedding-ada-002",
          "version": "1.0",
          "dimensions": 1536,
          "vector": [0.023, -0.019, 0.041, "... (1533 more values)"],
          "metadata": {
            "chunk_size": 512,
            "overlap": 0,
            "language": "en"
          }
        }
      ]
    }
  ]
}
```

## Use Cases

### 1. Content Discovery for Developers
**Scenario:** A developer wants to find blog posts about "machine learning deployment" across multiple tech blogs.

**Solution:** Instead of scraping and processing each blog's content, the developer can:
1. Check each blog's `open-embeddings.json` file
2. Generate an embedding for "machine learning deployment"
3. Calculate similarity scores against pre-computed embeddings
4. Rank and filter results by relevance

### 2. AI Platform Content Ingestion
**Scenario:** An AI platform needs to index web content for semantic search.

**Solution:** The platform can:
1. Discover websites with Open Embeddings files
2. Download embeddings instead of full content
3. Use embeddings for semantic search and recommendations
4. Reduce bandwidth and processing costs significantly

### 3. Content Creator Control
**Scenario:** A content creator wants to provide multiple representations of their content for different AI systems.

**Solution:** The creator can:
1. Generate embeddings with different models (e.g., general-purpose, domain-specific)
2. Provide different granularities (paragraph-level, document-level)
3. Include metadata about intended use cases
4. Control how their content is represented in AI systems

## Code Examples

### Python Parser

```python
import json
import requests
from typing import List, Dict, Optional

class OpenEmbeddingsParser:
    def __init__(self, base_url: str):
        self.base_url = base_url.rstrip('/')

    def fetch_embeddings(self) -> Optional[Dict]:
        """Fetch open-embeddings.json from the website"""
        urls = [
            f"{self.base_url}/.well-known/open-embeddings.json",
            f"{self.base_url}/open-embeddings.json"
        ]

        for url in urls:
            try:
                response = requests.get(url)
                if response.status_code == 200:
                    return response.json()
            except requests.RequestException:
                continue

        return None

    def find_similar_content(self, query_embedding: List[float],
                           threshold: float = 0.8) -> List[Dict]:
        """Find content similar to the query embedding"""
        embeddings_data = self.fetch_embeddings()
        if not embeddings_data:
            return []

        similar_content = []
        for content in embeddings_data.get('content', []):
            for embedding in content.get('embeddings', []):
                similarity = self.cosine_similarity(
                    query_embedding,
                    embedding['vector']
                )
                if similarity >= threshold:
                    similar_content.append({
                        'uri': content['uri'],
                        'title': content.get('title', ''),
                        'similarity': similarity,
                        'model': embedding['model']
                    })

        return sorted(similar_content, key=lambda x: x['similarity'], reverse=True)

    def cosine_similarity(self, a: List[float], b: List[float]) -> float:
        """Calculate cosine similarity between two vectors"""
        import math

        dot_product = sum(a[i] * b[i] for i in range(len(a)))
        norm_a = math.sqrt(sum(a[i] ** 2 for i in range(len(a))))
        norm_b = math.sqrt(sum(b[i] ** 2 for i in range(len(b))))

        return dot_product / (norm_a * norm_b)

# Usage example
parser = OpenEmbeddingsParser("https://example.com")
similar_content = parser.find_similar_content(query_embedding)
```

### JavaScript Parser

```javascript
class OpenEmbeddingsParser {
    constructor(baseUrl) {
        this.baseUrl = baseUrl.replace(/\/$/, '');
    }

    async fetchEmbeddings() {
        const urls = [
            `${this.baseUrl}/.well-known/open-embeddings.json`,
            `${this.baseUrl}/open-embeddings.json`
        ];

        for (const url of urls) {
            try {
                const response = await fetch(url);
                if (response.ok) {
                    return await response.json();
                }
            } catch (error) {
                continue;
            }
        }

        return null;
    }

    async findSimilarContent(queryEmbedding, threshold = 0.8) {
        const embeddingsData = await this.fetchEmbeddings();
        if (!embeddingsData) return [];

        const similarContent = [];

        for (const content of embeddingsData.content || []) {
            for (const embedding of content.embeddings || []) {
                const similarity = this.cosineSimilarity(
                    queryEmbedding,
                    embedding.vector
                );

                if (similarity >= threshold) {
                    similarContent.push({
                        uri: content.uri,
                        title: content.title || '',
                        similarity: similarity,
                        model: embedding.model
                    });
                }
            }
        }

        return similarContent.sort((a, b) => b.similarity - a.similarity);
    }

    cosineSimilarity(a, b) {
        const dotProduct = a.reduce((sum, val, i) => sum + val * b[i], 0);
        const normA = Math.sqrt(a.reduce((sum, val) => sum + val * val, 0));
        const normB = Math.sqrt(b.reduce((sum, val) => sum + val * val, 0));

        return dotProduct / (normA * normB);
    }
}

// Usage example
const parser = new OpenEmbeddingsParser('https://example.com');
const similarContent = await parser.findSimilarContent(queryEmbedding);
```

## Testing Your Implementation

### Validation Checklist

- [ ] JSON file is valid and well-formed
- [ ] File is accessible at specified locations
- [ ] All required fields are present
- [ ] Embedding dimensions match declared values
- [ ] Metadata includes necessary information
- [ ] CORS headers are properly configured
- [ ] File size is reasonable for bandwidth considerations

### Common Pitfalls

1. **Large File Sizes:** Embedding vectors can make files very large. Consider:
   - Breaking large sites into multiple files
   - Using compression
   - Implementing pagination for large content sets

2. **Outdated Embeddings:** Ensure embeddings are regenerated when content changes

3. **Model Compatibility:** Clearly specify model versions and parameters

4. **Security:** Be cautious about exposing sensitive information in embeddings

## Next Steps

1. **Implement a Parser:** Use the code examples above as starting points
2. **Generate Sample Data:** Create embeddings for your content
3. **Test Integration:** Verify your implementation works with AI platforms
4. **Contribute:** Share your implementations with the community

---

*Want to add your own examples? [Submit feedback](feedback.html) or contribute to the project repository.*
