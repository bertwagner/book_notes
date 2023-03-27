# Introductory Topics for Everyone

## Chapter 1 - Introduction and Motivation

 - 4 themes of controlled experiments:
   1. "It is hard to assess the value of an idea." - seemingly unimportant ideas can have huge returns.
   2. Small changes can have big impact.
   3. Big impact experiments are rare. Bing runs 10k+ experiments per year, big improvement features happen once every few years.
   4. Overhead of running experiments must be small.
 - It's useful to have "too good to be true" business rule alerts programmed around your experiment to check for bugs after deployment.
 - Overall Evaluation Criterion (OEC) must be measurable in the short term but be aligned with long-term strategic objectives.
 - 4 things are needed for useful experiments:
   1. You are able to split users into treatment and control groups.
   2. You have enough users to get meaningful results. Small changes to outcomes need more users.
   3. Key metrics (OEC) must be agreed upon and practically evaluated.
   4. Changes are easy to make.
 - Sometimes it is impossible to run controlled experiments - chapter 10 covers complementary techniques.
 - Success rates:
   - Microsoft: 33% of ideas tested led to improvements
   - Bing/Google: 12% success
   - Slack: 30% success
   - Netflix: 10% success
 - Improvmenets are usually measured in .1%-2%. Bing's yearly goal is 2% improvement.
 - Speed matters a lot:
   - Bing: 10 millisecond performance improvmenet pays for engineer
   - Amazon: 100 millisecond performance slow-down decreases sales 1%. 

## Chapter 2 - Running and Analyzing Experiments

 - Key OEC metrics should be normalized by sample sizes - instead of tracking "revenue", track "revenue-per-user".
 - Results can be statistically significant, but also need to be practically significant. ie. is the CBA of implementing the change worth it
 - Size of experiments has a direct impact on the precision of the result
   - If using "purchase indicator" instead of "revenue-per-user", standard error will be smaller, meaning won't need as many people going through the experiment to achieve the same sensitivity.
   - If practical significance is larger, sample size can be smaller since bigger changes are easier to detect.
   - If we want to use a lower p-value threshold, sample size will have to increase.
 - How long to run the experiment?
   - More users: "the user accumulation rate over time is likely to be sublinear" - meaning that the longer your experiment runs, the more likely you will have return users instead of new ones.
   - Day of the week effects: should probably run experiments for at least one week.
   - Seasonality and holidays: avoid or be aware of experiments running during times that may have unusual amounts of users.
   - Primacy and novelty affects: a new option/button may be clicked more initially because it is seen as new. Once the novelty wears off, clicks will decrease. Features that take time to adopt will take time to build the adopter base.
  - Making a decision:
    - Do you need to make tradeoffs between metrics? eg. increased revenue per user but lower engagement
    - Cost to launch:
      - Painted doors: it's cheap to build a fake feature to see if impacts an OEC (eg. create a coupon code field to see if it reduces revenue per user). Building the feature out fully will actually cost money. Is the CBA worth it?
      - Costs also include ongoing maintenance for the feature.
