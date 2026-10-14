# SMS Spam Classification — Simple Assignment

Source: https://www.kaggle.com/datasets/uciml/sms-spam-collection-dataset

This predicts ham/spam, not positive/negative sentiment. The project follows the provided finalproject.ipynb teaching style, with separate preprocessing cells and separately trained models. The original Kaggle spam.csv is included. All notebook code cells were executed; results are real outputs.

## Run on Kaggle
1. Open the source dataset and create a new notebook.
2. Import SMS_Spam_Classification_Basic.ipynb through the File menu.
3. Add the dataset under Input; check spam.csv is visible.
4. Run all cells in order. The loader searches /kaggle/input automatically.
5. Save Version with outputs, make it public if your teacher requires, and copy YOUR notebook URL.

## Run on Colab
1. Open https://colab.research.google.com/ and upload the notebook.
2. Upload spam.csv using the Files sidebar.
3. Run all cells. If necessary, run %pip install nltk first.
4. No NLTK corpus downloads are required.

## Submit on GitHub
1. Create a repository such as sms-spam-classification.
2. Extract the project ZIP.
3. Add file > Upload files: add the notebook, README, CSV and outputs folder.
4. Commit the files; submit your repository URL with your saved Kaggle notebook URL.

## Important choices
- Cleaning is deterministic and occurs before the stratified 80/20 split (seed 42).
- Exact raw and cleaned-text duplicates are removed before splitting.
- Empty cleaned messages are removed; this changes the population being evaluated.
- Bag-of-Words vocabulary and TF-IDF vocabulary/IDF are fitted only on training text.
- No pipelines or imputers. The three models are trained separately, not in a loop.
- Spam (1) is the positive class for F1. A classification report includes both classes.
- Top words are alphabetic stemmed tokens ranked by the primary Naive Bayes model's log probability ratio between spam and ham, not raw frequency. SMS abbreviations and dataset artifacts may appear.
- Numbers are removed to follow the reference; they can be useful in other spam models.
- Results describe one split; there is no claim of a universally best model.

## Conclusion
Bag-of-Words + Naive Bayes achieved the highest spam F1-score on this split (0.9304), with an accuracy of 98.42%. F1 is useful because ham messages are much more common than spam, so high accuracy alone can hide missed spam. These results come from one held-out split and do not establish that the same model will always perform best on new datasets.
