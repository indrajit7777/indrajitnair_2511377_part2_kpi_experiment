Part 2: KPI Framework, Business Experiment Analysis & Decision Recommendation

Business Context

A subscription-based digital product company tested a new onboarding and activation campaign. Users were split into Control and Treatment groups. Control users received the existing onboarding experience, while Treatment users received the new campaign experience.

Dataset Description

The dataset is stored at data/campaign_experiment_data.xlsx. It contains user-level experiment data including group assignment, region, device type, traffic source, plan type, funnel behavior, conversion, revenue, support tickets, refund requests, days to convert, and engagement score.

Business Problem

Leadership needs to decide whether the new onboarding campaign should be launched to all users. The decision affects marketing, product, customer success, and revenue teams. The target metric should improve paid conversion rate, but risks such as refunds, support tickets, slower conversion, weak engagement, and segment-level decline must be monitored. A recommendation should be made only after reviewing experiment metrics, guardrails, segment performance, and statistical evidence.

North Star Metric Selected

The North Star metric is Paid Conversion Rate.

Paid Conversion Rate = Users converted to paid subscription / Total users

This is the main success metric because the campaign objective is to improve conversion and early monetization. Funnel metrics such as landing page visit rate, trial start rate, and onboarding completion rate are supporting metrics because they explain why conversion changed, but they do not directly represent paid business growth.

Optimizing paid conversion blindly could create risks, including poor-quality conversions, higher refund rate, more support tickets, or weaker long-term engagement.

KPI Tree Summary

The KPI tree breaks paid conversion rate into acquisition quality, activation quality, engagement quality, and revenue quality. Guardrail metrics include refund rate, support ticket rate, average days to convert, engagement score, and segment-level decline.

Experiment Analysis Approach

The analysis was completed in analysis/experiment_analysis.xlsx.

Data preparation checks included:


Missing values
Group counts
Duplicate user IDs
Invalid binary values
Revenue outlier check
Segment distribution across groups


The original dataset had 1408 rows. After removing 8 duplicate user IDs, 1400 users were used in the final analysis.

Experiment Results

Treatment performed better than Control on the North Star metric.


Control paid conversion rate: 3.19%
Treatment paid conversion rate: 7.04%
Absolute lift: 3.85%


Treatment also improved landing page visit rate, trial start rate, onboarding completion rate, engagement score, and average days to convert.

Hypothesis Test Summary

A one-tailed two-proportion z-test was used to test whether Treatment improves paid conversion rate compared with Control.


Null hypothesis: Treatment does not improve paid conversion rate.
Alternative hypothesis: Treatment improves paid conversion rate.
Significance level: 0.05
Z statistic: 3.2640
P-value: 0.0005


Because the p-value is below 0.05, the result is statistically significant. The null hypothesis is rejected.

Guardrail Metrics Considered

Guardrails reviewed:


Refund rate
Support ticket rate
Average engagement score
Average days to convert
Revenue per converted user
Segment-level conversion decline


Refund rate and support ticket rate should be monitored after launch because Treatment shows higher support usage and a small refund rate. However, the conversion improvement is statistically significant and engagement/days-to-convert improved.

Final Recommendation

Recommendation: Launch with monitoring.

The Treatment campaign should be launched because it significantly improves paid conversion rate. However, rollout should include monitoring of support tickets, refund rate, and revenue quality.

Assumptions and Limitations


Duplicate user IDs were removed to avoid double-counting users.
Days to convert is only applicable for converted users.
Revenue outliers were retained because high revenue can be valid subscription behavior.
The analysis is based on 30-day outcomes only.
Longer-term retention and lifetime value were not available in the dataset.


Screenshots Included


screenshots/summary_metrics.png
screenshots/hypothesis_test_output.png
screenshots/kpi_tree_preview.png
