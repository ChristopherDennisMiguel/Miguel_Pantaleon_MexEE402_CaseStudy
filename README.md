# MexEE 402: Data Preprocessing Case Study

MexEE Elective 2: Data Science and Machine Learning
Batangas State University, Alangilan Campus
1st Semester, AY 2026-2027

## Members

| Name | Student Number | Section |
|---|---|---|
| Miguel Jr, Christopher Dennis |22-08815 |MEXE-4103 |
| Pantaleon, Marl Joshua |22-04266 |MEXE-4103 |

## Notebook links

| Chapter | Miguel | Pantaleon |
|---|---|---|
| Ch1_2_3 | [https://colab.research.google.com/drive/1yMTUnKs2T82QIF32Wto_s7ubeNjQndl2?usp=sharing]() | [[link](https://colab.research.google.com/drive/17PpWMHbsJXVUMhvc2t9jUeS-8CLLLKKv?authuser=1#scrollTo=2eSVoqbAbx-3)]() |
| Ch4 | [https://colab.research.google.com/drive/18W2wlBKByAaSpfa5qHaW2A3Ql6OkStYt?usp=sharing]() | [[link](https://colab.research.google.com/drive/1kHfqeRglQWC6HeIzIslxM2a40RfpKiX3?authuser=1#scrollTo=XpZ7dDWpgJNy)]() |
| Ch5 | [https://colab.research.google.com/drive/1QDMYzqzW6_DhhU1QdPVXL1HCWh_0qVPP?usp=sharing]() | [[link](https://colab.research.google.com/drive/1RXRZRqCZThI2zinxDmlsV6tDx-z4BK4g?authuser=1#scrollTo=5g90yFwq8iS2)]() |
| Ch6 | [https://colab.research.google.com/drive/16kbBKmZ0LcjKoX6Eag1URYE9r3j8FBOm?usp=sharing]() | [[link](https://colab.research.google.com/drive/17mwBu1Fm0Cujx9ogubMSObN40sQOOROS?authuser=1#scrollTo=yLWbtM0jpYUt)]() |
| Ch7 | [https://colab.research.google.com/drive/11t9VZS6iKZCqfmP2qJyg6VfLMCjG2nif?usp=sharing]() | [[link](https://colab.research.google.com/drive/1zEGdjWEnFPTEJYfXKdCBVJYySQMmHUl1?authuser=1#scrollTo=4fm48IxrUu30)]() |
| Ch8 | [https://colab.research.google.com/drive/1g3rFRUuPKh60ORGdgOwG7VJ20OGN3EJq?usp=sharing]() | [[link](https://colab.research.google.com/drive/1pDkf2gJCf0PSgLbfTK6-XxOzRDxPhc-I?authuser=1#scrollTo=b1aoM8wZw54M)]() |
| Ch9 | [https://colab.research.google.com/drive/1yjpPZA2qYiaIdvekVSA8B8gNP38dAe9i?usp=sharing]() | [[link](https://colab.research.google.com/drive/1-cqqjTNBKS4BbknVZrdjsfD-zHb8FJbi?authuser=1#scrollTo=yrCa6D0Z2vuX)]() |

## What we learned

Chapters 1, 2, & 3: Exploring and Cleaning Data

These chapters taught me that raw data is almost always a mess and needs serious work before it’s actually useful. I learned how to inspect a dataset's basic structure, spot missing values, and handle them through imputation or dropping rows. What surprised me most was how much missing data can quietly skew analysis if you don't check for it first, and how dropping unnecessary columns like `Rank` makes the whole dataset much cleaner to work with.

Chapter 4: Feature Engineering and Encoding

In this chapter, I realized that raw numbers and categories don't always give a model the full picture. Creating new combined features—like `Lemonade per Degree`—helps highlight relationships that weren't obvious at first glance. What really caught me off guard was how computers handle text differently based on meaning: ordered categories like `Little and Lots` can simply be converted to numbers, but unordered things like weather conditions need one-hot encoding so the model doesn't assume one weather type is "greater" than another.

Chapter 5: Scaling and Normalization

This chapter showed me why it's so important to put numerical features on equal footing. Without scaling, a model will naturally treat a column with big numbers like `Grades` (0 to 100) as far more important than `Study Hours` (0 to 20), simply because of scale. What surprised me was learning that scaling isn't always mandatory—it really depends on the specific machine learning model you choose to build.

Chapter 6: Dealing with Outliers

Here I learned how extreme values can throw off a model's understanding of normal patterns. Using methods like Z-scores and IQR gives us a mathematical way to flag data points that stick out too far from the rest. I was surprised to see how a single extreme number—like 100 in a set of small values—can get flagged differently depending on whether you use Z-scores or the IQR method.

Chapter 7: Feature Selection

This chapter showed me that having more data isn't always better, since keeping extra or useless features can actually slow down training and hurt model performance. I realized the difference between simply filtering variables using quick stats—like checking correlation heatmaps—and using active wrapper methods like RFECV. What surprised me most was how RFECV actually tests different combinations of features interactively with a model to find the absolute best subset.

Chapter 8: Constructing a Preprocessing Pipeline

This chapter taught me how to bundle all data preparation steps into one automated, repeatable workflow. Instead of manually applying transformations one by one, a pipeline acts like an assembly line that processes raw data cleanly every single time. What surprised me was how `ColumnTransformer` lets you route specific columns into completely different pipelines—like scaling numbers while one-hot encoding categories—all in a single execution step.

Chapter 9: Full Pipeline and Visualization

Bringing everything together on the Titanic dataset showed me the complete end-to-end preprocessing workflow. I learned how to clean missing values, discretize age into life stages, encode categories, and visualize the cleaned results. What surprised me most was seeing how much easier it is to spot real human patterns—like survival rates based on gender or passenger class—once the data is properly cleaned and visualized.
## Errors we found

List any mistake you found in the original notebooks, and the correct version.
There are real ones in there. Finding them earns points.

## Note on AI tools

We use ai tools such as Google Gemini and Chat Gpt that helps us to answer the Chapter Questions

## References

McKinney, W. (2021). Python for Data Analysis, 3rd ed. O'Reilly.
VanderPlas, J. Python Data Science Handbook.
Any other page or article you used.
