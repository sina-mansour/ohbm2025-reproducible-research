# 📙2️⃣ Visualization Tools Overview

This chapter offers a broad overview of tools and libraries that support the programmatic creation of publication-quality figures. While I don’t consider myself an expert in scientific visualization, I’ve explored a variety of tools in my own research, and I hope this section provides a helpful starting point for others. Since my experience is primarily with Python, the tools discussed here are mostly Python-based. However, I’ve included links at the end of the chapter that point to similar resources for other programming environments.

Most tools are introduced only briefly, with links to more comprehensive guides. The goal is to highlight what’s possible and to help you discover tools that might suit your own research needs.

The next two sections will cover general-purpose and neuroimaging-specific visualization libraries, respectively.

## 📊 General Visualization Tools

This section briefly introduces a set of Python libraries commonly used for general-purpose data visualization. These tools are widely applicable across scientific disciplines and can be used to generate high-quality plots for publications, presentations, and exploratory analysis.

### Basic Plotting Libraries

Two of the most widely used libraries for data visualization in Python are [**Matplotlib**](https://matplotlib.org/stable/plot_types/index.html) and [**Seaborn**](https://seaborn.pydata.org/examples/index.html):

- [**Matplotlib**](https://matplotlib.org/stable/plot_types/index.html) is a powerful and flexible low-level library for creating plots. It offers fine-grained control over every aspect of a figure.

```{figure} /assets/matplotlib.webp
---
width: 100%
name: matplotlib
---
A gallery of various plot types generated via [**Matplotlib**](https://matplotlib.org/stable/plot_types/index.html).

```

- [**Seaborn**](https://seaborn.pydata.org/examples/index.html) is built on top of Matplotlib and provides a higher-level, more convenient API, particularly well-suited for statistical data visualization.

```{figure} /assets/seaborn.webp
---
width: 100%
name: seaborn
---
A gallery of various plot types generated via [**Seaborn**](https://seaborn.pydata.org/examples/index.html).

```

These libraries support a wide range of common plot types—including line plots, scatter plots, bar plots, histograms, box plots, heatmaps, violin plots, and more—which you can explore in detail through the linked gallery pages.

Some key features worth highlighting:

- ✅ **Multi-panel layouts**: You can compose complex, multi-panel figures entirely within Matplotlib (and Seaborn), making them suitable for direct inclusion in publications.

```{figure} /assets/gridspec.webp
---
height: 300px
name: gridspec
---
Matplotlib's [`Gridspec`](https://matplotlib.org/stable/gallery/subplots_axes_and_figures/gridspec_multicolumn.html) provides a flexible way to make multiple panels in a single figure.

```

- ✅ **Flexible output formats**: Export figures to various formats such as PNG, PDF, SVG, and EPS.

- ✅ **LaTeX rendering**: Seamless integration with LaTeX lets you render mathematical notation directly in your plots.

```{figure} /assets/equations.webp
---
height: 300px
name: equations
---
Matplotlib has [built-in support for latex](https://matplotlib.org/stable/gallery/text_labels_and_annotations/tex_demo.html), making it possible to integrate equations in figures.

```

- ✅ **Integration with NumPy/Pandas**: Native support for working with common data structures.

We won’t cover how to write basic plotting scripts here, but links to tutorials and documentation are provided at the end of this chapter.

### Supporting Data Structures

In neuroimaging and other data-intensive fields, efficiently managing and transforming large datasets is essential. Several foundational Python libraries serve as the backbone of many visualization workflows:

- [**NumPy**](https://numpy.org/): Provides fast and efficient numerical operations on arrays and matrices.
- [**Pandas**](https://pandas.pydata.org/): Offers powerful data structures (like `DataFrame`) for tabular data, with built-in methods for handling missing data, filtering, grouping, and more.
- [**Xarray**](https://docs.xarray.dev/en/stable/): Designed for N-dimensional labeled arrays (e.g., time × region × subject), making it especially useful for spatiotemporal datasets and more complex data formats.

Most visualization libraries can directly accept these structures as input, making them interoperable within scientific analysis pipelines. For instance, a `.csv` file can be loaded into a `pandas.DataFrame`, which can then be passed directly to Seaborn for visualization.

### Interactive Visualizations

While static plots are great for publications, interactive visualizations are invaluable for data exploration and sharing results in dynamic formats (e.g., web dashboards, notebooks). Several libraries support building rich, interactive graphics:

- [**Plotly**](https://plotly.com/python/): Offers intuitive syntax for interactive plots, with features like hover info, zoom, and click events.

```{figure} /assets/plotly.webp
---
width: 100%
name: plotly
---
A gallery of various plot types generated via [**Plotly**](https://plotly.com/python/).

```

```{figure} /assets/plotly-interactive.webp
---
width: 100%
name: plotly-interactive
---
[**Plotly**](https://plotly.com/python/) can generate interactive visualizations.

```

- [**Altair**](https://altair-viz.github.io/gallery/index.html#example-gallery): A declarative library built on the Vega-Lite grammar of graphics, great for producing concise and interactive charts.
- [**Bokeh**](https://bokeh.org/): Ideal for building interactive dashboards or embedding visualizations in web applications.
- [**Panel**](https://panel.holoviz.org/): A versatile library for creating interactive apps and dashboards, supporting multiple plotting libraries (e.g., Bokeh, Plotly, Matplotlib, Altair) and well-suited for use in notebooks or standalone web apps.
- [**ipywidgets**](https://ipywidgets.readthedocs.io/en/stable/): Useful for adding interactivity within Jupyter notebooks, especially when combined with Matplotlib or Plotly.
- [**Dash**](https://dash.plotly.com/): A framework (built on top of Plotly) for creating full web applications with interactive graphs and controls using pure Python.

These tools are particularly useful in designing exploratory analysis, making interactive reports, and building reproducible visualizations inside notebooks.

### Visualizing Large Datasets with Shaders

For very large datasets, such as scatter plots with many points, traditional plotting libraries can become unresponsive or fail to render efficiently. This is where GPU-accelerated, shader-based visualization becomes useful.

[**Datashader**](https://datashader.org/) (by HoloViz) is specifically designed to render huge datasets by computing aggregate representations (with GPU support). Instead of plotting individual points, it computes and shades the density of data in image space, resulting in clean, informative visualizations even with billions of points.

```{figure} /assets/datashader.jpg
---
height: 400px
name: datashader
---
Datashader can be used to visualize dynamical system attractors (with 10 million points each).

```

### Choosing Effective Colormaps

Colormaps are a fundamental component of scientific visualization, shaping how patterns and contrasts in data are perceived. Poor choices can obscure structure or introduce misleading gradients.

Key considerations:
- **Perceptual uniformity**: Changes in value should be perceived evenly across the range.
- **Data type**: Use sequential colormaps for ordered data, diverging for values around a central reference (e.g., ± change), and categorical for discrete labels.

Matplotlib and Seaborn offer a variety of useful palettes; for instance, `viridis`, `plasma`, and `cividis` are perceptually uniform. For a wider range of options, the [**Colorcet**](https://colorcet.com/gallery.html) package provides a rich set of perceptually uniform and publication-ready colormaps designed with clarity and aesthetics in mind.

```{figure} /assets/colorcet.webp
---
width: 100%
name: colorcet
---
The [**Colorcet**](https://colorcet.com/gallery.html) package contains a wide array of perceptually uniform colormaps to suit different use cases.

```

Using appropriate colormaps not only improves figure readability and aesthetics, but also upholds scientific integrity by avoiding unintentional distortions in the data's visual representation.

---

## 🧠 Neuroimaging Visualization Tools

Having introduced a suite of general-purpose data visualization tools, we now turn to software packages that are specifically tailored for neuroscience and neuroimaging. These tools are designed to handle domain-specific data formats and support visualizations that are uniquely relevant to brain imaging research.

```{note}
This list includes several representative tools for each visualization type, but it is by no means exhaustive. We provide links to broader, community-maintained lists at the end of the section and encourage readers to explore online, as the neuroimaging ecosystem is constantly evolving.
```

### Handling Neuroimaging Data

Before visualization, neuroimaging datasets must be loaded and decoded into memory. The following Python libraries provide robust support for a variety of brain imaging file formats:

- [**NiBabel**](https://nipy.org/nibabel/): A foundational library for reading and writing many imaging file formats such as NIfTI, CIFTI, GIFTI, and FreeSurfer surfaces/labels.
- [**DIPY**](https://dipy.org/): A powerful library for diffusion MRI analysis and tractography, including support for DICOM/NIfTI I/O.


### Volume Slice Rendering

A foundational form of neuroimaging visualization involves displaying anatomical or functional slices from 3D volumetric scans (e.g., T1-weighted MRI, statistical maps). These figures are ubiquitous in the literature for their clarity and ease of interpretation.

```{figure} /assets/vsr.webp
---
width: 100%
name: vsr
---
An example of volume slice rendering, adapted from {footcite:t}`bolt2025autonomic`.

```

📦 Python tools for generating volume slice renders:
- [**NiBabel**](https://nipy.org/nibabel/coordinate_systems.html)

  ```{figure} /assets/nibabel.png
  ---
  width: 100%
  name: nibabel
  ---
  [**NiBabel**](https://nipy.org/nibabel/coordinate_systems.html) provides low-level access to volumetric data and can be used in combination with `matplotlib.pyplot.imshow` to generate slice visualizations..

  ```
- [**Nilearn**](https://nilearn.github.io/stable/auto_examples/index.html)

  ```{figure} /assets/nilearn.webp
  ---
  width: 100%
  name: nilearn-gallery
  ---
  [**Nilearn**](https://nilearn.github.io/stable/auto_examples/index.html) is a high-level library for statistical neuroimaging that includes built-in support for volume slice rendering and other visualization techniques.

  ```
- [**nanslice**](https://github.com/spinicist/nanslice/tree/master) is a lightweight library for visualizing slices from 3D volumes.

### Surface-based Visualizations

Surface-based visualizations render cortical metrics (e.g., thickness, functional activation) on a 3D model of the cortical sheet. These projections are particularly useful for visualizing data constrained to the cortical surface, offering an intuitive, continuous view of spatial patterns that might be obscured in standard volume slice renderings.



```{figure} /assets/surf.jpg
---
width: 60%
name: surf
---
An exemplary surface-based visualization depicting the principal functional gradient{footcite:p}`margulies2016situating`, adapted from {footcite:t}`huntenburg2018large`.

```

📦 Python tools for generating surface-based visualizations:
- [**Cerebro Brain Viewer**](https://github.com/sina-mansour/Cerebro_Viewer)

  ```{figure} /assets/cerebro_surf.png
  ---
  width: 100%
  name: cerebro-surf
  ---
  A set of surface-based visualizations from [**Cerebro Brain Viewer**](https://github.com/sina-mansour/Cerebro_Viewer).

  ```

- [**Brainplotlib**](https://github.com/feilong/brainplotlib)

  ```{figure} /assets/brainplotlib.png
  ---
  width: 50%
  name: brainplotlib
  ---
  An example surface-based visualizations from [**Brainplotlib**](https://github.com/feilong/brainplotlib).

  ```

- [**PySurfer**](https://pysurfer.github.io/auto_examples/index.html)

  ```{figure} /assets/pysurfer.png
  ---
  width: 40%
  name: pysurfer
  ---
  An example surface-based visualizations from [**PySurfer**](https://pysurfer.github.io/auto_examples/index.html).

  ```

- [**SurfIce**](https://www.nitrc.org/plugins/mwiki/index.php/surfice:MainPage)

  ```{figure} /assets/surfice.jpg
  ---
  width: 40%
  name: surfice
  ---
  An example surface-based visualizations from [**SurfIce**](https://www.nitrc.org/plugins/mwiki/index.php/surfice:MainPage).

  ```

### Volume-to-Surface Transformation

When data originates in volumetric space (e.g., atlas-based ROIs, or a brain mask), it can be useful to project it onto the cortical surface for clearer spatial interpretation.


```{figure} /assets/yba.png
---
width: 60%
name: yba
---
An exemplary ROI to surface transformation of the Yale Brain Atlas, adapted from {footcite:t}`mcgrath2022high`.

```

📦 Python tools for generating volume to surface transformations:

- [**Cerebro Brain Viewer**](https://github.com/sina-mansour/Cerebro_Viewer)

  ```{figure} /assets/cerebro_volsurf.png
  ---
  width: 40%
  name: cerebro-volsurf
  ---
  An exemplary surface transformation of subcortical structures from [**Cerebro Brain Viewer**](https://github.com/sina-mansour/Cerebro_Viewer).

  ```

- [**SurfIce**](https://www.nitrc.org/plugins/mwiki/index.php/surfice:MainPage)

  ```{figure} /assets/surfice_volsurf.jpg
  ---
  width: 40%
  name: surfice-volsurf
  ---
  An example surface-based visualizations of the AICHA template from [**SurfIce**](https://www.nitrc.org/plugins/mwiki/index.php?title=File:Surfice:Aicha.jpg).

  ```

### Tractography Visualization

Visualizing white matter fiber bundles from diffusion MRI is a key part of tractography-based studies. These plots often overlay streamlines on anatomical backdrops or 3D renderings of the brain.


```{figure} /assets/tract.webp
---
width: 100%
name: bundle
---
An exemplary tractography visualization of the white-matter bundles, adapted from {footcite:t}`cox2016ageing`.

```

📦 Python tools for tractography visualization:

- [**DIPY**](https://dipy.org/)

  ```{figure} /assets/dipy_tract.png
  ---
  width: 80%
  name: dipy_tract
  ---
  An example visualization of tractography streamlines along the corpus callosum via [**DIPY**](https://docs.dipy.org/stable/examples_built/visualization/viz_roi_contour.html#sphx-glr-examples-built-visualization-viz-roi-contour-py).

  ```
- [**SurfIce**](https://www.nitrc.org/plugins/mwiki/index.php/surfice:MainPage)

  ```{figure} /assets/surfice_tract.jpg
  ---
  width: 60%
  name: surfice-tract
  ---
  An example tractography visualizations from [**SurfIce**](https://www.nitrc.org/plugins/mwiki/index.php?title=File:Surfice:Fibers.jpg).

  ```

### Brain Network Visualizations

Connectivity-based neuroscience  research often utilizes dedicated network visualizations such as adjacency matrices (heatmaps), chord diagrams, or 3D brain network plots.


```{figure} /assets/network.png
---
width: 100%
name: network
---
Different visualizations of brain connectivity information via (A) heatmaps, adapted from {footcite:t}`zamani2022local`, (B) chord diagrams, adapted from {footcite:t}`klauser2021white`, and (C) network plots, adapted from {footcite:t}`seguin2023brain`.

```

📦 Python tools for brain connectivity visualization:

The following software packages can be used to produce these maps:
- Heatmaps:
  - General purpose libraries like Matplotlib, Seaborn, and Plotly can be used to programmatically generate connectivity matrix heatmaps.
  - [**Nilearn**](https://nilearn.github.io/stable/auto_examples/03_connectivity/plot_probabilistic_atlas_extraction.html#sphx-glr-auto-examples-03-connectivity-plot-probabilistic-atlas-extraction-py) contains functions to automate this process.
- Chord diagrams:
  - Specific packages such as [**pyCircos**](https://github.com/ponnhide/pyCircos), [**Chord**](https://github.com/shahinrostami/chord), and [**OpenChord**](https://github.com/pke1029/open-chord) were specifically built to make chord diagrams.

  ```{figure} /assets/pycircos.png
  ---
  width: 40%
  name: pycircos
  ---
  Example chord diagram made by [**pyCircos**](https://github.com/ponnhide/pyCircos).

  ```
  - The [**MNE**](https://mne.tools/stable/index.html) tools library also has dedicated a section on chord diagrams for connectivity.

  ```{figure} /assets/mne_chord.png
  ---
  width: 40%
  name: mne-chord
  ---
  An example chord diagram visualizations from [**MNE Connectivity**](https://mne.tools/mne-connectivity/stable/auto_examples/mne_inverse_label_connectivity.html#make-a-connectivity-plot).

  ```

- Brain Network visualizations:
  - [**Cerebro Brain Viewer**](https://github.com/sina-mansour/Cerebro_Viewer)

  ```{figure} /assets/cerebro_network.png
  ---
  width: 80%
  name: cerebro-network
  ---
  A 3D brain network visualization from [**Cerebro Brain Viewer**](https://github.com/sina-mansour/Cerebro_Viewer).

  ```
  - [**SurfIce**](https://www.nitrc.org/plugins/mwiki/index.php/surfice:MainPage)

  ```{figure} /assets/surfice_network.png
  ---
  width: 60%
  name: surfice-network
  ---
  An example brain network visualizations from [**SurfIce**](https://www.nitrc.org/plugins/mwiki/index.php?title=File:Surfice:Nodes.png).

### More Complex Visualizations

While beyond the scope of this 30-minute educational session, it should be noted that you could leverage full-fledged 3D rendering engines to create cinematic high-quality visuals and animations from neuroimaging data. For instance, you could use Python to drive visualizations in Blender, a powerful open-source graphics suite.

🎞️ For example, here is an animation created using a Python-Blender script:

<iframe width="800" height="600" src="https://www.youtube.com/embed/GeSC_7nUdTU" 
title="YouTube video" frameborder="0" 
allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
allowfullscreen></iframe>

The script to reproduce this figure is available [here](https://gist.github.com/sina-mansour/14c3ecff56b51d2ba5a3d0b2da7deec9), provided for individuals interested in further diving down this rabbit hole! 🐇🕳️

## 💠 Supplemental Guides and Resources

The neuroimaging community is continuously developing and curating exhaustive lists of visualization tools across multiple programming languages. As promised, below are a few recommended resources to explore further. These include methodological papers, curated galleries, and practical tools to help you go beyond the examples provided in this chapter.

### 📚 Key Publications

- {footcite:t}`pernet2019data`'s "Data visualization for inference in tomographic brain imaging" provides a structured guide to visualization choices for brain imaging, with helpful discussions on colormap selection and interpretability.
- {footcite:t}`chopra2023practical`'s "A Practical Guide for Generating Reproducible and Programmatic Neuroimaging Visualizations" presents a cross-language (R, Python, MATLAB) survey of tools with a focus on reproducibility and best practices.
- {footcite:t}`chamberland2025tractography`'s "Tractography visualization" (Chapter in the [Handbook of Diffusion MR Tractography](https://www.sciencedirect.com/book/9780128188941/handbook-of-diffusion-mr-tractography)) offers an in-depth look at diffusion imaging and fiber tracking visualization tools.

### 🛠️ Tools and Curated Resources

- [**Python Graph Gallery**](https://python-graph-gallery.com/): A comprehensive collection of general-purpose visualization examples built with matplotlib, seaborn, plotly, and more.
- [**DataCamp's Data Visualization Cheat Sheet**](https://www.datacamp.com/cheat-sheet/data-viz-cheat-sheet): A tutorial on most common general purpose visualizations and where to use them.
- [**BrainCode**](https://sidchop.shinyapps.io/braincode/) A code template generator for programmatic brain visualizations in R and Python. Great for learning syntax.
- [**NeuroHackAcademy's Data Visualization in Python**](https://neurohackademy.org/course/data-visualization-in-python/) Lecture is also worth checking out.

---

## 📑 References

```{footbibliography}
```
