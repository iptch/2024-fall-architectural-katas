Questions for AI expert Dario R.
---

- What LLM solutions exist for enterprises?
  - Azure 
  - Google Cloud
  - OpenAI
- 
- Is specialized knowledge necessary?
  - On the solution design level it is very highly specialize knowledge. You pay either for mistakes
  that are made or for highly skilled and experienced proffessionals.
  - Prompt engineering is just a lot of trial error, not rocket science.
  - 
  
- How often do models/versions need to be updated and why?
- What is the difference between context upload and training?
  - Training is called 'fine-tuning'. Train and Testset. 
  - Sets need to be large and well engineered.
- When can we expect deterministic behavior?
  - Temperature setting: Can be minimized. To 0 - Engineering 
  - Even if temperature 0, Ai the same, prompt the same, result may be the same.
  - Can lead to chaotic behavior.
  - 
- What are the costs? 
  - Base (license, platform use, ...)
    - Pay as you go, pay per token.  - with token-rate limit. Their experience, 
    500'000 prompts --> 500'000 USD. Textbased.
    - PTU: Flatrate but a token-rate limit. 60'000 / month: The cheapest of what you heard.
  - Per prompt? 
  - Per token (scales with the amount of text in the prompt & also incoming token)
- How easy is it to predict the cost?
  - PTU pricing is very intransparent. One number they have heard was 60'000 USD / month. But this may
  vary greatly across offerings.
  - Pay as you go pricing has transparent pricing. One needs to additionally know the prompt size as well as the 
  response size. With tools like Tiktoken, the number of tokens per prompt and response can be counted and the 
  corresponding price estimated.
  The response may be hard to predict but can also be limited by instructions in the prompt.
- How can we test our AI?
  - every change of prompt or model may lead to possible chaotic behavior
  - we need a large and good testset to test the new model + prompt
  - the more fine tunes your model, the more fine tuning is needed for the next test
  - Reinforcement learning --> human control for match
- Are you aware of special support for non-profit organizations?
  - no.
- How do APIs of AI Models look like (synchronous vs asynchronous vs long-running)
  - REST, may take a long time.
  - Streaming, is possible. non-blocking
  - If ratelimit is reached, it blocks you.
  - Token-prediction
- What is the delay?
  - max 60s
- Trend: Will it become better, cheaper?
  - Trend is cheaper and cheaper. Context caching also new possibility to optimize.
  - Traffic predication always helps. 
- When using LLM, do I need one of these services or is there another way?
  - You can use Opensource models, Meta, Mistral. It is sometimes very hardwarespecific.
  But to get it cheaper, you need it on-prem, and pay for maintenance-cost.
- Data privacy
  - You can make an agreement that don't save it, it's only processing. but it comes at the cost of
  you now having a new audit pflicht.
  - I don't know anything else about US regulations and whether data privacy might be an issue.
- User Accounts:
  - AD 

- Context is everything that is sent
- Context caching is possible for some LLMs (Google at the moment)
- Multimodale Models: Text, Audio, Images, PDF -> Image
- --> Resume Format needs to be changes
- OCR can not do anything - LLM can do more. Probably both needs to be fed.



- Operational coset with be major by AI, ours negligible.

- Lifecycle of models: EOL, intensive development will be EOL quickly
- Hacker could try to 
- Resume preprovessing for security reasons --> Prompt Injection
