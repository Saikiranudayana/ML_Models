# 📘 Hierarchical Clustering Algorithm

## 🔍 About

Hierarchical Clustering is an **unsupervised machine learning algorithm** used to group data into a hierarchy of clusters. Unlike **K-Means**, it does not require specifying the number of clusters (*k*) in advance. Instead, it builds a tree-like structure called a **dendrogram**, which represents nested groupings of data points and their relationships.

The main idea is to **continuously merge or split clusters** based on their similarity (distance), forming a hierarchy from individual points (fine-grained) to one big cluster (broad view).

There are two major types:

* **Agglomerative (Bottom-Up):** Each data point starts as its own cluster, and the algorithm iteratively merges the closest clusters until all points are in one cluster.
* **Divisive (Top-Down):** Starts with all data points in one cluster and recursively splits them into smaller clusters.

---

## ⚙️ How It Works

1. **Start:**

   * Agglomerative → each data point is its own cluster.
   * Divisive → all data points are in one cluster.

2. **Measure Similarity:**

   * Use a **distance metric** (e.g., Euclidean, Manhattan, Cosine).
   * Define **linkage criteria** (how to measure distance between clusters):

     * *Single linkage* → shortest distance between two points in clusters.
     * *Complete linkage* → farthest distance between points.
     * *Average linkage* → average distance between all pairs of points.
     * *Ward’s method* → minimizes variance between merged clusters.

3. **Merge or Split:**

   * Agglomerative → merge the closest clusters step by step.
   * Divisive → split clusters iteratively.

4. **Dendrogram Formation:**

   * Build a **tree-like structure** showing how clusters are combined at each step.
   * By cutting the dendrogram at a certain height, the desired number of clusters can be chosen.

---

## 🧮 Mathematical Intuition

Let two clusters be **Cᵢ** and **Cⱼ**, with points *xₚ ∈ Cᵢ* and *x\_q ∈ Cⱼ*.

* **Single Linkage Distance:**
  d(Cᵢ, Cⱼ) = min ||xₚ − x\_q||

* **Complete Linkage Distance:**
  d(Cᵢ, Cⱼ) = max ||xₚ − x\_q||

* **Average Linkage Distance:**
  d(Cᵢ, Cⱼ) = (1 / (|Cᵢ|·|Cⱼ|)) Σ ||xₚ − x\_q||

* **Ward’s Method (Variance Minimization):**
  ΔE = (nᵢ·nⱼ) / (nᵢ + nⱼ) · ||μᵢ − μⱼ||²

Here:

* nᵢ, nⱼ → number of points in clusters
* μᵢ, μⱼ → centroids of clusters
* ||μᵢ − μⱼ||² → squared distance between centroids

This ensures clusters are merged in a way that **minimizes within-cluster variance**.

---

## ✅ Advantages

* No need to pre-specify the number of clusters (*unlike K-Means*).
* Provides a full hierarchical structure (dendrogram) to explore different levels of clustering.
* Works well with small datasets and gives interpretable results.
* Different linkage methods provide flexibility depending on data structure.

---

## ⚠️ Limitations

* Computationally expensive (O(n² log n)) → not scalable for very large datasets.
* Sensitive to noise and outliers.
* Choice of distance metric and linkage method can significantly affect results.
* Once a merge or split is made, it cannot be undone (greedy approach).

---

## 🌍 Applications

* 🧬 **Bioinformatics:** Gene sequence clustering, phylogenetic tree construction.
* 📊 **Market Segmentation:** Grouping customers based on purchasing behavior.
* 📝 **Text Mining & NLP:** Document or topic clustering.
* 🏥 **Healthcare:** Grouping patients with similar medical conditions.
* 📈 **Finance:** Clustering stocks based on performance similarity.

---

✨ **In summary:** Hierarchical Clustering is a powerful unsupervised technique for understanding the **structure and relationships in data**. It is especially useful when the number of clusters is not known beforehand and when interpretability (via dendrograms) is important.

---
