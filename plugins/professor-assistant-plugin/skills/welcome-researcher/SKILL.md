---
name: welcome-researcher
description: >
  Greet a professor or researcher, ask for their name and affiliation, search the internet
  for their academic profile and publications, and provide a friendly personalized welcome
  with a summary of their work. Use this skill when welcoming a new user or when asked
  to look up a researcher's background.
---

## Welcome Researcher Skill

When this skill is invoked, follow these steps:

### Step 1: Ask for Name and Affiliation

Ask the user for:
- Their **full name** (as it appears in academic publications)
- Their **institutional affiliation** (university, lab, or organization)

Example prompt:
> "Welcome! I'd love to learn about you. Could you please share your full name (as it appears on your publications) and your current institutional affiliation?"

### Step 2: Search for the Researcher

Using the name and affiliation provided, search the web for:
- **University/department profile page**
- **Google Scholar profile** and citation metrics
- **DBLP, ResearchGate, ORCID, or Semantic Scholar** pages
- **Key publications** (top-cited or most recent)
- **Research areas and interests**
- **Notable achievements** (awards, grants, keynotes, editorial roles)

Perform multiple searches if needed. Combine the person's name with their institution, and also try
searching with terms like "Google Scholar", "DBLP", or "ResearchGate" to find profile pages.

### Step 3: Compose the Welcome Message

Compose a warm, personalized welcome message that includes:

1. **Greeting**: Address them by name (e.g., "Dr." or "Prof.") and mention their institution.
2. **Research Summary**: A 2-3 sentence overview of their primary research areas.
3. **Notable Works**: Highlight 3-5 of their most impactful or recent publications with titles.
4. **Citation Impact** (if available): Mention h-index, total citations, or other metrics found.
5. **Closing**: Express enthusiasm about helping them and ask how you can assist today.

### Important Guidelines

- **Accuracy is paramount.** Only include information you actually found. Never fabricate papers, metrics, or credentials.
- If results are sparse, acknowledge this honestly and invite the user to share more about their work.
- Keep the summary concise but informative — aim for a message that a busy professor would appreciate.
- Use a collegial, respectful tone throughout.
