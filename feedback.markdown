---
layout: page
title: Feedback
---

# Feedback & Community Input

We value your input and encourage active participation in shaping the Open Embeddings specification. Your feedback helps us create a standard that truly serves the needs of developers, content creators, and AI platforms.

## How to Provide Feedback

### 1. RFC Comments & Suggestions

**For technical specification feedback:**
- Review the [Draft RFC](rfc.html) thoroughly
- Submit issues via GitHub repository (link TBD)
- Propose changes through pull requests
- Join technical discussions in our community forums

**Key areas for feedback:**
- JSON schema design and completeness
- File format efficiency and scalability
- Implementation requirements and guidelines
- Security considerations and best practices
- Use case coverage and practical applications

### 2. Use Case Submissions

**Share your specific use cases:**

Help us understand how you would use Open Embeddings in your projects:

- **Content Discovery:** How would you use embeddings to find relevant content?
- **AI Platform Integration:** What challenges do you face with current embedding approaches?
- **Content Creation:** How would you want to control your content representation?
- **Developer Tools:** What tools would make implementation easier?

### 3. Implementation Feedback

**If you've implemented or tested the specification:**

- Share your implementation experience
- Report any ambiguities in the specification
- Suggest improvements to the file format
- Provide performance benchmarks and optimizations
- Contribute code examples and libraries

## Community Channels

### GitHub Repository
- **Issues:** Report bugs, suggest features, ask questions
- **Pull Requests:** Propose changes to the specification
- **Discussions:** Join broader conversations about the future of Open Embeddings

### Discussion Forums
- **Technical Discussions:** Deep dive into specification details
- **Use Case Sharing:** Share and discuss practical applications
- **Implementation Help:** Get help with your implementations

### Contact Information
- **Email:** feedback@open-embeddings.org
- **Community Discord:** [Link TBD]
- **Twitter:** [@OpenEmbeddings](https://twitter.com/OpenEmbeddings) [TBD]

## Feedback Form

**Quick Feedback Submission:**

*Note: This form is currently a placeholder. In the final implementation, this would be a functional contact form.*

```html
<form id="feedback-form" action="#" method="POST">
  <div class="form-group">
    <label for="feedback-type">Type of Feedback:</label>
    <select id="feedback-type" name="type" required>
      <option value="">Select...</option>
      <option value="technical">Technical Specification</option>
      <option value="use-case">Use Case / Requirements</option>
      <option value="implementation">Implementation Experience</option>
      <option value="general">General Comments</option>
    </select>
  </div>
  
  <div class="form-group">
    <label for="title">Subject:</label>
    <input type="text" id="title" name="title" required>
  </div>
  
  <div class="form-group">
    <label for="message">Message:</label>
    <textarea id="message" name="message" rows="6" required></textarea>
  </div>
  
  <div class="form-group">
    <label for="email">Email (optional):</label>
    <input type="email" id="email" name="email">
  </div>
  
  <div class="form-group">
    <label for="organization">Organization (optional):</label>
    <input type="text" id="organization" name="organization">
  </div>
  
  <button type="submit">Submit Feedback</button>
</form>
```

## FAQ

### General Questions

**Q: Who can contribute to the Open Embeddings specification?**
A: Anyone! We welcome contributions from developers, content creators, AI researchers, and organizations. This is an open-source project driven by community input.

**Q: How are decisions made about the specification?**
A: We use a consensus-driven approach with input from the community. Major changes go through a review process with public discussion periods.

**Q: Is there a formal governance structure?**
A: We're establishing a lightweight governance model with maintainers from different organizations and backgrounds. Details will be published soon.

### Technical Questions

**Q: How stable is the current specification?**
A: This is still a draft specification. We expect changes based on community feedback and implementation experience.

**Q: What about backward compatibility?**
A: We're committed to maintaining backward compatibility once we reach version 1.0. Until then, breaking changes are possible.

**Q: How does this relate to existing standards?**
A: We're building on existing web standards (JSON, HTTP, well-known URIs) and aiming for compatibility with current AI and web technologies.

### Implementation Questions

**Q: Are there reference implementations available?**
A: Yes! Check our [Examples](examples.html) page for code samples in Python, JavaScript, and other languages.

**Q: What about performance and file size concerns?**
A: We're actively working on guidance for managing large embedding files, including compression and pagination strategies.

**Q: How do I validate my implementation?**
A: We're developing validation tools and test suites. In the meantime, use the examples and checklist provided.

## Contributing Guidelines

### Code of Conduct
- Be respectful and inclusive in all interactions
- Focus on constructive feedback and collaborative problem-solving
- Respect different perspectives and use cases
- Help maintain a welcoming environment for all contributors

### Contribution Process
1. **Start with Discussion:** For major changes, start a discussion before implementing
2. **Clear Documentation:** Provide clear rationale for proposed changes
3. **Test Examples:** Include examples and test cases where applicable
4. **Review Process:** Be responsive to feedback during the review process

---

## Thank You

Your participation helps create a better standard for the entire community. Whether you're providing feedback, contributing code, or simply spreading the word, every contribution matters.

**Ready to contribute?** Start by reviewing the [RFC](rfc.html) and [Examples](examples.html), then join the conversation!

*Last updated: [Current Date]*
