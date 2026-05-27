**Group 05 (HighFive)**  
**Group 01 \-  Allegro Peer Review**

### **Strengths:**

Allegro has a clear technical direction. The human UI and AI-agent workflow are separated, but both still use one shared backend and database. This makes the architecture easier to follow and avoids having two disconnected systems. The ADRs explain the main choices well, especially using Cloudflare Workers, D1, and an LLM layer to structure issue data without giving AI full control.

The backend docs are detailed and useful. They explain setup, Wrangler, D1, auth, deployment, and troubleshooting clearly. The repo also has good process structure with issue templates for features, testing, and docs/research. The sprint planning docs show that frontend, backend, LLM/CLI, testing, and documentation work are being divided intentionally.

The frontend is clean and easy to [use](http://use.In). In terms of usability, the split-pane tracker layout works well, the filters are understandable, and the issue creation modal has options like priority and tags which makes it detailed but still structured. There is also a light/dark mode which improves accessibility. The multiple-team dashboard is unique because it makes the product feel more realistic for group work. The invite-user flow is a good idea if fully implemented so it mimics an actual multi-team product. The drag-and-drop log upload and skills.md idea also fit the AI-agent direction well.

### **Improvements:**

The main issue is that the documentation and architecture feel more complete than the actual working product. The repo describes a full UI → backend → LLM → D1 → external agent/CLI workflow, but the full loop still feels unfinished when tested. Since this is the main idea of Allegro, proving this workflow should be the priority.

The frontend has some usability issues. For example, after creating an issue, editing seems limited mostly to the issue title. Fields like description, priority, category, and tags do not seem editable afterward. Also,  if I mistakenly created an issue, currently there isn’t a way to delete that on the UI. There also does not seem to be an issue activity/history view, which is important for tracking human and agent updates. 

The issue list could be easier to scan. Statuses like Open, Done, and In Progress are shown through small tags, so users have to read each row carefully or use sort. Stronger color differences, borders, status dots, or grouped sections would make open work easier to find.

Documentation is strong in some areas but uneven overall. Some files in docs/process, docs/frontend, docs/backend, and docs/api are empty, repeated, or placeholder-level. The ai-use-log is a good idea, but it is mostly empty right now. Overall, there are many docs that need to be organized and completed or even merged.

Also, the GitHub Pages site triggered a Chrome “Dangerous site” warning using the link on READMe. This might be a false positive or configuration issue, but it might be worth checking.

**Questions:**

How will Allegro handle trust when an external AI agent updates an issue? If an agent marks something as resolved, does that become final right away, or does a human review it first?

The docs show that agents can update status and resolution notes, but are there stricter limits on what agents can edit compared to humans? For example, should agents be blocked from changing priority, tags, descriptions, or assignments?

What happens if the LLM structuring layer fails or gives bad output? The raw issue should probably still be saved instead of blocking issue creation.

How will Allegro handle cases where a human and an AI agent update the same issue at the same time? Which update wins, and will the user be warned if something gets overwritten?

### **Suggestions:**

The most important next step is showing one complete end-to-end demo: create an issue in the frontend, structure it with the LLM, store it in D1, fetch it through the CLI/API, update it from the agent side, and show the update back in the frontend.

Add simple version tracking for issue updates. Each issue could have a version or updated\_at field, so if a human and agent edit the same issue, the backend can detect conflicts instead of silently overwriting changes.

Also, a “help me” button on the website might be useful to describe all features. Since the project includes both a UI and CLI/agent workflow, less technical users may not immediately understand what the CLI is for or how the agent side connects to the website.

Adding a simple activity timeline or log would also help a lot. It could show issue creation, edits, status changes, comments, and agent updates. 

