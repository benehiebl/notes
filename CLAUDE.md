# LLM Wiki


A personal research knowledge base maintained by Claude Code.
Based on Andrej Karpathy's LLM Wiki pattern.


## Purpose


This wiki is a structured, interlinked knowledge base for research paper knowledge.
Claude maintains the wiki. The human curates sources, asks questions, and guides the analysis.
The wiki focuses on remote sensing, machine learning, deep learning and forest ecology. The wiki is ultimately used to provide citable knowledge for writing research papers.
These research papers are focused around developing deep learning models based on earth observation time series data to predict and map forest ecological variables, such as tree species cover or forest type.


## Folder structure


```
00_literature/          -- source documents (immutable -- never modify these)
01_notes/               -- markdown pages maintained by Claude containing summaries of research papers
02_concepts/            -- markdown pages maintained by Claude containing key concepts related to deep learning, machine learning, remote sensing and forest ecology
03_papers/              -- markdown pages maintained by human and Claude (modify only on direct request)
templates/              -- markdown pages maintained by human for obsidian templates
graphify-out/           -- /graphify output. only changed when /graphify is called
index.md    -- table of contents for the entire wiki
log.md      -- append-only record of all operations
```


## Ingest workflow


When the user adds a new source to `00_literature/` and asks you to ingest it:

use the /summarize-paper (for pdf) or the /summarize-codebase (for repository) skill to:
1. Read the full source document
2. Discuss key takeaways with the user before writing anything
3. Create a summary page in `01_notes/` named after the source filename
4. Create or update concept pages for each major idea or entity
5. Add wiki-links ([[page-name]]) to connect related pages
6. Update `index.md` with new pages and one-line descriptions
7. Append an entry to `log.md` with the date, source name, and what changed


A single source may touch several wiki pages. That is normal.


## Page format


Every summary page should follow the structure proposed in /summarize-paper (or summarize-codebase) skill.

Every concept page should follow this structure:


```markdown
# Page Title


**Summary**: One to two sentences describing this page.


**Sources**: List of files (from 01_notes/) this page draws information from (use backlinks [[name]]).
                For example: [[hiebl_2025_pretraining]], [[safonova_2021_small_data]]


**Last updated**: Date of most recent update.


---


Main content goes here. Use clear headings and short paragraphs which should be backed by citations via backlinks [[link]].
For example:
    ## Contextual Pretraining
    - Using pretrained Deep Learning Foundation models is a common approach in small data problems [[safonova_2021_small_data]]
    - conceptual in this context means, that ... [[hiebl_2025_pretraining]]


Link to related concepts using [[wiki-links]] throughout the text. And link to related notes using [[wiki-links]] throughout the text.


## Related pages


- [[related-concept-1]]
- [[related-concept-2]]
```

In general prefer bullet points over long sentences to state clear messages.



## Citation rules


- Every factual claim should reference its source file with backlinks [[wiki-link]] this is for cross referencing and referencing from concepts to notes.
- Use the format (source: [[filename]]) after the claim
- If two sources disagree, note the contradiction explicitly
- If a claim has no source, mark it as needing verification


## Question answering


When the user asks a question:


1. Read `index.md` first to find relevant pages
2. Read those pages and synthesize an answer
3. Cite specific wiki pages in your response
4. If the answer is not in the wiki, say so clearly
5. If the answer is valuable, offer to save it as a new wiki page


Good answers should be filed back into the wiki so they compound over time.


## Lint


When the user asks you to lint or audit the wiki:


- Check for contradictions between pages
- Find orphan pages (no inbound links from other pages)
- Identify concepts mentioned in pages that lack their own page
- Flag claims that may be outdated based on newer sources
- Check that all pages follow the page format above
- Report findings as a numbered list with suggested fixes


## Rules


- Never modify anything in the `00_literature/` folder
- Always update `index.md` and `log.md` after changes
- Keep page names lowercase with undescores (e.g. `machine_learning.md`)
- Write in clear, plain language
- When uncertain about how to categorize something, ask the user
- only use /graphify skill if directly called by human
