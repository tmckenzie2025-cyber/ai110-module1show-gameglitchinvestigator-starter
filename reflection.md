# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?
Bug 1: Hints point the wrong way.
Expected: When my guess was lower than the secret number the game should have told me to go higher.
Actual: The game told me to go lower which pointed me away from the answer.

Bug 2: New Game does not clear a win.
Expected: After winning clicking New Game should start a fresh round and remove the win message.
Actual: The "You already won" message stayed on screen after clicking New Game.

Bug 3: Attempts counter does not count down.
Expected: On Easy difficulty, after clicking New Game and making my first guess, the attempts left should have dropped from 6 to 5.
Actual: The counter still showed 6 after the first guess.

- What did the game look like the first time you ran it?
  It showed a title, an input box for the guess, a Submit button, a New Game button, show hint box and an attempts counter starting at different numbers depending on difficulty. 
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").
  The hints were backwards for some guesses. When my guess was below the secret number the game told me to go lower.
  The attempts counter did not count down. On Easy, after my first guess it still showed 6.

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
|Secret number is [50]. Guess [30]. | Hint says "Go Higher" because the guess is below the secret number.|Hint says "Go Lower" even though the secret number is higher. |none| 
|Win a game, then click "New Game." | Game resets with a new secret number the attempt count returns to the starting value and the win message is cleared.| The "You already won" message stays on screen after clicking "New Game."|none|
|On Easy difficulty, start a new game and submit the first guess [25].|Attempts left drops from 6 to 5 after the first guess. |Attempts left still shows 6 after the first guess.|none|

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
