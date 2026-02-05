# Age vs Strength in Powerlifting (SCORE Module)

This repo contains my SCORE module work on modeling how age relates to strength in powerlifting, with a focus on how that relationship looks different for elite vs non elite lifters.

The short version is simple: instead of only modeling the average lifter, I use quantile regression to look at different parts of the performance distribution. That lets us compare how high performers develop and peak versus everyone else.

## What this project does

Using OpenPowerlifting meet data, this project builds an instructional module that walks students through:

- Cleaning and filtering a very large real world dataset
- Visualizing age based trends in strength
- Fitting quantile regression curves for “elite” (90th percentile) and “non elite” (10th percentile) lifters
- Comparing model forms, where the takeaway is that a 4th order polynomial captures the rise, peak, and decline pattern best in this setting

In the poster and module results, the main story is that elite lifters tend to develop faster, both groups peak roughly in the mid 20s to mid 30s, and the decline rate is fairly similar. The biggest separation shows up in the early development phase.【turn1:0†Score Festival of Science Poster Final.pdf†L57-L67】

## Why SCORE matters (briefly, but honestly)

SCORE is funded by the National Science Foundation with a focus on improving statistics and data science education using sports data, by building classroom ready modules that feel real, not canned.【turn1:0†Score Festival of Science Poster Final.pdf†L5-L9】

That matters because students learn the hard parts the right way: messy data, real assumptions, and models that answer a practical question. This project is my contribution to that goal, built around a sport I care about and data that is big enough to be authentic.

## Data source and processing notes

- Source: OpenPowerlifting archive (bulk meet data)
- Original scale: 3.6 million rows
- Reduction steps used for the module:
  - removed rows with missing variables
  - filtered out lifters that did not place
  - limited to one competition type (SBD) with two equipment categories (Raw, Single ply)
  - sampled 500 lifters per age group
- Resulting scale: about 4,000 rows for the teaching dataset【turn1:0†Score Festival of Science Poster Final.pdf†L10-L20】

Those choices are not “because it is convenient.” They are there so students can run analyses quickly while still working with data that behaves like real performance data.

## Repo contents

Typical files you will see here:

- `Age_vs_Strength_QR_Module.qmd`  
  The main Quarto teaching module (walkthrough, visuals, modeling).

- `Powerlifting_Questions.qmd`  
  Student facing activity sheet.

- `Answers_Powerlifting_Questions.qmd`  
  Instructor key or solution set.

- `Age vs. Strength by Class.html`  
  Rendered module output (HTML).

- `Powerlifting Questions.htm`  
  Rendered questions handout (HTML).

- `tidy_male_lifters_quantreg.csv`  
  Tidy dataset used for the quantile regression work.

- `Score Festival of Science Poster Final.pdf`  
  One page poster summarizing the project.

## How to run it locally

This project is built in R using Quarto.

1. Install Quarto  
   Make sure Quarto is installed on your machine.

2. Install required R packages  
   At minimum, you will use packages like:
   - `tidyverse` (or `readr`, `dplyr`, `ggplot2`)
   - `quantreg`

3. Render the module  
   Open the `.qmd` files in RStudio and render, or run:

   - Render the main module: `Age_vs_Strength_QR_Module.qmd`
   - Render the activity sheet: `Powerlifting_Questions.qmd`
   - Render the answers: `Answers_Powerlifting_Questions.qmd`

If you are teaching from this, I recommend rendering the activity sheet and answers separately so you can hand students the questions file without spoilers.

## Methods, in plain terms

- Outcome: strength performance (for example total lifted, or best lift depending on the section)
- Predictor: age
- Model: quantile regression at key percentiles
  - 0.90 as a proxy for elite
  - 0.10 as a proxy for non elite
- Form: polynomial quantile regression, with the 4th order model used as the best fit to the observed pattern【turn1:0†Score Festival of Science Poster Final.pdf†L59-L63】【turn1:12†Age vs. Strength by Class.html†L10-L16】

## Future work

Ideas already scoped in the poster and module:

- multi level models tracking individual lifters across time
- prediction focused work, like what features best predict elite status
- exploring non linear forms like a lifespan style double exponential curve as an entry point to non linear regression【turn1:0†Score Festival of Science Poster Final.pdf†L69-L71】【turn1:0†Score Festival of Science Poster Final.pdf†L50-L52】

## Credits

- Joshua Larson
- Advisor: Dr. Ivan Ramler
- Department of Mathematics, Computer Science, and Statistics, St Lawrence University【turn1:0†Score Festival of Science Poster Final.pdf†L2-L4】

## Citation

If you use this module, please cite the repo and the OpenPowerlifting dataset, and consider referencing the SCORE framework that the module was built for.

---

Project artifact reference (for this upload):
:contentReference[oaicite:0]{index=0}
