---
layout: post
title:      "Hidden Technical Debt in Machine Learning"
date:       2019-03-10 23:16:21 +0000
permalink:  hidden_technical_debt_in_machine_learning
---

I have recently stumbled upon an article that I always knew out there in the wild. An article that delve on technical debt in Data Science / Machine Learning. Why am I so confident about this? This is because I have been accumulating technical debts while working on data science projects. And, because of my software engineering background I know someone out there will try to solve data technical debt through software engineering lens. 

And, indeed I found this wonderful research paper by Google reseachers (ten of them) - Hidden Technical Debt in Machine Learning Systems.


Here's an abstract from the paper itself

*Machine learning offers a fantastically powerful toolkit for building useful complex prediction systems quickly. This paper argues it is dangerous to think of these quick wins as coming for free. Using the software engineering framework of technical debt, we find it is common to incur massive ongoing maintenance costs in real-world ML systems. We explore several ML-specific risk factors to account for in system design. These include boundary erosion, entanglement, hidden feedback loops, undeclared consumers, data dependencies, configuration issues, changes in the external world, and a variety of system-level anti-patterns.*

This is a life saver for me, and it has been sticking right in front of working desk wall.

Here's some key concepts that I would like to share ("re-tweet"). First is the paper argument for the reason of higher likelihood of accumulating technical debt in Machine Learning (or in my case Data Science project).

*#1 The complex models erode boundaries.*
Machine Learning is a mix mesh, therefore it is not easy to enforce strict abstraction boundaries for machine learning systems by prescribing specific intended behavior. Similarly, in my data science project I faced with the challenges of not being able to encapsulate software logic while being fed with data.

*#2 Data dependencies cost more than code dependencies*
The paper stated that it is harder to untangle data depencency, rather code dependencies. In their analysis, code dependencies can be identified via static analysis by compilers and linkers. There is little tooling for data dependencies.

Moreover, what is more revealing in this paper is that Machine Learning code is just a small part of broader Machine Learning system such as:
<br>
1. Configuration of the systems.
<br>
2.  Data collection.
<br>
3. Feature extraction.
<br>
4. Data verification.
<br>
5. Machine Resource Management.
<br>
6. Analysis tools.
<br>
7. Process management tools.
<br>
8. Serving infrastructure.
<br>
9. Monitoring
<br>

*#3 Feedback Loops*
The advantage of a live Machine Learning system becomes its own disadvantage. In another words, its behavior is being modified on its own. According to the paper, this leads to a form of analysis debt, in which it is difficult to predict the behavior of a given model before it is released. These feedback loops can take different forms, but they are all more difficult to detect and address if they occur gradually over time, as may be the case when models are updated infrequently

*#4 ML-System Anti-Patterns*
This paper discussed about code glue (supporting code is written to get data into and out of general-purpose packages), and pipeline jungles (a special case of glue code, pipeline jungles often appear in data preparation), I'd like to delve more into dead experimental codepaths. This is interesting because I start to think I will do this more often because with data science projects I have a lot of freedom of expression without needing to think too much into the surrounding systems. I need to go deeper into this matter. The paper stated that "over time, these accumulated codepaths can create a growing debt due to the increasing difficulties of maintaining backward compatibility
and an exponential increase in cyclomatic complexity. Testing all possible interactions between codepaths becomes difficult or impossible. A famous example of the dangers here was Knight Capital’s system losing $465 million in 45 minutes, apparently because of unexpected behavior from obsolete experimental codepaths." I do not want to end up there. 

*#5 Configuration Debt*
I haven't notice this, and perhaps that's why they stated that "we have observed that both researchers and engineers may treat configuration (and extension of configuration) as an afterthought."

*#6 Dealing with Changes in the External World*
One of the strategy that they proposed is to rely less on human intervention, more on automatic alerts. The rationale behind this is because external changes occur in real-time, response must also occur in real-time as well. 

The paper close off with a few key questions (Note: I am practising this now):
<br>
1. How easily can an entirely new algorithmic approach be tested at full scale?
<br>
2. What is the transitive closure of all data dependencies?
<br>
3. How precisely can the impact of a new change to the system be measured?
<br>
Does improving one model or signal degrade others?
<br>
4. How quickly can new members of the team be brought up to speed?



















