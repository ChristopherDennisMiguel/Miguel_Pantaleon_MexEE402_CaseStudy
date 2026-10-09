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
| Ch1_2_3 | [Link](https://colab.research.google.com/drive/1yMTUnKs2T82QIF32Wto_s7ubeNjQndl2?usp=sharing) | [Link](https://colab.research.google.com/drive/17PpWMHbsJXVUMhvc2t9jUeS-8CLLLKKv?usp=sharing) |
| Ch4 | [Link](https://colab.research.google.com/drive/18W2wlBKByAaSpfa5qHaW2A3Ql6OkStYt?usp=sharing) | [Link](https://colab.research.google.com/drive/1kHfqeRglQWC6HeIzIslxM2a40RfpKiX3?usp=sharing) |
| Ch5 | [Link](https://colab.research.google.com/drive/1QDMYzqzW6_DhhU1QdPVXL1HCWh_0qVPP?usp=sharing) | [Link](https://colab.research.google.com/drive/1RXRZRqCZThI2zinxDmlsV6tDx-z4BK4g?usp=sharing) |
| Ch6 | [Link](https://colab.research.google.com/drive/16kbBKmZ0LcjKoX6Eag1URYE9r3j8FBOm?usp=sharing) | [Link](https://colab.research.google.com/drive/17mwBu1Fm0Cujx9ogubMSObN40sQOOROS?usp=sharing) |
| Ch7 | [Link](https://colab.research.google.com/drive/11t9VZS6iKZCqfmP2qJyg6VfLMCjG2nif?usp=sharing) | [Link](https://colab.research.google.com/drive/1zEGdjWEnFPTEJYfXKdCBVJYySQMmHUl1?usp=sharing) |
| Ch8 | [Link](https://colab.research.google.com/drive/1g3rFRUuPKh60ORGdgOwG7VJ20OGN3EJq?usp=sharing) | [Link](https://colab.research.google.com/drive/1pDkf2gJCf0PSgLbfTK6-XxOzRDxPhc-I?usp=sharing) |
| Ch9 | [Link](https://colab.research.google.com/drive/1yjpPZA2qYiaIdvekVSA8B8gNP38dAe9i?usp=sharing) | [Link](https://colab.research.google.com/drive/1-cqqjTNBKS4BbknVZrdjsfD-zHb8FJbi?usp=sharing) |

## What we learned

Chapters 1, 2, & 3: Exploring and Cleaning Data

These chapters taught us that raw data is almost always a mess and needs serious work before it’s actually useful. We learned how to inspect a dataset's basic structure, spot missing values, and handle them through imputation or dropping rows. What surprised us most was how much missing data can quietly skew analysis if you don't check for it first, and how dropping unnecessary columns like `Rank` makes the whole dataset much cleaner to work with.

Chapter 4: Feature Engineering and Encoding

In this chapter, we realized that raw numbers and categories don't always give a model the full picture. Creating new combined features—like `Lemonade per Degree`—helps highlight relationships that weren't obvious at first glance. What really caught us off guard was how computers handle text differently based on meaning: ordered categories like `Little and Lots` can simply be converted to numbers, but unordered things like weather conditions need one-hot encoding so the model doesn't assume one weather type is "greater" than another.

Chapter 5: Scaling and Normalization

This chapter showed us why it's so important to put numerical features on equal footing. Without scaling, a model will naturally treat a column with big numbers like `Grades` (0 to 100) as far more important than `Study Hours` (0 to 20), simply because of scale. What surprised us was learning that scaling isn't always mandatory—it really depends on the specific machine learning model you choose to build.

Chapter 6: Dealing with Outliers

Here, we learned how extreme values can throw off a model's understanding of normal patterns. Using methods like Z-scores and IQR gives us a mathematical way to flag data points that stick out too far from the rest. We was amaze to see how a single extreme number—like 100 in a set of small values—can get flagged differently depending on whether you use Z-scores or the IQR method.

Chapter 7: Feature Selection

We learned from this chapter how to select the best features by identifying which data is most relevant to the analysis. Also, by removing unnecessary features it can improve the model's performance and make the data easier to understand. What struck us is how much data can be reduced while still keeping the most important information.

Chapter 8: Constructing a Preprocessing Pipeline

We learned from this chapter how different data preparation steps work together in one workflow that can be repeated consistently. Instead of manually applying transformations one by one, a pipeline acts like an assembly line that processes raw data cleanly every single time. What surprised us was how ColumnTransformer lets you route specific columns into completely different pipelines, like scaling numbers while one-hot encoding categories, all in a single execution step.

Chapter 9: Full Pipeline and Visualization

We learned from this chapter how to apply different data preprocessing steps to the Titanic dataset, from handling missing values and grouping ages into life stages to encoding categories and visualizing the results. We understood how these steps help organize the data and make it easier to analyze. What fascinates us most was how much easier it is to identify patterns, such as differences in survival rates based on gender or passenger class, after the data has been properly cleaned and visualized.

## Errors we found

 Chapters 1–3: Warning from `inplace=True`
 What is Wrong: Using `inplace=True` triggers a `FutureWarning` in Pandas because modifying DataFrames in-place will no longer be supported in upcoming Pandas versions.
 - The Wrong Version:
   
   ```df['Year'].fillna(df['Year'].mean(), inplace=True)```
   
  ```df['Publisher'].fillna(df['Publisher'].mode()[0], inplace=True)```

  - The Correct Version:

    ```df['Year'] = df['Year'].fillna(df['Year'].mean())```
    
```df['Publisher'] = df['Publisher'].fillna(df['Publisher'].mode()[0])```

Chapter 4: Out-of-Bounds Edge Case in Binning Boundaries
What is Wrong: By default, `pd.cut()` uses right-inclusive intervals, meaning the first bin is $(70, 75]$. If your dataset happens to contain a temperature value of exactly 70, `pd.cut()` will fail to include it in the `'cool'` bin and assign it a `NaN` (missing) value instead.

- The Wrong Version

```bins = [70, 75, 85, 95, 100]```
```labels = ['cool', 'warm', 'hot', 'very hot']```
```df['Temperature Category'] = pd.cut(df['Temperature'], bins=bins, labels=labels)```

- The Correct Version:
  
  ```# Set include_lowest=True to catch the minimum boundary value (70)```
  
```df['Temperature Category'] = pd.cut(df['Temperature'], bins=bins, labels=labels, include_lowest=True)```

Chapter 6: Missing the Outlier with Z-score Cutoff

What is Wrong: The number `100` is obviously an outlier, but in a small dataset of 8 numbers, `100` pulls up the mean ($26.5$) and standard deviation ($28.1$) so high that its Z-score is only 2.615. Since 2.615 is less than 3, the threshold of `> 3` completely misses it.
- The Wrong Version:
  
```# Threshold set to > 3```

```outliers = data[np.abs(z_scores) > 3]```

```print("Outliers: ", outliers)```

```# Output: Outliers: []```

- The Correct Version
  
 ``` # Lower threshold to 2.5 for small sample sizes```

```outliers = data[np.abs(z_scores) > 2.5]```

```print("Outliers: ", outliers)```

```# Output: Outliers: [100]```

Chapter 9: Plotting the Wrong Column Index in NumPy Array
What is Wrong: `titanic_preprocessed` is a raw NumPy array output from `ColumnTransformer`. Column index `2` actually holds a 0/1 binary variable `(cat__Embarked_S)`, not the age data. This creates a histogram showing only 0s and 1s instead of age distributions.
- The Wrong Version:
  
```plt.hist(titanic_preprocessed[:, 2], alpha=0.5, label='After discretization')```

- The Correct Version:
 ``` # Use the named column from the converted DataFrame```

```plt.hist(titanic_preprocessed_df['num__Age'], alpha=0.5, label='After discretization')```

## Note on AI tools

We use ai tools such as Google Gemini and Chatgpt that helps us to answer the Chapter Questions and finding the errors.

## References

McKinney, W. (2021). Python for Data Analysis, 3rd ed. O'Reilly.
VanderPlas, J. Python Data Science Handbook.
Any other page or article you used.
