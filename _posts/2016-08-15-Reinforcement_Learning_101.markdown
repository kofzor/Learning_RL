---
layout: post
title:  "Reinforcement Learning 101"
date:   2016-08-15 20:53:58 +0200
categories: reinforcement-learning machine-learning
---

In this post I like to introduce you to Reinforcement Learning.

## Introduction ##

**Reinforcement Learning** is a field of research on the study of **agents** that can **self-learn** how to behave through feedback, **reinforcement**, from its **environment**. Throughout the years, various environments, or **problems**, have been considered and developed various algorithms that cultivate agents, or **solutions**.

Let's dive a bit deeper into the concepts. Suppose you have a robot on Mars. The robot is the agent and Mars is the environment. It is all alone and sending it instructions take up to several minutes. How are we ever going to maneuver it safely and make the robot succesfull?

<center> <img src="https://upload.wikimedia.org/wikipedia/commons/d/d8/NASA_Mars_Rover.jpg" width="50%"> </center><br/>

Fortunately, before we shipped the robot off to the red planet we supplied it with a **policy**. A policy describes how the agent should behave for different observations, *making decisions on its own*. Mathematically, a policy is a function from 

$$ \pi : \mathbb{O} \to \mathbb{A} , $$

where we denote a policy with $\pi$, $\mathbb{O}$ is the space of possible **observations**, and $\mathbb{A}$ is the space of possible **actions**. More generally, a policy maps the combination of observations and actions to a probability between 0 and 1:

$$ \pi : \mathbb{O} \times \mathbb{A} \to \{0,1\} . $$

In our case, the mars robot observes a rock and has the option of *avoid*, *destroy* or *pick up*, for which it has different probabilities. Suppose we equiped it with an annihilating laser and is destined to clean up Mars, then it chooses *destroy* with, *say*, probability *1*.

## Reinforcement ##

Let's continue our example. Our robot wanders about, destroying rocks as it encounters them. In an ideal world, we have full knowledge of the environment, or rather, we have a **model** of the environment that describes the action's consequences in the environment. Using this model, we can then check every course of action and choose the one to fill in the policy. Unfortunately, it is far more common that we do not have a model of the environment. It might be too costy or impossible to get, or worse our model does not correspond to reality!

For example, our robot had a rough landing and one of its wheels broke off. End of mission? Hopeless? No, this is where **reinforcement learning** steps in. Although the robot lacks a wheel, we can empower it with self-learning capability in the form of a **learning algorithm**. As it tries various combinations of steering and rotating its wheels, it can figure out what makes it move forward. Assuming the robot can sense that it moved, or got closer to some goal, then we can use this **reward signal** as a feedback mechanism to *reinforce* actions that lead to its achievement. Thus, learning a new policy by *exploring* actions.


<!---
Options for reinforce:
- Optimize energy and traction
- a wheel broke off, situation changed

For our robot, let's suppose we did not know that by the time it arrived on Mars that there was some seismic activity, causing new cliffs to appear. Obviously, we do not want our agent to drive into any cliffs.
-->


## Performance ##

In the literature, there is a vast amount of algorithms that enable an agent to learn through reinforcement over its actions. But, which one should one use? Is one of them the *best*? Surely, different algorithms have different requirements as well as objectives. Requirements are, e.g., the amount of memory or computational power available, or the type of environment. Clearly, requirements are closely related to the problem at hand. For example, we can not equip our little mars robot with supercomputer capabilities. They can be seen as a restriction to what you are allowed to use.

**Objectives** describe what we want the agent to achieve in the environment. For example, over the duration of the robot's lifetime, how well has it performed? Did it reach the goal in a timely manner? A non-exhaustive list of objectives are:


- *Online performance*; while learning how well does it perform?
- *Offline performance*; after a prespecified amount of time, what is the quality of its learned policy?
- *Time to level of performance*; how long did it take before it learned a prespecified quality of policy?

Mathematically, the objective takes a form of a *scoring function* :

$$ J : Environment \times Agent \to Score . $$

That is, given an environment and an agent, the scoring function gives a score that corresponds to the agent's performance within the environment. In the literature, a common choice is *Online Regret*: how much worse does it perform compared to an *optimal agent*. Evidently, an agent is optimal when it takes the best action every step of the way in the environment. The downside of Online Regret is that you need to know what is optimal, hence it is usually easier to score the agent on only its behaviour:

$$ score = \sum_{t \leq T} \gamma r_t $$




## Next topics

Modelling problems and solving them

Value Functions

Troubleshooting Reinforcement Learning

