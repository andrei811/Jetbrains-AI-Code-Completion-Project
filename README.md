# JetBrains AI Code Completion Evaluation Project

## Project Overview
This project evaluates the performance of a code completion model on examples generated from a personal project repository. The evaluation is based on the quality of the model's completions in predicting the missing middle part of the code, simulating real-world scenarios. The dataset is created by splitting the code into three parts: prefix, middle, and suffix. The model is then tested on its ability to predict the missing middle.

Manual review and automatic metrics such as Exact Match, chrf, Levenshtein Distance, and Jaro-Winkler Similarity are used to evaluate the quality of the model's predictions.

## Repository Contents
1. `dataset.json` \
This file contains the dataset of code completion examples. Each example is split into three parts: \
`Prefix`: The code before the cursor. \
`Middle`: The code that is missing and needs to be predicted by the model. \
`Suffix`: The code after the cursor. 

2. `preprocess.ipynb` \
A Jupyter notebook used to preprocess the code examples and split them into prefix, middle, and suffix parts. This notebook also performs initial setup and cleaning of the code before using it for testing the model.
 
3. `final_analysis.txt` \
A report containing the final analysis of the model’s performance. It includes a manual review of the model’s predictions, an evaluation of the automatic metrics, and conclusions about the model's strengths and weaknesses in code completion.

## Steps
### Preprocessing the Dataset
Created `preprocess.ipynb` to store preprocessed code examples from the repository. This notebook splits the code into the required prefix, middle, and suffix sections and saves the processed dataset into dataset.json.

### Running the Code Completion Model
Loaded the dataset and passed it to an open-source code completion model to predict the middle part of the code.

### Evaluation
Used the dataset and the predictions to evaluate the performance of the model. Metrics like Exact Match, chrf, Levenshtein Distance, and Jaro-Winkler Similarity can be computed based on the comparison of the predicted middle code and the actual code from the dataset.

### Analysis
The results of the model evaluation, including manual reviews, are available in `final_analysis.txt`. Reviewed the findings and analyze how well the model performed, paying attention to common patterns of failure or success.

### Metrics Overview
***Exact Match***: Measures whether the model's prediction exactly matches the missing code. \
***chrf***: Character-level F1 score, useful for partial matches. \
***Levenshtein Distance***: Measures how many single-character edits (insertions, deletions, substitutions) are needed to change the predicted string into the correct one. \
***Jaro-Winkler Similarity***: Measures how similar two strings are, with a focus on the beginning of the strings.

## Findings
The `chrf` metric correlated better with manual reviews, particularly for partial correctness. The `Jaro-Winkler` similarity correlated good with my judgement.
Exact matches were rare, highlighting the difficulty of precisely predicting code completions.
Some models correctly predicted patterns but used different variable names or syntax, which could still lead to functional correctness despite not being an exact match.

## Conclusion
This project provided insights into how open-source code completion models perform on custom datasets. The combination of metrics and manual review offers a thorough evaluation approach. Future work could involve exploring ways to improve model accuracy, particularly for specific use cases like handling user-defined variables or complex logic structures.

For more details, refer to the `final_analysis.txt` file.