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

- [The game is a number guessing game where the player tries to guess a secret number within a limited number of attempts. ] Describe the game's purpose.
- [hints were reversed (Too High told you to go Higher), the secret number converted to a string on every 2nd attempt making it impossible to win, and the score dropped below zero on wrong guesses. ] Detail which bugs you found.
- [ corrected the hint direction in `check_guess`, removed the string conversion bug in `app.py`, fixed scoring to never go negative, and refactored all logic functions into `logic_utils.py`.] Explain what fixes you applied.

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. User enters a guess of 40 → game returns "Go HIGHER"
2. User enters 70 → game returns "Go LOWER"
3. User enters 50 (the secret) → " Correct!" and balloons
4. Score updates correctly and never goes negative
5. Game ends after the correct guess

**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results

```
pytest
==================== test session starts =====================
platform win32 -- Python 3.13.4, pytest-9.1.0, pluggy-1.6.0
rootdir: C:\Users\HP\Downloads\bytebites_tinker_activity\ai110-module1show-gameglitchinvestigator-starter
plugins: anyio-4.14.0
collected 5 items                                             

tests\test_game_logic.py .....                          [100%]

===================== 5 passed in 0.16s ======================

# Paste your pytest output here, e.g.:
# pytest tests/
# ========================= X passed in 0.XXs =========================
```

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
