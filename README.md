# Matching - Catholic School vs Public School, Standardized Test Scores

This project makes use of matching techniques to compare two different groups without having a control group.

## Question
How do students in Catholic Schools perform on standardized tests compared to students in public schools?

## Data

5429 entries with the following features:
* `childid`
* `catholic`
* `race`
* `number_places_lived`
* `mom_age`
* `dad_age`
* `dad_education`
* `mom_education`
* `mom_score`
* `dad_score`
* `income`
* `poverty`
* `food_stamps`
* `score_standardized`

## Analysis

First, T-Tests and Chi-square tests were performed to ensure that there was, in fact, a difference between both groups across all variables.  Results showed that the groups are different.

Then the `race`, `dad_education`, and `mom_education` variables were collapsed into smaller buckets to avoid the Curse of Dimensionality.

Next, the common support region was visualized to assess the quality of the matching.<br>
![image](https://github.com/nwferreri/matching/assets/112211174/675ddded-eefc-4fcd-ae83-415d00e07995)<br>
Given the large overlap between the curves, the matching is of high quality.

Finally, a Causal Model was run using [Causal Inference](https://causalinferenceinpython.org/).

## Evaluation
The model was evaluated and showed a statistically significant Average Treatment Effect (ATE) of -0.133.

Two robustness checks were performed to corroborate findings.

The first was repeated sampling with 1000 iterations.  A histogram of results was generated.<br>
![image](https://github.com/nwferreri/matching/assets/112211174/4b95d604-ff98-4679-bf05-2b32c19f4e47)<br>
The average ATE for this test was -0.128.

The second robustness check was to remove one confounder.  `number_places_lived` was chosen.  ATE for this test was -0.137.

Both robustness checks increase confidence in the analysis.

## Conclusions

Based on the analysis, Catholic school students perform worse on standardized tests than their public school counterparts.
