![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Lab | M-Shots

This lab explores few-shot prompting techniques using the OpenAI API. See the full implementation in [lab-m-shots.ipynb](lab-m-shots.ipynb).

## What Was Done

Three prompting strategies were implemented and compared across two domains:

**F1 Championship Q&A** — used to illustrate the core concept:
- Zero-shot: plain system prompt, no examples
- One-shot: one Q&A pair embedded in the system prompt
- Few-shot (2 shots): two Q&A pairs, first in system-prompt style, then using proper `user`/`assistant` role pairs

**Weather Forecast** — the exercise implementation:
- Zero-shot: format specified via instructions only
- One-shot: one example city forecast added
- Few-shot (3 shots): three example city forecasts (Paris, Berlin, Tokyo) to reinforce format

## What Worked

- Even a single shot was enough for GPT-3.5 to reliably adopt the target output format
- The role-based approach (`user`/`assistant` turns) produced cleaner learning than embedding examples in the system prompt
- The weather few-shot correctly generalised format and summary style to unseen cities (Budapest)
- Sentiment classification with 3 labelled examples correctly handled an ambiguous negative case

## Key Learnings

- **Zero-shot** produces correct answers but no format control; useful when structure doesn't matter
- **One-shot** is usually sufficient for format adoption in large models — more shots have diminishing returns
- **Role-based shots** (`user`/`assistant` pairs) are more effective than inline examples in the system prompt because they mimic a real conversation, which is the format the model was trained on
- **Over-anchoring risk**: too many shots can reduce output variability and cause the model to repeat patterns mechanically rather than reason about the actual question
- Context window cost is real — each shot consumes tokens on every request, so shot count should be the minimum needed
