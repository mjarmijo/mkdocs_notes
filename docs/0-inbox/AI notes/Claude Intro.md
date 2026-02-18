## Claude models
opus 4.5 - use for complex tasks
sonnet 4.5 - use for everyday tasks. Has an extended thinking mode for deeper reasoning. Works through problems step by step making it suited for tasks using careful analysis.

What project should use extended thinking? Project planning, planning/trend analysis, technical problems, math, coding. Not necessary for simple questions, basic info, and general writing. 

Learning mode - guides your reasoning process instead of providing answers to help you develop critical thinking skills

## Accessing Claude
Claude.ai - mobile and desktop apps - idea for conversations, writing assistance, research, analysis. 

Claude code - agentic coding tool designed for developers, but can be used for all kinds of file manipulation. It can directly edit files, run commands, create commits.  See here for more details: https://anthropic.skilljar.com/Claude-code-in-action

Claude and slack - chat with Claude in the AI assistance header from any channel or conversation, or mention @Claude in threads. It can search your channels, mesages, and files, to find context. 

Claude for excel - work directly with Claude in excel where it can read, analyze, modify and create new workbooks. Think model analysis, assumption updates, errors/debugging, make templates, explain formulas. 

## Conversations with Claude
- talk to it like you would a coworker
- **Stage setting** - Set the role, objectives, and context
- **define your task** - what are the actions you want it to take?
- **specify rules** for style, tone and examples you can attach to show
- Upload documents or background information so Claude can consider it in response - it's a shortcut to help Claude understand your needs
	- Uploading documents are a shortcut to helping Claude understand your needs
	- pdf, csv, docs, txt, PNG, JPEG, web search, data sources like drive, calendar etc. and Claude will parse the content
- ![[Pasted image 20260216070623.png]]
- organize your conversations into **projects** with persistent context
- **Artifacts** turn your ideas into shareable objects
- Improve the responses you are getting by asking follow up questions, providing feedback (Can you expand on the second point?" or "That's helpful, but can you make it more concise?") about what is good/bad ("This is good, but the tone is too formal. Can you make it more conversational?"), and redirecting it/restarting your conversation. 
## Getting the best results

4D's of AI Fluency - 
- **Delegation:** Deciding on what work should be done by humans, what work should be done by AI, and how to distribute tasks between them. Includes understanding your goals, AI capabilities, and making strategic choices about collaboration.
- **Description:** Effectively communicating with AI systems. Includes clearly defining outputs, guiding AI processes, and specifying desired AI behaviors and interactions.
- **Discernment:** Thoughtfully and critically evaluating AI outputs, processes, behaviors and interactions. Includes assessing quality, accuracy, appropriateness, and determining areas for improvement.
- **Diligence:** Using AI responsibly and ethically. Includes making thoughtful choices about AI systems and interactions, maintaining transparency, and taking accountability for AI-assisted work.
![[Pasted image 20260216190349.png]]

Effective Claude users:

- **Treat first drafts as starting points.** Review what Claude produces, identify what's working and what isn't, then refine.
- **Give specific feedback.** "Make it shorter" is fine, but "Cut the first two paragraphs and make the conclusion more action-oriented" is better.
- **Know when to start fresh.** If a conversation has gone off track, sometimes it's faster to open a new chat with a clearer prompt than to try to redirect.

Evals - Evals are systematic ways to test how well Claude performs on specific types of tasks that matter to you. Running simple evals helps you:

- Understand where Claude adds the most value in your workflow
- Identify tasks where you'll need to provide more context or examples
- Build confidence in Claude's outputs for recurring tasks

A practical Eval approach:

1. **Gather examples.** Collect 5-10 examples of a task you do regularly—emails you've written, reports you've created, analyses you've done.
2. **Create test prompts.** Write prompts that would generate similar outputs. Include the context you'd naturally have when doing this work.
3. **Compare outputs.** Run your prompts and compare Claude's responses to your examples. Ask yourself:
    - Does Claude capture the key information?
    - Is the tone and style appropriate?
    - What's missing or could be improved?
4. **Refine your approach.** Based on what you learn, adjust your prompts, add examples to show Claude what good looks like, or identify where human review is essential.

To evaluate how Claude might work with your data reproduce a past analysis you've done, then evaluate the quality of its output against known results:

- Find a dataset you've manually analyzed
- Create prompts that request Claude to do the analysis on your behalf
- Compare Claude's results to your originals
- Note patterns and refine your prompt accordingly: Maybe Claude gets the right numbers but misses the overall patterns
![[Pasted image 20260216191243.png]]

## Projects
- **Projects are self-contained workspaces** with their own memory, chat histories, knowledge bases, and customized instructions. Think of them as dedicated environments for specific work streams. Each conversation within the project automatically has access to your knowledge base and follows your project instructions.
- **Project knowledge enhances Claude's understanding** by letting you upload relevant documents that Claude references across all chats within that project. No more re-uploading the same files each time.
- **Project instructions guide Claude's behavior**—you can specify tone, expertise level, response style, and more. These instructions apply to every conversation within the project.
- **Projects scale automatically**. When your knowledge base approaches context limits, Claude seamlessly enables Retrieval Augmented Generation (RAG) mode to expand capacity by up to 10x while maintaining response quality.
- **For Claude for Work users, projects enable collaboration**. Share projects with teammates so everyone benefits from the same context, instructions, and accumulated knowledge.

### Instructions
Project instructions tell Claude how to behave across all conversations in this project. Click on "Instructions" to open the instructions panel.

Good project instructions typically include:
- **Context about what you're working on:** "This project is for creating marketing content for our B2B software product."
- **Process instructions:** "First consider a blog structure that will entice this audience, then write the draft."
- **Tone and style preferences:** "Use a professional but conversational tone. Avoid jargon when possible."
- **Specific requirements:** "Always include a call-to-action at the end of marketing copy."

### Knowledge base
Your project's knowledge base is where you upload documents that Claude should reference. You'll find the files menu on the right side of your project's main page. Click the "+" button to add content. You can upload various file types including PDF, DOCX, CSV, TXT, HTML, and more. You can also connect to Google Drive to link documents directly.

**What to upload:**
- Reference documents (brand guidelines, style guides, templates)
- Background materials (research reports, meeting notes, requirements docs)
- Examples of work you want Claude to emulate
- Technical documentation or specifications
- **Pro tip:** Name your files descriptively. Claude uses file names to understand and retrieve the right information, so "Q4-2024-Brand-Guidelines.pdf" is more helpful than "document1.pdf."

Projects automatically scale to handle large amounts through a feature called Retrieval Augmented Generation (RAG). When your project knowledge approaches the context window limit, Claude seamlessly enables RAG mode. Instead of loading all project content into memory at once, Claude intelligently searches and retrieves only the most relevant information needed to answer your questions. This expands your project's capacity by up to 10x while maintaining response quality. You'll see a visual indicator when your project is RAG-enabled, but the experience should feel the same—you can still upload documents, chat with Claude, and get context-aware responses.

**How a RAG Model Works (The Three Steps)**
1. **[Retrieval](https://www.google.com/search?client=ubuntu-sn&channel=fs&q=Retrieval&mstk=AUtExfBRQLrm-PHSW5uMkhRzFenTK7FppSeDuE4jZkJdq8ppxell_4nS6D336h7YW3we7NehYIzBFPa9-yL-m0QaFB_av8lSn_nN-po9CepLmX8Adych0hwMP1CIsOT3PWb7dLc&csui=3&ved=2ahUKEwiVyPbErd-SAxWW5ckDHTOrBPwQgK4QegYIAQgAEBA):** When a user asks a question, the system searches an external data source (like a database, document store, or internet search) for relevant information
- **[Augmentation](https://www.google.com/search?client=ubuntu-sn&channel=fs&q=Augmentation&mstk=AUtExfBRQLrm-PHSW5uMkhRzFenTK7FppSeDuE4jZkJdq8ppxell_4nS6D336h7YW3we7NehYIzBFPa9-yL-m0QaFB_av8lSn_nN-po9CepLmX8Adych0hwMP1CIsOT3PWb7dLc&csui=3&ved=2ahUKEwiVyPbErd-SAxWW5ckDHTOrBPwQgK4QegYIAQgBEAE):** The retrieved, relevant data is added to the user's original prompt to provide context.
- **[Generation](https://www.google.com/search?client=ubuntu-sn&channel=fs&q=Generation&mstk=AUtExfBRQLrm-PHSW5uMkhRzFenTK7FppSeDuE4jZkJdq8ppxell_4nS6D336h7YW3we7NehYIzBFPa9-yL-m0QaFB_av8lSn_nN-po9CepLmX8Adych0hwMP1CIsOT3PWb7dLc&csui=3&ved=2ahUKEwiVyPbErd-SAxWW5ckDHTOrBPwQgK4QegYIAQgCEAE):** The LLM receives the enriched prompt and generates a response based on both its training and the provided information.

**Key Benefits of RAG**
- **Improved Accuracy:** Reduces "hallucinations" (confident, false answers) by providing factual,, up-to-date context.
- **Access to Proprietary Data:** Allows AI to answer questions based on private company documents, emails, or databases without retraining the LLM.
- **Cost-Effective:** It is cheaper to use RAG than to fine-tune or retrain large models to learn new information.
- **Trusted Sources:** Provides citations for the information used, allowing users to verify the answer.
### Best practices for projects
- **Start focused, then expand.** Begin with a specific use case rather than trying to create one project for everything. You can always add more content as you go.
- **Keep your knowledge base current.** Outdated documents can lead to outdated responses. Review and update your project knowledge periodically.
- **Write clear instructions.** Be specific about what you want. Vague instructions lead to inconsistent results.
- **Group related documents.** This helps Claude draw connections between different sources and provide more comprehensive responses.
- **Reference documents by name.** When asking questions, you can mention specific documents to help Claude focus its search: "Based on our Q3 report, what were the top customer concerns?"

## Skills
- Skills allow Claude to perform specialized, repeatable tasks - they are instructions, scripts and resources that are loaded automatically when needed. 
- Project store knowledge and context, Skills perform tasks.
- The two features complement each other. A skill can reference knowledge stored in a project—your "customer call prep" skill might pull from customer profiles uploaded to a project's knowledge base. The project provides the _what_ (information), the skill provides the _how_ (process).
- Skills to create excel, PowerPoint, word doc, PDFs etc. 
- Two types: Anthropic and custom
	- Anthropic are available to paid users and created/maintained by Anthropic --> document creation capabilities
	- Custom - you create for workflows or domain specific tasks. e.g. structure notes in a format, data analysis workflow, or apply guidelines to documents. 
	- Skills are steps and order of operations you want followed every time
	- Enable skills by first enabling `Code execution and file creation`
	- settings --> capabilities --> code execution and file creation --> scroll to skills and turn them off/on as needed. You also need to `allow limited network access` for Claude to edit any files that you upload. 
	- Custom skills will be listed in your settings, too
		-  Create an Excel spreadsheet tracking monthly expenses with formulas for totals"
		- "Turn this meeting notes document into a PowerPoint presentation"
		- "Generate a PDF report summarizing this data"
		- "Build a financial model in Excel with scenario analysis"
- You can upload your own files and have Claude update them. 
- Security - If you're installing a custom Skill from an external source, review its contents before use to understand what it does.
### Creating your own custom skills
- Create custom skills through a conversation with Claude
- Start a new chat and say, "I want to create a skill that does X"
- Claude will interview you about workflow, what it should do, what makes good output, and when you use the skill
- Upload any reference materials, guides, work examples, brand assets to help Claude understand
- Claude will create a skill for your to download as a ZIP file
- Upload it to your settings --> capabilities
- The custom skill will automatically be invoked when needed 

![[Pasted image 20260218065436.png]]

## Connectors

Links:
[Anthropic academy](https://www.anthropic.com/learn)

[Claude code in action](https://anthropic.skilljar.com/Claude-code-in-action)

<% tp.date.now("YYYY-MM-DD-HHmm") %>