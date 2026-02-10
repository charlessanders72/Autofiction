# Autofiction Workflow

A five-step process for generating and publishing short stories.

---

## Step 1: Pick an Idea

Find inspiration from one of these sources:

- **Daily Micro Fiction** — [www.dailymicrofiction.com/p/index](https://www.dailymicrofiction.com/p/index)
  - Pick a letter corresponding to the day of the month (1=A, 2=B, etc.)
  - Pick a topic that matches a current CNN headline
- **Public Domain** — Choose a story that recently entered public domain

Once you have a concept, identify the **tension or question** at its center — the thing that makes it a story rather than a news summary. What is at stake for a person inside this situation? What must they choose, lose, or confront?

**Output:** A concept with a clear human tension that can be explored through a fictional short story.

---

## Step 2: Create an Outline

Develop these elements:
- **Theme:** A universal claim about human nature — not a plot summary, but something true beyond this particular story. Then show how the **conflict tests** this claim and how the **character's arc resolves** it. For example:
  - *Thesis:* "Orders followed without question become crimes committed without conscience, until the moment someone looks you in the eye."
  - *Conflict tests it:* An agent who followed orders sits across from a nurse who lost the patient.
  - *Arc resolves it:* He cannot defend what he did when faced with a direct question.
- **Character(s):** At least one, with one sentence of backstory and details each
- **Setting/Atmosphere:** One sentence description of where/when the story takes place
- **Plot:** High-level outline of between two and four scenes

---

## Step 3: Generate the Story

Send the outline to **Claude Opus** with this prompt:

> We are going to create a story together. The story should fall roughly between 500 and 1,000 words, allowing for enough space to develop characters, conflict, and resolution while still remaining tightly structured and fast-paced.
>
> I will first provide you with the core building blocks of the narrative: the core theme or thesis, the list of characters, the setting and atmosphere, and the plot outline and central conflict. These will serve as the guiding framework for the draft you will generate.
>
> Although these elements set the boundaries, the creative development of the story within those limits will be your responsibility. When drafting, focus on blending narrative description, character development, and dialogue so that the story feels immersive and balanced.
>
> The story should open with a strong hook that immediately engages the reader and situates them in the world of the narrative. A central conflict must be present, and the main character should undergo some form of growth or change as that conflict progresses.
>
> To ensure a clear and manageable arc, the story should unfold in no more than four distinct scenes—ideally two or three—to avoid unnecessary sprawl and keep the pacing sharp.
>
> The ending should be abrupt and succinct, concluding precisely when the main conflict arc resolves without unnecessary denouement or explanation—readers should feel the story ends exactly where it needs to, even if it leaves them wanting more.
>
> The theme should never be stated outright by the narrator. Instead, express it through character choices, concrete detail, and what is left unsaid. The reader should feel the thesis without being told it.
>
> As you write, feel free to make creative adjustments to the material I provide if you identify opportunities that would meaningfully improve the narrative. These adjustments might include subtle changes to dialogue, character motivations, or even structural shifts, as long as the core thesis and spirit of the story remain intact.
>
> The story should end cleanly and decisively at the resolution of the conflict arc. Avoid using em dashes for punctuation; instead, rely on commas, semicolons, or periods to maintain stylistic consistency.
>
> Before beginning the draft, carefully select a tense (past, present, or future) and point of view (first, second, or third person) that best suits the genre and mood suggested by the thesis and plot. Once those decisions are made, proceed to expand the provided outline into a fully realized story.

Then append the outline from Step 2.

---

## Step 4: Logging

1. Save the story to the `stories/` directory with the filename format `YYYY-MM-DD-slug.md`
2. Each story file should include:
   - **Metadata:** Date, prompt source, tense/POV
   - **Outline:** The outline from Step 2
   - **Story:** The full generated text
3. Commit and push to a `claude/` feature branch
4. Update today's daily log (`memory/YYYY-MM-DD.md`) with session notes

---

## Step 5: Recursive Analysis

After the story is generated and logged, analyze it for **strengths** and **weaknesses** — examining craft elements such as character development, dialogue, pacing, theme expression, opening hooks, endings, and adherence to the protocol's guidelines.

Based on this analysis, make **at most one sentence-level change** to this protocol file (`PROTOCOL.md`). The change must be one of:

- **Add** a single sentence anywhere in the protocol
- **Modify** an existing sentence in the protocol
- **Remove** a single sentence from the protocol

The change should address a recurring weakness or reinforce a demonstrated strength — something that will improve future stories. If no meaningful change is warranted, no edit is required.

**Constraints:**
- Only one sentence may be changed per story (add, modify, or remove — pick one)
- The change must be motivated by a specific observation from the analysis
- Log the change (or the decision not to change) in the story file's metadata and in today's daily log

---

## Notes

- Target length: 500-1,000 words (tight and punchy)
- No em dashes, use commas, semicolons, periods
- Endings should be abrupt and decisive
- When possible, end on a concrete physical action rather than an internal thought; let the body resolve what the mind cannot.
- Show, don't tell.
