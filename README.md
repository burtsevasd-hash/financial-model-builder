# Financial Model Builder

A skill for building a complete financial model for a small business, from the client brief to handover.

It is a workflow, not a template. Eight steps, 26 prompts, eight checklists, a worked example. At eight points it stops and waits for the human to decide, because a model nobody argued with is a model nobody trusts.

## What it produces

| Step | Deliverable |
|---|---|
| 0 | Project passport: niche, location, scale, purpose, horizon, currency and jurisdiction |
| 1 | Parameter list across eight blocks, reviewed and trimmed, plus a client questionnaire as a one page web form |
| 2 | Client answers mapped into the parameters, scope and price, a quote |
| 3 | Market research with sources and confidence levels, a second model fact checking it, a unit cost calculation, a letter asking the client to confirm |
| 4 | The model: three sheets, monthly P&L, cash flow and working capital, investment need and payback, every cell a formula |
| 5 | Three scenarios compared on formulas, sensitivity analysis, parameter ranking, break points, conclusions |
| 6 | One HTML file the client can open on a phone: sliders, live charts, an analytical note and a presentation mode, reconciled against the spreadsheet to the last unit of currency |
| 7 | A 60 or 90 minute meeting script and twelve likely client questions answered with figures from the model |

## Language

The skill works in the language of the person using it. These instructions are in English so that anyone can read and adapt them, but nothing in the output has to be English: file names, sheet headers, the note, the deck and the interactive page all come out in the language of the project.

## Jurisdiction

Nothing about taxes is hardcoded. The passport carries the country, the region and the currency. At step 3 the skill researches the local rules itself, from primary sources only, and records the article or section number next to every statutory value. The worked example is Russian, the method is not.

## Install

**Claude Code**

```bash
cp -R financial-model-builder ~/.claude/skills/
```

The skill is then visible by name and triggers on requests about financial models, feasibility, payback or investment need.

**Codex**

Keep the folder anywhere and attach it to the session together with the project folder. First message: «Follow the instructions in SKILL.md from the skill folder. The project folder is attached.»

**Any other assistant**

Open `SKILL.md`, paste the «Role and rules» section at the start of the conversation, then take the prompts one at a time from `prompts`.

## Run it

1. Create a project folder and put the client brief in it as a text file.
2. Attach the folder and write: **«Build a financial model from the passport in this folder»**.
3. Answer at the eight stops. The skill names the stop and lists what needs confirming.
4. To go back, name the step: «redo step 4.1, the model structure».

## What is inside

```
financial-model-builder/
├── SKILL.md
├── README.md
├── prompts/              8 files, 26 prompts
├── checklists/           8 checklists by step
├── templates/            passport, parameter sheet, model structure,
│                         note and deck structure, a working sample page
└── example-bakery/       a finished project, with an English guide to it
```

## Credit

Built from a real engagement and the course that came out of it. The example is a bakery in Kazan: investment need 4.09 million roubles, payback at the sixteenth month of trading, and a funding gap of 1.13 million that the model found a month before the fit-out was due to start.
