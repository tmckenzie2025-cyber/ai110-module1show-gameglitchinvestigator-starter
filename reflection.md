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

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)? Claude
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
    While moving check_guess into logic_utils.py the AI removed a try/except TypeError block without being asked. It explained that the block only existed to handle the secret being converted to text on even attempts which I had removed. I verified this by tracing a guess of 9 against a secret of 50 by hand and the new pytest test passing confirmed it.
- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count.
    Most of the AI suggestions on this project were correct and simple and they matched what I needed so there was very little I had to reject. The only suggestion I did not follow was a recommendation to make a separate commit just to fix a small typo in one of my fix comments. I did not think a whole commit was necessary for a one-line comment at that point so I fixed the typo by hand and included it with my reflection updates instead. I verified the change by checking that the comment in app.py read correctly before staging it and confirming it appeared in my commit history with the reflection work.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed? 
    I used three checks for each bug. First I traced the code by hand with specific numbers to confirm the logic made sense. Then I ran python -m pytest to confirm the automated tests passed. Finally I played the live game with python -m streamlit run app.py and used the Developer Debug Info panel to see the secret number and confirm the game behaved correctly.
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
    After moving check_guess into logic_utils.py I ran the starter tests and all three failed. The tests expected a single value like “Win” but check_guess returns two values the outcome and the hint message. This showed me the tests were written for a different version of the function not that my fix was wrong. I also realized the starter tests only checked the outcome word which was never broken so they could not have caught the reversed hints. After updating the tests and adding a new test that checks a guess of 60 against a secret of 50 returns “Too High” with a message telling the player to go lower all 4 tests passed. For Bug 2 I tested manually by winning a game and clicking New Game which cleared the win message. During that test I also noticed my old guess stayed in the input box which I noted as a minor issue outside the scope of this fix.
- Did AI help you design or understand any tests? How?
    Yes. The AI updated the three starter tests so they unpack the two values check_guess returns and only check the outcome. It also wrote the new test that confirms the “Too High” message tells the player to go lower. I told it not to change check_guess itself because app.py expects two values back and changing the function would have broken the game.
---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
    Every time you click a button or type in a box Streamlit runs the whole script again from top to bottom. That is called a rerun. Normally that would wipe out every variable so Streamlit gives you session state which is like a notebook that survives each rerun and remembers things like the secret number, attempts, and whether you already won.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
    I want to keep giving the AI tight specific prompts that say what to change and what not to touch like “do not change check_guess.” It kept every change small and easy to review and I never had to undo anything. I also want to keep tracing the code by hand with real numbers before running it because that is how I understood why each bug happened.
- What is one thing you would do differently next time you work with AI on a coding task?
    Next time I would read the existing tests before trusting them. The starter tests only checked the outcome word, like “Too High,” which was never broken. That means they would have passed even with the reversed hints so they gave a false sense that the code worked. I would also check that the tests match how the function actually works since these expected one value when check_guess returns two.
- In one or two sentences, describe how this project changed the way you think about AI generated code.
    The game was written by an AI that claimed it was production-ready, and it still had reversed hints, a broken reset, and a counter that lagged behind. I now treat AI-generated code as a first draft that needs to be traced, tested, and played before I trust it.