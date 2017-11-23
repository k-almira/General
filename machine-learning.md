 # Machine Learning

## OCDevel Podcast:
* [Machine Learning 101](http://www.learningmachines101.com/)
 
Two definitions of Machine Learning are offered.  
 * Arthur Samuel described it as: "the field of study that gives computers the ability to learn without being explicitly programmed." This is an older, informal definition.

 * Tom Mitchell provides a more modern definition: "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

* Example: playing checkers.

   E = the experience of playing many games of checkers
   T = the task of playing checkers.
   P = the probability that the program will win the next game.

* In general, any machine learning problem can be assigned to one of two broad classifications:
Supervised learning and Unsupervised learning.
 
There are 3 steps in machine learning.
 1. infer / predict
 2. error / loss
 3. train / learn

***Data Set*** consists of:
* 70% Train
* 30% Predict

***algorithm***:
* Python or TensorFlow
* 3 types:
 1. ***supervised learning***
   -teach the computer to learn
   -linear regression
   -statistical regression
   -classification
 2. ***unsupervised learning***
   -it will learn on its own
   -not clear cut associations
 3. ***reinforcement learning***
   -AI (Deep Q Networks, Data Mining, Apps that cannot be coded, self-customizing programs, to understand human learning/brain)
   -reinforcement / punshiment
***pattern***

***model*** = ***algorithm*** + ***pattern***

# Podcasts:
* [TWiML and AI](https://twimlai.com/)
* [O'Reilly Data Show](https://www.oreilly.com/topics/oreilly-data-show-podcast)
* [Talking machines](http://www.thetalkingmachines.com/)
* [Linear Digressions](http://lineardigressions.com/)
* [Data Skeptic](https://dataskeptic.com/)
* [Partially Derivative](http://partiallyderivative.com/)

# Audiobooks:
* [The Singularity Is Near: When Humans Transcend Biology](https://www.amazon.com/Singularity-Near-Humans-Transcend-Biology/dp/B004ZF18PW/ref=as_li_ss_tl?_encoding=UTF8&me=&linkCode=sl1&tag=ha0d2-20&linkId=9d852e3d5f8b6f2d6cc88127c4c173e3)
* [Philosophy of Mind: Brains, Consciousness, and Thinking Machines](https://www.amazon.com/Philosophy-Mind-Consciousness-Thinking-Machines/dp/B00DTO5LQC/ref=as_li_ss_tl?ie=UTF8&qid=1487117614&sr=8-1&keywords=Philosophy+of+Mind:+Brains,+Consciousness,+and+Thinking+Machines&linkCode=sl1&tag=ha0d2-20&linkId=d7c1b4629401ed22a155817410495b4e)
* [Superintelligence: Paths, Dangers, Strategies](https://www.amazon.com/dp/B00LPMFE9Y/ref=as_li_ss_tl?ie=UTF8&linkCode=sl1&tag=ha0d2-20&linkId=31e656f5a68ca4c9232c3757aaafb79c)

# Courses:
* [Andrew Ng's Machine Learning Coursera course](https://www.coursera.org/learn/machine-learning/lecture/zcAuT/welcome-to-machine-learning)

# History:

* Greek mythology, Golums
* First attempt: Ramon Lull, 13th century
* Davinci's walking animals
* Descartes, Leibniz
* 1700s-1800s: Statistics & Mathematical decision making
  * Thomas Bayes: reasoning about the probability of events
  * George Boole: logical reasoning / binary algebra
  * Gottlob Frege: Propositional logic
* 1832: Charles Babbage & Ada Byron / Lovelace: designed Analytical Engine (1832), programmable mechanical calculating machines
* 1936: Universal Turing Machine
  * Computing Machinery and Intelligence - explored AI!
* 1946: John von Neumann Universal Computing Machine
* 1943: Warren McCulloch & Walter Pitts: cogsci rep of neuron; Frank Rosemblatt uses to create Perceptron (-> neural networks by way of MLP)
* 50s-70s: "AI" coined @Dartmouth workshop 1956 - goal to simulate all aspects of intelligence. John McCarthy, Marvin Minksy, Arthur Samuel, Oliver Selfridge, Ray Solomonoff, Allen Newell, Herbert Simon
  * Newell & Simon: Hueristics -> Logic Theories, General Problem Solver
  * Slefridge: Computer Vision
  * NLP
  * Stanford Research Institute: Shakey
  * Feigenbaum: Expert systems
  * GOFAI / symbolism: operations research / management science; logic-based; knowledge-based / expert systems
* 70s: Lighthill report (James Lighthill), big promises -> AI Winter
* 90s: Data, Computation, Practical Application -> AI back (90s)
  * Connectionism optimizations: Geoffrey Hinton: 2006, optimized back propagation
* Bloomberg, 2015 was whopper for AI in industry
* AlphaGo & DeepMind

 
## Coursera: ML Course by Andrew Ng: 
### Supervised Learning

In supervised learning, we are given a data set and already know what our correct output should look like, having the idea that there is a relationship between the input and the output.

Supervised learning problems are categorized into "regression" and "classification" problems. In a regression problem, we are trying to predict results within a continuous output, meaning that we are trying to map input variables to some continuous function. In a classification problem, we are instead trying to predict results in a discrete output. In other words, we are trying to map input variables into discrete categories.

Example 1:

Given data about the size of houses on the real estate market, try to predict their price. Price as a function of size is a continuous output, so this is a regression problem.

We could turn this example into a classification problem by instead making our output about whether the house "sells for more or less than the asking price." Here we are classifying the houses based on price into two discrete categories.

Example 2:

(a) Regression - Given a picture of a person, we have to predict their age on the basis of the given picture

(b) Classification - Given a patient with a tumor, we have to predict whether the tumor is malignant or benign.
 
### Unsupervised Learning

Unsupervised learning allows us to approach problems with little or no idea what our results should look like. We can derive structure from data where we don't necessarily know the effect of the variables.
We can derive this structure by clustering the data based on relationships among the variables in the data.
With unsupervised learning there is no feedback based on the prediction results.

Example:

Clustering: Take a collection of 1,000,000 different genes, and find a way to automatically group these genes into groups that are somehow similar or related by different variables, such as lifespan, location, roles, and so on.

Non-clustering: The "Cocktail Party Algorithm", allows you to find structure in a chaotic environment. (i.e. identifying individual voices and music from a mesh of sounds at a cocktail party).
 
### Model Representation

To establish notation for future use, we’ll use x(i) to denote the “input” variables (living area in this example), also called input features, and y(i) to denote the “output” or target variable that we are trying to predict (price). A pair (x(i),y(i)) is called a training example, and the dataset that we’ll be using to learn—a list of m training examples (x(i),y(i));i=1,...,m—is called a training set. Note that the superscript “(i)” in the notation is simply an index into the training set, and has nothing to do with exponentiation. We will also use X to denote the space of input values, and Y to denote the space of output values. In this example, X = Y = ℝ.

To describe the supervised learning problem slightly more formally, our goal is, given a training set, to learn a function h : X → Y so that h(x) is a “good” predictor for the corresponding value of y. For historical reasons, this function h is called a hypothesis. Seen pictorially, the process is therefore like this:


When the target variable that we’re trying to predict is continuous, such as in our housing example, we call the learning problem a regression problem. When y can take on only a small number of discrete values (such as if, given the living area, we wanted to predict if a dwelling is a house or an apartment, say), we call it a classification problem.
 
 
 
 
 
 
