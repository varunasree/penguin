Penguin Species Clustering
An unsupervised learning project that groups penguins into clusters using only physical measurements — no species labels used during clustering — then checks how well the discovered clusters match the real species.
Why this project
Most portfolio projects are supervised (a known label to predict). This one demonstrates unsupervised learning: finding structure in data with no labels at all, which is closer to real-world problems like customer segmentation, where "categories" often don't exist ahead of time.
Dataset
344 penguins across 3 species (Adelie, Chinstrap, Gentoo) with 4 physical measurements — bill length, bill depth, flipper length, and body mass — sourced via seaborn.load_dataset("penguins").
What's inside
EDA — visualizing how species naturally separate by bill and flipper measurements
Preprocessing — feature scaling (critical here, since body mass is in the thousands while bill depth is in the teens)
Cluster selection — elbow method and silhouette score across k=2 to k=7, with an honest discussion of where they disagree
K-Means clustering — evaluated against the true species labels using Adjusted Rand Index, even though those labels were never used to fit the model
Cluster profiling — describing what physically distinguishes each discovered cluster
Results
Adjusted Rand Index: 0.793 (1.0 = perfect match to true species, 0.0 = random) — the clustering recovered real species structure with no access to labels.
Silhouette score technically peaked at k=2, but k=3 was chosen based on domain knowledge (3 known species) and still produced a strong, well-separated result — a good example of why silhouette score shouldn't be the only factor in choosing k.
Gentoo penguins were separated almost perfectly (123/123) — they have distinctly longer flippers and higher body mass.
Adelie and Chinstrap were harder to separate since they're closer in size; most of the clustering "confusion" happened between these two.
Sample visualizations
True species vs. discovered clusters (PCA-reduced view)
�
Load image
Cluster selection: elbow method and silhouette score
�
Load image
How to run it
Bash
Tech stack
Python · pandas · scikit-learn · seaborn · matplotlib · Jupyter
Possible next steps
Compare against hierarchical clustering and DBSCAN
Test how well the clustering generalizes to a held-out sample
Try clustering with island and sex included as categorical features
License
MIT — see LICENSE
