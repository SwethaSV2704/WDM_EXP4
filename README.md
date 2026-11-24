### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns

### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```python
import pandas as pd
import matplotlib.pyplot as plt

# Read CSV file
df = pd.read_csv("clustervisitor.csv")

# Select Age feature
X = df["Age"].tolist()

# Number of clusters
k = 3

# Step 1: Choose initial centroids (first k values)

# ==========================
# PART – 1 Complete Code
# ==========================
centroids = X[:k]

while True:

    # Step 2: Assign each data point to the nearest centroid

    # ==========================
    # PART – 2 Complete Code
    # ==========================
    clusters = [[] for _ in range(k)]

    for age in X:
        distances = [abs(age - c) for c in centroids]
        cluster_index = distances.index(min(distances))
        clusters[cluster_index].append(age)

    # Step 3: Calculate new centroids and remaining steps

    # ==========================
    # PART – 3 Complete Code
    # ==========================
    new_centroids = []

    for cluster in clusters:
        if len(cluster) > 0:
            new_centroids.append(sum(cluster) / len(cluster))
        else:
            new_centroids.append(0)

    if new_centroids == centroids:
        break

    centroids = new_centroids

# Display cluster-wise output

# ==========================
# PART – 4 Complete Code
# ==========================
for i in range(k):
    print(f"Cluster {i+1}: {clusters[i]}")
    print(f"Centroid: {centroids[i]:.2f}\n")


```
### Output:
<img width="567" height="172" alt="image" src="https://github.com/user-attachments/assets/236f96da-2127-42cc-ba3f-1293e14186c6" />

### Visualization:
```python
# Visualize clusters

# ==========================
# PART – 5 Complete Code
# ==========================
colors = ['red', 'green', 'blue']

for i in range(k):
    plt.scatter(clusters[i], [i+1]*len(clusters[i]),
                color=colors[i], label=f'Cluster {i+1}')

plt.xlabel("Age")
plt.ylabel("Cluster")
plt.title("Visitor Segmentation using K-Means")
plt.legend()
plt.grid(True)
plt.show()
```
### Output:
<img width="481" height="348" alt="image" src="https://github.com/user-attachments/assets/505887e4-7db0-4d63-ad42-ddc2887a12ae" />


### Result:
Thus Cluster and Visitor Segmentation for Navigation patterns are exicuted successfully
