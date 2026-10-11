# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- A Streamlit number guessing game. The player picks a difficulty, guesses a secret number, and gets "Go HIGHER" or "Go LOWER" hints until they win or run out of attempts.

- The hints pointed the wrong way. A guess below the secret said "Go LOWER."
- New Game did not clear a win. The "You already won" message stayed on screen.
- The attempts counter lagged one guess behind.

- Moved `check_guess` into `logic_utils.py`, swapped the reversed hint messages, and removed the code that turned the secret into text on even attempts.
- Updated the New Game button to reset the game status, clear the guess history, and pick the secret from the correct range for the difficulty.
- Updated the starter tests to match the function's two return values and added a test that checks the "Too High" message says to go lower.


## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. Start the game on Normal difficulty (range 1 to 100) and open Developer Debug Info to see the secret, for example 58.
2. User enters a guess of 40. Game returns "Too Low" with the hint "Go HIGHER!"
3. User enters a guess of 70. Game returns "Too High" with the hint "Go LOWER!"
4. User enters a guess of 58. Balloons appear with "You won! The secret was 58."
5. User clicks New Game. The win message clears and a new round starts with a new secret.


**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results

```
# Paste your pytest output here, e.g.:
# pytest tests/
# ========================= X passed in 0.XXs =========================
```

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
