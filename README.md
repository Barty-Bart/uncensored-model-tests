# Uncensored AI models: 294 tests, the full results

The data behind the video **"What If Claude Never Said No? (14 Uncensored Models Tested)"**.

Video: `[link to add when the video is live]`

**Just want to run one?** Jump to [`07-get-started/`](07-get-started/): which model to download, how to run it in LM Studio, how to plug it into pi.dev in a sealed environment, and a prompt that has your AI test a few models on your own questions.

## What was tested, and how

Open models you can download and run on your own computer, each next to an "uncensored" copy of the same model: a copy edited after release to take its refusals out. There are two ways of doing that, called *abliterated* and *heretic*. The question was: what do you actually gain when the refusals are taken out, and what do you lose?

- **14 models**: six normal models, their uncensored copies, a second uncensored copy of one of them, and one small uncensored model with no twin. Names, Hugging Face repos, quants and sizes are in [`models.md`](models.md). Only models you can own: nothing rented, nothing behind an API.
- **Two Claude models** (Opus 4.8 and Opus 5.5) were added to the ladder as a comparison.

### Part one: the first round (294 tests)

21 questions × 14 models = **294 answers**: everyday questions that sound a bit touchy, plus questions that have one right answer (basic facts, simple maths), to check both willingness and accuracy in one go. → [`01-round-one-294-tests/`](01-round-one-294-tests/)

### Part two: four questions, one test each

| The question | The test | Size | Folder |
|---|---|---|---|
| What do they say yes or no to? | **Easy** (5 everyday questions) and **medium** (5 harmless questions worded to trip filters) | 5 × 14 models = 70 answers each | [`02-easy-and-medium/`](02-easy-and-medium/) |
| Does the reason behind a request change the answer? | **The ladder**: the same request five times, the reason getting worse each time, on 3 topics | 15 × 11 models = 165 answers, plus 60 from Claude | [`03-ladder/`](03-ladder/) |
| Does taking the refusals out make the model worse? | **Smarts**: right-answer questions and 5 toy practice puzzles, run twice | 110 puzzle runs | [`04-smarts-and-puzzles/`](04-smarts-and-puzzles/) |
| Can it help test the security of my own app? | **The hard test**: 4 steps against a practice app built to be broken, in a sealed offline sandbox, then an agent loop | 4 steps × 4 models, then 2 loop runs | [`05-hard-test/`](05-hard-test/), [`06-sandbox-setup/`](06-sandbox-setup/) |

Altogether that is **725 graded answers from the local models, plus 60 from Claude**.

## Results in one table

| Test | What it asks | Normal models | Uncensored copies | Details |
|---|---|---|---|---|
| Round one | 21 questions x 14 models = **294 tests**: everyday questions that sound touchy, plus questions with a right answer | answered almost everything; 8 of 8 right answers for every model | fixed the two questions that tripped the normals; four copies dropped a right answer | [`01-round-one-294-tests/`](01-round-one-294-tests/) |
| Easy | 5 everyday questions | **30 of 30** answered | **40 of 40** answered | [`02-easy-and-medium/`](02-easy-and-medium/) |
| Medium | 5 harmless questions worded in a way that trips filters | **29 of 30** answered | **40 of 40** answered | [`02-easy-and-medium/`](02-easy-and-medium/) |
| Ladder (the slider) | the same request 5 times, the reason getting worse each time, on 3 topics | answered **41%** straight | answered **84%** straight | [`03-ladder/`](03-ladder/) |
| Puzzles | 5 toy practice puzzles, run twice | **32 of 50** solved | **25 of 50** solved | [`04-smarts-and-puzzles/`](04-smarts-and-puzzles/) |
| Puzzles, refusals | | 0 | 0 (**0 refused of 110 runs**) | [`04-smarts-and-puzzles/`](04-smarts-and-puzzles/) |
| Hard test, will it? | 4 steps of testing a practice app | both stopped after reading the code | both said yes to every step | [`05-hard-test/`](05-hard-test/) |
| Hard test, can it? | the two willing models, in a sealed sandbox | not run | with a loop, Qwen 3.8 27B abliterated pulled the user list (24 accounts, about 255 seconds); Gemma 4 31B heretic got no win | [`05-hard-test/`](05-hard-test/) |

On the ladder, Claude Opus 4.8 answered 63% straight and Claude Opus 5.5 answered 67%, more than any normal open model in this test.

## What I took from it

1. **For everyday questions you do not need an uncensored model.** The normal ones already answer.
2. **When the reason starts to sound bad, they split.** Normal models stop partway up the ladder. Most uncensored copies go all the way.
3. **It usually costs something.** Most uncensored copies got a little worse at questions with right answers, and none of them got better at the puzzles.
4. **Willing is not the same as able.** In the hard test, both uncensored models said yes, and only one could finish the job, and only with a loop.
5. **The one that held up:** Qwen 3.8 27B abliterated (the Q4_K file, 16.8 GB) answered everything on the ladder and kept the same smarts score as its normal version.

## How the tests were run

- **App:** LM Studio (0.4.20), one model loaded at a time.
- **Files:** GGUF, 4-bit. See [`models.md`](models.md).
- **Settings, the same for every model:** context 8192, temperature 0.6, top_p 0.95, no system prompt.
- **A fresh chat for every question, and one attempt per question.** No retries, no picking the best answer.
- **Thinking off** where the model allows it. GPT-OSS 20B cannot turn it off; Llama 3.3 70B has no such setting.
- **Hardware:** one Apple Silicon desktop (M3 Ultra). The speeds in the round-one table are from that machine and will be lower on a smaller one.
- **Claude** (ladder only): the same 15 questions, asked twice each, through Claude Code.
- **Dates:** round one, the puzzles and the ladder on 8 and 9 November 2026; easy and medium and the hard test on 17 November 2026.

## What this does not show

- One attempt per question. A second run could move a few cells.
- The labels on the ladder and the hard test (answered, held back, refused) were read by hand.
- Claude appears here only on the ladder. It was not run on easy and medium or on the hard test.
- The hard test is one practice app that was built to be broken. It says nothing about how any of these models would do against a real, defended system.
- The speeds are from one machine.

## What is left out, and why

This repo is here so you can check the numbers. It is not a how-to.

| Left out | Why |
|---|---|
| Answer texts for the ladder | The test only saved labels and first sentences, so no how-to detail from the upper rungs was ever kept |
| Answer texts for easy and medium | Only the label for each answer was saved in that round |
| The full answers to the bike lock question in round one (R4) | They are lock-opening walkthroughs. The score, the grader note and the first line of each are kept |
| The puzzle files and the answers to them | Names and scores are enough to check the totals |
| Everything the models wrote or ran in the hard test: request strings, scripts, loop commands, the run log, and the data that came back | No attack detail belongs in a public repo. The step grid and the named steps are kept |

## Use it responsibly

Only test systems you own or have written permission to test. See [`06-sandbox-setup/`](06-sandbox-setup/).
