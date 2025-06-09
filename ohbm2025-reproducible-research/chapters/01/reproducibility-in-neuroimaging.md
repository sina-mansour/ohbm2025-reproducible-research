# 📗 Reproducibility in Neuroimaging

This chapter aims to highlight the importance of reproducible research practices and briefly explain what will be covered in the rest of the book.

## 🤨 Why Care about Reproducibility?

- **Science builds on science**, without reproducibility, findings can't be trusted or extended.
- In computational neuroscience and neuroimaging, findings are often results of complex pipelines, built with multiple software tools, and parameter choices.
- Without access to code, even small analytical tweaks can become untraceable.

> "Science is a social enterprise: independent and collaborative groups work to accumulate knowledge as a public good."
> 
> *Munafo et al. (2017)* {footcite:p}`munafo2017manifesto`

## 🤔 What's at Stake?

- **Credibility** of research outputs.

> "The authors of research papers have no obligation to share their data and code, and I have no obligation to believe anything they write."
>
> [*Andrew Gelman*](https://statmodeling.stat.columbia.edu/2023/09/10/the-authors-of-research-papers-have-no-obligation-to-share-their-data-and-code-and-i-have-no-obligation-to-believe-anything-they-write/) (professor of statistics and political science at Columbia University)

- **Wasted time** taken to re-implement procedures reported in previous works.
- **Reduced impact** of research findings, as they cannot be easily verified or built upon.

## 🔀 Categorizing Reproducibility:

{footcite:t}`botvinik2023reproducibility` identify three types of reproducibility:

1. **Analytical reproducibility**: Reproducing findings using the *same data* and *same methods*.
2. **Replicability**: Finding similar results in *independent datasets* using similar methods.
3. **Robustness to analytical variability**: Obtaining consistent results using *different analytical approaches*.

```{tip}
The goal of this session is to introduce practices for ensuring analytical reproducibility. This can serve as a foundation for achieving replicability and methodological robustness.
```

{footcite:t}`gorgolewski2016practical` cover 3 major topics in open science (see {numref}`OS-pillars`), with implications for reproducibility:
1. **Data**: Access to the original data is required to examine analytical reproducibility.
2. **Code**: Access to the implementation scripts is also needed. 
3. **Papers**: Access to documentations of methods, and interpretations of results.

```{figure} /assets/pillars.svg
---
height: 400px
name: OS-pillars
---
Three pillars of open science.{footcite:p}`gorgolewski2016practical`
```

```{tip}
In this session, we'll cover topics addressing **code** openness.
```

## 🚩 Let's Start

Now that we’ve covered why reproducibility matters and what this session will include, let’s jump in.
We’ll focus on two main topics:
- **{doc}`../02/reproducible-analysis-pipelines`**
- **{doc}`../03/reproducible-visualizations`**

---

## 📑 References

```{footbibliography}
```
