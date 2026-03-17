# DG1AID - Week 5 Notes
## Unit 2 - Data Science Concepts
### Aston University - Foundations of AI and Data Science (2025-26)

---

## Lecture Overview

Week 5 is the last week of Unit 2 and goes through the full Data Science Pipeline in detail, step by step. Every stage you need to understand for both the quiz and real data science work.

The pipeline is:
```
Gather → Store → Pre-process → Transform → Interpret → Visualise
```

**Key principle:** This is an iterative process. Each stage affects the next. Sometimes you need to go back to an earlier stage and start from there. **Never change results to fit your hypothesis.** Always follow the data.

---

## Step 1 - Gathering Data

### Quality Depends on Data

"Garbage in, garbage out" - the quality of your analysis results depends entirely on the quality of your input data.

If you train a language model on only 3 words, it will have a terrible conversation. If you measure student heights using a broken ruler, your analysis will be wrong no matter how sophisticated your statistics are.

**If you do not collect the right data, your analysis stops there.** You cannot answer a question about gender differences if you did not collect gender data. You cannot compare for-loop vs while-loop efficiency if you did not measure execution time.

### Primary vs Secondary Data

| Type | Definition | Important detail |
|---|---|---|
| **Primary data** | Collected directly by you or your team, specifically for this study. Did not exist before you collected it. | Examples: surveys, questionnaires, experiments, sensors |
| **Secondary data** | Collected previously by someone else for a different study. You are reusing it with permission. | Examples: government datasets, Kaggle, APIs, organisational databases |

**Important notes:**
- Primary and secondary are not always black and white. You might collect data for one purpose and then use it slightly differently - this creates a grey area.
- Secondary data requires extra verification. You must check it is accurate, check the source is reliable and check you have permission to use it.
- Neither type is inherently better. Both have pros and cons depending on your situation.
- Web scraping and APIs tend to be secondary (taking someone else's data). Sensors and surveys tend to be primary.

### Methods of Data Collection

| Method | Description | Pros | Cons |
|---|---|---|---|
| **Manual data entry** | Recording data by hand, writing in notebooks | Possible for small datasets, no technical setup | Human error, slow, does not scale |
| **Automated collection** | Sensors or programmes recording data automatically to files | Fast, consistent, scalable, reduces human error | Requires programming/hardware setup, software bugs possible |
| **APIs (Application Programming Interfaces)** | Programmatic access to data from websites and databases. Code that talks to other code. | Structured data, repeatable, automated | Often paid, rate limited (limits how much you can pull), reliability depends on the API provider |
| **Web scraping** | Writing code to crawl websites and extract specific data | Can collect data from any public webpage | Raw data needs parsing and cleaning, may violate terms of service, dependent on website structure |

**What is an API?** An API is a piece of code that lets you interact with someone else's system in a structured way. Instead of manually copying data from a website, you send a request to the API and it returns structured data (usually JSON format). For example, the Twitter API lets you pull tweets matching certain criteria.

**What is web scraping?** Writing code (usually Python with libraries like BeautifulSoup or Scrapy) that loads a web page and extracts specific elements. Google's search engine crawls the entire web continuously using this approach.

**Why human error is the biggest problem:** Whether it is manual entry, programming errors in automated systems, or bias in survey questions - human error at the data collection stage cascades through the entire pipeline. If you collect data poorly, no amount of sophisticated analysis can fix it.

---

## Step 2 - Storing Data

### Why Storage Matters

Data must be stored **securely** and **efficiently**. Poor storage choices can lead to:
- Data loss (the COVID-19 test results lost in Excel 2020)
- Security breaches (GDPR violations)
- Data bloat (storing unnecessary data wastes money and creates risk)
- Performance problems (wrong format for the analysis tools being used)

### Security Considerations

- **GDPR and legal requirements** apply to how data is stored and for how long
- **Encryption** (e.g. BitLocker, SSL) protects data from unauthorised access
- **Access controls** - only people who need the data should be able to access it
- **Data minimisation** - only collect and store data you actually need. If you are analysing aggregate student results, you do not need students' names.

### Common Storage Formats

| Format | Type | Best for | Notes |
|---|---|---|---|
| CSV (.csv) | Flat file | Simple, portable data | Plain text, easy to import everywhere |
| Excel (.xlsx) | Flat file | Small-medium datasets with formatting | Row limits, formatting can cause issues |
| TXT (.txt) | Flat file | Unstructured text data | Raw, minimal |
| SQL (MySQL, PostgreSQL) | Structured database | Large searchable structured data | Requires database setup |
| JSON | Semi-structured | Web APIs, config files | Flexible structure |
| XML | Semi-structured | Web services, document data | Verbose but flexible |
| MongoDB | NoSQL database | Unstructured or rapidly changing data | Flexible schema |
| Data warehouse | Centralised, large-scale | Business intelligence, analytics | Designed for querying not updating |
| Cloud (AWS S3, Azure Blob) | Cloud storage | Any scale | Pay-per-use, globally accessible |

### Ethical Storage Considerations

- Should you even store certain data? Collecting respondents' names when you only need their answers is unnecessary and creates privacy risk.
- How long should data be kept? GDPR requires data to be deleted when it is no longer needed.
- Could the data be used to identify specific individuals even if you intended it to be anonymous?
- Who has access? Is it the minimum number of people necessary?

---

## Step 3 - Data Pre-processing

### Why Pre-processing is Necessary

Raw data is almost never ready for analysis. This is universally acknowledged as the **most time-consuming step** in data science. Real-world data is messy, incomplete and inconsistent.

**Typical data quality problems:**

| Problem | Description | Example |
|---|---|---|
| Missing values | Some records have empty fields | A survey where some respondents skipped questions |
| Duplicate records | The same record appears more than once | A customer who appears in the database twice |
| Inconsistent formats | Same data represented differently | Dates as "01/03/2025" vs "March 1, 2025" vs "2025-03-01" |
| Outliers | Values that are abnormally high or low | A height of 4.5m (clearly an error) |
| Wrong data types | Numbers stored as text, categories stored as numbers | Age stored as "twenty-five" instead of 25 |
| Encoding issues | Characters from different character sets mixed up | Special characters appearing as ? or □ |
| Domain violations | Values outside the physically possible range | A temperature of -500°C or an age of -3 |

### Cleaning Strategies

**For missing values:**
1. **Remove the record** - if there are too many missing values in a row, delete it. Risk: you might be introducing bias if the missingness is not random.
2. **Imputation** - fill in the missing value with an estimate. Options:
   - Mean imputation: replace with the average of all known values
   - Median imputation: replace with the middle value (better for skewed data or when outliers are present)
   - Mode imputation: replace with the most common value (for categorical data)
   - Forward fill / backward fill: use the previous or next value in a time series
3. **Leave as NaN** - some algorithms can handle missing values natively

**For duplicates:**
- Identify and remove exact duplicates
- More complex: what about near-duplicates where the same person appears with slightly different name spellings?

**For inconsistent formats:**
- Standardise all dates to one format
- Convert all currencies to one currency
- Standardise measurement units
- Use consistent category labels (is it "Male" or "male" or "M"?)

**For outliers:**
- First decide: is this an error or a genuine extreme value?
- If error: remove or correct using the raw source
- If genuine: consider whether to keep it (it is real data) or remove it (it will distort statistics)
- Z-score method: values more than 3 standard deviations from the mean are likely outliers

**Data redundancy and checksums** can help prevent errors from occurring in the first place:
- Credit card numbers include a check digit calculated from the other digits
- Sudoku grids have built-in redundancy (each number must appear once in each row, column and box)
- QR codes include error correction - they can still be read even if part of the code is damaged

---

## Step 4 - Transforming Data

### Why Transform Data?

After cleaning, data often needs to be transformed before it can be fed into an algorithm. Different algorithms require data in different formats. Without transformation, results can be meaningless or biased.

**Key reasons:**
- Some algorithms require specific data formats (e.g. all numerical inputs, no categorical text)
- Reduces bias caused by scale differences between variables
- Highlights meaningful patterns that are obscured by raw values

### Common Transformations

**1. Normalisation and Standardisation**
Scaling data so that all variables are on a comparable scale.

Why this matters: If you have two variables - age (range 0 to 100) and salary (range £0 to £1,000,000) - and you run a machine learning algorithm on them, the algorithm will treat salary as astronomically more important than age just because the numbers are bigger. This is wrong - both should have equal opportunity to influence the model.

Two common approaches:
- **Min-max normalisation:** Scale everything to [0, 1]. Formula: (x - min) / (max - min)
- **Standardisation (Z-score):** Scale to have mean=0 and standard deviation=1. Formula: (x - mean) / std

**2. Encoding Categorical Variables**
Converting text categories to numbers because most algorithms need numerical input.

Example: Colour = {red, green, blue}
- Simple encoding: red=1, green=2, blue=3

Problem with simple encoding: the algorithm might assume green is "between" red and blue, or that blue (3) is three times red (1). These relationships do not exist.

Better approach - **One-hot encoding:**
- Create a separate binary column for each category
- red = [1, 0, 0], green = [0, 1, 0], blue = [0, 0, 1]
- No implied ordering or magnitude relationship

**3. Aggregating Data**
Pre-calculating summary statistics from raw data.

Example: Instead of storing every individual transaction for a customer, pre-calculate their total spend, average transaction value and number of transactions. This reduces data volume and makes analysis faster.

**4. Feature Creation (Feature Engineering)**
Constructing entirely new variables from existing raw data using domain knowledge or equations.

Examples:
- Calculate **BMI** from height and weight: BMI = weight(kg) / height(m)²
- Calculate **age** from date of birth and today's date
- Create a **profit margin** variable from revenue and cost
- Extract **hour of day** from a timestamp (to study time-based patterns)

Good feature engineering is one of the most impactful things a data scientist can do - the right features can dramatically improve model performance.

---

## Step 5 - Interpreting Data

### The Role of Interpretation

Turning analysis results into actionable insights. This is not just reading off numbers - it requires:
- Statistical understanding (what do the numbers actually mean?)
- Domain knowledge (what does this mean in context?)
- Communication skills (how do you explain this to a non-technical audience?)

**Important:** An average person will not understand raw statistical output. The data scientist's job is to interpret and contextualise the results, not just produce them.

---

### Descriptive Statistics

Descriptive statistics summarise large datasets into a handful of key numbers. They are divided into measures of central tendency and measures of spread.

#### Measures of Central Tendency - Where is the Centre?

| Measure | Definition | Formula | When to use | Affected by outliers? |
|---|---|---|---|---|
| **Mean** | The arithmetic average | Sum of all values ÷ count | Normally distributed data without extreme outliers | YES - very sensitive |
| **Median** | The middle value when data is sorted in order | Middle value (or average of two middle values for even count) | When outliers are present, skewed distributions | NO - robust to outliers |
| **Mode** | The most frequently occurring value | Most common value | Categorical data, finding the most typical value | NO |

**Example:** Test scores: [45, 50, 55, 60, 65, 70, 95]
- Mean = (45+50+55+60+65+70+95) / 7 = 440/7 = 62.9
- Median = 60 (the middle value when sorted)
- Mode = none (each appears once)

If you added another score of 95: [45, 50, 55, 60, 65, 70, 95, 95]
- Mean = 535/8 = 66.9 (pulled up by the outlier)
- Median = (60+65)/2 = 62.5 (barely affected)
- Mode = 95

**When to use which:**
- Mean works best when data is roughly symmetric and has no extreme outliers
- Median is better when data is skewed or has outliers (e.g. house prices - one £10 million mansion would massively distort the mean)
- Mode is most useful for categorical data (most common blood type, most popular product)

---

#### Measures of Spread - How Spread Out is the Data?

| Measure | Definition | Formula | Properties |
|---|---|---|---|
| **Range** | Difference between maximum and minimum values | max - min | Simple but very sensitive to outliers |
| **Variance** | Average of squared distances from the mean | Σ(x - mean)² / n | Units are SQUARED - less intuitive |
| **Standard Deviation** | Square root of variance | √(variance) | Same units as original data. Most commonly used. |
| **IQR (Interquartile Range)** | Range of the middle 50% of data | Q3 - Q1 | NOT affected by outliers. More robust than range. |
| **Percentile** | Value below which X% of data falls | Depends on n | 75th percentile = 75% of values are below this number |

**Understanding Quartiles:**
- Sort all data from smallest to largest
- Q1 (1st quartile, 25th percentile) - bottom 25% of data is below this
- Q2 (2nd quartile, 50th percentile) - the MEDIAN - bottom 50% is below this
- Q3 (3rd quartile, 75th percentile) - bottom 75% is below this
- IQR = Q3 - Q1 = the range containing the middle 50% of the data

**Understanding Standard Deviation intuitively:**
- Small std dev = data points are clustered close to the mean (everyone scores similarly)
- Large std dev = data points are spread far from the mean (some very high, some very low)

Example: Class A scores [68, 70, 72, 74, 76] - mean=72, std dev ≈ 2.8 (tightly clustered)
Example: Class B scores [45, 55, 72, 85, 95] - mean=70.4, std dev ≈ 18.4 (widely spread)

**Which to use:**
- Standard deviation is the most commonly reported measure of spread
- IQR is preferred when data has outliers (it ignores the extreme values at both ends)
- Range is useful for a quick rough estimate but is unreliable with outliers
- Variance is mainly used in statistical calculations, not reported directly (units are squared)

---

### Identifying Patterns and Trends

Common patterns to look for in data:
- **Correlations and relationships** - do two variables tend to increase together?
- **Changes over time** - is a metric increasing, decreasing or stable?
- **Comparisons between groups** - is there a difference between group A and group B?

---

### CRITICAL: Correlation Does NOT Imply Causation

This is one of the most important concepts in data science and statistics. It is specifically highlighted in the lecture as a "common pitfall."

**The statement:** Just because two variables move together (are correlated) does not mean one is causing the other.

**The classic example from the lecture:**
Shark attacks and ice cream sales are positively correlated. As ice cream sales go up, shark attacks go up.

Does eating ice cream cause shark attacks? Obviously not. Both increase in summer because of hot weather. Temperature is the real cause - it is a **confounding variable** (also called a lurking variable).

**Other real examples:**
- Countries with more televisions per household have higher life expectancy - does TV cause longevity? No. Both are caused by wealth.
- Nicolas Cage film releases correlate with swimming pool drowning rates - clearly not causal.
- Areas with more churches have more crime - does religion cause crime? No. Both are caused by population density.

**Why this matters for AI and data science:**
- A model trained on correlated data might learn to use ice cream sales to predict shark attacks. The predictions might even be accurate! But the model would fail completely in a scenario where ice cream sales and temperature were decoupled.
- Causal relationships are much more robust and generalisable than correlational ones.
- Making policy decisions based on correlation without understanding causation can be harmful.

**How to check for causation:**
- Run a controlled experiment (randomised controlled trial) where you change one variable and keep everything else constant
- Use causal inference techniques
- Apply domain knowledge and common sense

---

### Common Pitfalls in Data Interpretation

1. **Correlation vs causation** - already covered above
2. **Ignoring data limitations** - limitations are not a failure. They must be acknowledged and reported. Hiding limitations is unethical.
3. **Overgeneralising results** - results from your specific dataset may not apply to other populations, time periods or contexts. A study on UK university students cannot be directly applied to all humans.
4. **Simpson's Paradox** - a trend can appear in different groups of data but disappear or reverse when the groups are combined. Famous example: Berkeley admissions data appeared to show gender bias but the paradox resolved when departments were analysed separately.
5. **P-hacking** - running many different statistical tests until you find one that shows significance, then only reporting that one. Completely unethical but unfortunately common.
6. **Reporting only significant results** - if you run 20 experiments and only publish the one that showed a positive result, you are creating a misleading picture of the evidence.

---

## Step 6 - Visualising Data

### Why Visualisation Matters

- Looking at a chart is almost always easier than looking at raw data or even summary statistics
- Visual patterns are immediately apparent to the human brain
- Supports communication of insights to non-technical audiences
- Required for any professional data science report or presentation

### Choosing the Right Visualisation

This is crucial. The wrong chart can be more confusing than helpful - or worse, misleading.

**The choice depends on:**
- What question you are trying to answer
- What type of data you have
- Who your audience is
- What message you want to convey

| Question | Data type | Best chart | Why |
|---|---|---|---|
| How many fall into each category? | Categorical | Bar chart | Easy to compare heights |
| What proportion does each category make? | Categorical | Pie chart | Shows parts of a whole |
| How is this variable distributed? | Continuous | Histogram | Shows shape of distribution |
| What are the spread, median and outliers? | Continuous | Boxplot | Shows statistical summary visually |
| Is there a relationship between two variables? | Two continuous | Scatter plot | Shows correlation/pattern |
| How does this change over time? | Time series | Line chart | Shows trend |
| How do two or more groups compare across categories? | Grouped categorical | Grouped bar chart | Side-by-side comparison |
| What are the relationships between many variables? | Multiple variables | Heatmap, correlation matrix | Shows pairwise relationships |

### Good Visualisation Practices

- **Start the y-axis at zero** (unless there is a specific reason not to). Starting at a non-zero value exaggerates differences and misleads.
- **Label all axes** with clear names and units
- **Use appropriate scales** - log scale can be useful for data spanning many orders of magnitude
- **Avoid chartjunk** - unnecessary decoration, 3D effects, background images that add no information
- **Use colour meaningfully** - not just for decoration, and ensure it is accessible to colour-blind readers
- **Title your charts** - the reader should be able to understand the chart without the surrounding text
- **Be honest** - never truncate axes, cherry-pick time periods or choose chart types to mislead

**Reference:** "How to Lie with Statistics" by Darrell Huff (1954) - a classic book documenting all the ways charts and statistics can be used to mislead. Despite being 70 years old, every technique it describes is still used today.

---

## The Full Data Science Pipeline - Summary Table

| Stage | Key activities | Common problems | Key principle |
|---|---|---|---|
| Gather | Ask right questions, choose sources, collect | Collecting wrong data, insufficient sample size | Quality of output depends entirely on quality of input |
| Store | Choose format, secure storage, documentation | Data bloat, security breaches, format problems | Only store what you need, store it securely |
| Pre-process | Clean errors, handle missing values, standardise | Time-consuming, subjective decisions | This is the most time-consuming step |
| Transform | Normalise, encode, aggregate, feature engineer | Scale differences, wrong encoding | Prepare data for the specific algorithm being used |
| Interpret | Calculate statistics, identify patterns, explain | Correlation vs causation, overgeneralising | Never change results to fit the hypothesis |
| Visualise | Choose charts, design, communicate | Wrong chart type, misleading scales | The right chart makes insight immediate |

---

## Key Terms for Week 5

| Term | Definition |
|---|---|
| Data pipeline | The sequential process of data science: gather, store, pre-process, transform, interpret, visualise |
| Primary data | Data collected by you directly for this study |
| Secondary data | Data collected previously by someone else, reused |
| API | Application Programming Interface - structured programmatic access to external data |
| Web scraping | Code that automatically extracts data from websites |
| Imputation | Filling in missing values using estimates (mean, median, mode) |
| Normalisation | Scaling data to range [0,1] using min-max formula |
| Standardisation | Scaling to mean=0, std=1 using z-score formula |
| One-hot encoding | Converting categorical variables into binary indicator columns |
| Feature engineering | Creating new variables from existing ones using domain knowledge |
| Descriptive statistics | Summary statistics describing the key properties of a dataset |
| Mean | Sum of values divided by count. Sensitive to outliers. |
| Median | Middle value when sorted. Robust to outliers. |
| Mode | Most frequent value |
| Range | Maximum minus minimum |
| Variance | Average of squared distances from mean |
| Standard deviation | Square root of variance. Same units as data. |
| IQR | Interquartile range - Q3 minus Q1. Range of middle 50%. Not affected by outliers. |
| Percentile | Value below which X% of data falls |
| Q1, Q2, Q3 | Quartiles - divide sorted data into four equal parts |
| Correlation | Statistical relationship between two variables |
| Causation | When one variable directly causes a change in another |
| Confounding variable | A third variable that causes two other variables to appear correlated |
| Correlation ≠ causation | The most important rule in statistics - correlation does not mean one causes the other |
| EDA | Exploratory Data Analysis - initial analysis to understand data before formal modelling |
| Outlier | A value abnormally far from the rest of the data |
| Simpson's Paradox | A trend that appears in groups but disappears or reverses in combined data |
