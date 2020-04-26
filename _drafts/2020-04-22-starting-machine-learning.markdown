---
layout: post
title:  "Starting Machine Learning"
date:   2020-04-22 00:44:42 -0700
categories: thoughts
tags: [cs, machine learning, iris, python]
author: "Brandon"
---
Documenting my journey of learning machine learning. Starting off with a mini project I found <a href = "https://machinelearningmastery.com/machine-learning-in-python-step-by-step/">online</a>. The goal is to train a program to identify the species of an Iris based off its morphological traits. They will be separated into Iris-setosa, Iris-versicolor, and Iris-virginica.

Step 1: Making sure all modules are in order and import. Modules I am using:
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
Step 5: Testing different models

<b>Gaussian Naive Bayes (NB)</b> is a probabilistic model that is based on Baye's theorem. Given prior probability, the theorem is able to predict the probability of the hypothesis.

{% highlight ruby linenos%}
gnb = GaussianNB()
y_pred = gnb.fit(x_train,y_train).predict(x_test)
{% endhighlight %}
`Accuracy: `
