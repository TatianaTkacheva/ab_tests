# CTR analysis for the new algorithm of post recommendation

## 📌 Context

In our app, we have a news feed, where we conducted several experiments.

The goal of these experiments was to test the effectiveness of new news feed recommendation algorithms. In this projects, I show the analysis of the experiment for the algorithm that shows users the most similar posts to those **they have already liked**.

CTR from views to likes was chosen as the performance metric.

**Why CTR?**

* This is quite a conventional metric;
* It implies an obvious actions that show the interest in the posts - likes.

The main **hypothesis** is that **the new algorithm will lead to a change in the CTR** (assumingly, to an increase, but we will test a two-sided effect).

## 📊 Data
- **Source:** ClickHouse, `feed_actions` table
- **A/B test period:** November 21-27, 2025
- **Groups:** 
  - 1 — control (old algorithm)
  - 2 — test (new algorithm, "Showing the posts similar to already liked ones")

## 🔍 Analysis steps
1. A/A test to ensure there is no difference in groups before the experiment
    * Downloading the data via `pandahouse`
    * Calculating the CTR for each user: `likes / views`
    * Checking the distributions (visualizations + tests)
2. A/B test analysis
    * Downloading the data via `pandahouse`
    * Calculating the CTR for each user: `likes / views`
    * Checking the distributions (visualizations + tests)
    * Applying the Mann-Whitney U test to compare the groups
    * T-test and Mann-Whitney U test for a smoothed CTR (+ visualization)
    * Bootstrap (+ visualization)
    * Bucket transformation (+ visualization of distributions)
3. Summary of the results and recommendations

## 📎 Files
- `ctr_analysis.ipynb` — a notebook with the analysis

## 🛠 To launch the project on your computer
1. Copy `.env.example` file from the root [ab_tests](https://github.com/TatianaTkacheva/ab_tests/tree/main) repo to your `.env` file and fill it in with your data to access the DB
2. Install the requirements: `pip install -r requirements.txt`
3. Launch the Jupyter: `jupyter notebook`
4. Open the `ctr_analysis.ipynb` file and launch the chunks



💡 I appreciate any feedback, so if you have thoughts to share, please don't hesitate to contact me. You may find the available channels to connect with me on my [welcome page](https://github.com/TatianaTkacheva) 👈.
