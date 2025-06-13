# 📘2️⃣ Using Notebooks Effectively

Not every research project results in a full software package. Sometimes, the core of your work is a collection of analyses or experiments that can be best expressed as a collection of code snippets, visualizations, and narrative. In these cases, preparing a full software repository might feel like overkill or a barrier to sharing. This chapter explains how Jupyter notebooks can provide a good solution to make your analysis code openly accessible.

## 🚀 Jupyter Notebooks to the Rescue

```{image} /assets/jupyter-logo.png
:alt: Jupyter
:class: mb-2
:width: 200
:align: right
```

Jupyter notebooks offer a flexible, language-agnostic environment that blends code, rich text, and outputs in a single document. Whether you’re using Python, R, Julia, or another language, notebooks let you organize your work interactively. Combined with version control systems like Git and platforms like GitHub, notebooks provide a simple but powerful way to share reproducible research.

When you follow best coding practices (covered in the previous section), your notebooks become readable, reusable, and easier to maintain. Plus, thanks to native support on platforms like GitHub, users can preview both your code and its outputs without needing to run anything locally.

---

### Notebooks Support Multiple Languages

Jupyter is not limited to Python. It supports a wide variety of programming languages via "kernels," which are the computational engines that execute your code. Popular kernels include Python ([ipython](https://ipython.readthedocs.io/en/stable/install/kernel_install.html)), R ([IRkernel](https://irkernel.github.io/installation/)), Julia ([IJulia](https://julialang.github.io/IJulia.jl/stable/)), MATLAB ([Matlab Integration for Jupyter](https://au.mathworks.com/help/cloudcenter/ug/run-matlab-in-jupyter.html)) and many others. This flexibility allows you to write notebooks in the language best suited to your research domain or combine languages in the same project with multiple notebooks. (check here for an [exhaustive list of available kernels](https://gist.github.com/chronitis/682c4e0d9f663e85e3d87e97cd7d1624))


```{figure} /assets/jlab-launcher.png
---
height: 400px
name: jupyter-kernels
figclass: margin-caption
---
Whatever programming language you use, there's a good chance it already has a Jupyter integration.

```

### Native GitHub Rendering

GitHub automatically renders Jupyter notebooks, showing both the code cells and their outputs (plots, tables, text). [This](https://github.blog/news-insights/product-news/github-jupyter-notebooks-3/) makes it easy for collaborators, reviewers, or readers to explore your work directly in their browsers without downloading or running any code. The integration boosts transparency and lowers the barrier for others to understand and build upon your results.

### Integration with Live Execution Environments

One of the great strengths of notebooks is how easily they can be linked to live execution platforms:

- [**Google Colab**](https://colab.google/): Provides free cloud-hosted Jupyter environments with pre-installed libraries, GPU support, and seamless integration with [GitHub](https://colab.research.google.com/github/googlecolab/colabtools/blob/master/notebooks/colab-github-demo.ipynb). By simply adding a *Open in Colab* badge, others can run and modify your notebook instantly, no setup required (see [here](https://colab.research.google.com/github/googlecolab/colabtools/blob/master/notebooks/colab-github-demo.ipynb) for detail).

- [**Binder**](https://mybinder.org/): Offers a way to create custom, reproducible computing environments launched directly from your GitHub repository. Binder builds a Docker image with all dependencies defined in your repo (e.g., `requirements.txt`, `environment.yml`), allowing users to interact with your notebooks live in their browsers. (check [this step-by-step tutorial](https://book.the-turing-way.org/communication/binder/zero-to-binder) from The Turing Way to find out how)

These services make it simple to share not just static scripts, but fully executable research notebooks.

---

### Recommended directory structure

To keep your project organized and simple, consider a clear directory layout:

```{code-block} bash
──▶ project_directory/              # To be tracked by git
    ├── notebooks/                  # All Jupyter notebooks (.ipynb files)
    │   ├── step_1/                 # Divide your analysis into different steps
    │   │   └── analysis_1.ipynb
    │   ├── step_2/
    │   │   └── analysis_2.ipynb
    ┆   ┆
    │   └── README.md               # Overview or instructions for notebooks
    ├── data/                       # Raw/processed data files
    ├── scripts/                    # [OPTIONAL] Standalone scripts and utility functions
    ├── docs/                       # [OPTIONAL] Documentation
    ├── environment.yml             # or requirements.txt (for dependencies)
    └── README.md                   # Project overview and instructions
```

This structure separates notebooks from scripts and data, making your project easier to manage and maintain. By adopting this layout from the beginning, you can seamlessly track your progress with Git. When your project is ready for publication, you can simply make the repository public—sharing open code (and potentially data) alongside your manuscript.

### Additional Points to Consider

- **Clear Narrative and Modularization**: Keep your notebooks readable by using markdown cells to explain your analysis steps, and consider modularizing complex code into external scripts or functions imported into the notebook.

- **Avoid Large Outputs in Notebooks**: To keep notebooks lightweight and fast to load, avoid embedding very large data outputs or images. Instead, save large results externally and reference them.

- **Use Git LFS for large files**: If your notebooks or data files are large, consider using [**Git Large File Storage (LFS)**](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage) to manage them efficiently within your repository.
