# Get started: run an uncensored model at home

This is the setup used in the video, written so you can copy it. It runs a model on your own computer, gives it a harness so it can actually do things, and keeps it sealed off from anything real.

## 1. Pick a model

| If you have… | Download | Why |
|---|---|---|
| A 24 GB graphics card or a 32 GB Mac | **Qwen 3.8 27B abliterated**, the `Q4_K` file (16.8 GB): [`huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF`](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | The pick from the tests. It answered everything on the ladder, kept the same smarts score as its normal version, and was the only model that got through the practice app (with a loop). |
| The same machine, and you'd rather keep the refusals | **Gemma 4 31B** (normal), 18.3 GB: [`unsloth/gemma-4-31B-it-GGUF`](https://huggingface.co/unsloth/gemma-4-31B-it-GGUF) | The most capable model across these tests. Expect the odd refusal. |
| A smaller machine (around 16 GB) | **Gemma 4 12B** (normal), 7.1 GB: [`unsloth/gemma-4-12b-it-GGUF`](https://huggingface.co/unsloth/gemma-4-12b-it-GGUF) | A small download that still answered the everyday questions. |
| Skip | Llama 3.3 70B abliterated | It needs a much bigger machine, and it still held back on part of the ladder. |

Keep your normal model as well. For everyday work it is usually the smarter one; switch to the uncensored copy only when you need the yes.

## 2. Run it in LM Studio

[LM Studio](https://lmstudio.ai) is a free desktop app for running models locally.

1. Install LM Studio.
2. Search for the model by its Hugging Face name (above) and download the file listed.
3. Load the model and chat with it to check it works.
4. Start LM Studio's **local server** (in its developer / server view). This gives other apps on your machine an OpenAI-compatible address to talk to the model. Nothing leaves your computer.

A plain chat window can only write text. To let the model run commands, read what comes back and try again (the "loop" from the video), it needs a harness.

## 3. Give it a harness: pi

[pi.dev](https://pi.dev) is a small, lightweight agent harness that works well with local models. With pi, the model can run shell commands and use tools inside the environment you give it.

In the tests, pi was pointed at LM Studio as a model provider (pi lets you add custom providers in its `models.json`; see pi's own docs for the current format).

### Let your AI set it up for you

Paste this into Claude Code, Codex or a similar assistant on the machine you'll use:

```text
I want to run a local model inside the pi agent harness (https://pi.dev), in a safe, sealed environment.

1. Check that LM Studio is installed and its local server is running, and tell me the server address and the loaded model's id.
2. Read pi's current documentation and install pi.
3. Add LM Studio as a custom provider in pi's models.json, pointing at that local server, using the loaded model's id.
4. Create an isolated environment for pi to work in: a container or VM with no internet access and no access to my personal files. Only mount the one project folder I name.
5. Start pi inside that environment with the LM Studio model and run one harmless test command so I can see it working.
6. Show me every file and setting you changed, and explain how to stop it and remove it.

Do not give the model access to anything outside that environment. Ask me before any step that needs my password.
```

## 4. Keep it sealed

- Run it in an isolated environment with **no internet**, and with nothing mounted except the project you want it to work on.
- **Only test systems you own**, or have written permission to test. Never point it at someone else's site, app, network or account.
- An uncensored model on your own machine has nobody checking what you do with it. That is your responsibility.

More on how the hard test was sealed: [`../06-sandbox-setup/`](../06-sandbox-setup/).

## 5. Find the best model for your own use case

These results are one set of tests on one machine. The best way to choose is to test a few models on your own questions. You can have your AI assistant run the whole evaluation for you:

```text
I want to choose the best local model for my use case, and I'd like you to run a small evaluation.

My use case: <what I want the model to do>
What a good answer looks like: <what I want to achieve>
Models to compare: <2 to 4 models I've downloaded in LM Studio>

1. Write 10 test questions that match my use case: a mix of everyday ones, ones that are a bit touchy but harmless, and ones with a right answer I can check.
2. Show me the questions before running anything.
3. Run every question against every model through LM Studio's local server, in a local environment with no internet connection. One fresh chat per question, the same settings for every model.
4. Save the answers to a file: one table with a row per question and a column per model, plus whether each model answered, held back or refused.
5. Give me the answers side by side without telling me which model wrote which, so I can pick the best ones blind. Then reveal the models and summarise which one did best for my use case.
```

Ten of your own questions will tell you more than any leaderboard.
