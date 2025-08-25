# LLM_RL
Apply RL techniques to small LLMs like **Qwen3-0.6B** or **Gemma 3-270M**.

---

## Hangman Game

### Non-thinking / Non-reasoning Prompt
The following prompt form is used as the input:

```

You are playing a game of Hangman.

Your task is to guess a single character.

The word has a certain number of letters.
The current state of the word is shown with guessed letters filled in and blanks for the unknown letters.
The number of incorrect guesses remaining is listed.
All letters that have been guessed so far are listed.

You will format your response as a single uppercase letter at the end

The word has 8 letters.
The current state is: _ _ p _ _ t _ _
Incorrect guesses remaining: 6
Guessed letters: ['T', 'P']

Correct response:

```
Only single letter guess is follow instead of full word guess is for simple style control

**Note:** This prompt is designed for a single-token output. Set `max_new_tokens = 1`.  
If `max_new_tokens` is set to 64 or higher, small LLMs often produce unnecessary text.

#### Example
**Qwen2.5-0.5B-Instruct (max_new_tokens = 64):**
```

V

Output:

Assistant: To solve this Hangman game, I need to analyze the current state of the word and determine which letter has not yet been guessed. Here's how I would approach it step-by-step:

1. **Current State**: The word currently contains underscores (_) for each of its 8 letters.
```

---
## Model Testing

**Test dataset size:** 10,429 samples  

### Pre-trained Model Guess Distribution (in %)

| Category                        | Qwen2.5-0.5B | Qwen2.5-0.5B-Instruct |
|---------------------------------|--------------|------------------------|
| Already guessed                 | 73.83%       | 84.94%                 |
| Non-alphabetic guess            | 26.06%       | 2.73%                  |
| Guess is not a single character | —            | 9.95%                  |
| Guess empty                     | —            | 1.61%                  |
| Guess is not a character in word| 0.08%        | 0.66%                  |
| Correct guess                   | 0.03%        | 0.11%                  |

---
