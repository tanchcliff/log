# LLM Training

Overview on the major phases of LLM development, in particular what happens during training.
There are two distinct phases - pretraining and post-training.

## Pretraining 

Pretraining can be understood as 'building the brains'.
This is the most computationally expensive and data intensive phase.
Model is fed trillions of tokens from the internet to get the LLM to be good at next token prediction.
Weights are updated until the model understands grammar, facts and basic reasioning patterns.
At the end of pretraining, we arrive at a base model otherwise known as a foundation model.

# Post-training

Post-training is for everything that happens after the base model is built. 
While dataset used in this phase is smaller than pre-training, quality matters much more.
First, Supervised Fine-Tuning(SFT) is done. High quality prompt response pairs are fed to the model.
Model adapts its behavior according to the Instruction-Following format.
The aim is to show the model how to behave as a helpful assistant.
Second, there is Reinforcement Learning from Human Feedback (RLHF) which is an alignment step moving the model from predicting what a human would say to saying what a human will likely prefer.
Various steps in RLHF:
- Preference Labeling: Humans are shown two different model responses to the same prompt and asked to rank them (e.g., "Response A is more helpful/safer than Response B").
- Reward Model: A separate, smaller model is trained to predict these human preferences. It becomes a "digital judge."
- Optimization: The LLM is then "nudged" (using algorithms like PPO or DPO) to generate outputs that get high scores from this digital judge.
