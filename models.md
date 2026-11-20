# The 14 models

Each normal open model next to an uncensored copy of the same model. "Abliterated" and "heretic" are two ways of editing a model after release to remove its refusals. All files are GGUF, 4-bit, run in LM Studio.

| Model | Type | Hugging Face repo | Quant | Download size (GB) | Ran in |
|---|---|---|---|---|---|
| Gemma 4 12B | normal | `unsloth/gemma-4-12b-it-GGUF` | Q4_K_M* | 7.1 | round one, easy and medium |
| Gemma 4 12B heretic | heretic | `culturerevolt/gemma-4-12b-heretic-abliterated-GGUF` | Q4_K_M* | 7.4 | round one, easy and medium |
| Gemma 4 31B | normal | `unsloth/gemma-4-31B-it-GGUF` | Q4_K_M* | 18.3 | round one, easy and medium, ladder, puzzles, hard test |
| Gemma 4 31B heretic | heretic | `llmfan46/gemma-4-31B-it-uncensored-heretic-GGUF` | Q4_K_M* | 18.7 | round one, easy and medium, ladder, puzzles, hard test |
| Qwen 3.6 35B-A3B | normal | `unsloth/Qwen3.6-35B-A3B-GGUF` | UD-Q4_K_M | 22.1 | round one, easy and medium, ladder, puzzles |
| Qwen 3.6 35B-A3B heretic | heretic | `llmfan46/Qwen3.6-35B-A3B-uncensored-heretic-GGUF` | Q4_K_M | 21.2 | round one, easy and medium, ladder, puzzles |
| Qwen 3.6 35B-A3B abliterated | abliterated | `huihui-ai/Huihui-Qwen3.6-35B-A3B-abliterated-MTP-GGUF` | Q4_K | 21.7 | round one, easy and medium |
| GPT-OSS 20B | normal | `unsloth/gpt-oss-20b-GGUF` | Q4_K_M | 11.6 | round one, easy and medium, ladder, puzzles |
| GPT-OSS 20B heretic | heretic | `DavidAU/OpenAi-GPT-oss-20b-HERETIC-uncensored-NEO-Imatrix-gguf` | IQ4_NL | 11.8 | round one, easy and medium, ladder, puzzles |
| Qwen 3.8 27B | normal | `unsloth/Qwen3.8-27B-GGUF` | UD-Q4_K_M | 16.5 | round one, easy and medium, ladder, puzzles, hard test |
| Qwen 3.8 27B abliterated | abliterated | `huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF` | Q4_K | 16.8 | round one, easy and medium, ladder, puzzles, hard test |
| Llama 3.3 70B | normal | `unsloth/Llama-3.3-70B-Instruct-GGUF` | Q4_K_M* | 42.5 | round one, easy and medium, ladder, puzzles |
| Llama 3.3 70B abliterated | abliterated | `bartowski/Llama-3.3-70B-Instruct-abliterated-GGUF` | Q4_K_M* | 42.5 | round one, easy and medium, ladder, puzzles |
| Qwen 3.8 9B heretic (no normal twin tested) | heretic | `mradermacher/Qwen3.8-9B-heretic-uncensored-GGUF` | Q4_K_M* | 5.6 | round one, easy and medium, ladder, puzzles |

\* The test plan called for Q4_K_M for every model. Where a row is starred, the exact file name was not written down in the results, so the quant shown is the planned one.

The Qwen 3.8 27B abliterated file that was tested is the **Q4_K** file, 16.8 GB.

12 of the 14 fit on a graphics card with 24 GB of memory or a Mac with 32 GB. The two Llama 3.3 70B files (42.5 GB) need a bigger machine.
