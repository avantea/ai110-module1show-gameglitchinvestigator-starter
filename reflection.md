# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").
The game had several logic bugs when I started. The hint system did not match the number range or the guesses I entered. For example, the game says the number is between 1 and 100, but when I guessed 100, it told me to go higher. Negative numbers and very large numbers also gave confusing hints. The attempt counter seemed off because it said I was out of attempts when I expected one attempt left. Starting a new game also caused the game to stop working correctly.

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input Used | Expected Behavior | Actual Behavior | Console Error / Output |
|---|---|---|---|
| Guess of 100 | Since the game says the number is between 1 and 100, the game should not say to go higher. | Game said to go higher. | none |
| Guess of -1 | Game should reject the input or explain that guesses must be between 1 and 100. | Game gave a misleading hint saying to go lower. | none |
| Guess of 89859325 | Game should reject the input as outside the valid range. | Game said to go higher. | none |
| Reaching one attempt left | Game should allow the final attempt before ending. | Game said all attempts were done too early. | none |
| Starting a new game | Game should reset the score, attempts, and secret number. | Game stopped working correctly. | none |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

Correct suggestions:
GitHub Copilot identified that the secret number was sometimes being converted to a string before comparison. This caused incorrect hint behavior because string comparisons do not work the same way as numeric comparisons. I verified the suggestion by reviewing the code, removing the string conversion, and testing the game manually.

Incorrect suggestions:
One AI suggestion initially appeared to fix the comparison logic, and the automated tests passed, but the live Streamlit game still behaved incorrectly. I discovered that app.py was still using old logic instead of the refactored functions in logic_utils.py. I verified this by manually testing the game and inspecting the code rather than relying only on the AI's recommendation.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

I verified my fixes using both automated tests and manual gameplay. I updated tests/test_game_logic.py and ran `python3 -m pytest`, which resulted in all tests passing. I also ran the Streamlit application and tested invalid inputs such as -1 and large numbers, verified the high/low hints, tested the New Game button, and checked the attempt counter behavior. Manual testing helped identify issues that were not caught by the automated tests.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

Streamlit reruns the entire script every time a user interacts with the app, such as clicking a button or entering a value. Session state is used to store information that should persist between reruns, such as the secret number, score, and number of attempts. Without session state, the game would reset every time the page reran.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

One habit I want to reuse is testing changes frequently instead of waiting until the end. Running pytest and manually testing the Streamlit app helped me catch bugs that I would have missed otherwise.
One thing I would do differently next time is ask the AI to explain the root cause of a bug before asking it to generate a fix. Understanding the problem first made it easier to verify whether the AI's suggestions were actually correct.
This project changed the way I think about AI-generated code because I learned that AI can help find bugs and suggest solutions, but its suggestions still need to be reviewed and tested carefully. Passing tests does not always mean the application works correctly, so human judgment is still important.