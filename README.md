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

- [ ] Describe the game's purpose.
The game's purpose is to ensure you guess the correct secret number. Through the user guesses, the game will tell
you to guess a number higher or lower than the guess you made. IN a limited number of attempts, you have to 
guess the right number which grants you points, otherwise you lose points!
- [ ] Detail which bugs you found.
1. The number range for each difficulty were basically the same. Even though the easy difficulty is ranges 1-20, the 
game made it where it was 1-100.
2. The game itself could not restart when clicking the restart game button
3. The secret number stayed the same for all difficulties, bypassing the range for the easy difficuly.
4. The game would tell you to go Higher even though the secret number was low and would tell you to go lower when the 
secret number was a high number

- [ ] Explain what fixes you applied.
1. I swapped HIGHER and LOWER messages to match the correct logic for the game
2.  Added a check to reset the game state when the difficulty changes, ensuring that the secret number and attempts 
are reset appropriately for the new difficulty level.
3. used low-high variables from get_range_for_difficulty instead of hardcoded values 
in order to make the game work properly with different difficulties
4. Used a new game button where low and high are used from get_range_for_difficulty
5. Updated the statuc check to display the correct message when the game  is won or lost
while showing the final score and secret number.
6.  Updated the message to display the correct secret number and score when the game is lost.
7. Updated the status check to display the correct message when the game is won or lost, 
and show the final score and secret number.
## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. Select a difficulty: Easy
2. User will see number of attempts they have (6) and number range to guess from (1-20)
3. User enters 4
4. Game says: HIGHER
5. User enters 10
6. Game says: GO LOWER
7. User enters 7
8. Score updates based on guesses
8. Game says: Congratulations, you win!
9. Start new game!

**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->


## 🧪 Test Results

```
# Paste your pytest output here, e.g.:
# pytest tests/
# ========================= X passed in 0.XXs =========================
```

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
