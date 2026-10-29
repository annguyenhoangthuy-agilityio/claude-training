# Claude 101 Notes

| Field | Value |
|---|---|
| Planned date | |
| Actual sessions | 2026-10-21 |
| Status | In progress |
| Blockers | |

Oct 21, 2026 ·&#32;

### Lesson 2: Your First Conversation with Claude

**Writing effective prompts**

- Every interaction starts with a prompt, and **prompt + context** shape the response
- Talk to Claude like a **coworker**: natural, concise, conversational
- **3-part prompt framework** (adapted from the 4D Framework):
  1. **Set the stage**: your role, objectives, and relevant work context
  2. **Define the task**: the action you want (write, analyze, build…) plus the key details
  3. **Specify rules**: style, tone, format, and examples to show what good looks like
- **Example**: "I'm the marketing lead at an indie streaming startup preparing a Series A pitch deck *(stage)*. Research the indie film streaming market: trends, competitors, growth opportunities *(task)*. Use current web research with citations, as a professional report of up to 5 pages with an exec summary, market analysis, competitive landscape, and opportunities *(rules)*."

### Lesson 3: Getting Better Results

**Common challenges and how to fix them**

- **Too generic** (not enough context): add audience, role, constraints, and the situation
- **Wrong length** (Claude is guessing): state the length explicitly, e.g., "2 paragraphs" or "under 100 words"
- **Wrong format** (it knows *what* you want, not *how*): show an example or spell out the structure
- **Confident but wrong** (plausible errors, especially niche facts): verify key facts, ask for sources or a confidence level, turn on web search
- **Wrong tone** (it defaults to helpful and professional): describe the tone in plain words or give a writing sample

**The iteration mindset**

- The first prompt **starts a conversation**; it isn't a one-shot request
- Treat first drafts as **starting points**: review, keep what works, refine
- Give **specific feedback** ("cut the first 2 paragraphs and make the conclusion action-oriented" beats "make it shorter")
- Know when to **start a fresh chat** with a clearer prompt

**Evaluating Claude for your workflows (evals)**

- **Evals** = systematic tests of how well Claude handles *your* recurring tasks (applying Discernment)
- Why: they show where Claude adds the most value, where it needs more context or examples, and they build trust for repeat tasks
- **Simple 4-step eval**:
  1. **Gather** 5–10 examples of work you've already done
  2. **Write test prompts** with the context you'd normally have
  3. **Compare** Claude's output to yours: key info, tone and style, gaps
  4. **Refine** your prompts or examples, and mark where human review is essential
- **Delegation–Diligence loop** (data example: Rio's quarterly analysis): rerun a past analysis whose answers you already know → check each result → refine → retest
  - If it matches your known results, you can **trust the approach** for new data
  - If it still doesn't after several refinements, **don't delegate** that task
  - Record the context you had to add so you can reuse it (e.g., "consider program type"), and watch for the AI inferring data it doesn't actually have
- Not data-savvy? Use Claude as an analyst partner (formulas, data cleanup) and keep asking it to explain each step
- ⚠️ Validation builds confidence but **doesn't remove responsibility**: you still check results and disclose AI's role

### Lesson 4: How You'll Work with Claude on Your Desktop

- The desktop app is the home base. The work comes in **3 shapes**: recognize the shape first, and the right tab follows

**1. Turn by turn → Chat** (Claude as a thinking partner)

- Use it when each answer shapes your next question, you want your judgment on every turn (drafting, editing), or the task is quick
- Desktop extras: **quick entry** (double-tap Option on Mac), **screenshots/window sharing**, **dictation**, **desktop connectors**

**2. Handing work off → Cowork** (delegating, not chatting)

- Use it for **multi-step** tasks, **finished files saved into your folders**, work that **spans your tools**, or **scheduled/background** work
- You stay in control: Claude asks scoping questions, shows its plan, lets you watch and steer, and asks approval before key actions (sending email, sharing files)
- Key features:
  - **Local folder access**: reads a folder and saves results back to it (Chat only gives you downloads)
  - **Scheduled tasks**: run remotely even when your computer sleeps, unless they need local files
  - **Subagents**: parallel workers that produce one finished deliverable
  - **Projects**: grouped tasks with shared files, instructions, and memory
  - **Browser use** (Claude in Chrome), **computer use** (research preview), **plugins** (role-based bundles)
- Examples: answer a question across meeting notes, Slack, and email, then update a deck; summarize 50+ docs into a memo; a Monday-morning briefing
- Plans: Pro, Max, Team, Enterprise

**3. Building software → Code tab** (Claude Code, for developers)

- Works directly in a codebase: read, write, test, run commands; visual diffs, terminal, git rollback
- **Local** (a folder on your machine) or **Cloud** (a GitHub repo; keeps running after you close the app)
- Autonomy modes: **Manually approve**, **Accept edits**, **Plan**

**Quick pick**: ask, brainstorm, or draft → **Chat** · multi-step, file, cross-tool, or scheduled → **Cowork** · code → **Code**

### Lesson 5: Introduction to Projects

- **Projects** = self-contained workspaces, each with its own chats, knowledge base, instructions, and memory, dedicated to one work stream
- **When to use**: ongoing work (not one-off questions) that has **reusable reference material**, **consistent response requirements**, or **team collaboration** needs

**Setup (3 steps)**

1. **Create**: name it, add a description (for humans; Claude doesn't see it), set visibility (private or shared with your org)
2. **Instructions**: apply to every chat in the project. Include context, process, tone/style, and specific requirements (e.g., "always end with a CTA")
   - You can also automate workflows, e.g., "When I upload a meeting transcript, summarize it with this template"
3. **Knowledge base**: upload PDF, DOCX, CSV, TXT, HTML, or connect Google Drive. Add guidelines, templates, background docs, and sample work to emulate

**Key behaviors**

- Knowledge is used automatically in **every chat** in the project, so there's no re-uploading
- Chats don't share context with each other unless the info is **in the knowledge base**
- Files uploaded *inside a chat* stay out of the knowledge base, which keeps it uncluttered
- **Scales with RAG**: near the context limit, Claude searches the files and pulls in only what's relevant, for **up to 10x** the capacity

**Collaboration (Team/Enterprise)**

- Permissions: **Can view** (read and chat) · **Can edit** (change instructions, knowledge, members) · **Owner** (full control, including visibility)
- Share with specific people or everyone in the org; shared projects appear under "Shared with me"
- e.g., a brand team shares a voice-and-tone project so anyone can write on-brand

**Best practices**

- **Start focused**: one use case per project, then expand
- Keep the knowledge base **current**, since outdated docs mean outdated answers
- Write **clear, specific instructions**
- Use **descriptive file names** (e.g., `Q4-2025-Sales-Report.pdf`) and group related files
- **Mention documents by name** in prompts to focus Claude's search

**Example projects**: product launch, research hub, client account hub, event planning, job description generator

### Lesson 6: Creating with Artifacts

- **Artifacts** = standalone outputs (doc, deck, design, dashboard, prototype) shown in their own window beside the chat, rather than buried in it
- Claude makes one when the output is something to **edit, reuse, or share**; you can also just ask, "Create this as an artifact"
- **Paid plans**: everything is saved in the **Artifacts tab**, separate from the chat. The conversation is where you *create*; the tab is where outputs *live*. (On Free, an artifact stays in its chat)

**3 dedicated types** (beta, paid plans)

- **Claude Design**: landing pages, one-pagers, mockups, prototypes. Can use your design system; drag and resize on the canvas
- **Claude Slides**: decks built from notes, reports, or the chat. Edit slides and present inside Claude; export to PPTX or PDF
- **Claude Docs**: living docs that you and colleagues co-edit in real time; Claude explains its choices in comments. Charts from connected tools are **snapshots** (ask Claude to refresh them). Export to Google Docs or DOCX
- You can convert between them: "turn this doc into a deck"
- **Any plan**: dashboards, trackers, flowcharts, interactive pages, code
- **Artifact vs. file creation**: an artifact lives in Claude and is shared by **link**; file creation gives you a downloadable Word, Excel, PowerPoint, or PDF

**Working on an artifact** (mix these freely)

- **Edit directly**: fix typos, move a logo, without waiting for a rewrite
- **Comment for Claude** on a specific spot; @-mention Claude in a doc and it explains what it changed
- **Just ask** in the chat
- Editing, commenting, and sharing happen on desktop or web; on mobile you can only view

**Sharing**

- **Private** until you share. Permissions: view, comment, or edit; recipients need a Claude account
- **Pro/Max**: share by link or publish publicly (the chat stays private)
- **Team/Enterprise**: org-only by default; external sharing needs an admin to turn it on
- **Export**: deck → PPTX/PDF · design → PPTX/PDF/HTML · doc → Google Docs/DOCX

**Tips**

- Ask for the **deliverable**, not just the content ("turn Q3 results into a one-page doc for leadership")
- Be **specific** about features
- Say **who the end user is**
- Create artifacts **at the end** of a conversation, once Claude understands the problem
- **Refresh** embedded data when you need it current

### Lesson 7: Working with Skills

- **Skills** = folders of instructions, scripts, and resources that Claude loads **only when relevant**. Think of them as expertise packages for repeatable tasks
- Plans: Pro, Max, Team, Enterprise (feature preview)

**2 types**

- **Anthropic Skills**: built in (Excel, Word, PowerPoint, PDF) and invoked automatically
- **Custom Skills**: made by you or your org for your own workflows (brand guidelines, meeting-notes format, analysis methods)

**Enabling**

- **Settings > Capabilities** → turn on **Code execution and file creation** (skills need the sandbox) → toggle individual skills
- Enterprise: an owner must enable it first · Team: on by default

**Using skills**

- Usually **automatic**: Claude picks the right skill from your request; you'll see it named in Claude's thinking
- Works on **your real files** (xlsx, pptx, docx, pdf): Chat creates a **new version** rather than editing the original; download it or save to Drive
- May need **Allow limited network access** turned on
- 🔒 Skills can run code: install custom skills only from **trusted sources** and **review** external ones first; your custom skills are private to your account

**Creating a custom skill** (by chatting, no code needed)

1. Tell Claude what the skill should do
2. Answer its interview questions (purpose, what good output looks like, when to use it)
3. Upload reference material (templates, style guides, examples)
4. Save the generated skill; it then runs automatically when relevant

- Manage and edit skills in the **Customize** tab; ask Claude to iterate on them

**Skills vs. Projects**: *projects store knowledge, skills perform tasks*

- **Projects** = the *what*: reference material, long-term context, team collaboration; available in every chat in the project
- **Skills** = the *how*: steps, order, methodology for repeatable multi-step workflows; applied when invoked
- They complement each other: a skill can use knowledge stored in a project (e.g., a call-prep skill pulling customer profiles)

### Lesson 8: Connecting Your Tools

- **Connectors** turn Claude from an assistant into an **informed collaborator** that works with your real tools and data, so you don't start from scratch every time
- Claude can **read** (search, retrieve, analyze) and **act** (create, update, run tasks), depending on the permissions you grant
- Powered by **MCP (Model Context Protocol)**: the "USB-C for AI", an open standard that lets anyone build connectors

**2 types**

- **Web connectors**: cloud services (Google Drive, Notion, Slack, Asana, Gmail…)
- **Desktop extensions**: run locally in the Desktop app (local files, browser control, native apps like Figma). Install via **Settings > Extensions**

**Setup (web)**

1. Find it at **claude.ai/directory** or under **+ > Connectors** in a chat
2. Click **Connect** → sign in to the service
3. **Review the permissions** → authorize
4. **Test**: "Can you access my \[tool\]?"

- The directory lists connectors, not apps: one connector can cover several tools (e.g., **Atlassian Rovo** = Jira + Confluence). If a tool is missing, add a **custom connector**

**Example prompts**

- **PM tools** (Jira, Asana, Linear): "My highest-priority tasks due this week?", "Create a task…", "Summarize the launch status"
- **Communication** (Slack, Gmail): find a thread, draft a reply, "what did the team decide yesterday?"
- **Docs** (Notion, Drive, Confluence): look up guidelines, summarize meeting notes
- **Business** (Stripe, HubSpot): revenue trends, deal status

**Security**

- **Scoped access**: you can toggle individual permissions
- **Claude sees only what you can see** (your inbox, not your CEO's)
- **Revocable anytime** in Claude's settings or the service's
- Install custom connectors **only from trusted sources**

### Lesson 9: Enterprise Search

- **Enterprise Search** = an "**Ask {Org Name}**" project in the sidebar, like a pre-built project with your whole company's knowledge already loaded
- Built for **information gathering** across tools, with custom instructions from Anthropic
- Plans: **Team and Enterprise** only; an admin must set it up
- Searches SharePoint, Slack, Gmail, Drive, and more, combines them into **one answer, and always cites sources**

**Good questions to ask**

- **Catching up**: "What happened yesterday while I was out?", "Current blockers on project X?"
- **Policies and processes**: remote work, expense reports, time off
- **Research**: why customers pick competitors, roadmap discussions
- **Onboarding**: how a system works, who to ask about billing
- **Tracking**: key decisions from last week's meetings, team contributions

**2-step setup**

- **Admin (Owner)**: Ask Your Org → Set up → connect **Documents** (Drive/SharePoint) and **Chat** (Slack/Teams), which are required; Email is optional → name it → Finish
- **User**: open the project → guided onboarding → sign in to each service → start asking. More connectors means fuller results

**Security**: shows only what **you already have access to**; conversations stay private; your data isn't indexed or stored separately

### Lesson 10: Research for Deep Dives

- **Research** = Claude as a **systematic investigator**: it works **agentically**, running many searches that build on each other (sometimes hundreds of sources) across the web and connected tools
- Takes **minutes**, not seconds; runs in the background
- Works with **Thinking**: plans and breaks down the question first, then gathers
- **Every claim is cited**, so it's easy to verify

**How it works**: 1. Plan → 2. Search repeatedly, following leads → 3. Synthesize into a report → 4. Cite sources

**Which tool to use**

- **Research**: multi-source reports, comparisons (competitors, vendors), planning complex projects, cited briefings, hours of manual work
- **Web search**: a quick fact from 1–2 sources, when speed matters
- **Thinking**: deep reasoning with no outside info (math, debugging, logic)
- **Enterprise Search**: internal company knowledge (policies, past decisions)

**How to use**: **+** → **Research** (needs **web search** on) → enter the prompt → watch progress

**Prompt tips** (worth the effort, since a run takes minutes)

- Be **specific about the goal** ("Analyze the EV battery market: key players, tech trends, supply chain risks for investment decisions")
- **Specify the structure** you want; Claude organizes findings around it
- Add **constraints**: budget, timeline, geography
- Ask Claude to **help write the Research prompt** first

**With integrations**: mix internal and web sources, e.g., "Summarize Project X discussions across my email and Slack, then research industry best practices" or "Research each company on next week's calendar"

### Lesson 12: Other Ways to Work with Claude

- Claude is an intelligence, and **claude.ai is just one way in**. Specialized tools bring Claude to **where you already work**

| Tool | Use it when you want to… | Where it runs |
| --- | --- | --- |
| **Claude.ai** | General tasks, research, writing, analysis, file creation | Web, desktop, mobile |
| **Claude Code** | Build features in plain English, debug from error messages, explore an unfamiliar codebase, automate chores (lint, merge conflicts, release notes) | Terminal, IDE, browser |
| **Cowork** | Hand off multi-step tasks: research briefs, docs, file organizing, data analysis | Desktop (+ web/mobile beta) |
| **Claude Tag** | Summarize long threads, draft replies, prep for meetings, onboard from channel history, hand a bug report to Claude Code | Slack (tag Claude in a thread) |
| **Claude Design** | Turn a brief, sketch, or screenshot into a working UI prototype; compare variations; use your design system | Web |
| **Claude for Excel** | Understand formulas across tabs, update assumptions safely, trace #REF!/#VALUE! errors, build pivots and charts | Excel sidebar |
| **Claude for PowerPoint** | Outline → first-draft deck, tighten copy and speaker notes, restructure slides, keep your template and branding | PowerPoint sidebar |
| **Claude for Word** | Notes → draft in your template, revise sections, work through tracked changes and comments, ground claims in sources | Word sidebar |
| **Claude for Outlook** (beta) | Triage mail, draft replies using thread and calendar context, summarize long chains | Outlook sidebar (separate install) |
| **Claude in Chrome** (beta) | Summarize pages, manage your inbox, automate forms and multi-step web flows, pull context from internal tools and dashboards | Chrome sidebar |

- ⚠️ **Claude in Chrome**: use it for **low-risk tasks on trusted sites**. It asks before risky actions (purchases, personal data), and some site categories (financial, adult) are blocked by default
- 💡 **BA/PM use**: Tag to summarize Slack discussions, Word for requirement drafts and review comments, Chrome to pull context from Jira or internal dashboards
