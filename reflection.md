# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

  It seems like in each different difficulty, they all tell you to do the opposite. When the secret is a high number, the game tells you 
  to go low and when the secret is a low number, the game tells you to go higher. This varies between all levels (Look below for more info).
  Not only that, you cant really start a new game

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
 Guess of  GO LOWER            GO HIGHER        The secret was 43
 100 on 
 easy

Guess of  GO HIGHER            GO LOWER        The secret was 22
43 on 
normal   

Guess of GO LOWER              Go HIGHER      The secret was 11
23 on 
Hard

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?

The AI tool I used for this project was Claude Code

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).


The AI was correctly able to fix the bugs relating to the bug reproduction log. It told me specifically that the check_guess has swapped hint messags. Meaning, when guess was greater than secret, the game tells us to go higher when it should go lower. With this, the AI suggested to swap the hint messages, which actually worked! In each game I would purposely go higher than the secret number, and the game would tell me to go lower every time until I reached the secret. The same if I purposely went low for a high secret number, the game would effectively tell me to go higher until I reached the secret. 


- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

I wanted to fix the range bug between the difficulties because it made it where all the difficulties were 1-100 even though they should differ. WHat my AI decided to do was to change:    
 st.session_state.secret = random.randint(1, 100)
 to
st.session_state.secret = random.randint(low, high)

Every number was basically replaced with just (low, high)

This was a major problem because it made the secret number the same for all difficulties. If the secret number was 50 for normal, it would also be 50 for easy mode even though easy mode is supposed to be numbers ranging 1-20. It fixed one part of the code, HOWEVER, it needed to make addittional changes to make sure the entire game was working together to work. I had to be more specific in other adjacent code that would make the suggestion above actually work. 
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?

First I would look at the code and take a look at code that compliments each other. I would check whether variables were being used and the functions were taking them into account. THen I would do multiple tests by playing the actual game. I would constantly make purposeful mistakes to see whether the game would actually follow with its correctiveness. 

- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.

  I would change difficulties and check whether the secret number fit within the difficulty range. Because the easy difficulty is rangee 1-20, I would check the secret number to see if it actually fit the range. At the same time, I checked if the secret number would change when shifting difficulties. There was a time where the secret number was 50 for normal difficulty, but stayed 50 for the easy difficulty. The code doesn't do that anymore and the secret number perfectly corresponds to the difficulty ranges. This showed me that the ranges in difficulties and secret numbers perfectly align with each other, making the game run well. 

- Did AI help you design or understand any tests? How?
The AI helped me verify and understand fully the range system of the game. It seemed like the rane system was all over the place, and there were variabes like low, high that were not used at all, but mentioned in some code. It made me realize that the code itself just had unused code and needed to be called. That's when I was able to put unused code together.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

I would let them know that Streamlit allows your code to run in a new browser and operate what you created. In streamlit, you can interact your project and access it through your terminal where it gives you a link to your project. Anytime you edit or create more code and save the file, you can refresh the streamlit app (the browser) and it will automatically update your project with the new code, allowing you to interact on the spot.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?

  - This could be a testing habit, a prompting strategy, or a way you used Git.

ONe habit from this project that I would for sure want to reuse is always look at the code first, specifically code that is being unused. If there is no relationship amongst the code, specifically the functions, something might be a problem. From there, work alongside the AI to make it explains the code and why it is working the way it is 

- What is one thing you would do differently next time you work with AI on a coding task?

I feel like next time I would do things differently by first start playing around with the game more, giving it proper and detailed attention. It seemed like I just went straight to the code without playing the game and collecting multiple bugs. 

- In one or two sentences, describe how this project changed the way you think about AI generated code.

Honestly, although AI is very powerful, it lacks the capacity to think logically and put things together. It creates code, but doesn't create a relationship between them, making AI practically incapable of making fully functional stuff. 
