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
> The theme should never be stated outright by the narrator. Instead, express it through character choices, concrete detail, and what is left unsaid. The reader should feel the thesis without being told it. If you find yourself explaining what a character understands or realizes, cut the explanation and trust the reader to infer it from what the character does next. When interior reflection or backstory is necessary, anchor it with physical detail or action to maintain pacing; even a character's thoughts can be grounded in what their hands are doing or what their body registers.
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
3. Commit and push to a `claude/` feature branch (skip this in CI — the workflow handles git operations)
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

## Stock Characters

A reference list of characters who have appeared in previous stories. These can be reused, referenced, or adapted in future stories to build continuity across the Autofiction universe.

### Protagonists (POV Characters)

| Character | Age | Occupation | Story | Key Detail |
|-----------|-----|------------|-------|------------|
| Marcus Pruitt | 44 | DHS Enforcement and Removal Operations agent | *Last Van South* | Former Army military police; deployed to Minneapolis; haunted by a raid gone wrong |
| Mika Bergstrom | 29 | Swedish Olympic alpine skier | *The Body You Were* | Three Olympic golds; career-ending nerve injury; raised by a single father/ski coach |
| Margot Linden | 38 | High school English teacher | *Brillig* | Lives alone in Penrose, Colorado; reads "Jabberwocky" to her dead father's urn every Tuesday |
| Mei Lai | 34 | Freelance translator | *One Way Ticket* | Left Hong Kong in 2020; lives in Brixton, London; father imprisoned for journalism |
| Nadia Vasquez | 31 | Junior legal researcher | *Flag for Review* | Two years out of law school; owes her career to the mentor whose name she finds on a flight manifest |
| Oksana Mehta | 34 | Translator (Ukrainian-born, Jain-Indian mother) | *The Locked Thing* | Raised between two traditions of non-violence; father killed by a Russian missile in 2022 |
| Meredith Crane | 40s | Morning news anchor | *The Green Room* | Known for unflappable on-camera composure; mother disappeared voluntarily |
| Dariush Tavakoli | 58 | Iranian diplomat | *The Clean Text* | Left Tehran as a student during the revolution; brother killed in the Iran-Iraq War; believes diplomacy prevents war |
| Maya Okafor | 42 | Nigerian-American pediatric nurse | *The Coleslaw* | Moved to a Northern Virginia suburb five years ago; daughter Chiamaka, husband Emeka |
| Dr. Lena Reyes | 41 | Pediatric surgeon | *The Measure* | Trained in Mexico City; returned to Havana out of obligation; works through the Cuban fuel crisis |
| Dr. Anaya Rao | 47 | Pediatrician | *The Shot* | Solo practice in Bethesda; daughter of Indian immigrants who ran a clinic in Hyderabad; risks her license to vaccinate a child |

### Supporting Characters

| Character | Age | Occupation | Story | Key Detail |
|-----------|-----|------------|-------|------------|
| Elena Reyes | 38 | ER nurse at Hennepin Healthcare | *Last Van South* | Salvadoran-born, permanent US resident; treated a shooting victim from Marcus's raid |
| Dr. Jonas Petrov | 40s | Italian orthopedic surgeon | *The Body You Were* | Handles Olympic injuries; delivers career-ending news with quiet steadiness |
| Walter Linden | 71 (deceased) | Retired machinist | *Brillig* | Margot's father; loved Carroll and Lear; wrote "good" in the margin of "Jabberwocky" |
| Jimmy Lai | 60s | Imprisoned journalist/publisher | *One Way Ticket* | Mei's father; sentenced to 20 years in Hong Kong; quotes Camus in his final messages |
| Judge Emory Sands | 67 | Federal appellate judge | *Flag for Review* | Nadia's mentor; name found on an Epstein-investigation flight manifest |
| Sergei Volkov | 52 | Russian deputy negotiator | *The Locked Thing* | Career diplomat; pleasant face; treats concessions as gifts he is offering |
| Detective Ray Solis | 50s | Lead investigator | *The Green Room* | Methodical, detached; flat brown eyes; delivers unwelcome truths without apology |
| Catherine Hale | 45 | American envoy, former CIA Iran desk | *The Clean Text* | Left intelligence for diplomacy; enters rooms without knocking; says nothing when it matters |
| Doug Brenner | 56 | Retired postal worker, neighborhood association president | *The Coleslaw* | Posted a racist video mocking a child's name; refuses to apologize |
| Tomas | 9 | Son of a fisherman from Regla | *The Measure* | Emergency appendectomy patient; his father rowed him across Havana harbor in the dark |
| Grace Okonkwo | 32 | Nigerian-American mother | *The Shot* | Son Emeka had measles at three, nearly lost his hearing; demands MMR for her daughter Adaeze |

### Minor/Recurring Characters

| Character | Story | Role |
|-----------|-------|------|
| Royce | *Last Van South* | Federal agent who fired the fatal shots during the raid |
| Sofia | *Last Van South* | Five-year-old girl in the raided apartment |
| Rafael | *Flag for Review* | Nadia's colleague on the document review team |
| Kravchuk | *The Locked Thing* | Ukrainian Deputy Minister at the peace talks |
| Collins | *The Locked Thing* | American mediator at the Oman negotiations |
| Patricia Crane | *The Green Room* | Meredith's mother; walked away from her own life voluntarily |
| Danny | *The Green Room* | Meredith's TV producer |
| Linda Brenner | *The Coleslaw* | Doug's wife; organizes the July 4th block party; gives the toast about community |
| Chiamaka Okafor | *The Coleslaw* | Maya's 9-year-old daughter; name means "God is beautiful" in Igbo |
| Emeka Okafor | *The Coleslaw* | Maya's husband |
| Yusnel | *The Measure* | Night nurse; rigged a bicycle to a ventilator pump |
| Daimarys | *The Measure* | Nurse; hand-bags a newborn's ventilation through the blackout |
| Patty | *The Shot* | Dr. Rao's office manager; delivers the medical board memo |
| Adaeze Okonkwo | *The Shot* | Grace's 15-month-old daughter; receives the MMR vaccine |

---

## Notes

- Target length: 500-1,000 words (tight and punchy)
- No em dashes, use commas, semicolons, periods
- Endings should be abrupt and decisive
- When possible, end on a concrete physical action rather than an internal thought; let the body resolve what the mind cannot.
- Show, don't tell.
- Open with the conflict already in motion; establish atmosphere through the action, not before it.
- When a memory or flashback surfaces, cut directly to concrete detail; avoid framing language that explains which version of the memory this is or why it is arriving.
