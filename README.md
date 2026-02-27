# A/B Testing

👋 Hello and welcome to a repo with my A/B testing projects.
Here, I've collected the A/B and A/A test cases from my study projects done within the Analyst Simulator at [Karpov.courses](https://karpov.courses/). This study program involves a series of complex projects that simulate the real-life tasks of a product analyst at a startup developing a mobile app with a news feed and messenger.

## 📊 Projects

## 1. CTR analysis for the new algorithm of posts' recommendation in the news feed
In this project, I conducted an A/B test analysis for a new algorithm for recommending posts in the news feed in a mobile app we are developing.

A key metric — **CTR** (likes/views).

**What has been done:**
- Downloading the data from a ClickHouse DB (via pandahouse in Python)
- Calculating the users' CTR
- Comparing the groups with the help of z-test, t-test, Mann-Whitney U test, smoothed CTR, bootstrap, bucketization
- Visualization of the distributions
- Analysis of the resuls and formulation of recommendations

**Key results:**
- Found a **bimodality** of the CTR distribution in a test group
After the data transformation (with the use of several approaches):
- CTR in a test group: **20.03%**
- CTR in a control group: **20.96%**
- p-value = **0.0000** (statistically significant)
- ❌ the test is not successfull, the new algorithm even decreased the CTR + bimodality in the distribution implies potentail problems: uncounted external factors or segment specifics

**[→ To check the project](ctr_ab_test/)**  
*Stack: Python, pandas, numpy, scipy, statsmodels, pandahouse, matplotlib, seaborn*


## 2. Monte Carlo A/A test
In this project, I ran simulated A/A tests to evaluate the power of an upcoming test for a new news feed post recommendation algorithm.

A key metric — **CTR** (likes/views).

**What has been done:**
- Downloading the data from a ClickHouse DB (via pandahouse in Python)
- Calculating the users' CTR
- Simulating A/A tests to calculate the test power for different algorithm and experiment modifications
- Analysis of the results and recommendations for further steps

**Key results:**
- ❌ The analysis shows the potential test power lower than the conventional benchmark of 80% with different parameters of the test (sample size, test period) and algorithm modifications.

**[→ To check the project](monte_carlo_aa_test/)**  
*Stack: Python, pandas, numpy, scipy, statsmodels, pandahouse*


## 🚀 To launch the projects on your computer
1. Copy the `.env.example` file into your `.env` file and fill it with your data to access the DB
2. Install the necessary requirements: `pip install -r requirements.txt`
3. Launch the Jupyter: `jupyter notebook`
4. Open the necessary notebook and launch the chunks one-by-one

## 📁 Files
- `.gitignore` - a list of objects ignored for the git uploading (cache files, secrets)
- `.env.example` — a template to connect with the DB
- `requirements.txt` — technical requirements
