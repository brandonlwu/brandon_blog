---
layout: post
title:  "Starting Machine Learning"
date:   2020-04-26 00:44:42 -0700
categories: thoughts
tags: [cs, machine learning, iris, python]
author: "Brandon"
---
Documenting my journey of learning machine learning. Starting off with a mini project I found <a href = "https://machinelearningmastery.com/machine-learning-in-python-step-by-step/">online</a>. The goal is to train a program to identify the species of an Iris based off its morphological traits. They will be separated into Iris-setosa, Iris-versicolor, and Iris-virginica.

Step 1: Make sure all modules are in order and import. Modules I use:
<ul>
<li>sklearn</li>
<li>scipy</li>
<li>pandas</li>
<li>matplotlib</li>
<li>numpy</li>
</ul>
{% highlight ruby linenos%}
import sklearn
print('Python: {}'.format(sklearn.version))
#and so forth with other modules
{% endhighlight %}
Step 2: Load Dataset.
{% highlight ruby linenos%}
names = ['sepal-length', 'sepal-width', \
'petal-length', 'petal-width', 'class']
dataset = read_csv(url, names=names)
{% endhighlight %}
Step 3: Visualize Data:
{% highlight ruby linenos%}
scatter_matrix(dataset)
pyplot.show()
{% endhighlight %}
Which will appear like the following:
<img src="{{ 'assets/img/iris_visualize_data.png' | relative_url }}">
Step 4: Split the Data Set into a training and test set.
{% highlight ruby linenos%}
x = array[:,0:4]
y = array[:,4]
x_train, x_test, y_train, y_test = train_test_split(x, y, \
  test_size=0.20, random_state=1)
{% endhighlight %}
Step 5: Create different models

<b>Gaussian Naive Bayes (NB)</b> uses prior probability to predict the probability of the hypothesis.

{% highlight ruby %}
models = []
models.append(('NB', GaussianNB()))
{% endhighlight %}

<b>Logistic Regression</b> is conceptually similar to linear regression. A logistical model is fit to produce a categorical output.

{% highlight ruby %}
models.append(('LR', LogisticRegression(solver='liblinear', \
multi_class='ovr')))
{% endhighlight %}

<b>Linear Discrimination Analysis (LDA)</b> is similar to PCA. LDA maximizes the difference of separation of known categories for identification.

{% highlight ruby %}
models.append(('LDA', LinearDiscriminantAnalysis()))
{% endhighlight %}

<b>K-nearest Neighbors</b> uses the closest k number of neighbors to generate a prediction.

{% highlight ruby %}
models.append(('KNN', KNeighborsClassifier()))
{% endhighlight %}

<b>Decision Trees</b> employ a tree of decision-nodes to create a prediction.

{% highlight ruby %}
models.append(('CART', DecisionTreeClassifier()))
{% endhighlight %}

<b>Support Vector Machines</b> create a support vector classifier to create predictions.

{% highlight ruby %}
models.append(('SVM', SVC(gamma='auto')))
{% endhighlight %}

Step 6: Test Models
{% highlight ruby %}
for name, model in models:
	kfold = StratifiedKFold(n_splits=10, random_state=1,\
        shuffle=True)
	cv_results = cross_val_score(model, X_train, Y_train,\
        cv=kfold, scoring='accuracy')
	results.append(cv_results)
	names.append(name)
	print('%s: %f (%f)'%(name,cv_results.mean(),cv_results.std()))
{% endhighlight %}

`Results:` <br>
`NB: 0.951166 (0.052812)`<br>
`LR: 0.955909 (0.044337)`<br>
`LDA: 0.975641 (0.037246)`<br>
`KNN: 0.950524 (0.040563)`<br>
`CART: 0.958858 (0.053754)`<br>
`SVM: 0.983333 (0.033333)`
