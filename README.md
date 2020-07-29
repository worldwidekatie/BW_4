# BW_4

## For current up-to-date instructions, see the [Post Here MVP Algorithm Instructions](https://github.com/worldwidekatie/BW2/blob/master/Subreddit_MVP_Instructions.ipynb)

# **SFW UPDATES**
### * The SFW nearest neighbors can be downloaded [here](https://github.com/worldwidekatie/BW_4/blob/master/nn_cleaned.joblib)
### * The SFW Tfidf can be downloaded [here](https://github.com/worldwidekatie/BW_4/blob/master/tfidf_cleaned.joblib)
### * The link for the SFW subreddit data frame is:
```
df = pd.read_csv("https://raw.githubusercontent.com/worldwidekatie/BW_4/master/cleaned_subs.csv")
```
### * New Prediction Function:
```
def predict(title, body):
  predictions = []
  query = tfidf.transform([title+body])
  pred = model.kneighbors(query.todense())

  for i in pred[1][0]:
    if subreddits[i] not in predictions:
      predictions.append(subreddits[i])
  
  return predictions[:5]
  ```
