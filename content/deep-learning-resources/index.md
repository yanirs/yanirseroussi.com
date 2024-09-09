---
title: Deep learning resources
author: Yanir Seroussi
type: page
summary: Useful posts and papers on the topic of deep learning (circa 2015).
date: 2015-07-06T00:38:44+00:00

---
This page summarises the deep learning resources I've consulted in [my album cover classification project][1].

### Tutorials and blog posts

  * <a href="http://cs231n.github.io/" target="_blank" rel="noopener">Convolutional Neural Networks for Visual Recognition Stanford course notes</a>: an excellent resource, very up-to-date and useful, despite still being a work in progress
  * <a href="http://deeplearning.net/tutorial/" target="_blank" rel="noopener">DeepLearning.net's Theano-based tutorials</a>: not as up-to-date as the Stanford course notes, but still a good introduction to some of the theory and general Theano usage
  * <a href="http://lasagne.readthedocs.org/en/latest/" target="_blank" rel="noopener">Lasagne's documentation and tutorials</a>: still a bit lacking, but good when you know what you're looking for
  * <a href="https://github.com/enlitic/lasagne4newbs" target="_blank" rel="noopener">lasagne4newbs</a>: Lasagne's convnet example with richer comments
  * <a href="http://danielnouri.org/notes/2014/12/17/using-convolutional-neural-nets-to-detect-facial-keypoints-tutorial/" target="_blank" rel="noopener">Using convolutional neural nets to detect facial keypoints tutorial</a>: the resource that made me want to use Lasagne
  * <a href="http://benanne.github.io/2015/03/17/plankton.html" target="_blank" rel="noopener">Classifying plankton with deep neural networks</a>: an epic post, which I found while looking for Lasagne examples
  * <a href="https://en.wikipedia.org/wiki/Main_Page" target="_blank" rel="noopener">Various Wikipedia pages</a>: a bit disappointing &ndash; the above resources are much better

### Papers

  * <a href="http://arxiv.org/abs/1412.6980" target="_blank" rel="noopener">Adam: a method for stochastic optimization (Kingma and Ba, 2015)</a>: an improvement over SGD with Nesterov momentum, AdaGrad and RMSProp, which I found to be useful in practice
  * <a href="http://papers.nips.cc/paper/4443-algorithms-for-hyper-parameter-optimization" target="_blank" rel="noopener">Algorithms for Hyper-Parameter Optimization (Bergstra et al., 2011)</a>: the work behind <a href="https://github.com/hyperopt/hyperopt" target="_blank" rel="noopener">Hyperopt</a> &ndash; pretty useful stuff, not only for deep learning
  * <a href="http://arxiv.org/abs/1412.1710" target="_blank" rel="noopener">Convolutional Neural Networks at Constrained Time Cost (He and Sun, 2014)</a>: interesting experimental work on the tradeoffs between number of filters, filter sizes, and depth &ndash; deeper is better (but with diminishing returns); smaller filter sizes are better; delayed subsampling and spatial pyramid pooling are helpful
  * <a href="http://arxiv.org/abs/1404.7828" target="_blank" rel="noopener">Deep Learning in Neural Networks: An Overview (Schmidhuber, 2014)</a>: 88 pages and 888 references (35 content pages) &ndash; good for finding references, but a bit hard to follow; not so good for understanding how the various methods work and how to use or implement them
  * <a href="http://arxiv.org/abs/1409.4842" target="_blank" rel="noopener">Going deeper with convolutions (Szegedy et al., 2014)</a>: the GoogLeNet paper &ndash; interesting and compelling results, especially given the improvement in performance while reducing computational complexity
  * <a href="http://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks" target="_blank" rel="noopener">ImageNet Classification with Deep Convolutional Neural Networks (Krizhevsky et al., 2012)</a>: the classic paper that arguably started (or significantly boosted) the recent buzz around deep learning &ndash; many interesting ideas; fairly accesible
  * <a href="http://www.cs.toronto.edu/~gdahl/papers/momentumNesterovDeepLearning.pdf" target="_blank" rel="noopener">On the importance of initialization and momentum in deep learning (Sutskever et al., 2013)</a>: applying Nesterov momentum to deep learning &ndash; good read, simple concept, interesting results
  * <a href="http://jmlr.org/papers/volume13/bergstra12a/bergstra12a.pdf" target="_blank" rel="noopener">Random Search for Hyper-Parameter Optimization (Bergstra and Bengio, 2012)</a>: very compelling reasoning and experiments showing that random search outperforms grid search in many cases
  * <a href="http://sergeykarayev.com/files/1311.3715v3.pdf" target="_blank" rel="noopener">Recognizing Image Style (Karayev et al., 2014)</a>: identifying image style, which is similar to album genre &ndash; found that using models pretrained on ImageNet yielded the best results in some cases
  * <a href="http://arxiv.org/abs/1409.1556" target="_blank" rel="noopener">Very deep convolutional networks for large scale image recognition (Simonyan and Zisserman, 2014)</a>: VGGNet paper &ndash; interesting experiments and architectures &ndash; deep and homogeneous
  * <a href="http://arxiv.org/abs/1311.2901" target="_blank" rel="noopener">Visualizing and Understanding Convolutional Networks (Zeiler and Fergus, 2013)</a>: interesting work on visualisation, but I'll need to apply it to understand it better

 [1]: https://yanirseroussi.com/2015/06/06/hopping-on-the-deep-learning-bandwagon/
