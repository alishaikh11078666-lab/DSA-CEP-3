# DSA Complex Engineering Problem 3

**Course:** Data Structures & Algorithms  
**Author:** Abdul Qadeer  
**Institution:** DHA Suffa University  
**Language:** Python 3.x  

## 📌 Project Overview
This project simulates a hierarchical file system, similar to what is found in Linux or Windows operating systems. It provides an in-memory representation of files and directories, allowing users to create, delete, navigate, and globally search for files with highly optimized time complexities.

## ⚙️ Algorithms & Data Structures Used
The simulator achieves high performance by combining several core data structures:

### 1. N-ary Tree (Hierarchical Structure)
* **Purpose:** Represents the nested structure of directories and files.

* **Implementation:** Each `FileNode` can have an arbitrary number of children. The root node acts as the absolute path (`/`).

### 2. Local Hash Tables (Fast Traversal)
* **Purpose:** Allows instant lookups of a file or folder within a specific directory.
* **Implementation:** Instead of a list of children, each `FileNode` uses a Python dictionary (`self.children`) mapping the child's name to its node, reducing local search time from O(C) to O(1).

### 3. Global Hash Table (Instant Search)
* **Purpose:** Enables global file searching without needing to traverse the entire tree.
* **Implementation:** An inverted index (`self.global_index`) tracks every file created. Searching for "project.py" instantly returns its node pointer in O(1) time, from which its absolute path is reconstructed.

### 4. Stack (Directory Navigation)
* **Purpose:** Manages the Current Working Directory (CWD) state, simulating commands like `cd`.
* **Implementation:** The `cwd_stack` appends nodes as the user navigates deeper and can easily pop nodes to move back up the hierarchy.

## 📊 Complexity Analysis

Let **N** be the total number of files/directories, **C** be the number of children in a specific directory, and **D** be the maximum depth of the directory tree.

| Operation | Component Used | Time Complexity (Avg) | Time Complexity (Worst) | Space Complexity |
| :--- | :--- | :---: | :---: | :---: |
| **Create File/Dir** | Hash Table | O(1) | O(C) (Hash Collision) | O(1) |
| **Delete File/Dir** | Hash Table | O(1) | O(C) (Hash Collision) | O(1) |
| **Global Search** | Hash Table + Pointers | O(D)* | O(N) | O(1) |
| **Change Directory** | Stack | O(1) | O(1) | O(D) |
| **Display Tree** | Recursive DFS | O(N) | O(N) | O(D) |

> *Note: While the Hash Table lookup for a file is O(1), reconstructing the absolute path string by traversing parent pointers takes O(D) time.*

## 🚀 How to Run

### 1. Setup the Repository
Clone the repository to your local machine:
```bash
git clone [https://github.com/alishaikh11078666-lab/FileSystem-DSA-CEP-3.git](https://github.com/alishaikh11078666-lab/FileSystem-DSA-CEP-3.git)
cd FileSystem-DSA-CEP-3
