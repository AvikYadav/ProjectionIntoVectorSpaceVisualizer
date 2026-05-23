# 3D Vector Projection Visualizer

This project provides an interactive 3D visualization of core linear algebra concepts, specifically focusing on the projection of a vector onto a subspace (lines and planes) in $\mathbb{R}^3$.

Built with Python, `numpy`, and `plotly`, this tool dynamically plots vector spaces, calculates projection vectors, and verifies the orthogonality of the resulting error vectors.

##  Features

* **Subspace Visualization:** Uses Singular Value Decomposition (SVD) to automatically determine the effective rank of a matrix and visualize its column space (whether it spans a 1D line, a 2D plane, or all of $\mathbb{R}^3$).
* **Vector Projection:** Computes and plots the projection of any vector $\vec{b}$ onto a given subspace.
* **Error Vector & Orthogonality:** Calculates the error vector and programmatically proves that the error vector is orthogonal (perpendicular) to the base subspace.
* **Interactive 3D Graphs:** Renders an interactive, rotatable 3D environment using Plotly, allowing for intuitive exploration of the geometric relationships.

##  Mathematical Foundation

This script implements fundamental linear algebra formulas to calculate projections.

Given a matrix $A$ (whose columns form the basis of our subspace) and a vector $\vec{b}$ that we want to project onto the column space of $A$:

**1. The Projection Matrix ($P$):**


$$P = A(A^T A)^{-1}A^T$$

**2. The Projection Vector ($\vec{p}$):**


$$\vec{p} = P\vec{b}$$

**3. The Error Vector ($\vec{e}$):**


$$\vec{e} = \vec{b} - \vec{p}$$

The code verifies the core property of orthogonal projections: the error vector is orthogonal to the subspace, meaning the dot product of the transposed error vector and the base vector matrix evaluates to zero ($A^T \vec{e} = 0$).

## 🛠️ Installation & Requirements

To run this notebook, you will need Python 3 installed along with the following libraries:

```bash
pip install numpy plotly

```

## 💻 Usage

1. Clone this repository and navigate to the project directory.
2. Open the `visualize.ipynb` notebook using Jupyter Notebook, JupyterLab, or VS Code.
3. Run the cells in sequence.

**Customizing the Vectors:**
You can easily modify the subspace and the vector you wish to project by altering the variables in the second cell of the notebook:

```python
# Change the basis vectors to define a new line or plane
base_vector = np.array([
    [1],
    [0],
    [0]
], dtype=float)

# Change the target vector
vector_b = np.array([1, 1, 1], dtype=float).reshape(-1,1)

```

By default, the script renders the visualization directly in your default web browser for maximum interactive performance (`pio.renderers.default = "browser"`).

## 📂 Code Structure

* `plot_vector()`: Helper function to plot individual vectors with magnitude tooltips.
* `plot_span()`: Core visualization function that evaluates the rank of the input matrix and plots a line, a mesh plane, or a 3D bounding box accordingly.
* `inverse_matrix()`: Utility to safely compute matrix inverses while checking for singularities.
* Main execution flow: Calculates projections, computes error vectors, and verifies orthogonality via the dot product.
