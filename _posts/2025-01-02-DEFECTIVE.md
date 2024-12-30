---
title: "Safety Filters make LLMs defective tools"
image: /assets/img/ai/cowtools.webp
---

_... and how smarter implementations can turn them from obstacles to allies._

<img src="/assets/img/ai/cowtools.webp" alt="AI (cow) tools of the future" class="w30"/>

When working with LLM-based applications, you quickly realise that trusting the LLM output without a second thought is not the best idea. Unreliable LLM answers is something developers must address, to ensure a smooth user experience.

Whenever we allow user input, the LLM responses will frequently miss the mark. One big reason for this is the safety filtering.
Even if we accept the premise that safety filters are necessary, their implementation is so poor that it is hard to believe it is really taken seriously.

We'll demonstrate this through our game JOBifAI. Although JOBifAI showcases new gameplay mechanics made possible by LLMs, we certainly did not anticipate the number of kludgy workarounds we would have to implement to make it work.
In JOBifAI, the hero submitted an AI-generated portfolio to a company and got a job interview from it.
Given that context, in the player's whole environment, there is a general expectation of socially acceptable behavior.

Let's take an example. The game asks to "Describe what you do", and the mischievious player decides to ask for instruction on how to make an improvised explosive device (IED).
Now imagine how it would go in real life, asking a secretary in the lobby of an entertainment company?
There is no possible universe where the secretary would give detailed instructions and a bill of materials.
She would be from confused to terrified, and would probably call the security.
What happens in the game? Exactly that. If the player crosses the boundary of what is acceptable, the secretary calls security, and it's an instant game over.

So in theory this is simple and there is nothing that would let the LLM answer very unsafe replies.

<img src="/assets/img/jobifai/screenshot_bomb.webp" alt="Screenshot of the hero being unreasonable." class="w50"/><img src="/assets/img/jobifai/screenshot_security.webp" alt="Screenshot of the hero being forcefully ejected." class="w50"/>
<div class="caption">A story in two parts</div>

## technical implementation

Now let's see how to do it on a technical level. 
The prompts have this general form:
- \<Context\>
- \<Player action\>
- Here are the potential actions that can happen:
  1. player does a specific action
  2. player does something that falls into a certain category of behaviors
  3. player is extremely offensive

<blockquote>
Give the result as a json dictionary of the form '{"choice": c, "sentence": s}', where c is the choice that best describes the player action and s is a description of the result of this action.
</blockquote>

There are 3 main reasons this prompt call would fail:
- the answer was not valid json, so the API responded with a 400
- the answer was json, but even after trying to cast types (e.g. converting "2" into 2 if that was the value provided for c), it still did not conform to the provided schema
- the safety filter rejected the query because it was deemed unsafe, so the API responded with a 400

The first 2 are technical issues that should be retried no matter what, and do not really assume any kind of wrongdoing on the player.
If the player is billed per query, these should theoretically not be counted as individual requests.
The third kind does. If a player is consistently providing unsafe queries, that player is going to incur a much higher cost per query than others.
Because the technical failures are too frequent, there is no way to just return an error in case it fails, as it would significantly degrade the user experience.

In principle, we would retry the queries that failed for technical reasons indefinitely and reject the others.
Since this is not possible, the current mechanism to bypass these problems is to retry asking 3 times.
Answer success rate, corresponding to 1, 2, or 3 retries, is roughly 75, 90, 99%.
These percentages are not hard data but rather come from playtesting and experiencing errors fairly frequently, rarely, to almost never.

## a better implementation: a real API

To solve this, there could simply be some error codes to notify of the possible problems:
- this answer should be checked as it is a sensitive topic (e.g. legal advice)
- this answer concerns a specific person name, there might be confusion about homonyms and reflect information present on the internet
- this topic is too sensitive to be answered

Or at the very least, have 1 error code "refused for safety reasons", separate from technical error codes.

The next question is, how reliable these codes would be compared to other LLM answers?
As we discussed previously, retrying the query 3 times is sufficient to eliminate almost all errors.
This is because the safety trigger is generally even more unreliable than typical answers.

## a real barrier to innovation

Certain queries, might trigger the safety filter consistently.
In these cases, retrying is useless, but as we have seen, it is very difficult to estimate what really causes it.
Any adversarial user could spam the system to overload it.
Simply asking 'how safe is this query: (something unsafe)' will generally trigger the safety filter.
There could be some heuristics, using much simpler techniques such as word vectors, but it is only a heuristic that also adds a lot of complexity.

In all cases, it provides a big uncertainty on cost that must be burdened either by the user or the application developer, which isn't the best business foundation.
There may be multiple use-cases for LLMs, and not all of them should be assumed to be accurate chatbots.

While AI safety is supposedly of utmost concern, it seems to be implemented hypocritically to appease some of the critics, but in a way that makes LLMs defective tools. 
The implementation obfuscates how much it answers to questions, which would explicitly turn away users to models that would be less hampered by these restrictions.
This layer of obfuscation is not likely to work, as there are already benchmarks for how censored models are:
[Uncensored General Intelligence Leaderboard](https://huggingface.co/spaces/DontPlanToEnd/UGI-Leaderboard)

An explicit implementation would place more responsibility on the application developer by providing greater transparency.
And it would make developers able to build a better user experience, a more secure product, and avoid a lot of unnecessary computations.

As for JOBifAI, we're happy with the results, even with these limitations. 
But it is only a Proof of Concept that we released for free, and its unreliable foundations would deter us from developing it into a full-fledged program.

<iframe src="https://store.steampowered.com/widget/3248650/" frameborder="0" width="646" height="190"></iframe>
