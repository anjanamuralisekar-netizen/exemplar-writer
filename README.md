# Exemplar Writer — Complete Reference Package

## What this package does

**Exemplar Writer** is a reusable writing system for generating or rewriting human-readable prose through a Jungian-style exemplar voice while controlling four things independently:

1. **Exemplar** — the personality, stance, vocabulary, and rhetorical posture.
2. **Channel** — the format and constraints, such as website copy, LinkedIn, email, UI, microcopy, or headlines.
3. **CEFR reading level** — how easy or sophisticated the language should be.
4. **Cadence + register** — sentence rhythm and how formal/spoken the writing feels.

It also contains editorial operations for making copy tighter, clearer, more memorable, and less machine-like.

---

# 1. Exact character mapping

These names are **fixed**. Do not substitute other names.

| Exemplar | Character | Core Energy |
|---|---|---|
| Sita | **Sita** | Calm clarity, revealing truth |
| Savitri | **Savitri** | Forward momentum, discovery |
| Janu | **Janu** | Crafted confidence, intentionality |
| Yashoda | **Yashoda** | Warm steadiness, protection |
| Durga | **Durga** | Bold courage, determination |
| Tara | **Tara** | Provocative challenge, liberation |
| Mohini | **Mohini** | Visionary transformation |
| Ahalya | **Ahalya** | Simple clarity, hope |
| Anjana | **Anjana** | Belonging, practicality |
| Megha | **Megha** | Playful wit, perspective |
| Rathi | **Rathi** | Warm connection, depth |
| Rani | **Rani** | Authoritative clarity, standards |

**Important:** the character name identifies the exemplar only. Do not import mythology, biography, religious symbolism, or traits associated with the name unless the user explicitly asks for that.

---

# 2. Package contents

```text
exemplar-writer/
├── SKILL.md
├── README.md
└── references/
    ├── language-level.md
    ├── cadence.md
    ├── register.md
    ├── composite.md
    ├── custom-channel.md
    ├── exemplars/
    │   ├── sita.md
    │   ├── savitri.md
    │   ├── janu.md
    │   ├── yashoda.md
    │   ├── durga.md
    │   ├── tara.md
    │   ├── mohini.md
    │   ├── ahalya.md
    │   ├── anjana.md
    │   ├── megha.md
    │   ├── rathi.md
    │   └── rani.md
    └── channels/
        ├── website.md
        ├── linkedin.md
        ├── ui.md
        ├── micro.md
        ├── email.md
        └── headline.md
```

**Do not use only SKILL.md if your setup supports reference files.** The skill is deliberately split into a main instruction file plus supporting references. The main file tells the model when and how to use those references.

---

# 3. How the system works

For each writing task, the intended flow is:

```text
USER'S GOAL
   ↓
Choose exemplar
   ↓
Resolve to fixed character
   ↓
Read exemplar reference
   ↓
Choose/read channel reference
   ↓
Apply CEFR level
   ↓
Apply cadence
   ↓
Apply register
   ↓
Draft
   ↓
Editorial refine pass
   ↓
Quality checklist
   ↓
FINAL COPY
```

### Example

If the user says:

> Write a LinkedIn post explaining why AI customer support should not sound robotic. Make it confident but approachable.

A suitable route could be:

- Exemplar: **Sita**, possibly layered with **Anjana**
- Channel: `references/channels/linkedin.md`
- CEFR: B2 unless another level is requested
- Cadence: varied, conversational, no repetitive AI-style rhythm
- Register: confident and approachable
- Then run the editorial refine pass

---

# 4. Using it with Claude

The exact Claude interface can vary, but the safest approach is to make the entire `exemplar-writer` folder available to the Claude environment rather than copying only the README.

## Option A — Claude skill / skills environment

If your Claude setup supports skills or a skills directory:

1. Unzip `exemplar-writer-complete.zip`.
2. Keep the folder structure intact.
3. Add the **entire `exemplar-writer/` folder** to the skills location used by your Claude environment.
4. Make sure `SKILL.md` is at the root of that folder.
5. Keep the `references/` directory beside `SKILL.md`.
6. Start a new Claude conversation/session if required by your environment.
7. Ask Claude to use **Exemplar Writer** for the writing task.

A useful first test prompt is:

> Use the Exemplar Writer skill. Write a short LinkedIn post about making AI support feel human. Use Sita, B2 English, and a confident conversational register.

## Option B — Claude Project / uploaded knowledge

If your Claude interface does not provide a skills mechanism but allows project knowledge/files:

1. Create a Claude Project.
2. Upload the complete package or the Markdown files from the package.
3. Preserve the folder/file names if the interface allows it.
4. Add a project instruction telling Claude to treat `SKILL.md` as the governing instruction and consult the relevant files in `references/` before writing.
5. Test the fixed character mapping explicitly.

Suggested project instruction:

> Use `SKILL.md` as the governing Exemplar Writer specification. When writing or rewriting human-readable prose, follow its routing process and consult the relevant files under `references/`. The exemplar-to-character mapping in `SKILL.md` and `references/` is authoritative. Do not substitute character names.

### Claude test

Ask:

> Rewrite this website paragraph using the Durga exemplar. Keep the reading level at B2. Which fixed character does Durga resolve to, and what channel reference should you consult?

The expected character is **Durga**.

---

# 5. Using it with ChatGPT

There are two practical ways to use this package in ChatGPT, depending on the ChatGPT setup you are using.

## Option A — Project files / knowledge

If you have a ChatGPT Project or another ChatGPT configuration that lets you provide files as project knowledge:

1. Create/open the Project where you want to use Exemplar Writer.
2. Upload the **complete package** or its Markdown files.
3. Keep `SKILL.md` together with the `references/` directory.
4. Add an instruction telling ChatGPT that `SKILL.md` is the governing writing specification.
5. Start your writing request.

Suggested instruction:

> Use the Exemplar Writer package as the governing writing system for human-readable prose. Follow `SKILL.md`, and consult the appropriate files under `references/` for exemplars, channels, CEFR, cadence, register, composites, and custom channels. Use the exact exemplar-to-character mapping. Do not replace the character names or import mythology associated with them unless explicitly requested.

## Option B — Give the package to a custom GPT / configured assistant

If your ChatGPT setup provides a knowledge-file area for a custom assistant:

1. Upload the Markdown files as knowledge/reference material.
2. Put the main behavioral rules from `SKILL.md` into the assistant's instructions if your configuration allows it.
3. Put the reference Markdown files into the knowledge area.
4. Test with a simple exemplar + channel request before relying on it for production copy.

### Important ChatGPT note

The ZIP is a **file package**, not a universal one-click installer. Whether `SKILL.md` is automatically treated as executable skill instructions depends on the ChatGPT environment you are using. If the environment supports a dedicated skills mechanism, install it there. If it only supports uploaded knowledge/files, use the package as the assistant's instruction/reference material.

---

# 6. The best way to prompt it

You do not need to specify every axis every time. The system can infer missing choices, but explicit instructions produce more predictable results.

## Minimal prompt

> Write a landing page for an AI sales chatbot using Exemplar Writer.

The system should choose a suitable exemplar and channel.

## Better prompt

> Write a landing page for an AI sales chatbot.
> Exemplar: Janu
> Channel: website
> Reading level: B2
> Register: confident, clear, professional
> Keep the copy concise and conversion-focused.

## Rewrite prompt

> Rewrite the copy below using Sita. Keep the meaning and facts unchanged. Use B2 English and preserve the original register. Make the sentences tighter and less repetitive.

## Composite prompt

> Use a composite of Sita and Durga. Let Sita handle explanation and Durga handle the call to action. Do not average the two voices.

The detailed composite rules are in `references/composite.md`.

---

# 7. Choosing an exemplar quickly

| If you want the copy to feel... | Choose |
|---|---|
| Clear, thoughtful, truth-seeking | **Sita** |
| Curious, exploratory, forward-moving | **Savitri** |
| Designed, intentional, crafted | **Janu** |
| Warm, safe, protective | **Yashoda** |
| Brave, decisive, action-oriented | **Durga** |
| Challenging, provocative, liberating | **Tara** |
| Transformational, visionary | **Mohini** |
| Simple, reassuring, hopeful | **Ahalya** |
| Practical, relatable, inclusive | **Anjana** |
| Witty, playful, memorable | **Megha** |
| Human, warm, emotionally connected | **Rathi** |
| Authoritative, disciplined, high-standard | **Rani** |

---

# 8. Choosing the channel

Use the channel reference that matches the destination:

- **Website** → `references/channels/website.md`
- **LinkedIn** → `references/channels/linkedin.md`
- **UI / product interface** → `references/channels/ui.md`
- **Microcopy / short copy** → `references/channels/micro.md`
- **Email** → `references/channels/email.md`
- **Headline** → `references/channels/headline.md`

If the requested channel is not one of these, use `references/custom-channel.md`.

---

# 9. CEFR reading level

The default is **B2**.

If the user specifies a reading level, follow it. If they specify an audience instead (for example, children, non-native English speakers, executives, developers), infer an appropriate level rather than blindly forcing B2.

See `references/language-level.md` for the full rules.

---

# 10. Rewrite vs. generate

This distinction matters.

### When rewriting

Preserve:

- the original meaning
- factual claims
- important terminology
- intended audience
- the source register unless the user asks for a change

Then improve clarity, structure, cadence, and exemplar alignment.

### When generating from scratch

Use the requested exemplar's natural stance, vocabulary, sentence patterns, cadence, and energy from the beginning.

Do not manufacture facts, proof points, statistics, customer claims, or product capabilities that the user has not supplied.

---

# 11. Editorial refinement

The system is not just a persona generator. After drafting, perform a refinement pass.

Look especially for:

- unnecessary words
- repeated sentence structures
- generic AI phrasing
- predictable three-part lists
- excessive em-dash use
- repeated rhetorical devices
- claims that sound stronger than the evidence
- metaphors imported from another exemplar's language domain
- unnecessary formality
- over-explaining obvious points

The six editorial operations in `SKILL.md` are:

**CUT · COMPRESS · HOOK · VARY · EDGE · DEFER**

The goal is not to make every sentence flashy. The goal is to make the copy feel deliberate and human.

---

# 12. How to verify that the package is working

Run these simple tests after installing it.

### Test 1 — Fixed identity

> What exemplar is Sita?

Expected: **Sita**.

### Test 2 — Another identity

> What exemplar is Durga?

Expected: **Durga**.

### Test 3 — Channel routing

> Write a website headline using Janu. Which channel reference should you use?

Expected: Janu resolves to **Janu**, and the website channel reference is used.

### Test 4 — Reading level

> Rewrite this paragraph at B1 level without changing its meaning.

The output should use simpler vocabulary and sentence structure rather than merely shortening the text.

### Test 5 — Composite

> Use Sita for explanation and Durga for the call to action.

The output should have distinct roles rather than a blended average voice.

---

# 13. Common mistakes to avoid

### Mistake: uploading only README.md

The README explains the package. It is not the complete writing system.

**Fix:** provide `SKILL.md` and the `references/` directory.

### Mistake: uploading only SKILL.md

The main skill explicitly routes to reference files.

**Fix:** keep the complete package together.

### Mistake: changing the character names

Do not rename Sita, Savitri, Janu, Yashoda, Durga, Tara, Mohini, Ahalya, Anjana, Megha, Rathi, or Rani.

### Mistake: treating the names as mythology prompts

The names are fixed identifiers for the exemplars. The voice comes from the exemplar definition, not from mythology associated with the name.

### Mistake: letting the exemplar override brand facts

The exemplar controls voice and stance. It must not invent facts, proof, features, policies, statistics, or customer results.

### Mistake: using one cadence everywhere

Different channels and exemplars need different rhythm. Always run the cadence refinement pass.

---

# 14. Recommended production workflow

For serious copy, use this prompt structure:

```text
TASK
What needs to be written or rewritten?

AUDIENCE
Who will read it?

CHANNEL
Where will it appear?

EXEMPLAR
Which exemplar should lead? If composite, state each role.

READING LEVEL
CEFR level or audience-appropriate level.

REGISTER
Formal / professional / conversational / direct / warm / etc.

CONSTRAINTS
Length, claims, words to avoid, required CTA, SEO terms, brand rules, etc.

SOURCE
Existing copy or factual material, if this is a rewrite.

OUTPUT
Exact format required.
```

Example:

```text
TASK
Create a homepage hero section for an AI customer-support product.

AUDIENCE
SaaS founders and support leaders.

CHANNEL
Website.

EXEMPLAR
Janu with a light Sita influence.

READING LEVEL
B2.

REGISTER
Confident, clear, modern.

CONSTRAINTS
No hype. No invented statistics. Keep the headline under 10 words.

OUTPUT
Headline, subheadline, CTA.
```

---

# 15. If a custom channel is needed

Use `references/custom-channel.md`.

A custom channel can either:

- completely replace the stock channel constraints, or
- extend a stock channel while adding new constraints.

Give the model the channel name, purpose, structure, length constraints, formatting rules, audience, and any prohibited patterns.

---

# 16. Package maintenance

When changing the system:

1. Update `SKILL.md` for global behavior.
2. Update an exemplar file for persona-specific behavior.
3. Update a channel file for channel-specific behavior.
4. Update the README when installation or usage changes.
5. Keep the exact character mapping synchronized everywhere.
6. Re-run the verification tests above.
7. Repackage the **entire folder**, not just the changed file.

The package should always ship with the complete `references/` tree.

---

## Quick reference

**Main instruction:** `SKILL.md`

**Fixed mapping:**
Sita · Savitri · Janu · Yashoda · Durga · Tara · Mohini · Ahalya · Anjana · Megha · Rathi · Rani

**Default CEFR:** B2

**Editorial operations:** CUT · COMPRESS · HOOK · VARY · EDGE · DEFER

**Best practice:** provide the complete package, let `SKILL.md` route to the references, and explicitly specify exemplar + channel + audience when consistency matters.
