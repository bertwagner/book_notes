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

## Chapter 3 - Twyman's Law and Experimentation Trustworthiness

 - Twyman's Law - The more unusual or interesting the data, the more likely they are have to been the result of an error.
 - When we see surprising results, we try to build a story around it if it is positive or find a flaw to dismiss it if it is negative.
   - To increase trust in experiments,  must have set of tests to indicate something might be wrong with the result.

### Common errors for misinterpretation of statistical results
 - Lack of statistical power - Null hypotheses: there is no difference in metric value between Control and Treatment. A common mistake is to assume if a metric is not statistically significant, that it has no Treatment effect. It could be there, but experiment is underpowered to detect the effect size being seen.
 - Misinterpreting p-values - p-value is the probablity of obtaining a result equal to or more extreme than what is observed, assuming the Null hypothesis is true. There are many ways to misinterpret this. 
 - P-Value Peeking - Don't look at p-value results as they come in - you might stop experiment early if the p-value results line up with what you want.
 - Multiple Hypothesis Tests - Don't run multiple tests and choose the one with the best p-value result. It is likely the result and effect size are likely to be biased.
 - Confidence intervals - CIs represent how often the confidence interval should contain the true Treatment effect. CIs can overlap up to 29% and still be statistically significant.
 - Threats to internal validity:
   - Experiment users should not interfere with one another (social networks, skype, two sided market places, etc...)
   - Survivorship bias: Analyzing users who have been active for some time might be survivorship bias - only the ones who want to use the treatment stick around.
   - Intention to treat: Analyzing only people who choose to participate leads to selection bias and overstates the treatment effect.
   - Sample Ratio Mismatch (SRM): If ratio of users between variatns is not close to the designed ratio, the experiment suffers from SRM. 
     - With large numbers, ratios smaller than .99 or greater than 1.01 can indicate serious issues.
     - SRM checks are critical and must be put in as guardrails.
     - SRM can happen due to:
       - Browser redirects (performance differences, bots, bookmarking redirected treatment page).
       - Lossy instrumentation (1x1 tracking gifs aren't perfect, not all users enable javascript).
       - Residual or carryover effects (new experiments have new code which are more likley to have bugs. Can run A/A test first to ensure no new bugs).
       - Bad hash functions for randomization
       - Time of day effects
 - Threats to External Validity - Can an experiment be generalized to other populations?
   - Generalizing across populations is easy to test - just rerun the experiment.
   - Generalizing across time is harder. Sometimes need to leave a hold-out group running for months to test.
     - Primacy effects: when a change is introduced, it may take a while for users to adopt it.
     - Novelty effects: highly visual new features attract users initially, but they drop off once it is not new anymore.
     - Detecting primacy and novelty effects can be done by plotting usage over time: Treatment effects should be constant over time.


## Chapter 4: Experimentation Platform and Culture
