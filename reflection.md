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
