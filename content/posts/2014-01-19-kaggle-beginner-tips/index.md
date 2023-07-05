---
title: Kaggle beginner tips
author: Yanir Seroussi
type: post
date: 2014-01-19T10:34:28+00:00
url: /2014/01/19/kaggle-beginner-tips/
summary: First post! An email I sent to members of the Data Science Sydney Meetup with tips on how to get started with Kaggle competitions.
tags:
  - data science
  - Kaggle
  - Kaggle beginners

---
These are few points from an email I sent to members of the [Data Science Sydney Meetup][1]. I suppose other Kaggle beginners may find it useful.

My first steps when working on a new competition are:

  * Read all the instructions carefully to understand the problem. One important thing to look at is what measure is being optimised. For example, minimising the mean absolute error (MAE) may require a different approach from minimising the mean square error (MSE).
  * Read messages on the forum. Especially when joining a competition late, you can learn a lot from the problems other people had. And sometimes there's even code to get you started (though code quality may vary and it's not worth relying on).
  * Download the data and look at it a bit to understand it better, noting any insights you may have and things you would like to try. Even if you don't know _how_ to model something, knowing _what_ you want to model is half of the solution. For example, in the <a href="http://www.kaggle.com/c/dsg-hackathon" target="_blank" rel="noopener">DSG Hackathon</a> (predicting air quality), we noticed that even though we had to produce hourly predictions for pollutant levels, the measured levels don't change every hour (probably due to limitations in the measuring equipment). This led us to try a simple "model" for the first few hours, <a href="http://www.kaggle.com/c/dsg-hackathon/forums/t/1821/general-approaches-to-partitioning-the-models/10631#post10631" target="_blank" rel="noopener">where we predicted exactly the last measured value</a>, which proved to be one of our most valuable insights. Stupid and uninspiring, but we did finish 6th :-). The main message is: look at the data!
  * Set up a local validation environment. This will allow you to iterate quickly without making submissions, and will increase the accuracy of your model. For those with some programming experience: local validation is your private development environment, the public leaderboard is staging, and the private leaderboard is production.<br /> What you use for local validation depends on the type of problem. For example, for classic prediction problems you may use one of the classic <a href="https://en.wikipedia.org/wiki/Cross-validation_%28statistics%29" target="_blank" rel="noopener">cross-validation techniques</a>. For forecasting problems, you should try and have a local setup that is as close as possible to the setup of the leaderboard. In the <a href="https://www.kaggle.com/c/yandex-personalized-web-search-challenge/">Yandex competition</a>, the leaderboard is based on data from the last three days of search activity. You should use a similar split for the training data (and of course, use exactly the same local setup for all the team members so you can compare results).
  * Get the submission format right. Make sure that you can reproduce the baseline results locally.

Now, the way things often work is:

  * You try many different approaches and ideas. Most of them lead to nothing. Hopefully some lead to something.
  * Create ensembles of the various approaches.
  * Repeat until you run out of time.
  * Win. Hopefully.

Note that in many competitions, the differences between the top results are not statistically significant, so winning may depend on luck. But getting one of the top results also depends to a large degree on your persistence. To avoid disappointment, I think the main goal should be to learn things, so spend time trying to understand how the methods that you're using work. Libraries like sklearn make it really easy to try a bunch of models without understanding how they work, but you're better off trying less things and developing the ability to reason about why they work or not work.

An analogy for programmers: while you can use an array, a linked list, a binary tree, and a hash table interchangeably in some situations, understanding when to use each one can make a world of difference in terms of performance. It's pretty similar for predictive models (though they are often not as well-behaved as data structures).

Finally, it's worth watching <a href="http://anotherdataminingblog.blogspot.com.au/2013/10/techniques-to-improve-accuracy-of-your_17.html" target="_blank" rel="noopener">this video</a> by Phil Brierley, who won a bunch of Kaggle competitions. It's really good, and doesn't require much understanding of R.

Any comments are welcome!

 [1]: http://www.meetup.com/Data-Science-Sydney/
