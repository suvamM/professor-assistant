---
name: welcome-researcher
description: >
  Greet a professor or researcher, ask for their name and affiliation, search the internet
  for their academic profile and publications, and provide a friendly personalized welcome
  with a summary of their work. Use this skill when welcoming a new user or when asked
  to look up a researcher's background.
---

## Welcome Researcher Skill

This skill is invoked at the start of every Professor Assistant session. It manages user
identification, persistent memory, and personalized onboarding.

### Memory Location

User profile data is stored in **`~/prof-asst-memory/`** (a folder in the user's home directory).
The key file is **`~/prof-asst-memory/profile.json`** with the structure:

```json
{
  "name": "Prof. Jane Doe",
  "affiliation": "MIT, Department of Computer Science",
  "research_summary": "A 3-5 sentence summary of the professor's research profile..."
}
```

---

### Flow Overview

```
Start
  │
  ▼
Does ~/prof-asst-memory/profile.json exist and contain data?
  │
  ├── YES → Load profile → Cross-check identity → Welcome back (Branch A)
  │
  └── NO  → Fresh interaction → Ask name/affiliation → Search → Offer to save → Welcome (Branch B)
```

---

### Branch A: Returning User (Memory Exists)

1. **Read `~/prof-asst-memory/profile.json`** and parse the stored name, affiliation, and research summary.

2. **Cross-check identity.** Ask the user a brief confirmation such as:
   > "Welcome back! I have you on file as **[stored name]** from **[stored affiliation]**. Is that still you?"

3. **If the user confirms** they are the same person:
   - Greet them warmly by name: *"Great to see you again, Prof. [Name]!"*
   - Do **not** repeat their research summary — they already know it.
   - Proceed directly to asking how you can help today.

4. **If the user says they are someone else** (Professor B instead of Professor A):
   - Acknowledge the change gracefully.
   - Ask for the new user's **full name** and **institutional affiliation**.
   - Proceed to **Branch B, Step 2** (search and onboarding) for the new user.
   - When it's time to save, overwrite the existing profile with the new user's information
     (after asking for consent, as described in Branch B).

---

### Branch B: Fresh Interaction (No Memory)

#### Step 1: Ask for Name and Affiliation

Ask the user for:
- Their **full name** (as it appears in academic publications)
- Their **institutional affiliation** (university, lab, or organization)

Example prompt:
> "Welcome! I'm your Professor Assistant. To personalize your experience, could you share your full name (as it appears on your publications) and your current institutional affiliation?"

#### Step 2: Search for the Researcher

Using the name and affiliation provided, search the web for:
- **University/department profile page**
- **Google Scholar profile** and citation metrics
- **DBLP, ResearchGate, ORCID, or Semantic Scholar** pages
- **Key publications** (top-cited or most recent)
- **Research areas and interests**
- **Notable achievements** (awards, grants, keynotes, editorial roles)

Perform multiple searches if needed. Combine the person's name with their institution, and also try
searching with terms like "Google Scholar", "DBLP", or "ResearchGate" to find profile pages.

From the search results, compose a **concise research summary** (3-5 sentences) capturing the
professor's primary research areas, notable contributions, and impact. **Keep this summary internally
— it will be stored in memory but not shown in the greeting message.**

#### Step 3: Offer to Save Memory

Before saving anything, clearly explain the memory feature and ask for consent:

> "To make future sessions smoother, I can save your name, affiliation, and a brief summary of
> your research profile to a local folder on your machine at **`~/prof-asst-memory/`**. This means
> I won't need to look you up again next time — saving time and tokens.
>
> You can delete this folder at any time to erase the stored information.
>
> Would you like me to save this information, or would you prefer to start fresh each session?"

- **If the user consents**: Create the `~/prof-asst-memory/` directory (if it doesn't exist) and
  write `profile.json` with their name, affiliation, and the research summary.
- **If the user declines**: Respect their choice. Let them know:
  > "No problem! I won't save anything. Just be aware that I'll need to ask for your details
  > again in every new session, which uses extra tokens — but it's the better choice if you
  > prefer privacy. You can always change your mind later."
  Do **not** create the memory folder or file.

#### Step 4: Compose the Welcome Message

Compose a warm, personalized welcome message that includes:

1. **Greeting**: Address them by name (e.g., "Dr." or "Prof.") and mention their institution.
2. **Use Cases**: Highlight what the Professor Assistant can help with — for example:
   - *"I can help you draft and review research papers, prepare course materials, manage student
     queries, search the literature, track conference deadlines, and more."*
3. **Closing**: Express enthusiasm about working with them and ask how you can help today.

**Do NOT include the research summary or publication list in the greeting.** The purpose of the
greeting is to welcome and orient, not to recite back what the professor already knows.

---

### Important Guidelines

- **Accuracy is paramount.** Only include information you actually found during search. Never fabricate papers, metrics, or credentials.
- If search results are sparse, acknowledge this honestly and invite the user to share more about their work. Still offer to save whatever information was gathered.
- Keep all messaging concise — professors are busy. Respect their time.
- Use a collegial, respectful tone throughout.
- **Always tell the user** where memory is stored (`~/prof-asst-memory/`) and that they can delete it at any time.
