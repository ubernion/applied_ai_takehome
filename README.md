# Hey!

Thank you for your interest in VZ Labs. To test if you're a right fit for the team, we've designed this small project that you should be able to build at home.

The goal of this project is to create a interactive LLM Radio. Imagine listening to the radio, and being able to *chime in* and interact with the radio host(s), to direct the conversation, to give an opinion, or just to ask for information? 

The end experience should be exactly the same as listening to a radio show, with the exception that you can participate in it (the important nuance here is that you aren't *expected* to partake in the conversation, so it should always flow and keep going without necessitating the user's input). 

The radio show format would be like a news show or talk show - going through the news and then talking about societal events, movies, all that type of stuff. Kind of like a podcast, I guess.

Depending on the level of execution this can be rather tricky to implement! We hence propose different "levels" of completion of the project, the higher the harder.

- **Level 1** - Host and User only
- **Level 2** - Multi-Speakers (Host + Guest(s) + User)
- **Level 3** - Voice (with actual TTS voices for each speaker)

**Constraints:** Our only constraint is that we require you to use OpenRouter API which will allow you (and us!) to easily switch between models and providers.

We provide each participant with an OpenRouter api key with $30 of credits pre-loaded, which should be largely sufficient for the task at hand. 

We propose the following "naive" method to implement the project (this is not a requirement, and there is surely better way to do this).

First, we propose to introduce a **Radio Host** role, which will orchestrate the conversation and distribute talking time between interlocutors.

The **Radio Host** will be able to trigger tools that will:
1. Give one of the interlocutors a "turn" / permission to speak.
2. A max talking time (this can be modeled as a budget of tokens that the **Guest** can spend)

Second, we introduce the generic **Guest** role, which will partake in the discussions, will always generate responses within the token budget assigned by the **Host**, and generate responses at his turn. Guests are other LLM instances with different personas/prompts (can even be different models thanks to OpenRouter!).

Third, we introduce the **User** role, which obviously represents the end user of our little project. The **User** should be able to request permission to speak (just click a button). If denied, the Host just tells them and the show continues.

The token budget works by appending a max_tokens setting in the request that's gonna be the budget itself, which will represent talking time. 


The hand-in can be a webapp, CLI, whatever - any medium works. The conversation should keep going even if the user never participates (it's like a radio show!).
