# DG1AID - Week 1 Notes
## Unit 1 - What is AI? Foundations and History
### Aston University - Foundations of AI and Data Science (2025-26)

---

## What is Artificial Intelligence?

There is no single agreed definition of AI. Different organisations define it differently depending on their focus. Here are the key definitions you need to know:

- **IEEE** - systems performing human-like cognitive tasks
- **ACM** - making machines do things that would require intelligence if done by humans
- **EU AI Act** - machine-based systems that generate outputs such as predictions, recommendations or decisions that influence real or virtual environments
- **Stanford HAI** - systems that sense, reason, learn and act
- **Feynman (lecturer's personal definition)** - "What I cannot create I do not understand"

All definitions converge on one idea: systems performing tasks that normally require human-level cognition, without necessarily implying consciousness.

---

## The Four Approaches to AI (Russell and Norvig)

This is one of the most important frameworks in the module. Russell and Norvig identified four ways of defining and building AI, organised by two questions:
- Are we measuring against human performance or rational/ideal performance?
- Are we focused on thought processes or behaviour/actions?

| Approach | Focus | Description | Example |
|---|---|---|---|
| Acting Humanly | Behaviour vs humans | Behave indistinguishably from a human | Passing the Turing Test |
| Thinking Humanly | Thought vs humans | Reason and process information the way humans do | Cognitive modelling, psychology |
| Thinking Rationally | Thought vs ideal logic | Reason correctly using formal logic | Logic-based AI, theorem provers |
| Acting Rationally | Behaviour vs ideal outcome | Do the right thing to achieve goals | Rational agents, modern AI |

Most modern AI falls into the **Acting Rationally** category - systems are designed to achieve goals effectively, not necessarily to mimic human thought processes.

---

## Weak AI vs Strong AI

### Weak AI (Narrow AI)
- Systems that appear intelligent but do not have genuine understanding or consciousness
- Programmed to perform specific, well-defined tasks
- Examples: ChatGPT (language), AlphaGo (chess/go), Face ID (facial recognition), Spotify recommendations
- All AI that exists today is Weak AI
- Can be superhuman at its specific task while being completely incapable outside it

### Strong AI (AGI - Artificial General Intelligence)
- Hypothetical AI with genuine understanding, consciousness and the ability to perform any intellectual task a human can
- Would be able to learn any task, reason across domains and potentially be self-aware
- Does not currently exist
- Timeline is fiercely debated - some say decades away, some say never

---

## The Turing Test (1950)

Alan Turing proposed the **Imitation Game** in his 1950 paper "Computing Machinery and Intelligence." He argued that instead of asking the philosophically impossible question "can machines think?", we should ask a more practical question: can a machine behave so intelligently that a human cannot tell it apart from another human?

**How it works:**
- A human judge communicates via text with two parties - one human, one machine
- If the judge cannot reliably determine which is the human and which is the machine, the machine passes
- The test is deliberately text-only to avoid unfair advantages for humans in physical appearance and voice

**Why it is now considered obsolete:**
- Modern LLMs like ChatGPT and Claude could pass it trivially if permitted to - but they are designed to identify themselves as AI
- Passing only proves the ability to imitate human conversation, not genuine intelligence or understanding
- A system could pass by being a convincing actor without understanding anything
- John Searle's Chinese Room argument proves this directly

**Key quote:** "The question of whether Machines Can Think is about as relevant as the question of whether Submarines Can Swim." - Dijkstra (1984)

This quote captures why the Turing Test fails - it measures the wrong thing. Submarines do not swim but they move through water effectively. AI does not think in the human sense but it processes information effectively.

---

## Alternative Tests to the Turing Test

| Test | What it measures | How it works | Key weakness |
|---|---|---|---|
| Winograd Schema | Common-sense reasoning | Disambiguating sentences that require real-world knowledge | Can be gamed with large enough training data |
| Lovelace Test | Genuine creativity | Must produce something its creators cannot explain how it created | Hard to objectively define genuine creativity |
| Coffee Test | Embodied intelligence | Go into an unfamiliar house and make a coffee | Tests physical robotics as much as intelligence |
| Robot College Student | General intelligence | Complete a university degree | Extremely broad and hard to evaluate consistently |
| Mirror Test | Self-awareness | Recognise itself in a mirror | Originally designed for animals, not AI |

---

## Searle's Chinese Room (1980)

John Searle's thought experiment is one of the most important arguments against Strong AI.

**The experiment:** Imagine a person sitting in a room with a rulebook for Chinese symbols and two slots - one for incoming messages and one for outgoing responses. They receive Chinese symbols, manipulate them according to the rules and output Chinese symbols. To anyone outside, this looks like fluent Chinese conversation. But the person inside understands nothing - they are just following rules.

**The argument:** Large language models are doing exactly this. They manipulate symbols (words and tokens) according to learned rules (weights and probabilities) without genuinely understanding any of it. Passing a language test does not prove understanding.

**Conclusion:** Symbol manipulation is not the same as understanding. Strong AI is impossible under this view.

---

## The Mind-Body Problem

How do physical brain states (neurons firing) produce mental states (consciousness, understanding, emotion)? This is one of the oldest unsolved problems in philosophy.

For AI, this raises critical questions:
- Could a machine made of silicon and electricity ever have genuine mental states?
- Is consciousness tied to biological matter specifically?
- Does intelligence require a body situated in an environment (embodied cognition)?

**Embodied cognition** - the theory that intelligence cannot be separated from having a physical body that interacts with the environment. A mind that only processes text may be fundamentally limited compared to one that has physical experience of the world.

---

## Brief History of AI

### The Theoretical Foundations (1936-1956)

**1936 - Alan Turing publishes "On Computable Numbers"**
Established the theoretical basis for all modern computation. Introduced the concept of the Turing Machine - a theoretical device that could follow any sequence of instructions to solve any mathematical problem. Every computer ever built is essentially a physical implementation of this theoretical model.

**1943 - McCulloch and Pitts propose Artificial Neural Networks**
Looked at how biological neurons work and created the first mathematical model. A neuron receives inputs, applies weights, and fires an output if a threshold is exceeded. This idea underpins every neural network ever built.

**1943 - Donald Hebb proposes Hebbian Learning**
"Neurons that fire together wire together." If two neurons consistently activate at the same time, the connection between them strengthens. This is how the brain learns and is still the conceptual basis of modern neural network training.

**1950 - Turing proposes the Turing Test**
"Computing Machinery and Intelligence" - defines the goal of AI as human-like behaviour and makes a bold prediction that machines would pass his test by the year 2000.

**1952 - Arthur Samuel creates checkers program**
The first ever machine learning program. It did not just play checkers - it improved its own play by learning from experience. Proof that machines could learn without being explicitly programmed for every situation.

**1956 - Dartmouth Conference - "Artificial Intelligence" coined**
John McCarthy, Marvin Minsky and others held a conference at Dartmouth College. They coined the term "Artificial Intelligence" and established it as a formal field of study. This is considered the official birthday of AI.

**1958 - Frank Rosenblatt invents the Perceptron**
The first physical hardware that could learn. Based on McCulloch and Pitts' artificial neuron. Could be trained on examples to classify patterns. But it was too simple - could only solve linearly separable problems.

### The Rise and Fall (1960s-1990s)

**1960 - ELIZA built by Weizenbaum at MIT**
The first chatbot. Simulated a therapy session by reflecting questions back at users using simple pattern matching. People genuinely believed it understood them - it did not. It was entirely rule-based. Showed that making machines appear human was easier than making them intelligent.

**1965 - Newell and Simon's Logic Theorist**
Could prove mathematical theorems faster than humans. First AI system to solve problems previously only solvable by humans.

**1966 - Shakey the Robot at MIT**
First mobile robot with planning capability. Could perceive its environment, reason about it and take action. Integrated perception, reasoning and action for the first time.

**1969 - Minsky and Papert publish "Perceptrons"**
Mathematically proved that single-layer perceptrons could not solve many classes of problems (specifically non-linearly separable problems like XOR). This was devastating for neural network research. Funding dried up. The First AI Winter began.

**1970s - MYCIN developed**
Expert system that could diagnose bacterial infections better than junior doctors. First commercially successful AI. Used hundreds of hand-coded if-then rules encoding expert medical knowledge.

**1973 - Lighthill Report published in UK**
Claimed AI had made no progress on real-world problems. Led to UK government cutting AI research funding significantly.

**1980 - XCON developed**
Expert system for automatically configuring computer systems for DEC. Saved the company $25 million per year. Triggered massive commercial interest in expert systems.

**1987 - DARPA cuts AI research funding**
XCON's success led to massive overhyping of expert systems. When they failed to scale beyond narrow domains, confidence collapsed. The Second AI Winter began.

**Key insight:** The winters were NOT intellectually stagnant. Critical ideas were developed during this cold period that would later change everything.

### Seeds of the Modern Era (1980s-1990s)

**1985 - Bayesian Networks coined by Pearl**
Introduced formal reasoning under uncertainty. Instead of rigid rules, could say "if X then Y with 80% probability." Foundation of probabilistic AI.

**1986 - Backpropagation developed by Rumelhart, Hinton and Williams**
The single most important algorithm in modern AI. Made it possible to efficiently train multi-layer neural networks by propagating errors backwards through the network and adjusting weights. Without this, deep learning would be impossible.

**1989 - Q-Learning developed by Watkins**
Enabled machines to learn from delayed rewards - learning what to do in situations without being told the answer, just by receiving rewards or punishments for outcomes. Foundation of modern Reinforcement Learning.

**1989 - Hidden Markov Models introduced by Rabiner**
Statistical models for systems with hidden states. Essential for speech recognition and later for sequence modelling in NLP.

### The Return (1997-2012)

**1997 - IBM's Deep Blue beats Garry Kasparov**
Headline news worldwide. Deep Blue was not truly intelligent - it brute-forced billions of possible chess moves per second. But it proved machines could outperform humans at tasks considered to require high intelligence. The Second AI Winter ended.

**1998 - LeNet-5 created by LeCun**
First successful Convolutional Neural Network (CNN). Could recognise handwritten digits with remarkable accuracy. Laid the groundwork for modern computer vision.

**2001 - ImageNet project launched**
Project to create a massive labelled image dataset - eventually 1.2 million images across 1000 categories. Without this dataset, the 2012 deep learning revolution would not have happened.

**2003 - Bengio publishes Neural Probabilistic Language Model**
First successful deep learning network for natural language processing.

**2004 - NVIDIA releases the GeForce 6800 GPU**
Researchers realised that GPUs - originally designed for video games - could be used to train neural networks dramatically faster than CPUs. This hardware breakthrough enabled everything that followed.

### The Deep Learning Revolution (2006-present)

**2006 - Hinton publishes "A Fast Learning Algorithm for Deep Belief Nets"**
Solved the vanishing gradient problem that had prevented training very deep networks. Made networks with 10+ layers practical.

**2011 - IBM's Watson wins Jeopardy**
Retrieved facts from 200 million documents to generate responses to unstructured natural language questions. Demonstrated AI's ability to work with ambiguous, real-world language at scale.

**2012 - AlexNet wins ImageNet competition**
Achieved 84% accuracy on image classification, destroying the competition. Catalysed the deep learning boom. Proved that deep neural networks trained on GPUs could solve real vision problems at superhuman level.

**2013 - Google Translate switches to neural networks**
Replaced 20+ years of hand-coded rule-based translation with a neural network overnight. Quality jumped dramatically.

**2014 - GANs (Generative Adversarial Networks) invented by Goodfellow**
First system to produce photorealistic images without hand-crafted rules. A generator network creates fake images and a discriminator network judges whether they are real. They compete - the generator gets better at fooling the discriminator.

**2017 - Vaswani introduces the Transformer Architecture**
"Attention is All You Need." A fundamentally new approach to neural networks that could process all tokens in parallel (not sequentially), understand long-range context and scale efficiently with more data and compute. Every modern LLM is built on this architecture.

**2018 - GPT-1 released by OpenAI**
117 million parameters. First large language model based on the Transformer.

**2022 - ChatGPT released**
100 million users in 2 months - fastest growing product in history. AI moved from research tool to daily utility for billions of people.

**2022 - Stable Diffusion and DALL-E**
AI image generation democratised. Anyone could generate photorealistic images from text descriptions.

**2024 - EU AI Act enters into force**
World's first legally binding AI-specific legislation.

---

## AI Paradigm Shifts Summary

| Era | Paradigm | Core Idea | Why it changed |
|---|---|---|---|
| 1940s-50s | Connectionism | Neural networks as biological inspiration | Limited compute power |
| 1950s-80s | Symbolic AI | Rules and logic (symbols and inference) | Could not handle ambiguity or real-world messiness |
| 1980s-90s | Statistical AI | Probability and data (no hand-coded rules) | Required manual feature engineering |
| 1990s-2000s | Computational Intelligence | Fuzzy logic, evolutionary algorithms, hybrid | Never dominated the field |
| 2000s | Deep Learning Foundation | Neural nets + GPUs + big data | Compute and data finally sufficient |
| 2010s | Deep Learning Dominance | Transformer architecture, context-aware | Replaced all previous approaches for language and vision |
| 2020s | AI as Infrastructure | Democratised, open models, zero-shot | Daily utility for billions of non-technical users |

---

## Modern AI Applications

### Language and Interaction
- **LLMs** - ChatGPT, Claude, Gemini, Grok. Generate and reason with text.
- **Chatbots and Assistants** - Siri, Alexa, Google Assistant
- **Speech Recognition and Synthesis** - voice input and output, voice cloning

### Perception
- **Computer Vision** - Face ID, medical imaging, self-checkout cameras, speed cameras
- **Generative AI** - DALL-E, Stable Diffusion, Midjourney. Visit thispersondoesnotexist.com - every face is AI-generated.

### Prediction and Personalisation
- **Recommendation Systems** - Netflix (70% of watch time driven by recommendations), Spotify, Amazon
- **Machine Translation** - DeepL, Google Translate. In 2013 Google switched from 20 years of rules to a neural network overnight.
- **Forecasting** - demand prediction, logistics, financial risk

### Autonomy and Security
- **Autonomous Systems** - Tesla self-driving, Waymo, Amazon warehouse robots (750,000+)
- **Fraud Detection** - real-time anomaly detection in financial transactions
- **Search** - Google Search ranks billions of pages using AI

### Applied Science
- **AlphaFold** (DeepMind/Google) - solved the protein folding problem in 2020. Biggest scientific breakthrough in decades. Protein structure determines drug function.
- **GraphCast** (Google) - AI weather forecasting that outperforms traditional models
- **AlphaTensor** (DeepMind) - discovered faster algorithms for matrix multiplication

---

## How AI Models Work

### What is a Model?
A model is a mathematical function that takes an input and produces an output. Neural network models have billions of **parameters** (also called weights) - numbers that have been tuned through training to produce useful outputs.

### Training Process
1. Feed the model enormous amounts of training data
2. The model makes predictions (for LLMs: predict the next word)
3. Calculate how wrong the prediction was (the loss)
4. Use backpropagation to adjust all weights slightly in the right direction
5. Repeat billions of times
6. The model learns by compressing patterns from the data into its weights

**Key insight:** In learning to predict text, the model is forced to learn about the world. To predict what comes after "The capital of France is", it must learn geography.

### Hardware
- **CPU (Central Processing Unit)** - general purpose chip, 8-16 cores, good at sequential tasks
- **GPU (Graphics Processing Unit)** - originally for games, thousands of cores working simultaneously, ideal for the parallel matrix maths of neural networks
- **TPU (Tensor Processing Unit)** - Google's chips designed specifically for neural network maths. Even more efficient than GPUs for AI specifically.

Training GPT-3 required thousands of GPUs running for months and used enough electricity to power 120 US homes for a year.

### When You Ask Claude a Question
1. Your text is broken into **tokens** (roughly 4 characters each)
2. Each token is converted to a vector of numbers (embedding)
3. Vectors pass through dozens of transformer layers - the "thinking"
4. The model outputs a probability distribution over all possible next tokens
5. A token is selected and added to the response
6. This repeats token by token until the response is complete

**There is no database being searched.** All knowledge is compressed into the model's weights during training. This is why models have a knowledge cutoff date.

---

## Limitations of AI

- **Limited Reasoning and Generalisation** - excels at trained tasks, struggles outside them
- **Lack of True Understanding** - processes patterns, does not understand meaning (Searle's Chinese Room)
- **Brittleness** - can fail unexpectedly when conditions change slightly
- **Explainability** - most modern AI is a black box - cannot explain its own decisions
- **Alignment and Control** - ensuring AI does what you actually want is an unsolved problem
- **No Goals or Intentions** - AI has no awareness, desires or motivations of its own

### AI Myths vs Reality

| Myth | Reality |
|---|---|
| AI understands language like humans | AI detects patterns, does not understand meaning |
| AI is objective and unbiased | AI reflects biases in its training data |
| AI can reason generally | Excels at narrow tasks but struggles with general reasoning |
| AI systems are reliable and robust | Can fail unexpectedly outside familiar conditions |
| Bigger models automatically mean better intelligence | Architecture, data and training matter as much as scale |
| AI is autonomous and self-directed | AI has no goals, intentions or awareness |
| AI will soon replace all human jobs | AI changes jobs more than it replaces them |

---

## AGI Definitions

| Source | Definition |
|---|---|
| Goertzel (2023) | Capacity not task-specific, generalises across qualitatively different contexts, flexibly interprets tasks |
| Weinbaum and Veitas (2017) | Distils principles of intelligence independent of problem domain, performs any intellectual task a human can |
| Legg and Hutter (2007) | Intelligence measures an agent's ability to achieve goals in a wide range of environments |
| Goertzel (2012) | Ability to achieve complex goals in complex environments |

**Key criticisms of AGI definitions:**
- Human-centric - define intelligence as "doing what humans do"
- Recency bias - based on current understanding
- Ignore evolution - do not account for how intelligence develops
- Focus on goal achievement rather than the process of becoming intelligent

---

## Key Terms to Know

| Term | Definition |
|---|---|
| Artificial Intelligence | Systems performing tasks that normally require human-level cognition |
| Weak AI / Narrow AI | AI that performs specific tasks without genuine understanding |
| Strong AI / AGI | Hypothetical AI with genuine understanding across all domains |
| Neural Network | Mathematical model inspired by biological neurons |
| Machine Learning | AI that learns from data rather than following hand-coded rules |
| Deep Learning | Machine learning using multi-layer neural networks |
| LLM | Large Language Model - trained on massive text data |
| Backpropagation | Algorithm for training neural networks by adjusting weights |
| Transformer | Architecture that powers all modern LLMs |
| Parameter / Weight | Numbers inside a model that encode its knowledge |
| Token | Chunk of text (roughly 4 characters) that models process |
| GPU | Graphics Processing Unit - ideal for parallel neural network maths |
| Training | The process of adjusting model weights using data |
| Inference | Running a trained model to generate output |
