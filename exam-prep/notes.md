Joakim Edvardsen

# Exam notes

## Course Content

- [x] [Supervised learning](#supervised)
- [x] [Unsupervised learning](#unsupervised)
- [x] Representing data and engineering features
- [x] [ML pipeline](#ml-pipelines)
- [x] Feature engineering & dimensionality reduction
  - [x] Hold out validation (Train, test, validate)
  - [x] [K-fold cross-validation](#kfold)
- [ ] Artificial neural networks
- [ ] Training deep neural nets
- [ ] Convolutional neural networks
- [ ] Recurrent neural networks
- [ ] GPUs & cloud computing tools

<h2 id="supervised">Superviced</h2>

Uses the data to predict a result. Iterativly makes better and better prediction by looking at the difference between it's prediction and the actual value (accuracy) and adjust the weights and biases accordingly (backwards propgation and gradient descent).

Usually more accurate then unsuperviced, but reqires all the data upfront with labels.

### Classification

Classifies the input into classes.

**Example:** spam vs not spam

### Regression

Output is a continuos value used to predict things like price and time.

**Example:** house pricing

<h2 id="unsupervised">Unsuperviced</h2>

Finds hidden patterns in the dataset. Cannot make predictions, only group data together.

### Clustering

Groups the data into different groups based on for example shape, color.

**Example:** Customer segmentation, grouping different customers into groups based on age, gender, hobbies etc...

### Association

Looks for relationsships within the dataset

**Example:** Store analyzing, to find which items are commonly bought together

<h2 id="ml-pipelines">ML Pipelines</h2>

- Automate ML workflows
- Iterative: every step is repeated to improve the accuracy of the model
- Not one-way flows. More like cyclic

### Pipeline parts

- Data collection
- Data cleaning
- Feature extraction
- Model validation
- Visualisation

### From slides

- Created to allow ata flow from raw format to useful information
- Provides mechanisms to cross-validate while setting different parameters

### My understanding / summary

When training a model, there are some hyperparameters involved (learning_rate, ephocs, etc). To manually tweek these till you get a good result for your model can be tedious. Therefore you can create a pipeline that iterates and progressivly makes the model better and better by tweeking these hyperparameters.

<h2 id="kfold">K-Fold Coss Validation</h2>

Drawbacks with train, test split is that you want to maximaze both the train and test sets. Also if you do not have a lot of data, you might not have enough to split it an still get good results.

With K-Fold, you split your data into k bins, where each bin has det same number of data points. Then you train your model and validate it where you leave one bin as your test set and the rest as your train set. You do this k times and each time you leave a different bin for your test set. At the end you take the average test results as your final result.

Drawback with this method is that it takes more computing time as you have to do the learning experiment k time, however you get a more accurate result

```python
k = 10                                # Number of bins

data = some_data                      # Load some data
bins = data.split(k)                  # Split it into k bins

for n in range(k):
  test_set = bins[n]                  # Pick one as test set
  train_set = binds - binds[n]        # The rest is then train set
  model.train(train_set)              # Train the model
  result += model.evaluate(test_set)  # Evaulate the model and store all result

return result / k                     # Return the average of all test results
```

_K-Fold algorithm sudo code_
