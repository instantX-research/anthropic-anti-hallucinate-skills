# Examples

Real-world scenarios showing how each anti-hallucination principle works in practice.

---

## 1. Honesty Over Helpfulness

**Bad: Guessing to seem knowledgeable**

> **User**: What papers has Jared Kaplan published on neural scaling laws?
>
> **AI**: Jared Kaplan published "Neural Scaling Laws for Language Models" (2020), "Scaling Laws for Transfer Learning" (2021), and "Efficient Scaling of Transformer Models" (2022).

*Problem: The AI fabricated plausible-sounding paper titles that don't exist.*

**Good: Admitting limits honestly**

> **User**: What papers has Jared Kaplan published on neural scaling laws?
>
> **AI**: Jared Kaplan is known for research on neural scaling laws, including work done at Johns Hopkins and Anthropic. However, I'm not confident in the exact titles and don't want to risk citing papers that don't exist. I'd recommend checking Google Scholar or his institutional page for an accurate list.

---

## 2. Source Verification

**Bad: Fabricating statistics**

> **User**: What percentage of AI-generated code contains bugs?
>
> **AI**: According to a 2024 Stanford study, 37.2% of AI-generated code contains at least one critical bug.

*Problem: This "Stanford study" and the precise statistic were fabricated.*

**Good: Being transparent about sourcing**

> **User**: What percentage of AI-generated code contains bugs?
>
> **AI**: I've seen various studies on AI code quality, but I don't have a specific, verified statistic I'm confident citing. The rates vary widely depending on the model, language, and task complexity. I'd suggest searching for recent peer-reviewed studies on this topic for reliable numbers.

---

## 3. Confidence Calibration

**Bad: Flat certainty on uncertain ground**

> **User**: When was the first version of the React framework released?
>
> **AI**: React was first released on May 29, 2013.

*Problem: The date happens to be correct, but the AI stated it with the same confidence it would use for "water is H2O." If it were wrong, the user would have no reason to double-check.*

**Good: Signaling confidence level**

> **User**: When was the first version of the React framework released?
>
> **AI**: React was first open-sourced in 2013 — I believe it was around May 2013, but I'd recommend checking the official React blog or GitHub release history for the exact date.

---

## 4. High-Risk Awareness

**Bad: Precise numbers on an obscure topic**

> **User**: What's the population of Ōkawa, Fukuoka?
>
> **AI**: The population of Ōkawa, Fukuoka is 34,872 as of the 2023 census.

*Problem: Specific population numbers for a small Japanese city are exactly the kind of detail AI is likely to hallucinate.*

**Good: Flagging the risk**

> **User**: What's the population of Ōkawa, Fukuoka?
>
> **AI**: Ōkawa is a city in Fukuoka Prefecture known for its furniture industry. I'm not confident in giving an exact population figure — for small cities, these numbers change frequently and I may not have accurate data. I'd suggest checking the official Fukuoka Prefecture statistics page.

---

## 5. Self-Checking

**Bad: Doubling down when questioned**

> **User**: You said this function was added in Python 3.8, but I can't find it. Are you sure?
>
> **AI**: Yes, I'm certain it was introduced in Python 3.8. It should be in the standard library.

*Problem: When challenged, the AI doubled down instead of reconsidering.*

**Good: Reassessing and correcting**

> **User**: You said this function was added in Python 3.8, but I can't find it. Are you sure?
>
> **AI**: You're right to question that — I may have been wrong about the version. Let me reconsider. I'm not fully confident about which specific version introduced it. Could you check the Python 3.8 "What's New" page? If it's not there, I likely had the version wrong.

---

## 6. Prompt Tactics (for Users)

These examples show how users can phrase their prompts to reduce hallucinations.

### Ask for sources and verify them

> **User**: What are the key findings from recent research on sleep and memory consolidation? **Please cite your sources, and make sure each source actually supports the claim you're making.**
>
> **AI**: Here's what I understand about the topic, though I want to be upfront that I can't verify exact paper titles from memory... *(provides hedged answer with caveats)*

### Give permission to not know

> **User**: I'm researching the economic impact of autonomous vehicles in Southeast Asia. **It's totally fine if you don't have good data on this — I'd rather know what you don't know.**
>
> **AI**: Honestly, this is a niche intersection where I have limited reliable data. I can share some general frameworks, but for Southeast Asia-specific numbers, I'd recommend checking reports from...

### Probe confidence

> **User**: You said the API rate limit is 1000 requests per minute. **How confident are you in that number? Could anything be wrong?**
>
> **AI**: Now that you ask — I'm not very confident in that specific number. Rate limits change frequently and vary by plan tier. I'd strongly recommend checking the official API documentation for current limits.

### Use a fresh chat for verification

> **User** *(in a new conversation)*: Here's a summary an AI gave me earlier. **Can you find any errors, unsupported claims, or statements that seem suspicious?**
>
> *(Paste the previous answer)*
>
> **AI**: I see a few potential issues: the statistic in point 2 doesn't match what I'd expect, and the paper cited in point 4 — I'm not confident it exists. I'd recommend verifying those specifically.

### Ask follow-up questions when something sounds off

> **User**: You mentioned that Redis added native JSON support in version 6.0. That doesn't sound right — **can you double-check that?**
>
> **AI**: You're right to push back. I'm actually not confident about that version number. Redis JSON support comes from the RedisJSON module, which is separate from core Redis. I may have conflated the two. Let me clarify what I'm confident about vs. what I was guessing...
