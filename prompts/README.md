Method 1: Copy-Paste Magic (Works on ANY Chatbot)
```
<instructions>
Generate 5 responses to the user query, each within a separate <response> tag. Each <response> must include a <text> and a numeric <probability>. Randomly sample responses from the full distribution.
</instructions>

[Your actual prompt here]
```
example:
```
<instructions>
Generate 5 responses to the user query, each within a separate <response> tag. Each <response> must include a <text> and a numeric <probability>. Randomly sample responses from the full distribution.
</instructions>

Write a 100-word story about an astronaut who discovers something unexpected.
```
Want more? Just ask: “Give me 5 more”.​

Method 2: System Prompt (Pro Move)
If you’re using ChatGPT’s custom instructions or building an AI app, add this to your system prompt:​
```
You are a helpful assistant.
For each query, please generate a set of five possible responses, each within a separate <response> tag.
Responses should each include a <text> and a numeric <probability>.
Please sample at random from the tails of the distribution, such that the probability of each response is less than 0.10.
```
This makes EVERY response more creative automatically.​
