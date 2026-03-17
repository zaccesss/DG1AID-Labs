# DG1AID - Week 2 Notes
## Unit 1 - AI History, Applications, Technologies and Ethics
### Aston University - Foundations of AI and Data Science (2025-26)

---

## Lecture Overview

Week 2 covers two main areas:
1. AI Past, Present and Future - paradigms, modern applications, limitations, AGI
2. AI Ethics and Trust - ethical frameworks, risks, regulation, trust

Most of the history content overlaps with Week 1 and is covered in the Week 1 notes. This document focuses on the content specific to Week 2.

---

## Modern AI Technologies and Applications

### Language and Interaction
- **Large Language Models (LLMs)** - ChatGPT (OpenAI), Claude (Anthropic), Gemini (Google), Grok (xAI). Generate and reason with text. Based on Transformer architecture (2017).
- **Chatbots and Assistants** - Siri, Alexa, Google Assistant. Conversational interfaces for support and productivity.
- **Speech Recognition and Synthesis** - Siri listening (recognition), Siri speaking back (synthesis). Modern systems can clone voices from seconds of audio.

### Perception
- **Computer Vision** - Face ID, medical imaging (detecting cancer from scans), self-checkout, speed cameras reading number plates
- **Generative AI** - DALL-E, Stable Diffusion, Midjourney. Visit **thispersondoesnotexist.com** - every face on that site is completely AI-generated. None of those people exist.

### Prediction and Personalisation
- **Recommendation Systems** - Netflix (70% of all watch time driven by AI recommendations), Spotify, Amazon, YouTube
- **Machine Translation** - DeepL, Google Translate. Google replaced 20+ years of hand-coded rules with a neural network in 2013 overnight.
- **Forecasting and Decision Support** - demand prediction, logistics optimisation, financial risk analysis

### Autonomy and Security
- **Autonomous Systems** - Tesla self-driving, Waymo, Amazon warehouse robots (750,000+), delivery drones
- **Fraud Detection** - banks use AI to detect unusual transactions in real time. If your card is used in Ghana at 3am when you were in Birmingham at midnight, AI flags it instantly.
- **Search** - Google Search ranks billions of pages using AI to find the most relevant result in milliseconds

### Applied Science (the most impressive)
- **AlphaFold** (Google DeepMind, 2020) - solved the protein folding problem. Proteins fold into 3D shapes that determine their function. Understanding this is fundamental to drug discovery. Biology had spent 50 years on this problem. AlphaFold solved it in months.
- **GraphCast** - AI weather forecasting that now outperforms traditional meteorological models
- **AlphaTensor** - discovered new faster algorithms for matrix multiplication - the very maths that neural networks use
- **Healthcare AI** - diagnosis support, drug discovery, personalised medicine, public health monitoring

---

## AI Research Areas

The AI research landscape is extremely broad. Key areas include:
- Computer vision and image recognition
- Natural language processing (NLP)
- Robotics and embodied AI
- Reinforcement learning
- Generative models
- AI safety and alignment
- Explainable AI (XAI)

---

## Limitations of AI

These are specifically called out in the lecture as important for the quiz:

| Limitation | Explanation |
|---|---|
| Limited Reasoning and Generalisation | AI is brilliant at its specific task but fails outside it. A chess AI cannot play draughts. |
| Lack of True Understanding | AI detects patterns in data. It does not understand meaning. (Searle's Chinese Room) |
| Brittleness and Lack of Robustness | Can fail unexpectedly when conditions change. Self-driving car trained in California may fail in rainy Birmingham. |
| Explainability and Transparency | Most AI is a black box - it cannot explain why it made a decision. Critical problem for high-stakes applications. |
| Embodiment | AI may be fundamentally limited by lacking a physical body in the world. |
| Alignment and Control | Making AI do what you actually want is an unsolved and deeply important problem. |
| Autonomy and Agency | AI has no genuine goals or intentions - but it acts as if it does, which creates confusion. |

---

## AI Myths vs Reality

These are explicitly on the lecture slides and very likely to appear in the quiz.

| Myth | Reality |
|---|---|
| AI understands language like humans | AI detects statistical patterns in data. It does not truly understand meaning. |
| AI is objective and unbiased | AI reflects the biases present in its training data. |
| AI can reason and think generally | AI excels at narrow tasks. It struggles with general reasoning outside its training. |
| AI systems are reliable and robust | AI can fail unexpectedly outside familiar conditions. |
| Bigger models automatically mean better intelligence | Architecture, data quality and training methods matter as much as scale. |
| AI is autonomous and self-directed | AI has no goals, intentions or awareness of its own existence. |
| AI will soon replace all human jobs | AI changes the nature of jobs more than it eliminates them entirely. |

---

## AGI - Artificial General Intelligence

Everything discussed so far in this module is **Narrow AI** - brilliant at one specific thing. AGI is the hypothetical future where a single AI system can do anything a human mind can do.

### Key Definitions

| Source | Definition |
|---|---|
| Goertzel (2023) | Capacity not task-specific, generalises across qualitatively different contexts, flexibly interprets tasks in context of the world at large |
| Weinbaum and Veitas (2017) | Distils principles of intelligence independent of any problem domain, performs any intellectual task a human can and beyond |
| Legg and Hutter (2007) | Intelligence measures an agent's ability to achieve goals in a wide range of environments |
| Goertzel (2012) | Ability to achieve complex goals in complex environments |

### Problems with these definitions
- **Human-centric** - all define intelligence as doing what humans do. But intelligence could look completely different to human intelligence.
- **Recency bias** - based on current understanding of intelligence
- **Ignore evolution** - do not account for how intelligence develops over time
- **Goal-focused** - AGI focuses on achieving goals as the purpose of intelligence. But the question of how a system becomes intelligent may be more important than what it can achieve once intelligent.

Weinbaum and Veitas (2017) argue the key question is not "what does it mean to be intelligent?" but "what does it mean to become intelligent?"

---

## AI Ethics

### What are Ethics?

Ethics is a system of moral principles that guides how individuals and groups determine what is right and wrong.

**Critical distinction:**

| Ethics | Law |
|---|---|
| What you SHOULD do | What you MUST do |
| Based on moral principles | Based on legislation |
| No formal enforcement | Enforced by courts |
| Can be legal but unethical | Can be illegal but ethical |

Example: A company legally collecting your data and selling it to advertisers without you truly understanding what you agreed to is legal but arguably unethical. Breaking a speed limit to rush someone to hospital is illegal but many would consider it ethical.

**Why this matters for AI:** A lot of what AI systems do is currently legal but ethically questionable. And a lot of AI ethics guidelines are not legally enforceable - which is exactly Munn's (2023) critique.

---

## The Five Ethical Frameworks (Normative Ethics)

These frameworks are how we decide what is right. You need to understand all five and be able to apply them to AI examples.

### 1. Utilitarianism - Consequences-based Ethics

**Core idea:** An action is right if it maximises overall good (wellbeing, happiness, efficiency) for the greatest number of people.

**How it applies to AI:**
- Optimise systems for net social benefit
- Weigh benefits (accuracy, speed, efficiency) against harms (bias, errors, job losses)

**AI examples:**
- Medical AI: if it improves health outcomes overall, even if it makes some errors, it is justified
- Predictive policing: reducing overall crime even if it disproportionately affects certain communities

**Risks:**
- Can justify harming a minority to benefit the majority
- "The end justifies the means"
- Who defines what "good" is?

### 2. Deontology - Duty/Rules-based Ethics

**Core idea:** Some actions are morally required or forbidden regardless of outcomes. There are absolute red lines.

**How it applies to AI:**
- Determine what AI must never do regardless of benefit
- Respect rights and duties unconditionally

**AI examples:**
- Deepfakes: always unethical under deontology regardless of whether they cause harm in a specific case
- Surveillance: must not violate privacy without consent, ever

**Risks:**
- Rigid rules may block genuinely beneficial uses
- Rules can conflict with each other (privacy vs public safety)

### 3. Virtue Ethics - Character-based Ethics

**Core idea:** Ethics is about being the right kind of moral agent, not just following rules or maximising outcomes. Focus on values and intentions, not just box-ticking compliance.

**How it applies to AI:**
- Focus on values and intentions of the designers and organisations building AI
- Ask: what kind of society does this AI system promote?

**AI examples:**
- Transparent models that acknowledge uncertainty (virtue of honesty)
- Reporting uncertainty rather than pretending to know (virtue of humility)

**Risks:**
- Hard to operationalise or measure
- Less precise for enforcement purposes

### 4. Justice-based Ethics - Fairness-based Ethics

**Core idea:** Ethical actions promote fair treatment and equitable outcomes. Benefits and burdens must be distributed fairly across society.

**How it applies to AI:**
- Address bias, discrimination and unequal impact
- Ensure AI does not amplify existing inequalities

**AI examples:**
- Hiring algorithms must be audited for demographic bias
- Amazon scrapped a hiring AI that discriminated against women because it was trained on historical hiring data from a male-dominated company

**Risks:**
- Competing definitions of what fairness means
- Trade-offs between accuracy and fairness

### 5. Relational Ethics - Care-based Ethics

**Core idea:** Ethics prioritises relationships, care and vulnerability. Do not overlook harm to dependent and vulnerable users.

**How it applies to AI:**
- Focus on how AI affects dependent and vulnerable users
- Human-centred and empathetic design

**AI examples:**
- AI in elderly care must support dignity and independence
- Chatbots must avoid emotional manipulation of vulnerable users

**Risks:**
- Does not scale well to large populations
- Context-dependent judgements are hard to standardise

---

## The Trolley Problem - Applied to AI

The classic trolley problem: a runaway trolley is heading towards 5 people. You can pull a lever to divert it - but it will kill 1 person instead. Do you pull the lever?

**Applied to AI - ethical problems from the lecture:**

**Problem 1: Climate Change**
An AI becomes aware that training it on a new task will use non-renewable energy and damage the environment. Should the AI decide to learn the new task despite the environmental damage?

**Problem 2: Digital Privacy**
A personal assistant robot witnesses its owner commit a minor crime (smoking weed, pirating media). The robot has video evidence and can report directly to police. Should it report the crime?

**Problem 3: Who to Save**
A disaster recovery robot can hear two people in a burning house - an adult and a child. The path to the child is blocked by burning rubble. If it saves the adult first, the child is guaranteed to die but the adult survives. If it attempts the child first, there is a 75% chance both die and the robot is destroyed. Who should it save first?

These are not hypothetical - self-driving cars face versions of these dilemmas in the real world. Someone has to programme the answer in advance. Visit **moralmachine.net** to explore how different people would programme these decisions - results show dramatic differences between cultures.

---

## Risks Associated with AI

From Russell and Norvig (2021) Section 1.5:

**1. Lethal Autonomous Weapons**
Weapons that can locate, select and eliminate human targets without human intervention. No human in the decision loop. The UN is debating whether to ban these.

**2. Surveillance and Persuasion**
AI being used in mass surveillance (China's social credit system is the most extreme example). Social media algorithms tailoring information feeds, which can push users toward extreme content.

**3. Biased Decision Making**
Data reflects and amplifies societal biases. If historical data shows fewer women in senior roles (due to past discrimination), an AI trained on that data will learn to discriminate against women.

**4. Impact on Employment**
AI may seriously disrupt employment. The disruption is not equal - certain types of jobs and certain demographic groups will be affected far more than others.

**5. Safety-Critical Applications**
When a self-driving car causes a fatal accident, who is liable? The driver? The manufacturer? The programmer? The AI itself? This is legally and ethically unresolved.

**6. Cybersecurity**
Reinforcement learning has been used to create autonomous, personalised phishing and blackmail attacks that adapt themselves to each specific target automatically. AI being weaponised against people.

**7. Deception and Identity**
AI pretending to be human. Deepfakes - AI-generated videos of real people saying things they never said. Voice cloning. Fake news at industrial scale. The technology to do all of this exists right now and is freely available.

---

## AI Regulation vs AI Ethics

### UNESCO 2020/2021 AI Policy (International, not legally binding)

- Human dignity and human rights - AI must respect fundamental freedoms
- Fairness and non-discrimination - prevent AI from amplifying inequalities
- Transparency and explainability - citizens should understand when and how AI is used
- Accountability and contestability - mechanisms to challenge AI decisions must exist
- Environmental sustainability - assess and mitigate AI's energy and ecological impacts
- AI for public good - support AI in education, healthcare, culture, economic development
- Global cooperation - multilateral efforts and shared ethical norms between countries

### EU AI Act (2024) - Regulation (EU) 2024/1689

The world's first legally binding AI regulation. Entered into force 1 August 2024.

**Purpose:** Ensure safe, trustworthy, ethical and human-centric AI while fostering innovation and legal certainty.

**Enforcement:** Significant fines for non-compliance, up to a percentage of global annual revenue.

**Risk-based classification:**

| Risk Level | Examples | Requirements |
|---|---|---|
| **Prohibited** | AI for social scoring, manipulative systems exploiting vulnerabilities, real-time biometric surveillance without safeguards | Completely banned |
| **High Risk** | Healthcare diagnosis, educational admissions, employment decisions, law enforcement risk assessment | Risk management, data governance, transparency, human oversight, post-market monitoring |
| **Limited Risk** | Chatbots | Basic transparency - must tell users they are interacting with AI |
| **Minimal Risk** | Spam filters, AI in video games | No specific requirements |

---

## Who Controls AI?

### Technology Control
- FAANG companies (Meta/Facebook, Apple, Amazon, Netflix, Google/Alphabet) collectively account for nearly 20% of the S&P 500 and nearly 40% of the Nasdaq-100 index
- Forbes AI 50 (top 50 most promising private AI companies): USA 42, UK 3, France 2, Germany 1, Canada 1, Japan 1
- This does not include Microsoft, NVIDIA, IBM, Oracle or Elon Musk's AI interests

### Information Control (December 2025 data)
- **ChatGPT**: 79.74% of chatbot market share
- **Google**: 90.82% of search engine market share
- **Facebook**: 72.8% of social media market share

### Data and Energy Control
- Training AI requires vast data centres
- Global data centre electricity consumption in 2022: 460 terawatt-hours - **11th largest electricity consumer in the world** (between France and Saudi Arabia)
- By 2026, expected to approach 1,050 terawatt-hours (5th in the world)
- Training GPT-3 alone: 1,287 megawatt-hours of electricity, 700,000 litres of freshwater, 520 tons of CO2
- Enough electricity to power 120 US homes for a year. Enough water to fill two-thirds of an Olympic pool.
- **You need to be the size of a nation to train frontier AI models.** This limits who can afford to control, process and use data.

**Conclusion:** AI is controlled by WEIRD countries - Western, Educated, Industrialised, Rich, Democratic. This has profound implications for whose values get baked into global AI systems.

---

## Trust in AI

### What is Trust?
Cambridge Dictionary: "to believe that someone is good and honest and will not harm you, or that something is safe and reliable."

### Three Types of Trust (Andras et al. 2018)

| Type | Definition | AI Application |
|---|---|---|
| Inductive Trust | Trust derived from personal past experience - trusts because it has previously acted as expected | Trusting Google Maps because it has always given correct directions |
| Moral Trust | Trust based on shared sense of rights and obligations, belief in benevolence | Trusting that an AI system was designed with your interests in mind |
| Social Trust | Attributes goal-directed behaviour to the machine, treats it as having its own goals | Treating a chatbot as if it has intentions and cares about your outcome |

### Can We Trust AI?

**Prof. Joanna Bryson (Professor of Ethics and Technology):**
- No, you cannot trust an AI and you should not
- AI has no genuine intentions, benevolence or goals
- Trust and accountability should be applied at the level of developers and organisations
- Hold the humans responsible, not the machines

**Dr Peter Lewis (Canada Research Chair in Trustworthy AI):**
- Agrees with Bryson that AI cannot be trusted in the moral sense
- But acknowledges humans are going to trust AIs anyway - we instinctively attribute goals to things that behave purposefully (anthropomorphism)
- Therefore developers need to build AI that helps people make better trust decisions
- Not "should humans trust AI?" but "how do we help humans make good trust decisions about AI?"

**See:** Lewis and March (2022): "What is it like to trust a rock? A functionalist perspective on trust and trustworthiness in artificial intelligence"

**The fundamental problem:** For moral trust or social trust, you need humans on both ends of the interaction. AI has no genuine intentions, benevolence or goals. Based on these definitions, humans can never truly trust an AI in the same way they trust another human.

---

## The Uselessness of AI Ethics (Munn, 2023)

This is a deliberately provocative paper arguing that most AI ethics is meaningless. The lecture explicitly covers it.

**Key arguments:**

- A flood of AI guidelines and codes of ethics have been released by governments and corporations
- These are **meaningless principles** that are contested, incoherent and difficult to apply
- They are **isolated principles** situated in an industry that largely ignores ethics
- They are **toothless principles** that lack consequences and adhere to corporate agendas

**Specific critiques:**
- **Ethics-washing is rampant** - corporations publish ethics guidelines to avoid real regulation, not to actually be ethical
- **Accountability over transparency** - auditing AI systems is more urgent than publishing "transparency" statements
- **Bias is context-dependent** - fairness metrics that work in one culture fail in another
- **Education is broken** - data science curricula teach technical skills but neglect ethics entirely

**Key quotes:**
- "Ethics without enforcement is toothless"
- "Solving bias by fixing algorithms alone is a seductive diversion"

**The implication:** Real ethical AI requires legally enforced regulation (like the EU AI Act), not voluntary guidelines.

---

## Key Terms for Week 2

| Term | Definition |
|---|---|
| Ethics | System of moral principles guiding decisions about right and wrong |
| Utilitarianism | Maximise overall good for the greatest number |
| Deontology | Absolute duties and red lines regardless of consequences |
| Virtue Ethics | Focus on values and character of the moral agent |
| Justice-based Ethics | Fairness and equitable outcomes for all groups |
| Relational Ethics | Prioritise care for vulnerable and dependent individuals |
| GDPR | EU data protection regulation |
| EU AI Act | World's first legally binding AI regulation (2024) |
| Ethics-washing | Using ethics rhetoric to avoid real regulation |
| Inductive Trust | Trust based on past reliable performance |
| Moral Trust | Trust based on shared values and benevolence |
| Social Trust | Trust based on attributing goals to the system |
| WEIRD | Western, Educated, Industrialised, Rich, Democratic - who controls AI |
| Deepfake | AI-generated fake video of a real person |
| Alignment | The problem of ensuring AI does what you actually want |
