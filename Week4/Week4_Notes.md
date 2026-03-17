# DG1AID - Week 4 Notes
## Unit 2 - Introduction to Data Science
### Aston University - Foundations of AI and Data Science (2025-26)

---

## Lecture Overview

Week 4 begins Unit 2. It covers:
- What is Data Science?
- What is data? Data types and representations
- A brief history of Data Science
- Applications of Data Science
- Data and Ethics (GDPR)

**Key message from the lecturer:** Data Science is not just for mathematicians and statisticians. It is now essential for computer scientists, engineers, biologists, journalists, sports analysts - anyone who works with data. And data is everywhere.

---

## What is Data Science?

There is no single agreed definition. Different sources define it slightly differently:

**Gemini (2026):**
"An interdisciplinary field that combines mathematics, statistics, artificial intelligence, and computer science to analyse large datasets and uncover actionable insights. It involves gathering, cleaning, and modelling data to identify patterns, predict future trends, and support strategic decision-making across various industries."

**Oxford Languages (2026):**
"The science of analysing and extracting information from large sets of data, which typically combines elements of statistics, maths, computing, and other subjects."

**Igual and Segui (2024):**
"The pipeline of any data science goes through asking the right questions, gathering data, cleaning data, generating hypotheses, making inferences, visualising data, assessing solutions, etc."

**Summary - what data science is:**
- An interdisciplinary field spanning maths, stats, computer science, AI and subject-specific domains
- More recently includes machine learning and AI
- Uses data to support decision-making and predictions
- **Bases decisions purely on data and results - never on assumptions or pre-existing knowledge**
- Helps visualise data so that non-technical audiences can understand
- Starts with the right questions and ends with the answers - no shortcuts, no assumptions

**Important:** A negative result is still a result. If the data does not support the hypothesis, you must present that honestly. Never adjust results to fit what you expected.

---

## What is Data?

- **Datum** (singular) - a single observation, measurement or fact
- **Data** (plural) - multiple measurements or observations
- Data are raw facts, observations or measurements
- Data can be: numbers, text, images, audio, video, sensor readings, social media posts, anything
- Most people think of data as spreadsheets of numbers - but data is much broader than this
- **Data becomes INFORMATION when meaning is added to it**

Example: "1.78" is a datum. "Isaac's height is 1.78m" is information.

---

## Examples of Data Sources

| Source | Examples | Notes |
|---|---|---|
| Surveys and experiments | Questionnaires, lab results | Likert scale: 1=Strongly Disagree to 5=Strongly Agree |
| Sensors and IoT devices | Temperature sensors, accelerometers, GPS | F1 cars generate ~1 million data points per second via sensors |
| Business transactions | Sales records, financial data | Meeting targets, inventory levels |
| Social media and websites | View counts, likes, follower networks | Number of YouTube views, Twitter followers |
| Public datasets | Government data, Kaggle, academic repositories | Free to use, but verify quality |

---

## Data Types

This is one of the most important topics for the quiz. You need to know all the data types and be able to classify examples.

### Qualitative vs Quantitative

| Type | Description | Examples |
|---|---|---|
| **Qualitative** | Text-based, descriptive, open-ended answers | "What is your main concern about AI?", survey comments |
| **Quantitative** | Numerical, measurable | Height, test scores, number of goals, salary |

### Categorical Data (subtypes of Qualitative)

| Subtype | Description | Examples |
|---|---|---|
| **Nominal** | Categories with NO natural order. You cannot rank them. | Colours (red, blue, green), country names, blood type, nationality |
| **Ordinal** | Categories WITH a natural order. You CAN rank them. | Star ratings (1 to 5), grades (A, B, C), satisfaction scale (low, medium, high) |

**Key test for ordinal vs nominal:** Can you meaningfully say one is "better" or "more" than another? If yes, it is ordinal. If no, it is nominal.

### Numerical Data (subtypes of Quantitative)

| Subtype | Description | Examples |
|---|---|---|
| **Discrete** | Countable values. Usually whole numbers. Cannot have fractional values. | Number of students (cannot have 2.5 students), goals scored, number of cars |
| **Continuous** | Measurable values. Can be any real number. Can have infinite precision. | Height (1.78m, 1.782m, 1.7823m...), temperature, time, weight |

**Key test for discrete vs continuous:** Can you have a fractional value? If you cannot (you cannot score 2.5 goals), it is discrete. If you can (you can be 1.785m tall), it is continuous.

### Structured vs Unstructured vs Semi-structured

| Type | Description | Examples |
|---|---|---|
| **Structured** | Organised in rows and columns. Easily searchable. | Excel spreadsheets, SQL databases, CSV files |
| **Semi-structured** | Some organisation but not fully tabular | JSON files, XML files, emails with standard headers |
| **Unstructured** | No predefined format. Hard to search automatically. | Text documents, images, videos, audio recordings |

---

## Big Data - The 3 Vs

Big Data refers to datasets so large, fast and varied that traditional data processing tools cannot handle them.

The three defining characteristics are the **3 Vs**:

| V | Meaning | Example |
|---|---|---|
| **Volume** | How MUCH data there is | Facebook generates petabytes of data per day |
| **Velocity** | How FAST new data is generated | Stock market generates thousands of transactions per second |
| **Variety** | How many different FORMATS and types exist | Text, images, video, sensor readings, financial records all at once |

**Why Big Data became important:** Web 2.0 (from 2004 onwards) transformed the internet from "read-only" to "participative." Users started generating content at unprecedented scale. Social media, smartphones and IoT devices created data at a scale that was impossible to process with traditional methods.

**A cautionary example:** In 2020, the UK lost 16,000 COVID-19 test results. They were stored in an old Excel format (.xls) that had a maximum row limit of 65,536. When the file exceeded that limit, records were silently lost. Big Data requires the right infrastructure.

---

## Data Storage and Representation

Data can be stored and represented in several ways depending on the use case:

### Tables and Spreadsheets
- Excel (.xlsx), CSV (.csv), Google Sheets
- Rows represent individual records (observations), columns represent variables (features)
- Good for small to medium datasets
- Excel can handle up to ~1 million rows - insufficient for Big Data

### Vectors and Matrices
- Used for mathematical analysis (NumPy in Python)
- A **vector** is a 1-dimensional array - one row or column of data
- A **matrix** is a 2-dimensional array - rows and columns of data
- Faster to process mathematically than spreadsheets
- You used these in the Week 3 lab

### Databases
- **SQL (Structured Query Language)** databases - structured, searchable, reliable for large datasets
- Examples: MySQL, PostgreSQL
- **NoSQL ("Not Only SQL")** databases - flexible, for unstructured or semi-structured data
- Examples: MongoDB, Cassandra

### Graphs and Networks
- As covered in Week 3, data relationships can be represented as graphs
- Can use colour or size differences on edges to represent weights or strengths

### Cloud Storage
- AWS (Amazon Web Services), Microsoft Azure, Google Cloud
- Allows storage and processing of arbitrarily large datasets
- No need for expensive local hardware

---

## Data Visualisation

### Why Visualise Data?

- Raw numbers are hard to interpret and spot patterns in
- Looking at 1,000,000 data points and trying to identify trends manually is practically impossible
- Visualisations allow non-technical stakeholders (managers, the public, policymakers) to understand results
- Visualisations can reveal patterns that are invisible in tables
- However: visualisations can also mislead (covered more in Week 5)

### Common Chart Types and When to Use Them

| Chart Type | Use for | Key features |
|---|---|---|
| **Bar chart** | Comparing frequencies or values across categories | Easy to compare heights of bars |
| **Pie chart** | Showing proportions of a whole | All slices must add to 100% |
| **Histogram** | Showing distribution of a single continuous variable | Similar to bar chart but for continuous data |
| **Boxplot (box-and-whisker)** | Showing spread, median and outliers | Shows Q1, median, Q3, and outliers |
| **Scatter plot** | Showing relationship between two continuous variables | Each point = one observation |
| **Heatmap** | Showing relationships between two categorical variables | Colour intensity shows frequency |
| **Line chart** | Showing change over time | Continuous variable on x-axis |
| **Dashboard** | Multiple visualisations in one view | Customisable, interactive |

---

## Main Concepts in Data Science

### The Data Science Pipeline

The full process of data science always follows this general sequence:

1. **Ask the right questions** - what are you trying to find out? What hypotheses do you want to test?
2. **Collect data** - gather the data needed to answer your questions
3. **Clean and prepare data** - fix errors, missing values, inconsistencies
4. **Exploratory Data Analysis (EDA)** - calculate basic stats, generate charts to understand the data before formal analysis
5. **Modelling and machine learning** - run statistical tests or train ML models
6. **Communicate results** - present findings honestly, with context

**This is covered in much more detail in Week 5.**

### What Does a Data Scientist Do?

- Works with datasets of all sizes (more data = more certainty, but sometimes only small datasets are available)
- Always states the size of the dataset and considers the **power of the study** (how confident can you be with this amount of data?)
- Uses programming and statistical tools to analyse data
- **Translates data insights into real-world impact** - not just producing numbers but explaining what they mean and what to do about them

---

## Brief History of Data Science

### Pre-Web and Web 1.0 Era (before 2004)

**Web 1.0 (approximately 1991-2004):** The "read-only" web. Static websites. Limited user interaction.

- **Early 1960s:** Term "Data Science" coined to describe a new profession supporting the interpretation of large amounts of data
- Relied entirely on traditional statistical tests: t-test, chi-squared test (χ²), correlation, regression
- **1962:** John W. Tukey publishes "The Future of Data Analysis" - the seminal paper arguing for combining statistics with computers. He wrote: "as I have watched mathematical statistics evolve, I have had cause to wonder and to doubt...I have come to feel that my central interest is in data analysis..."
- **1977:** International Association for Statistical Computing (IASC) formed. Mission: link traditional statistical methodology, modern computer technology and domain expertise to convert data into information and knowledge.
- **1994:** Business Week runs cover story "Database Marketing" - companies were already gathering large amounts of personal information and planning targeted marketing campaigns using that data. This is the direct precursor of today's targeted advertising.
- **2001:** Software-as-a-Service (SaaS) created - the precursor to cloud computing (Azure, AWS). Allowed data mining to flourish without needing expensive local infrastructure.

### Web 2.0 Era (2004 to present)

**Web 2.0 (2004-present):** The "participative" or "social" web. Users create content. Social media. Smartphones.

- **2008:** The term "data scientist" becomes a buzzword. Credit goes to DJ Patil and Jeff Hammerbacher for popularising the term.
- **2011:** Job listings for data scientists increased by 15,000%
- **2012:** Harvard University declared data scientist the "sexiest job of the 21st century"
- Big Data and Machine Learning (ML) become the primary approaches to data collection, storage and analysis
- ML uses data to train itself (according to human-specified parameters) to recognise patterns
- **2013:** IBM claimed 90% of all data in the world had been created within the last 2 years (reflects the explosion of social media, smartphones and IoT)
- **2015:** Google Voice (speech recognition) improved by 49% after switching to deep learning techniques

### Web 3.0 Era (now and future)

**Web 3.0:** Semantic, decentralised and intelligent technologies.

- **Blockchain:** Technology for verifying and tracking data as entries on a distributed ledger. Underpins all cryptocurrencies and NFTs. Basis: Bitcoin whitepaper by Satoshi Nakamoto (2008) - only 8 pages long.
- AI and LLMs continue to incorporate user data for training and personalisation
- Targeted advertising is becoming increasingly sophisticated
  - Famous example: Target predicted a teenager's pregnancy before her father knew, based on her purchasing behaviour changes (Forbes, 2012)
- Cloud computing democratises data science - anyone can access large-scale compute without owning the hardware

---

## Applications of Data Science

### Business and Marketing
- **Sales forecasting** - predict future demand to optimise inventory and production
- **Recommendation systems** - Netflix, Spotify, Amazon, YouTube
- **Customer segmentation** - group customers by behaviour to target marketing
- **Sentiment analysis** - analyse customer reviews and social media at scale

### Healthcare
- **Disease prediction** - identify high-risk patients before they become ill
- **Medical image analysis** - AI detecting cancer from scans, sometimes better than doctors
- **Personalised medicine** - tailor treatments to individual patient data
- **Public health monitoring** - tracking disease spread, vaccination rates

### Finance
- **Fraud detection** - real-time anomaly detection in transactions
- **Algorithmic trading** - automated buying and selling based on data signals
- **Credit scoring** - assessing loan risk from financial history
- **Blockchain and cryptocurrencies** - decentralised financial systems

### Science, Engineering and Technology
- **Navigation and traffic prediction** - Google Maps, Waze
- **Spam filtering** - classifying emails automatically
- **Social media feeds** - algorithmic curation of content
- **Scientific research** - protein folding (AlphaFold), climate modelling (GraphCast)

### Government and Public Policy
- **City planning** - optimise road networks and infrastructure
- **Public health** - track outbreaks, allocate resources
- **Benefits and welfare** - targeting support to those who need it

---

## Data and Ethics

Data science does not exist in an ethical vacuum. Every stage of the data pipeline has ethical implications.

### Privacy and Consent

**GDPR (General Data Protection Regulation, 2016)**
- EU legislation - applies inside the EU and to any organisation serving EU users, regardless of where they are based
- Three core principles: users must have **control**, **transparency** and **security** over their own data
- Users have the right to know what data is collected, how it is used and to request deletion
- Fines for non-compliance: up to **€20 million OR 4% of global annual turnover**, whichever is HIGHER

**Key ethical questions around data:**
- How long should data be kept? (Data that is no longer needed should be deleted)
- Can we collect data "just in case" we need it in future? (Generally no - you should only collect what you need)
- Should users have to actively consent, or is it opt-out? (Opt-in is more ethical but harder to implement commercially)
- What counts as personal data? (Name, email, IP address, browsing history, health records...)

**Popular saying:** "If a product is free, you are the product." Facebook, Google and other platforms are free because they collect and monetise your data.

### Ethical Data Considerations

**Bias and Fairness:**
- Data reflects societal biases - if historical data shows fewer women in senior roles (due to past discrimination), AI trained on that data will learn to perpetuate that bias
- Real example: Amazon had to scrap a CV-screening AI in 2018 because it systematically downgraded applications from women
- Models can amplify unfair outcomes, not just reflect them
- Fairness must be designed in, not added as an afterthought

**Transparency and Accountability:**
- AI models making important decisions (loan approvals, parole decisions, medical diagnoses) should be explainable
- The person affected by a decision has the right to understand why
- Decisions should be auditable - there must be a record of how they were made
- **Humans remain responsible for outcomes, not the AI** - you cannot blame an algorithm

**Data ethics applies at EVERY stage of the pipeline:**
- Collection: are you collecting what you are legally and ethically allowed to?
- Storage: is it secure? Is it being kept longer than necessary?
- Analysis: are you applying the right tests? Are you looking for confirmation of your bias?
- Results: are you reporting negative results? Are you overgeneralising?
- Communication: are your visualisations honest?

---

## Key Terms for Week 4

| Term | Definition |
|---|---|
| Data Science | Interdisciplinary field combining maths, stats, CS and AI to extract insights from data |
| Datum | A single observation or measurement |
| Data | Multiple observations or measurements |
| Information | Data with meaning added |
| Qualitative data | Descriptive, text-based data |
| Quantitative data | Numerical data |
| Nominal | Categorical data with no natural order |
| Ordinal | Categorical data with a natural order |
| Discrete | Countable numerical data (whole numbers) |
| Continuous | Measurable numerical data (any real number) |
| Structured data | Organised in rows and columns |
| Big Data | Datasets too large for traditional tools |
| 3 Vs | Volume, Velocity, Variety - defining characteristics of Big Data |
| GDPR | EU data protection regulation (2016). Fines up to 20M euros or 4% turnover. |
| EDA | Exploratory Data Analysis - initial analysis before formal modelling |
| Primary data | Collected directly by you for this specific study |
| Secondary data | Previously collected by someone else for a different purpose |
| Data pipeline | The sequential process: gather, store, clean, transform, interpret, visualise |
| Imputation | Filling in missing values using estimates from available data |
