# Self-Intro Factory

**One self. Different rooms, different words.**

10 scenarios × 24 layered questions → a finished self-introduction in Chinese and English. One HTML file. No dependencies. Runs entirely offline.

[中文](README.md) · [Scenario specs](docs/scenes.md) · [Question bank](docs/questions.md)

🔗 **Live demo**: <!-- paste the GitHub Pages URL here after enabling it -->

---

## The problem

Most people have exactly one self-introduction and use it everywhere. It reads like a diary entry in a job interview, and like a résumé in a group chat.

This tool fixes that by changing **which questions get asked** — not by trimming the same answer.

- An interviewer wants to know if you can do the job → it only asks what kind of trouble makes people think of you first
- Classmates just need to remember you → it never asks about your skills
- An oral examiner is grading your fluency → it spends the time on pronunciation instead of asking what you refuse to compromise on

**The question count drops from 11 to 2** depending on the room — because the wrong questions are never asked in the first place.

## 10 scenarios

| # | Scenario | Length | Questions |
|---|---|---|---|
| 1 | Job interview | 1–3 min | 11 |
| 2 | Competition / defense / election | 1–2 min | 9 |
| 3 | Full version (fallback) | ~1 min | 8 |
| 4 | English oral exam | 30 s–1 min | 6 |
| 5 | New team / group project | ~30 s | 6 |
| 6 | First class / class meeting | 20–40 s | 6 |
| 7 | Short version (fallback) | ~20 s | 5 |
| 8 | Social icebreaker / party | 10–20 s | 4 |
| 9 | Online community intro | 10–15 s | 3 |
| 10 | Name only | 5–10 s | 2 |

Word budgets are derived from a 220 characters/min (Chinese) and 150 wpm (English) speaking rate, and a live meter shows the estimated spoken duration as you answer. Per-scenario selection rules, tone and pitfalls are in [`docs/scenes.md`](docs/scenes.md).

## 24 questions in 6 layers

```
deep  │ G5 Ahead   G4 Core   G3 Story              ← only 1–3 min scenarios have room
mid   │ G2 Capability   G1 Hook                    ← 30 s – 1 min scenarios
base  │ G0 Identity (always required, ~60 seconds) ← every scenario, even "name only"
```

The important part is that **the order is inverted**: answer the four G0 questions first, *then* pick a scenario, and only fill in what that scenario is missing. The base layer is answered once and reused for any scenario — a class introduction today, an interview tomorrow, same four answers.

Full bank in [`docs/questions.md`](docs/questions.md) (Chinese + English).

## How to use it

1. Download `index.html` and open it in a browser (or use the live demo above)
2. Answer the four G0 questions (~60 seconds)
3. Pick a scenario — it tells you how many questions that room needs
4. Answer only those
5. Generate — you get both a Chinese and an English version, ready to copy or download as `.md`

A few things it does for you:

- **It trims automatically when you run over.** There is a priority order: decorative details (a small habit, a hobby) are cut first, and the spine — your proudest achievement *and its outcome* — goes last. The result panel lists exactly what was cut, and every cut can be restored with one click.
- **Chinese and English are budgeted separately.** They are not translations of each other, so "Chinese keeps the example, English keeps only the conclusion" is expected behaviour, not a bug.
- **An optional English answer per question**, if you would rather not let a model guess.
- **"Copy AI prompt"** packages every answer into a single writing brief you can hand to any LLM.

## Privacy

The one thing a tool like this must never do is upload what you refuse to compromise on. So:

- **No dependencies, no network requests.** No npm, no CDN, no AI API. One HTML file does the whole job.
- **Your answers stay in your own browser** (localStorage). Nothing is transmitted anywhere.
- To verify: open it with your network disconnected — it works exactly the same. Or read the source; there is not a single `fetch` in it.

## A note on skipped question numbers

After you pick a scenario, the question numbers may not be consecutive (the interview version jumps from 3 to 9). **That is by design, not a bug** — the missing ones belong to the "Hook" layer, which an interview has no room for, so they are never rendered. The page says so inline.

## Repository layout

```
index.html                 the tool (single file, just open it)
README.md                  Chinese readme
README.en.md               English readme (this file)
docs/questions.md          the 24-question layered bank
docs/scenes.md             full specs for all 10 scenarios + trimming rules
docs/research.md           prior-art survey of similar GitHub projects
docs/original-brief.md     the original requirements doc this started from
```

## Relationship to existing projects

Before building this I went through GitHub. The finding: **every individual piece already exists, but nobody has combined them into this shape.**

| Project | Its approach | How this differs |
|---|---|---|
| [`Forlives/21-day-self-interview`](https://github.com/Forlives/21-day-self-interview) | 21 days × 3 questions, bilingual | The closest match. But it takes 21 days, and what it returns is a mirror of your own words, not something you can use. |
| [`forsonny/deep-discovery`](https://github.com/forsonny/deep-discovery) | 100 escalating self-interrogation questions | Asks only. Never writes. |
| [`Gogolian/preserver`](https://github.com/Gogolian/preserver) | 990+ questions across 33 categories | The most complete bank; built to feed a model. |
| [`baoyudu/digital-self`](https://github.com/baoyudu/digital-self) | Free-form AI conversation builds a profile | Needs an API key; outputs a pile of markdown. |
| [`asdxzc2/inner-field`](https://github.com/asdxzc2/inner-field) | 225 daily questions plus scoring scales | Produces a letter over 225 days. |
| [`TKGy3y9yjo/biography-system`](https://github.com/TKGy3y9yjo/biography-system) | 3 styles × bilingual autobiography + PDF | Almost an exact feature match — but zero stars and abandoned. |

**The four gaps this project occupies**: a finished draft in one sitting; questions designed to become prose rather than to prompt reflection; bilingual as two modes of expression rather than translation; and zero dependencies with everything local. Full survey in [`docs/research.md`](docs/research.md).

## License

[MIT](LICENSE) — do whatever you want with it.
