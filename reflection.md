# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
It was actually confusing, becuase i put like 89 and then it returned go lower, then i put 30, it still said go lower,then i now put 1 which is the least thing and it said go lower again, i was like there is definitely sth wrong with this.
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards")yess, that was what i explained. The hints were actually backwards

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| | | | |
| | | | |
| | | | |

| Input | Expected Behavior | Actual Behavior | Console Output /Error  |
|------------|-------------------|-----------------|------------------------|
| Guess of 89 when secret is 99 | Hint says "Go HIGHER" | Hint said "Go LOWER" | none |
| Any guess on the 2nd attempt | Compares numbers normally | Secret became text, couldn't win | TypeError on comparison |
| Several wrong guesses | Score stays at 0 or above | Score dropped below 0 | none |
---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)? Claude
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result). Claude identified that the hint messages were swapped and explained the int-vs-string comparison bug on second guesses
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result). 
When I asked the AI to help fix the scoring, it suggested adding extra conditions to handle special cases and award bonus points for streaks. However, this made the function more complex than necessary and introduced new bugs. I decided not to use that approach and instead kept a simpler version that leaves the score unchanged for incorrect guesses. This version passes the tests and aligns better with the game's logic. I verified this by running pytest and confirming that update_score(0, "Too Low", 1) returns 0.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed? I mean by playing the game and running pytest
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
  The test that hit different for me was test_too_high_says_go_lower. I ran it and it failed the first time not because my logic was wrong, but because the function was returning a tuple ('Too High', ' Go LOWER!') when the test expected just the string "Too High". That showed me something important: the test was not even testing what I thought it was testing yet. It was catching a mismatch in how I was returning data, before it could even check whether the logic was correct. That was genuinely surprising. I thought once the game played correctly in the browser, everything was fine.
- Did AI help you design or understand any tests? How?
Yes, but I had to push back on it. The AI initially gave me tests that were too detailed — checking the exact emoji in the message string, which means if I ever change the wording the test breaks even if the logic is still correct. I trimmed it down to only check the outcome word like "Too High", not the full message. 
---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
Okay so imagine you are filling a form online, and every time you click submit, the whole page refreshes and clears everything you typed. That is literally what Streamlit does by default, every button click reruns the entire script from line one. So if you wrote secret = random.randint(1, 100) outside of any protection, every click picks a new secret and you can never win because the target keeps moving. Session state is just Streamlit's way of saying "remember this specific thing across reruns, don't reset it." Once I put the secret inside if "secret" not in st.session_state, it only gets created once and stays put. That one change is what made the game actually winnable.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?

  - This could be a testing habit, a prompting strategy, or a way you used Git.
  Opening the "Developer Debug Info" tab first before touching any code. Seeing the actual secret number while playing made it obvious within two guesses that the secret was changing 
- What is one thing you would do differently next time you work with AI on a coding task?
I mean actually getting the plans and everything perfectly before asking it to code, cos if i dont tell it exactly what to do and just prompt, like if i dont plan with it, it might give me a code that is good but not comprehensive enough for what i wanted
- In one or two sentences, describe how this project changed the way you think about AI generated code.
Ehm, like i said you just have to be sure of what the ai is going to code before it codes and then checking for errors too, though AI is becoming perfect these days