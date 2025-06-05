# M-Shots Learning Report

## Summary

I believe this exercise's aim is to explore how M-Shot prompting (Zero-shot, One-shot, Few-shot) affects GPT-3.5's behavior. I used it in a practical, personalized use case: reflecting on my daily experience as an AI Engineering bootcamp student.

The task was to evaluate a journal entry and return a classification for:
- **Sentiment** (Positive, Neutral, Negative)
- **Readiness** (Ready, Confused, Overwhelmed)

I submitted the same reflection to the model using each prompt style.

---

## Results

**Input Reflection**:  
*"Today was hard. I got stuck on OpenAI's API key setup and it frustrated me."*

### Zero-Shot Result:
GPT returned a long, human-sounding feedback paragraph.  
**Output**:
> “This reflection demonstrates perseverance and self-awareness… I recommend offering support…”

**Issue**: No structured `Sentiment` or `Readiness`. GPT tried to coach me instead of classify.


### One-Shot Result:
GPT returned motivational feedback:
> “Remember, overcoming obstacles is part of the learning process…”

**Issue**: Better tone imitation, but still no structured classification.


### Few-Shot Result:
> `Readiness: Perseverant`  
> `Sentiment: Positive`

**Success**: This was the only version that returned clear, formatted labels. GPT followed the pattern I gave it.


## Lessons Learned

- Zero-shot prompts leave too much room for GPT to guess what you want.
- One-shot improves tone alignment, but not structure unless formatting is enforced.
- Few-shot is the most effective way to teach GPT exactly what to return.
- GPT doesn’t "learn" in the traditional sense, but copies patterns it sees.
- Prompt structure (format, tone, labels) is as important as content.

