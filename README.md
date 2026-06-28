# Symbolic-Regression-with-Genetic-Programming-DEAP-
A machine learning project that uses Genetic Programming (GP) to perform symbolic regression — automatically discovering a mathematical formula that predicts depression prevalence rates from other mental health indicators.

What it does

Instead of fitting a fixed model type (like linear regression), this project evolves a population of mathematical expressions over multiple generations, selecting, crossing over, and mutating them until the best-fitting formula emerges. The target variable is the share of the population diagnosed with depression, predicted from four other mental illness prevalence rates.

Dataset

Mental Illnesses Prevalence — Kaggle

6,420 observations across countries and years, with the following features:

Schizophrenia - Share of population with schizophrenia
Depression - Share of population with depression (target)
Anxiety - Share of population with anxiety disorders
Bipolar - Share of population with bipolar disorder
Eating - Share of population with eating disorders


Download mental_illnesses_prevalence.csv from Kaggle and place it in the same directory as the notebook before running.



Approach


EDA — histograms, boxplots, correlation heatmap, and scatter plots to understand feature relationships
Preprocessing — feature standardization with StandardScaler, 80/20 train/test split
GP setup (via DEAP) — primitive set including arithmetic operators, sin, cos, log, sqrt, and ephemeral constants; protected versions of division, log, and sqrt to avoid numerical errors
Evolution — population of 300 individuals, 40 generations, tournament selection, one-point crossover (p=0.5), uniform mutation (p=0.2), max tree depth of 17
Evaluation — RMSE on the held-out test set; best individual tracked via Hall of Fame


Results

The best evolved expression achieved RMSE = 0.708 on the test set. The model captures the general trend well, though it tends to smooth over local extremes — a known trade-off with symbolic regression, where interpretability and accuracy compete with expression complexity.

Evolution charts show rapid fitness improvement in early generations followed by stabilization, consistent with typical GP convergence behavior.

Requirements

deap
scikit-learn
pandas
numpy
matplotlib
seaborn

Install with:

bashpip install deap scikit-learn pandas numpy matplotlib seaborn

Running the notebook

bashjupyter notebook regresjav2.ipynb

Key concepts demonstrated


Genetic Programming for symbolic regression
Custom protected mathematical primitives
Evolutionary algorithm operators (selection, crossover, mutation)
Exploratory data analysis on real-world health data
Model evaluation with RMSE
