Hey!

Thank you for your interest in VZ Labs. To test if you're a right fit for the team, we've designed this small project that you should be able to build at home.

The goal of this project is to create a interactive LLM Radio. Imagine listening to the radio, and being able to _chime in_ and interact with the radio host(s), to direct the conversation, to give an opinion, or just to ask for information? 

The end experience should be exactly the same as listening to a radio show, with the exception that you can participate in it (the important nuance here is that you aren't _expected_ to partake in the conversation, so it should always flow and keep going without necessitating the user's input). 

Depending on the level of execution this can be rather tricky to implement! We hence propose different "levels" of completion of the project, the higher the harder.


Level 1 - Text Only

Level 2 - Multi-Speakers

Level 2 - Voice


Constraints: Our only constraint is that we require you to use OpenRouter API[https://openrouter.ai/docs] which will allow you (and us!) to easily switch between models and providers.

We provide each participant with an OpenRouter api key with $30 of credits pre-loaded, which should be largely sufficient for the task at hand. 


We propose the following "naive" method to implement the project (this is not a requirement, and there is surely better way to do this).

First, we propose to introduce a _Radio Host_ role, which will orchestrate the conversation and distribute talking time between interlocutors.

The _Radio Host_ will be able to trigger tools that will 

1. Give one of the interlocutors a "turn" / permission to speak.

2. A max talking time (this can be modeled as a budget of tokens that the _Guest_ can spend)

Second, we introduce the generic _Guest_ role, which will partake in the discussions, will always generate responses within the token budget assigned by the _Host_, and generate responses at his turn.

Third, we introduce the _User_ role, which obviously represents the end user of our little project. The _User_ should be able to request permission to speak.


We expect you to use _streaming_
