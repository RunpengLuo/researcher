---
layout: default
---

I always want to record the things I’ve learned and the good books I’ve read (or continue to read). Here, I share some of my favorite book titles, personal study notes, and short tutorials. Feel free to read and share them if you find them useful.

---

## Study Notes

* Bioinformatics Algorithms (from [this book](https://www.bioinformaticsalgorithms.org))
    * [Chapter 1. Genome Replication](files/docs/Bioinformatics_Algorithms___Chapter_1.pdf) <small>Dec 26, 2024</small>

---

## Tutorials

{% for post in site.posts %}* [{{ post.title }}]({{ site.baseurl }}{{ post.url }}) <small>{{ post.date | date: "%b %-d, %Y" }}</small>
{% endfor %}

---

## Favorite Textbooks

1. [Bioinformatics Algorithms (An Active Learning Approach)](https://www.bioinformaticsalgorithms.org) by Phillip Compeau & Pavel Pevzner
2. [Convex Optimization](https://web.stanford.edu/~boyd/cvxbook/) by Stephen Boyd & Lieven Vandenberghe
3. [Combinatorial Optimization (Algorithms and Complexity)](https://store.doverpublications.com/products/9780486402581) by Christos H. Papadimitriou & Kenneth Steiglitz
4. [Information Theory, Inference, and Learning Algorithms](https://www.inference.org.uk/mackay/itila/) by David J. C. MacKay
5. [Introduction to Probability](http://www.athenasc.com/probbook.html) by Dimitri P. Bertsekas & John N. Tsitsiklis
