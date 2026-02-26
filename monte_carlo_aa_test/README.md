# Synthetic A/A test with a Monte Carlo approach

## Context

Our ML team plans to launch a new algorithm, which will recommend the users posts based on their interests. The initial assumptions are as follows:

* The algorithm adds 1-2 more views for each user
* The probability of the algorithm to have an effect is 90%
* The algorithm will have an effect only for users with 50+ views

We assume that increase in views will lead to the increase of post likes. Then, the question is: **will we find any differences in the average likes count per user after launching this algorithm?** 

To answer the question before launching the A/B test, I conducted a series of A/A simulations.

Initially, the planned period for the A/B test is 1 week. So, the A/A test is initially conducted for 1 week period samples. The analysis also includes simulations for a longer period.


**Important assumptions**: 
* we assume that the WAU for 1 week of A/B testing in our app will be the same as for the A/A test period. Also, we plan to split users into two groups at a 50/50 ratio. So, the sample size for each group is calculated based on this assumptions.

* **Formula for the algorithm effect**: based on the data from the ML team, I simulate the effect of the algorithm on views as follows: *test_group_metrics + ((1 + np.binomial(n=1, p=0.5, size=sample_size)) * np.binomial(n=1, p=0.9, size=sample_size) * (test_group_metrics >= 50))*

* The number of simulations is 20000.

* The final t-test is conducted with the Welch correction for unequal variances. The alpha-level is conventionally 0.05.

## 📊 Data
- **Source:** ClickHouse, `feed_actions` table
- **Initial A/A test period:** November 14-20, 2025

## 🔍 Analysis steps
1. Downloading the data via `pandahouse`
2. Calculating the overall sample
3. Calculating the sample for each group (50/50 split)
4. Calculating the CTR for each user: `likes / views`
5. Conducting the simulation to find the test power for initial parameters
6. Calculating the power for different modifications of the algorithm and parameters of the experiment:
    * Finding the test power for an algorithm effect for users with **30+ views**
    * Finding the test power for a test period of **2 weeks**
    * Finding the test power for a narrow sample (only those users potentially affected by the algorithm)
7. Summarizing the results and formulating the recommendations

## 📎 Files
- `monte_carlo_analysis.ipynb` — a Jupyter notebook with the analysis

## 🛠 To launch the project on your computer
1. Copy the `.env.example` file from the root [ab_tests](ab_tests/) repo and fill it in your `.env` file with your data to access the DB
2. Install the requirements: `pip install -r requirements.txt`
3. Launch the Jupyter: `jupyter notebook`
4. Open the `monte_carlo_analysis.ipynb` file and launch the chunks
