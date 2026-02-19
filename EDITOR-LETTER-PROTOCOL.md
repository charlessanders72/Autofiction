# Editor's Letter Workflow

A four-step process for generating a weekly "Letter from the Editor" that reviews the past week's Autofiction stories.

---

## Step 1: Gather the Week's Stories

Read every story file in `stories/` dated within the past seven days. For each story, note:

- **Title and date**
- **Prompt source** (Daily Micro Fiction letter and CNN headline)
- **Theme thesis** (from the outline's Theme section)
- **Protagonist** (name, age, occupation, demographic profile)
- **Tense/POV**
- **Recursive analysis notes** (strengths, weaknesses, protocol changes)

If fewer than three stories exist for the week, expand the window to the most recent seven stories regardless of date. The letter needs enough material to identify patterns.

**Output:** A working inventory of the week's stories with the elements listed above.

---

## Step 2: Identify Threads

Analyze the inventory from Step 1 for recurring patterns across three categories:

### Thematic Threads

Look for tensions and questions that surface across multiple stories. These are not plot summaries; they are the deeper claims about human nature that the stories collectively make. Examples of what to look for:

- Do several stories explore the same moral structure (complicity, refusal, obligation)?
- Is there a shared emotional register (grief, defiance, quiet resignation)?
- Do the news headlines cluster around a particular crisis, and if so, what does the fiction reveal about it that the news cannot?

Name each thread in a short phrase (e.g., "The geometry of complicity," "Bodies that carry what language cannot").

### Craft Patterns

Review the recursive analysis notes across the week's stories. Look for:

- Which craft strengths recurred? Which weaknesses?
- Did the protocol change during the week, and if so, what does the arc of those changes reveal about where the project's craft is heading?
- POV and tense distribution: is the project varying enough, or settling into habits?

### Character and World

Survey the protagonists and supporting characters across the week:

- What demographics, professions, and age ranges appeared?
- Are characters beginning to rhyme with each other across stories (similar dilemmas in different uniforms)?
- Did any story expand or complicate the Autofiction universe in a notable way?

**Output:** A set of named threads (3-5 is ideal) with brief notes on which stories contribute to each.

---

## Step 3: Write the Letter

Draft a letter of **400-800 words** addressed to the reader. The letter should read as a weekly editorial — literate, opinionated, and grounded in specific references to the stories it discusses.

### Voice and Tone

The editor's voice is:

- **Observant, not promotional.** The letter reflects on what the week's fiction accomplished and where it fell short. It does not sell the stories; it thinks alongside them.
- **Specific, not vague.** Every claim about a theme or pattern should cite at least one story by title and reference a concrete moment (a line, an image, a structural choice).
- **Honest about limitations.** If the week's stories share a blind spot (similar protagonists, repetitive endings, a narrow emotional range), the letter should name it without apology.
- **Brief on craft, generous on meaning.** Readers care more about what the stories are *about* than how they were *made*. Craft observations belong, but they should serve the larger conversation about theme and meaning.

### Structure

The letter does not need to follow a rigid template, but a natural shape might be:

1. **Opening:** A short observation — a sentence or two — that frames the week. This is not a thesis statement; it is a door. It might be an image from one of the stories, a question the week raised, or a connection between the fiction and the news cycle that produced it.
2. **Body:** Walk through the thematic threads identified in Step 2. Discuss 2-4 threads, weaving in specific story references. Let the threads talk to each other; the letter is strongest when it shows how stories that seem unrelated are actually in conversation.
3. **Honest reckoning:** A paragraph (even a sentence) about what the week's stories did not do. A pattern that went unbroken, a voice that went unheard, a risk not taken. This is the letter's conscience.
4. **Close:** End on a single image, question, or forward-looking thought. Do not summarize. Do not congratulate. The close should leave the reader thinking, not satisfied.

### Constraints

- Do not summarize plots. Assume the reader has read the stories (or will).
- Do not use em dashes. Use commas, semicolons, or periods.
- Do not editorialize about AI authorship or the nature of the project itself. The letter speaks from inside the fiction, not above it.
- Do not rank or grade the stories. The letter is a conversation, not a scorecard.

**Output:** A draft letter of 400-800 words.

---

## Step 4: Log and Commit

1. Save the letter to the `stories/` directory with the filename format `YYYY-MM-DD-editors-letter.md`, where the date is the date the letter is written (typically the last day of the week it covers, or the day it is generated).
2. The file should include:
   - **Metadata:** Date, date range covered, list of stories reviewed (titles and dates)
   - **Thread inventory:** The named threads from Step 2 (brief, not the full analysis)
   - **Letter:** The full text from Step 3
3. Commit and push to a `claude/` feature branch (skip this in CI — the workflow handles git operations).
4. Update today's daily log (`memory/YYYY-MM-DD.md`) with a note that the editor's letter was generated.

---

## Notes

- The editor's letter is a reflection, not a review. Its purpose is to surface the larger conversation happening across the week's fiction, to notice what the individual stories cannot see about themselves.
- When the week's stories cluster around a single news event or crisis, resist the urge to write about the crisis directly. Write about what the fiction found inside it.
- If a week produced only one or two stories, the letter can still be written, but it should be shorter and more focused. A single story examined closely is better than thin observations stretched across too little material.
- The letter should be legible to someone who has never read the stories, even though it assumes they have. Specificity accomplishes this: a concrete image from a story communicates even without full context.
- Frequency: weekly by default, but the letter can be generated on any cadence that matches the project's output. If stories are produced daily, a weekly letter keeps pace. If production slows, the window can expand.
