# K-Means Clustering from Scratch

This project implements the **K-Means Clustering Algorithm** from scratch in Python without using high-level clustering libraries.
It demonstrates how centroids are initialized, points are assigned, and clusters are recalculated iteratively until convergence.

---

## 📌 Features

* Implements **K-Means++ initialization** to choose better starting centroids.
* Assigns data points to the nearest cluster.
* Recalculates centroids iteratively until they stop moving.
* Visualizes the final clusters using **Seaborn** and **Matplotlib**.
* Uses **Scikit-learn’s `make_blobs`** to generate synthetic datasets.

---

## 📂 File Structure

* `k_means_clustering_from_scratch.py` → Main Python script containing the algorithm.

---

## ⚙️ Installation

Clone the repository and install the required dependencies:

```bash
git clone https://github.com/your-username/k-means-from-scratch.git
cd k-means-from-scratch
pip install -r requirements.txt
```

Create a `requirements.txt` with:

```
numpy
pandas
matplotlib
seaborn
scikit-learn
```

---

## ▶️ Usage

Run the script directly:

```bash
python k_means_clustering_from_scratch.py
```

This will:

1. Generate sample data (3 clusters).
2. Initialize centroids using K-Means++.
3. Perform clustering until convergence.
4. Display the final cluster plot.

---

## 📊 Example Output

After running, you’ll see a scatter plot with clusters assigned different colors (`red`, `blue`, `green`).

---

## 📖 How the Algorithm Works

The **K-Means algorithm** partitions `n` data points into `k` clusters. Each cluster is represented by a **centroid**, which is the average of all points assigned to it.

### Step-by-Step Process

1. **Centroid Initialization (K-Means++)**

   * Select the first centroid randomly from the dataset.
   * For each subsequent centroid:

     * Compute the squared distance of every point from its nearest already-chosen centroid.
     * Choose the next centroid with probability proportional to this squared distance.
   * Repeat until all `k` centroids are chosen.

   ✅ This ensures centroids are well spread out, avoiding poor starting positions that can lead to bad clustering results.

2. **Assign Points to Nearest Centroid**

   * For each point, calculate the **Euclidean distance** to each centroid.
   * Assign the point to the cluster with the closest centroid.

   Formula:

   $$
   d(p, c) = \sqrt{(p_x - c_x)^2 + (p_y - c_y)^2}
   $$

3. **Recalculate Centroids**

   * For each cluster, compute the **mean of all assigned points**.
   * Update the centroid’s coordinates to this mean.

   Formula:

   $$
   c_{new} = \frac{1}{n} \sum_{i=1}^{n} p_i
   $$

4. **Repeat Until Convergence**

   * Continue reassigning points and updating centroids.
   * Stop when centroids no longer move significantly (or exactly equal in this script).

---

## 🔄 Working of This Implementation

Here’s what happens inside `k_means_clustering_from_scratch.py` when you run it:

1. **Data Generation**

   * Creates a dataset with 300 points and 3 natural clusters using `make_blobs`.

2. **Centroid Initialization**

   * Uses K-Means++ to choose initial centroids in a spread-out manner.

3. **Clustering Loop**

   * Assigns each point to its nearest centroid.
   * Recalculates new centroid positions based on the mean of assigned points.
   * Repeats until centroids stop changing.

4. **Visualization**

   * Uses **Seaborn** to plot the points, colored by cluster.
   * Final centroids represent the learned cluster centers.

---

## 🧩 Pseudocode for K-Means

```text
Input: Dataset with n points, number of clusters k
Output: k clusters with centroids

1. Initialize centroids using K-Means++:
   a. Choose one point uniformly at random as the first centroid.
   b. For each data point x, compute distance²(x, nearest chosen centroid).
   c. Select the next centroid with probability proportional to distance².
   d. Repeat until k centroids are chosen.

2. Repeat until convergence:
   a. Assign each point to the nearest centroid.
   b. Update each centroid as the mean of assigned points.

3. Return final centroids and cluster assignments.
```

---

## ✅ Future Improvements

* Generalize for `k` clusters instead of just 3.
* Add support for higher-dimensional datasets.
* Optimize performance with vectorized operations.
* Evaluate clustering quality using metrics like **Silhouette Score**.

---

## 📝 License

This project is open-source and available under the **MIT License**.
