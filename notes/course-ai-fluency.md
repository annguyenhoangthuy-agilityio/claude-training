# AI Fluency Notes

Oct 14, 2026 · @Quan Nguyen

## Course 1: AI Fluency

<https://academy.claude.com/courses/ai-fluency-framework-foundations>

### Lesson 1: Introduction to AI Fluency

- Focus is **human–AI collaboration**, not just AI as a technology
- **AI Fluency** = working with AI effectively, efficiently, ethically, and safely
- Framework built on the **4D competencies**: Delegation, Description, Discernment, Diligence
- Goal: lasting skills that stay relevant as AI evolves
- Requires practical skills **plus** a mindset shift in how we work with AI

### Lesson 2: Why do we need AI Fluency?

Three ways to work with AI:

- **Automation**: AI completes specific tasks from your instructions
- **Augmentation**: You and AI collaborate as partners in thinking and execution
- **Agency**: You configure AI to act independently for you, setting its knowledge and behavior rather than assigning single tasks

### Lesson 3: The 4D Framework

- The 3 modes of engaging with AI are **Automation**, **Augmentation**, and **Agency** (see Lesson 2)
- **The 4Ds** are the core competencies:
  - **Delegation**: decide what work to do with AI and what to do yourself
  - **Description**: communicate effectively with AI
  - **Discernment**: evaluate AI outputs critically
  - **Diligence**: collaborate with AI responsibly
- The 4Ds apply across **all 3 modes**
- Building them prepares you for future AI capabilities

### Lesson 4: Generative AI Fundamentals

- **Generative AI** creates new content, while traditional AI analyzes and classifies existing data
- **LLMs** (e.g., Claude) predict and generate language; *large* = billions of parameters
- **3 enablers**: transformer architecture (2017), huge amounts of digital data, massive compute (GPUs/TPUs, clusters)
- **Scaling laws**: more size, data, and compute lead to predictably better performance, and to **emergent abilities** nobody explicitly programmed
- **Training**: *pre-training* (predict the next word over billions of texts), then *fine-tuning* (follow instructions, avoid harm; uses human feedback and reinforcement learning)
- **Prompts**: the model generates new text from patterns it learned; it doesn't retrieve stored answers
- **Context window** = the AI's working memory (prompts + responses + shared content); it's limited, and the model can't see beyond it without tools like web search
- **Key strengths**: learns from vast data, **in-context learning** (adapts to a new task from your prompt without retraining), emergent capabilities from scale

### Lesson 5: Capabilities & Limitations

- Recap: what generative AI is, its 3 enablers, and pre-training → fine-tuning (see Lesson 4)
- **Capabilities**: versatile across tasks, aware of the conversation, can connect to external tools
- **Limitations**:
  - Knowledge cutoff date
  - **Hallucinations** (confident but wrong output)
  - Context window limits
  - Struggles with complex reasoning
- **Best results combine human and AI strengths**: humans bring critical thinking, judgment, creativity, and ethical oversight

### Lesson 6: A Closer Look at Delegation

- **Delegation** = deciding what work you do yourself, what you do together with AI, and what AI handles alone
- 3 sub-skills:
  - **Problem Awareness**: know your goals and the nature of the work before involving AI
  - **Platform Awareness**: know what different AI systems can and can't do
  - **Task Delegation**: split the work so each side plays to its strengths
- Requires **domain expertise plus an understanding of AI**
- Goal: not automating everything, but finding the **best human–AI partnership** for each task

### Lesson 8: A Closer Look at Description

- **Description** = communicating with AI so the two of you collaborate productively. It goes beyond clever prompts: explaining tasks, giving context, steering a conversation that's going wrong, and guiding the AI's reasoning
- AI can't read your mind, so **don't make it guess**. Set explicit requirements
- 3 types:
  - **Product**: *what* you want. Ask yourself: what's the context? What exactly should it do? What format? Who's the audience, and what style fits?
  - **Process**: *how* the AI should approach the work, which can matter as much as the goal
    - 3 ways to guide it: general guidance (*manual*), step-by-step instructions (*cookbook*), or examples (*demonstration*)
    - Specify which data to use, which issues to cover and in what order, and the analysis style, workflow, or technique
  - **Performance**: *how the AI behaves*. Decide what kind of thinking partner you need:
    - Narrow toward an answer, or explore options?
    - Challenge your assumptions, or follow your lead?
    - Detailed, or concise?
    - Explain its reasoning, or just give the answer?
- ⭐ **Main lesson of the course**: AI is an **interactive partner**, not a database or vending machine, and it behaves differently depending on context
- Being clear up front saves time and gives better results

### Lesson 9: Effective Prompting Techniques

- **Prompting** = the Description competency in practice. Brief the AI like a helpful new colleague who needs clear directions
- It combines good human communication with AI-specific needs: be more explicit than you would with a person, mind the context window, and sometimes use structured formatting
- **6 foundational techniques**:
  1. **Give context**: say what you want, why you want it, and *who you are* (e.g., "I'm preparing for a job interview, I have an ecology degree…")
  2. **Show examples** (few-shot / n-shot): try without examples first; when you add them, cover diverse cases
  3. **Specify constraints**: format, length, language, design details
  4. **Break into steps** (chain of thought): most useful when the task can be done many ways or depends on your domain expertise
  5. **Ask it to think first**: thinking *before* the answer improves quality (explaining afterwards doesn't), and it shows you where the AI goes astray
  6. **Define role, style, or tone**: e.g., "as a UX expert…" or "a science teacher talking to a 10-year-old"
- ⭐ **Secret weapon**: ask the AI to help write or improve your prompt
- **Iterate**: add specificity, try another technique, ask for variations or a different format, check its confidence, or **start a fresh chat** when one goes off track
- ✅ **What works**: a clear task overview, format specs with examples, explicit constraints, rich background
- ❌ **Mistakes to avoid**: assuming it reads your mind, cramming unrelated tasks into one prompt, a vague definition of success, giving no feedback
- Techniques change as models improve, but the communication principles stay

### Lesson 10: A Closer Look at Discernment

- **Discernment** = critically evaluating what AI produces, how it produces it, and how it behaves. It's your **quality control**, and the flip side of Description
- Requires **domain expertise** (to judge quality) plus knowing AI's typical shortcomings
- 3 types:
  - **Product**: judge the output. Is it accurate? Right for the audience and purpose? Coherent? Does it meet the requirements and add value?
  - **Process**: judge *how it got there*. Watch for logical errors, attention lapses, inappropriate steps, getting stuck on one interpretation, and circular reasoning (e.g., ideas you rejected creeping back in). This matters most on complex tasks
  - **Performance**: judge *how it interacts with you* (process = the work; performance = the collaboration). Is it too many questions or too brief? Does it respond well to feedback? Is it efficient?
- **Giving feedback**: say what the problem is and why, suggest a concrete fix, and revise your instructions or examples
- When discernment finds a problem, **better Description** is usually the fix, though sometimes you need to rethink **Delegation** (wrong tool or approach)
- 🔁 Description and Discernment form a **continuous loop** of instruct → evaluate
- Even the best AI needs human judgment and oversight

### Lesson 12: A Closer Look at Diligence

- **Diligence** = taking responsibility for your AI collaborations. It covers the **ethical and safe** side of AI fluency, where the other 3Ds cover effectiveness and efficiency
- Analogy: driving isn't just getting from A to B; you also follow the rules and watch out for others
- 3 types:
  - **Creation**: be intentional about *which* AI you use and *how*. How was it trained? Who owns and can access the data you input? Does it fit your values and your org's policies? (e.g., check data protection and company rules **before** sharing sensitive info)
  - **Transparency**: be honest about AI's role with everyone who needs to know. Who should know, how, when, and in how much detail? (e.g., tell teammates which parts of a proposal were AI-assisted)
  - **Deployment**: **you, not the AI, are responsible** for what you share. Verify facts, check for bias, confirm usage rights, and hold it to the same standard as work you did alone
- Expectations differ by context (personal, academic, creative, professional), so **know them and meet them**
- Build personal AI guidelines, learn your org's policies and industry standards, and keep up with AI laws, which are still evolving

### Lesson 13: Conclusion

- AI Fluency grows through **intentional practice** of the 4Ds
- **Delegation**: your expertise and judgment are the foundation
- **Description**: clear communication bridges your intentions and what the AI can do
- **Discernment**: evaluate outputs critically, within the system's limits
- **Diligence**: accountability, transparency, responsibility
- The best outcomes come when humans and AI **build on each other's strengths**
- The framework is built to stay relevant as AI evolves
