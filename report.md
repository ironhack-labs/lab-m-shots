# Report: Prompt Experiments on Sentiment Classification

## What I Did
I tried 3 different prompts to see how the model reacts when classifying product reviews.

1. **Sentiment + Short Reason**  
   - Review: "Honestly, I like the design, but the performance was even better."  
   - Answer: `Positive - great performance compared to design`  
   - Pretty good, it caught the problem and gave a short reason.

2. **Star Rating (1★–5★)**  
   - Review: "It does what it promises, nothing more and nothing less."  
   - Answer: `3★`  
   - This felt fair, kind of neutral. Could also be 2★, but 3★ makes sense.

3. **Good/Bad/Meh Token**  
   - Review: "It functions okay, but the battery dies too fast. Not sure I’d recommend it."  
   - Answer: `Bad`  
   - Straight to the point. Worked fine here.

---

## What Didn’t Work Great
- The **star rating** is a bit fuzzy. Neutral reviews could be 2★ or 3★.  
- The **short reason** prompt might sometimes get longer than I asked for.  

---

## What I Learned
- If I want short, clean outputs, I need to tell the model very clearly (like “only one word”).  
- Different styles change the “feel” of the answer:  
  - Reason = more detail  
  - Stars = easy to understand  
  - Tokens = super quick but not very nuanced  
- The model mostly did the right thing, but the style affects how usable the result is.

---

## Conclusion
All 3 prompts worked in their own way:
- `Negative - disappointing performance`  
- `3★`  
- `Bad`  

Formal prompts give the most reliable answers, but simpler ones (stars, tokens) are easier to read.
