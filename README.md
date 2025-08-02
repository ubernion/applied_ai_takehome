# Hey!

Thank you for your interest in VZ Labs. To test if you're a right fit for the team, we've designed this small project that you should be able to build at home.

The goal of this project is to create a interactive LLM Radio. Imagine listening to the radio, and being able to *chime in* and interact with the radio host(s), to direct the conversation, to give an opinion, or just to ask for information? 

The end experience should be exactly the same as listening to a radio show, with the exception that you can participate in it (the important nuance here is that you aren't *expected* to partake in the conversation, so it should always flow and keep going without necessitating the user's input). 

The radio show format would be like a news show or talk show - going through the news and then talking about societal events or movies, debating etc...

Depending on the level of execution this can be rather tricky to implement! We hence propose different "levels" of completion of the project, the higher the harder. We strongly encourage having a working **text-only** prototype, before implementing the TTS/STT features.

- **Level 1** - Text Only + Host and User only 
- **Level 2** - Handle Multi-Speakers (Host + Guest(s) + User)
- **Level 3** - Include Voice (with actual TTS voices for each speaker)

**Constraints:** Our only constraint is that we require you to use [OpenRouter API](https://openrouter.ai/docs/) which will allow you (and us!) to easily switch between models and providers.

We provide each participant with an OpenRouter api key with $30 of credits pre-loaded, which should be largely sufficient for the task at hand. 

We propose the following "naive" method to implement the project (this is not a requirement, and there is surely better way to do this).

First, we propose to introduce a **Radio Host** role, which will orchestrate the conversation and distribute talking time between interlocutors.

The **Radio Host** will be able to:

1. Give one of the interlocutors a "turn" / permission to speak.
2. Assign to that inerlocutor a max talking time (this can be modeled as a budget of tokens that the **Guest** can spend)

Second, we introduce the generic **Guest** role, which will partake in the discussions, will always generate responses within the token budget assigned by the **Host**, and generate responses at his turn. Guests are other LLM instances with different personas/prompts (can even be different models thanks to OpenRouter!).

Third, we introduce the **User** role, which obviously represents the end user of our little project. The **User** should be able to request permission to speak (just click a button). If denied, the Host just tells them and the show continues.

The token budget works by appending a max_tokens setting in the request that's gonna be the budget itself, which will represent talking time. 


The hand-in can be a webapp, CLI, whatever - any medium works. The conversation should keep going even if the user never participates (it's like a radio show!).

Send submissions to [ilan@vzlabs.ai](mailto:ilan@vzlabs.ai) with a small note on your work. Don't hesitate to open a issue here or to shoot me an email if anything is unclear.

## Example

**Host**: Alright, welcome back to Tech Talk Radio! We're discussing OpenAI's latest moves and, uh, honestly I'm not sure what to make of their new strategy. Sarah, what's your take on this?

**Guest (Sarah)**: Yeah, so like, I think they're trying to balance the whole safety thing with actually shipping products. It's this weird tightrope walk where they want to be responsible but also stay competitive. And honestly? I think they're doing an okay job at it, even if people are critical.

**Host**: That's a fair point. Mike, you've been pretty vocal about the industry lately. What do you think?

**Guest (Mike)**: Thanks for asking! So I actually think both OpenAI and Anthropic are kinda missing the bigger picture here. Everyone's focused on safety and capabilities, but the real bottleneck is compute costs. Like, it doesn't matter how safe or capable your model is if nobody can afford to run it at scale.

**User**: [requests to speak]

**Host**: Oh perfect timing! We have a listener who wants to chime in. Go ahead, you've got the floor!

**User**: I actually work in AI and I think Mike's onto something, but it's not just compute costs. It's also about accessibility. These models are great but they're still too complex for regular developers to integrate properly.

**Host**: That's a really good point! Thanks for sharing that. Sarah, does that connect with what you were saying earlier?

**Guest (Sarah)**: Totally! It's like, we're building these Ferrari engines but most people just need a reliable Honda, you know? 

**Host**: I love that analogy. Speaking of tech in everyday life, did anyone catch that new sci-fi movie "The Algorithm"? It's basically about AGI taking over but... well, Mike, you saw it right?

**Guest (Mike)**: Oh man, don't get me started! Like, they really thought AGI would communicate through interpretive dance? Come on...
