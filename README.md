# econ5200-lab9-ab-testing

# Diagnosing Experimental Failures in A/B Testing

## Objective

I worked through several ways an A/B test can give a wrong or misleading answer, and checked each one with fixes or simulations.

## Methodology

- Debugged an analyst's CUPED (variance reduction) code and fixed three bugs.
- Ran sample ratio mismatch (SRM) tests on two experiments: one with 100,000 users and a 0.60 pp imbalance, and one with 20 million users and a 0.05 pp imbalance.
- Simulated a marketplace where discounted buyers take inventory from the control group, then compared the A/B test's naive ATE with the effect of rolling the discount out to everyone.
- Ran a Bayesian A/B test and computed P(B > A), the expected loss of shipping B, and a ship decision rule. I cross-checked the result with a permutation test.
- Wrote my own function for the Bayesian test and used it on a test with four times the users.
- Simulated peeking: 1,000 experiments with no true effect, each checked at 50 points, compared with a single test at the end.
- (Challenge) Applied CUPED to the LaLonde job training data, using re74 and re75 as covariates.

## Key Findings

- **CUPED bugs:** The analyst reported 0.0% variance reduction. After my three fixes it was 82.7%, and the standard error fell from 0.1539 to 0.0641.
- **SRM:** The 0.60 pp imbalance among 100,000 users gave a chi-squared of 14.40. The 0.05 pp imbalance among 20 million users gave 20.00. A much smaller imbalance produced a larger statistic because the sample was so large.
- **Interference:** The naive ATE was 0.1861, against 0.1428 for rolling the discount out to everyone. The A/B test overstated the effect by 23.3% of the naive estimate.
- **Bayesian vs. frequentist:** P(B > A) was 0.8866 and the expected loss of shipping B was 0.000473, so the ship rule said False. The permutation test gave p = 0.2302.
- **Larger sample:** My own Bayesian function, run on a test with four times the users, gave P(B > A) = 0.9951.
- **Peeking:** With no real effect, 32.4% of experiments crossed p < 0.05 at least once across the 50 looks, against 5.3% with a single test at the end.
- **LaLonde (challenge):** Using re74 and re75 as covariates cut the variance by XX.X%.


hereswhat the ai ave me
