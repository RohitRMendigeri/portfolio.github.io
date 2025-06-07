# 💼 Rohit's Portfolio

Welcome to my portfolio! I'm an aspiring software engineer with a strong foundation in **Data Structures**, **Algorithms**, and **Advanced Problem Solving**. This GitHub Pages portfolio demonstrates how I apply these concepts through real-world case studies inspired by my dream company — **Google**.

Whether it’s optimizing search results, scaling systems, or building intelligent applications, I’m passionate about solving challenging problems that impact billions of users. Dive into my work and see how I turn theory into practice.

---

## 👤 About Me

- **Name:** Rohit Mendigeri  
- **SRN:** 01FE22BCS226
- **College:** KLE University
  
---

## 🌐 Domain: Google

### 🏢 About Google

Google is a global tech leader that specializes in internet-related services and products, including:
- **Search Engines**
- **Cloud Computing**
- **Online Advertising**
- **Operating Systems (Android, Chrome OS)**
- **Hardware (Pixel, Nest, Fitbit)**
- **Artificial Intelligence & Machine Learning**

It operates under its parent company **Alphabet Inc.**, which houses a diverse set of sub-companies and technologies that are shaping the future.

### 🔍 Sub-Domains Under Google

1. **Google Search** – World's most widely used search engine  
2. **Gmail** – Scalable and smart email service  
3. **Google Maps** – Real-time geolocation and navigation  
4. **YouTube** – Video sharing and content discovery platform  
5. **Google Photos** – Cloud-based photo storage and management  
6. **Google Cloud Platform (GCP)** – Infrastructure and services for scalable apps  
7. **Android** – Mobile OS powering billions of devices  
8. **Waymo** – Self-driving technology (Alphabet subsidiary)  
9. **DeepMind** – AI research and advanced machine learning  
10. **Google Ads & Analytics** – Digital marketing and business intelligence  

### ❤️ Why Google?

Google embodies innovation, scale, and impact. Its engineering culture encourages experimentation and excellence, making it the ideal environment for someone like me who loves building intelligent systems and solving large-scale problems. Through this portfolio, I aim to demonstrate how my technical skills align with the challenges faced in various Google products.

---
## 📌 Case Study 1: Powering Search Suggestions and High-Speed Routing

###  Challenges in Real-Time Systems  
Systems like Google Search and Google DNS must handle massive-scale data with **low latency**, **high accuracy**, and **scalability**. The core challenge is to find the best match for a given prefix—quickly and efficiently.



###  Solution Overview: Using Trie (Prefix Tree)  
A **Trie** is a tree-like data structure ideal for **prefix-based lookup**. Each node represents a character (or bit), and paths from the root form complete strings or IP prefixes. Tries power:

-  **Autocomplete systems:** Predicting user search queries.  
-  **IP routing systems:** Matching IP addresses to the longest prefix route.



###  Data Structures Used  
- **Trie:** For efficient prefix matching.  
- **Hash Map:** To store query frequencies (Autocomplete).  
- **Min Heap / Priority Queue:** To rank top-K suggestions (Autocomplete).  
- **Binary Trie:** Each node represents 0 or 1, ideal for IP address prefixes (Routing).


###  Algorithms  

####  Autocomplete  
1. Insert queries into the Trie along with frequency counts.  
2. For a given prefix input:  
   - Traverse to the corresponding prefix node.  
   - Perform DFS to collect all possible suffixes.  
   - Use a Min Heap to efficiently extract top-K frequent suggestions.

####  IP Routing  
1. Insert IP prefixes (e.g., `192.168.0.0/16`) into a binary Trie.  
2. Convert destination IP addresses to binary form and perform the **longest prefix match** to determine the next hop.


###  Token Management in AI Models
In today’s world, AI is used widely across various applications. Large language models like GPT (e.g., Gemini or ChatGPT) rely on tokens to understand and maintain the context of a conversation.

A Trie can be extremely useful in this scenario. It can efficiently store, process, and retrieve tokens, making it ideal for managing vocabulary, autocomplete, and fast lookup operations—especially when dealing with large sets of tokenized data. These tokens are then further used in transformers ,etc.


###  Time & Space Complexity

| Operation            | Time Complexity        | Space Complexity       |
|----------------------|------------------------|-----------------------|
| Insert Queries/Routes | O(N × L) or O(R × 32)  | O(N × L) or O(R × 32) |
| Prefix Lookup        | O(P) or O(32)          | O(K) (for suggestions)|
| Suggestion Retrieval | O(M log K)             | —                     |

*Where:*  
- N = number of queries, L = average length of query  
- R = number of routes, P = prefix length, K = number of suggestions, M = total characters in matched suffixes
- 32 = shows the bits in IPV4


###  Real-World Usage at Google  
-  **Autocomplete:** Google Search, Gmail, YouTube, Android Keyboard  
-   **Routing:** Google Public DNS (8.8.8.8), Content Delivery Networks (CDNs), and Google’s global server infrastructure

Tries enable both **intelligent suggestions** and **high-speed routing**, making them essential for building responsive, scalable, and efficient systems.

---
## 📌 Case Study 2: Route Optimization for Google Maps Navigation

###  Challenge
Google Maps needs to compute **shortest and fastest routes** from millions of locations in real-time. The challenge lies in handling **dynamic road conditions** like traffic, closures, construction, and accidents — all while keeping routing **fast and accurate**.


###  What is A* Search?

A\* (A-Star) is a **best-first search** algorithm that finds the **optimal path** by balancing two factors:

- `g(n)`: Actual cost from start node to current node
- `h(n)`: Heuristic estimate of the cost from current node to goal

It selects the path with the lowest **f(n) = g(n) + h(n)**.

Compared to Dijkstra’s algorithm (which uses only `g(n)`), A\* adds **goal awareness** through `h(n)`, making it more efficient in practice.



###  Heuristic Design in Real Systems

We can use **informed heuristics** that are both fast and realistic:

-  **Straight-line distance** (Haversine or Euclidean) — base estimate.
-  **Real-time traffic data** — adds weight to congested roads.
-  **Road type priority** — highways are faster than city roads.
-  **Time-of-day effects** — rush hour patterns, school zones.
-  **Dynamic closures & incidents** — makes some edges temporarily unusable.

These heuristics can help guiding the search efficiently while adapting to **real-world constraints**.


###  Handling Dynamic Edge Weights

Real-world roads aren't static:

- **Live edge weight updates** for changing travel times (traffic).
- **Edge pruning** for closed or under-construction roads.
- **Replanning on-the-fly** using updated graph data.

A* allows quick rerouting by recalculating the optimal path from the current node when conditions change — this is critical for **live navigation**.


###  Time and Space Complexity

| Operation         | Complexity         |
|------------------|--------------------|
| Time (Worst Case) | O(E) or O(V + E) log V (with Min Heap) |
| Space             | O(V)               |

- `V` = number of nodes (intersections)
- `E` = number of edges (roads)

In practice, **A\*** performs significantly faster due to the heuristic narrowing the search area.



###   Usage

-  **Google Maps**: Live route planning, rerouting  updates.
-  **Ride-sharing platforms** (e.g., Uber, Lyft): Smart driver dispatch and route prediction.
-  **Logistics/Delivery**: Optimized paths for time-sensitive delivery.

---
# 📌Accelerating Location-Based Search

### Challenge in Real-Time Systems  
Rapidly finding the nearest points of interest—such as businesses, data centers, or delivery hubs—based on a user’s current position. In large-scale, high-traffic environments, latency is critical: users expect sub-second responses for “find nearby” queries.


### Solution Overview: Using KD-Tree (K-Dimensional Tree)  
A **KD-Tree** is a binary space-partitioning structure that organizes points in a K-dimensional space (e.g., latitude and longitude when K = 2). By recursively splitting the dataset along alternating dimensions, KD-Trees enable efficient nearest-neighbor and range queries, making them ideal for real-time, location‐aware services.

- **Maps & Local Search:**  
  Quickly locate nearby ATMs, restaurants, or gas stations using the user’s GPS coordinates.

- **Delivery & Logistics:**  
  Assign the closest available driver or courier to a pickup point, minimizing travel time and cost.

- **Cloud Infrastructure & CDNs:**  
  Route user requests to the geographically nearest data center or edge server, reducing latency.


### Data Structures Employed  
- **KD-Tree**  
  - Organizes N geo-points (e.g., `[lat, lon]`) in a balanced binary tree.  
  - Each node splits its subset of points along one dimension (cycling through latitude, longitude, latitude, …).  
  - Enables average-case \(O(\log N)\) nearest-neighbor queries.

- **Max Heap (Priority Queue)**  
  - Maintains the top-K closest points when performing a K nearest-neighbors (KNN) search.  
  - As the KD-Tree search descends, any candidate farther than the current Kth nearest is pruned.



### Algorithm: K-Dimensional Search (K = 2 for latitude/longitude)  
1. **Build Phase** (\(O(N \log N)\), \(O(N)\) space)  
   - Recursively select a splitting dimension (alternating between latitude and longitude).  
   - Sort or compute the median of points along that dimension.  
   - Create a node storing the median point; recurse on left/right subsets.

2. **Query Phase** (Average \(O(\log N)\))  
   - Start at the root, comparing the target point’s coordinate in the current split dimension.  
   - Recursively traverse toward the subtree that contains the target.  
   - Upon backtracking, check whether the “other side” of the split could contain closer points—prune if the splitting plane is farther than our current Kth nearest.  
   - Use a Max Heap to track the top-K closest points seen so far.  

3. **Result Collection** (\(O(K)\) extra space)  
   - After traversal, extract the K nearest points from the Max Heap in descending order of distance (or read them inwards if maintaining a size-K min-heap instead).



### Time & Space Complexity  

| Operation          | Time Complexity    | Space Complexity |
|--------------------|--------------------|------------------|
| Build (bulk insert)| \(O(N \log N)\)    | \(O(N)\)         |
| Nearest Neighbor   | \(O(\log N)\) avg  | \(O(K)\)         |
| Range Query        | \(O(\log N + R)\)  | \(O(R)\)         |

- **N** = total number of locations  
- **K** = dimensions (e.g., 2 for lat/lon)  
- **R** = number of reported points in a range query



### Kd can be used in 

1. **Maps & Local Search**  
   - **“Find nearby cafés”**:  
     - User’s GPS = `[lat₀, lon₀]`.  
     - Query a KD-Tree of millions of POIs to return the closest 10 eateries in under 50 ms.


3. **CDN & Edge Routing**  
   - **“Route user traffic”**:  
     - Predefine server locations (data centers, edge nodes) in a static KD-Tree.  
     - For each incoming request, map its IP to geolocation and perform a KD-Tree lookup to identify the nearest node, reducing round-trip latency.

4. **High-Dimensional ML Pipelines **  
   - we can also build KD-Trees over high-dimensional feature vectors to accelerate KNN-based recommendations or clustering tasks. 

---




---
## 📌 Case Study 4: Optimizing Storage and Bandwidth with Lossless Data Compression

### 🚧 Challenge  
Compress large volumes of data efficiently without losing any information.

### 🛠️ Solution Overview: Huffman Encoding  
A **lossless compression algorithm** that assigns shorter binary codes to frequent symbols and longer codes to rare ones, reducing overall data size.

### Working  
1. Count frequencies of symbols.  
2. Build a binary tree from least to most frequent symbols.  
3. Assign unique prefix codes by traversing the tree.  
4. Replace symbols with their binary codes for compression.


###  Real-World Usage at Google  
- Compressing images (JPEG in Google Photos)  
- Audio compression in YouTube Music
- HTTP/2 header compression in Google Chrome

---

## 📌 Case Study 5: Instantaneous Time-Series Analysis for Monitoring and Analytics

###  Challenge  
Google systems like YouTube Analytics and Cloud Monitoring must perform **real-time range queries** (sum, min, max) and updates on **large time-series data** efficiently.



###  Solution: Segment Trees  
A **Segment Tree** is a binary tree that enables **log-time range queries and updates** by dividing data into manageable segments.

🔧 Use Cases:
-  Track views/clicks in a date range  
-  Detect anomalies in system metrics  
-  Real-time monitoring in dashboards


###  Core Data Structures  
- **Segment Tree Array:** Compact binary representation  
- **Lazy Propagation (Optional):** For efficient range updates


###  How It Works  

- **Build:** Recursively divide and compute values  
- **Query [L, R]:** Combine relevant segments  
- **Update:** Modify value and update parent nodes


###  Complexity

| Operation     | Time       | Space    |
|---------------|------------|----------|
| Build         | O(N)       | O(2 × N) |
| Query/Update  | O(log N)   | —        |



###  Real-World Use at Google  
-  **YouTube Analytics:** Fast stats over time ranges  
-  **Cloud Monitoring:** Min/max for anomaly detection  
-  **Google Ads:** Aggregate metrics over campaigns
Segment Trees offer a great trade-off between speed and flexibility for Google's dynamic data needs.

---
## 📌 Case Study 6: Enabling Efficient Version Control with Queries

### Challenge  
Modern systems like Google Docs, Sheets, and BigQuery need to:
- Track data over time (version control),
- Support rollback/undo, and  
- Enable temporal queries — all without duplicating entire datasets for each change.


### Solution: Persistent Segment Trees  

A Persistent Segment Tree maintains multiple versions of a data structure by copying only the modified nodes during updates, while sharing unchanged parts. This allows time-based querying and editing to be efficient in both space and time.

#### Algorithmic Insights  
- Each update creates a new root, preserving previous versions.
- Time & space per update: O(log n).
- Supports:
  - `update(index, value, version)` → returns new version  
  - `query(left, right, version)` → returns range result from a specific version

#### Core Concepts  
- Immutability + Sharing: Trees use structural sharing instead of full duplication.
- Functional Approach: Perfect for stateless backends and version-aware analytics.


### Use Cases  

| Use Case              | Description |
|-----------------------|-------------|
| Google Docs           | Maintain full edit history without copying entire documents |
| Google Sheets         | Versioned formulas/data to support undo, audit logs |
| BigQuery              | Enable historical range queries over time-partitioned data |
| Cloud IDEs            | Efficient Undo/Redo, branchable code state management |
| CI/CD Systems         | Track config/data changes across deployment snapshots |



### Why It's Powerful  
- Memory-Efficient: Only log(n) new nodes per version  
- Time-Aware Queries: Critical for analytics and debugging  
- Immutable + Parallelizable: Great for distributed/cloud systems

Persistent Segment Trees combine algorithmic elegance with real-world practicality, enabling Google-scale systems to be both version-aware and performance-efficient.


---

## 📌 Case Study 7:  Optimizing Large-Scale Offline Range Queries for Analytics

###  Challenge  
In analytics systems like **Google Trends**, **YouTube Analytics**, or **Ad Reporting**, we often need to process **many offline range queries** like:

> users watched videos between day 20 and day 40  
> the most frequent query between time A and B

Running each query separately can be slow—especially on large datasets with tight performance needs.



###  Solution: Mo’s Algorithm  
**Mo’s Algorithm** is an offline query optimization technique for **range queries**. It **reorders** the queries smartly to minimize redundant work when moving from one query to another.

 Key Idea: Sort all queries to **minimize array changes**, then process them using a **sliding window** with efficient insert/remove logic.



###  Core Components  
- **Range Queries:** Typically of the form `[L, R]`  
- **Sorting Strategy:** Queries are sorted by blocks of √N (and R for tie-breaking)  
- **Add/Remove Functions:** Efficiently manage changes when moving the window


###  working  
1. Divide array into blocks of size √N  
2. Sort queries by block of L, then R  
3. Initialize current window `[moLeft, moRight]`  
4. For each query:  
   - Adjust `moLeft` and `moRight` using `add()` or `remove()`  
   - Record the answer for that range  

> Because adjacent queries change the window slightly, total cost is minimized.



###  Time & Space Complexity

| Operation      | Time              | Space |
|----------------|-------------------|--------|
| Preprocessing  | O(Q log Q)        | O(Q)   |
| Query Handling | O((N + Q) √N)     | O(N)   |

*Where:*  
- N = array size  
- Q = number of queries



###   Uses 
-  **YouTube Analytics:** Fast unique user queries over watch history  
-  **Ad Campaign Reporting:** Frequency and count-based range stats  
-  **Google Trends:** Offline computation of trends over time intervals  
-  **Search Query Logs:** Efficient querying for frequency, count, or mode across ranges

Mo’s Algorithm shines when we know all queries upfront and want **speed without full recomputation**—perfect for **batch reporting** and **offline analytics**.

---
## 📌 Case Study 8: Achieving Stable and Fair Matching in Resource Allocation( Deferred Acceptance Algorithm)

### Challenge  
Efficiently pair two groups based on mutual preferences, ensuring **no two entities would prefer to deviate from their assigned match**—i.e., no instability.



### Solution: Gale–Shapley Algorithm (Deferred Acceptance)

This classic algorithm finds a **stable matching** in O(n²) time:
1. One group (e.g., candidates) proposes to its top-ranked options.
2. The receiving group (e.g., companies) tentatively accepts the best proposal so far, rejecting others.
3. Rejected candidates move to their next preferred choice.
4. The process repeats until all are matched.

- **Guarantees Stability:** No two individuals would swap and be happier.
- **Group-Optimality:** The proposing group always gets its best possible stable match.


### Time & Space Complexity

| Operation         | Complexity |
|-------------------|------------|
| Time (worst-case)  | O(n²)      |
| Space             | O(n²)      |



### More Use Cases
- Mentor-Mentee Matching in internal programs  
- Cloud VM Scheduling based on workload and hardware affinity  
- Local Ads Delivery matching businesses to ad slots with mutual preferences  

Stable Marriage is a powerful abstraction for **fair, stable, and preference-driven assignments** across diverse use cases.

---
## 📌 Case Study 9: Finding the Optimal Path in Cost-Sensitive Systems

### Challenge  
Efficiently finding the lowest-cost path or optimal solution in large-scale graphs with varying edge costs, such as optimizing network routing or task scheduling in Google’s infrastructure.



### Solution: Uniform Cost Search  
UCS is a graph search algorithm that always expands the node with the smallest cumulative cost first, guaranteeing the **optimal path** when edge costs vary.

- Uses a **priority queue** to select the next node with the least total cost so far.  
- Continues exploring until the goal node is reached, ensuring the path found is the minimum-cost.  
- Handles **multiple goal nodes** by stopping as soon as any goal is reached with the lowest cost.  
- More suitable than BFS when edge costs are non-uniform.



### Time & Space Complexity

| Operation           | Complexity          |
|---------------------|---------------------|
| Time (worst-case)   | O(b^(1 + ⌊C*/ε⌋))   |
| Space               | O(b^(1 + ⌊C*/ε⌋))   |

*Where:*  
- b = branching factor  
- C* = cost of optimal solution  
- ε = minimum edge cost  


### Applications at Google

- **Network Routing:** Computing least-cost paths across Google’s global data center networks, balancing latency and bandwidth costs.  
- **Task Scheduling:** Ordering job executions in Google Cloud to minimize resource consumption and costs.  
- **Google Maps Navigation:** Finding cheapest routes considering dynamic costs like traffic and tolls.  
- **Distributed Resource Allocation:** Assigning compute/storage resources efficiently across clusters based on cost metrics.

Uniform Cost Search enables **optimal, cost-aware decision making** across Google’s large-scale, weighted graph problems, especially where multiple potential goals exist.

---
## 📌 Case Study 10: A Foundation for Security: Enabling Cryptography and Data Integrity

### Challenge  
Google requires **efficient modular arithmetic** operations for cryptography, data integrity, and distributed systems, where modular division is needed but direct division is not possible.



### Solution: Modular Multiplicative Inverse (MMI)  
MMI computes the inverse of an integer **a** modulo **m**, finding **x** such that:

(a × x) ≡ 1 (mod m)


This enables modular division critical for:

- **Cryptographic protocols:** RSA, ECC for secure communication  
- **Error detection and correction:** Checksums and hashing  
- **Consistent hashing:** Load balancing in distributed storage  

Common methods to compute MMI:  
- Extended Euclidean Algorithm (efficient and general)  
- Fermat's Little Theorem (when modulus is prime)



### Time & Space Complexity

| Operation                 | Complexity         |
|---------------------------|--------------------|
| Extended Euclidean Algo    | O(log m)           |
| Fermat's Little Theorem   | O(log m)           |


### Applications at Google

- **Encryption & Decryption:** Secure data transmission between Google services.  
- **Integrity Checks:** Hash-based authentication and error correction.  
- **Distributed Systems:** Efficient and balanced resource allocation using consistent hashing.  

MMI is a fundamental building block enabling **secure, efficient, and reliable modular arithmetic** in Google's large-scale systems.

---
## 📌 Case Study 11:  Powering Scalable, Low-Latency Access to Ordered Data

### Challenge  
Google services need to manage **large, dynamic datasets** with fast search, insertion, and deletion operations while maintaining sorted order and supporting range queries. Traditional balanced trees can be complex to implement and maintain at scale.



### Solution: Skip List  
A **Skip List** is a layered, probabilistic data structure that enables **fast average-case O(log n)** operations by maintaining multiple forward pointers that “skip” over elements, creating express lanes through the list.

- Data is stored in sorted order across multiple linked list levels.  
- Nodes are randomly promoted to higher levels to balance the structure without complex rotations.  
- Searches start from the highest level and drop down, skipping many elements for speed.


### Real-Time Use Cases at Google  
- **Bigtable & LevelDB:** Skip Lists are core to their internal indexing, enabling efficient range scans and real-time updates on large distributed datasets.  
- **Google Cloud Spanner:** Uses Skip List variants for managing transactional indexes that require quick updates and lookups.  
- **Real-time Analytics & Caching:** Facilitates fast insertion and queries in memory caches and streaming data processing systems.  
- **Concurrent Data Structures:** Skip Lists adapt well to multi-threaded environments, making them suitable for high-concurrency Google infrastructure components.

### Time Complexity  

| Operation  | Average Time Complexity |
|------------|------------------------|
| Search     | O(log n)               |
| Insert     | O(log n)               |
| Delete     | O(log n)               |



Skip Lists offer a simpler and more concurrent-friendly alternative to balanced trees, making them ideal for Google’s need to handle massive, ordered data efficiently and reliably.

---
# 📌 Case Study 12: Real-Time Spam Detection in Gmail 

## 🔍 The Challenge  
Gmail must detect spam **immediately** upon email arrival. With billions of emails sent daily, reprocessing entire datasets is too expensive.  
We need an efficient method to extract insights from **continuous data streams**.

## ✅ Suggested Solution: Sliding Window Algorithm  
The **Sliding Window** technique allows us to process only the **most recent subset** of data efficiently.

- ✅ **Time Efficiency**: Only new data is processed as the window slides.  
- ✅ **Space Efficiency**: Only the current window’s data is stored in memory.  

> Where `k` is window size, `m` is length of the pattern, `n` is length of the text, `z` is total output size.

## ✨ Proposed Applications in Gmail

### 1. Spam Phrase Detection  
- **Rabin-Karp Algorithm**: Rolling hash enables fast matching of phrases inside the window.  
- **Aho-Corasick Algorithm**: Detects multiple spam phrases simultaneously in linear time.

### 2. Sender Behavior Monitoring  
- **Time-based sliding window** can track email sending rates.
- **Token Bucket algorithm** can allow brief bursts but flag sustained high-volume behavior.

  
### ⏱️ Time & Space Complexity
| Operation                    | Time Complexity | Space Complexity |
|-----------------------------|------------------|------------------|
| Window Slide Update         | O(1)             | O(k)             |
| Phrase Matching (Rabin-Karp)| O(m + n)         | O(1)             |
| Multi-pattern Matching (Aho-Corasick) | O(n + z) | O(m·k)          |

### ⚙️ Supporting Data Structures  
| Data Structure    | Use Case                                                  |
|-------------------|------------------------------------------------------------|
| `Deque`           | Tracks max/min values, e.g., spike in send rate            |
| `HashMap`         | Stores frequency of phrases or sender activity             |
| `Rolling Hash`    | Efficient comparison of phrases inside the content window  |

## 🎯 Final Impact  
This approach enables **real-time spam filtering** without overloading Gmail’s systems, while maintaining user experience and system responsiveness.


---
##  📌 Case Study 13: Google Bigtable – Scalable Structured Data Storage

##  Problem Statement

Google required a storage system that could:

- Handle **petabytes of structured data**
- Provide **low-latency access**
- Support **real-time read/write operations**
- Scale across **thousands of commodity servers**

Traditional RDBMS systems couldn’t meet these requirements. Hence, **Bigtable** was developed.

---

##  Solution:

**Bigtable** is a distributed, sparse, multidimensional sorted map. The data model can be visualized as: (row_key, column_family:column_qualifier, timestamp) → value


This design supports:

- **Versioning** (with timestamps)
- **Efficient lookups**
- **Horizontal scalability**



##  Core Data Structures in Bigtable

### 1. MemTable
- An **in-memory** sorted data structure (usually implemented as a Red-Black Tree or Skip List).
- Accumulates writes.
- Flushed to disk as **SSTables** when full.

### 2. SSTable (Sorted String Table)
- Immutable file storing key-value pairs sorted by key.
- Organized to allow **binary search** and **range scans**.
- Used for **persistent storage** on disk.

### 3. Write-Ahead Log (WAL)
- Also known as a **commit log**.
- Records mutations before applying to the memtable.
- Ensures **durability** in case of crashes.

### 4. Bloom Filters
- Used to **quickly check** if an SSTable might contain a key.
- Probabilistic, avoids unnecessary disk reads.
- Time complexity: O(1) for lookup.

### 5. Tablet
- A **horizontal partition** of a Bigtable table.
- Each tablet is served by one tablet server.
- Tablets contain SSTables + a memtable + metadata.

### 6. B+ Tree-Like Structure
- Underlying datastructure in SSTables to support **fast range queries**.
-  Uses binary Search.




##  Bigtable Workflow: Read/Write Operations

###  Write Path

1. **Client sends a write** (put/delete).
2. Write is recorded in the **Write-Ahead Log (WAL)**.
3. Write is inserted into the **MemTable**.
4. When MemTable grows large:
   - It's **flushed** to disk as an **SSTable**.
   - SSTables are stored in **GFS (Google File System)**.

###  Read Path

1. Client requests a key or key range.
2. Bigtable checks:
   - **MemTable** (for recent writes)
   - **Bloom Filters** to identify relevant SSTables
   - **SSTables** (older, persisted data)
3. Results are **merged** (newest timestamp wins).



##  Compaction Process

To maintain performance, Bigtable performs **compaction**:

- **Minor Compaction**: Merge small SSTables.
- **Major Compaction**: Merge all SSTables into one.
- **Garbage Collection**: Removes deleted/expired entries.

This keeps read paths efficient by reducing the number of SSTables per tablet.



##  Time  Complexity

| Operation         | Time Complexity      | Notes                                    |
|-------------------|----------------------|-------------------------------------------|
| **Write**         |  O(1)                | Buffered in memtable                      |
| **Read (lookup)** | O(log n + k)         | Log n for SSTable + k for merging versions |
| **Range Scan**    | O(k)                 | Efficient due to SSTable sorting          |
| **Compaction**    | O(n)                 | Depends on size of SSTables being merged  |




##  Use in Google's Ecosystem

Bigtable is used in:

- **Google Search** – Indexing web pages
- **Google Maps** – Spatial data
- **Google Analytics** – Event data
- **YouTube** – Metadata and user preferences
- **Google Earth** – Geospatial data

It also inspired:

- Apache HBase (Hadoop ecosystem)
- Cassandra (Facebook, now open source)
- Amazon DynamoDB (inspired by similar principles)

---
# 📦 Case Study: Enhancing Android App Update Integrity with Merkle Trees

## 🏢 Organization: Google – Play Store


Google Play Store delivers large-scale app updates (APKs/AABs) to billions of Android devices. Ensuring **security**, **efficiency**, and **data integrity**—especially on unreliable networks or against tampered APKs—is crucial.

---

## 🧩 Key Challenges

- **Large File Sizes**: APKs often exceed 100 MB.
- **Update Resumption**: Failed downloads traditionally require restarting.
- **No Chunk-Level Verification**: Full-file checksums can't detect partial tampering.
- **Tampered APKs**: Sideloaded or hacked apps may include malicious code.
- **Efficient Patching**: Users often have older app versions; downloading the entire new version is inefficient.

---

## ✅ Solution: Merkle Tree-Based Integrity Verification

Introducing Merkle Trees enables **chunk-level verification and secure patching** during updates.

### 🔧 How It Works

1. **Chunking**: APK/AAB is split into fixed-size blocks (e.g., 4 KB).
2. **Leaf Hashing**: Each chunk is hashed using SHA-256.
3. **Tree Construction**: Hashes are recursively combined up to a signed Merkle Root.
4. **Verification**: 
   - Clients use Merkle Proofs to validate each chunk.
   - If any chunk is corrupted or modified (e.g., via sideloading), validation fails.
5. **Delta Updates**:
   - Only changed chunks are downloaded (e.g., between app version 1.0 and 1.1).
   - Verified using Merkle proofs, ensuring only correct, untampered blocks are accepted.



## 🚀 Benefits

- ✅ Detects tampered APKs (even if modified offline)
- ✅ Secure resumption of interrupted downloads
- ✅ Efficient updates by downloading only changed chunks
- ✅ Reduces bandwidth and load on Google's infrastructure
- ✅ Scales to billions of devices



## 🧠 Underlying Concepts

- **Merkle Tree**: Binary tree of SHA-256 hashes built from app chunks.
- **Merkle Proof**: Enables client to verify individual chunk integrity.
- **Digital Signature**: Authenticates the Merkle Root and prevents tampering.



## 💡 Suggestion for Enhancement

By integrating Merkle Trees more deeply with delta update mechanisms, Google can further:

- Improve **differential patching** granularity
- Reduce unnecessary data transmission
- Catch **any unauthorized modifications**, even if a single byte is altered

---
# 📌 Case Study 12B: Live Engagement Analytics in YouTube using Sliding Window

## 🔍 The Challenge  
YouTube receives massive user engagement data every second. We need to process these streams in **real time** to support:

- 📉 Viewer drop-off analysis  
- 📈 Peak interaction tracking  
- 🎯 Ad placement optimization  

## ✅ Suggested Solution: Sliding Window for Streaming Analytics  
By continuously moving a time window across live data, we can extract insights with minimal overhead.

- ✅ **Real-time feedback**  
- ✅ **Low memory consumption**  
- ✅ **Avoid full data reprocessing**



##  Applications in YouTube

### 1. Watch-Time Drop Detection  
- Analyze **engagement logs** within a sliding window to detect where viewers stop watching.
- Flag timestamps like `00:45–01:15` as boring or disengaging.

### 2. Real-Time Engagement Monitoring  
Use sliding windows to track:
-  **Live peak viewer counts**
-  **Burst in likes/subscribers**
-  **Optimal ad display timing**
-  **Spikes in comments/interactions**

###  Time & Space Complexity
| Operation                        | Time Complexity | Space Complexity |
|----------------------------------|------------------|------------------|
| Engagement Window Slide Update   | O(1)             | O(k)             |
| Aggregate Metrics (sum, avg, etc)| O(1) or O(log k) | O(k)             |
| Spike/Peak Detection (e.g. via deque)| O(1)         | O(k)             |

> Where `k` is the sliding window size (e.g., 60s of interactions).

##  Supporting Data Structures  
| Data Structure    | Use Case                                                       |
|-------------------|-----------------------------------------------------------------|
| `Deque`           | Efficient peak/min tracking within current window              |
| `HashMap`         | Aggregation and categorization of interaction types            |
| `Rolling Hash`    | Less relevant here, but can be used in video content fingerprinting |

##  Final Impact  
Sliding Window-based analysis empowers YouTube to **adapt content delivery** and **enhance viewer experience**, all while handling massive-scale, high-frequency data.

---
## 📊 Business Case Studies

### 1. 🚀 Improving Search Result Relevance
- **Challenge:** How can we improve the accuracy and speed of Google Search?
- **Solution:** Implemented a search engine simulation using **Trie** for autocomplete and **Edit Distance (Dynamic Programming)** for typo correction. Graph algorithms help cluster similar queries.
- **DSA Concepts Used:** Trie, Hashing, Dynamic Programming, Graph Clustering  
- **Impact:** Better user query understanding and faster retrieval with reduced search latency.

---

### 2. 📨 Email Categorization at Scale (Gmail)
- **Challenge:** How can Gmail categorize millions of emails in real-time?
- **Solution:** Designed a classification system using **Priority Queues** and **Pattern Matching**, simulating how emails are tagged into Primary, Social, and Promotions.
- **DSA Concepts Used:** Priority Queue, HashMaps, Regex Matching  
- **Impact:** Efficiently manages incoming email load and enhances user experience.

---

### 3. 🗺️ Google Maps Route Optimization
- **Challenge:** How to find the most efficient route with real-time traffic?
- **Solution:** Built a routing algorithm using **Dijkstra's** and **A\*** to simulate shortest paths with dynamic traffic weights.
- **DSA Concepts Used:** Graphs, Heaps, Shortest Path Algorithms  
- **Impact:** Real-time navigation with dynamic rerouting boosts commute efficiency.

---

### 4. 📺 YouTube Recommendation Engine
- **Challenge:** How can YouTube recommend personalized and engaging videos?
- **Solution:** Created a simple recommendation system using **Graph traversal** and **Frequency Trees** based on user behavior.
- **DSA Concepts Used:** Trees, Graphs, Frequency Counters  
- **Impact:** More relevant content suggestions leading to longer watch times.

---

### 5. 🖼️ Google Photos Compression Engine
- **Challenge:** How to store billions of images efficiently?
- **Solution:** Developed a basic image compression model using **Huffman Encoding**.
- **DSA Concepts Used:** Trees, Greedy Algorithms, Dynamic Programming  
- **Impact:** Optimized memory storage with lossless image compression.

---

### 6. 🧮 Distributed Log Processing (MapReduce)
- **Challenge:** How to process petabytes of data across multiple servers?
- **Solution:** Simulated a **MapReduce** model using **Divide and Conquer** techniques and **Parallel Computing** strategies.
- **DSA Concepts Used:** Divide and Conquer, Sorting, Hash Maps, Parallelism  
- **Impact:** Efficient and scalable data processing framework.

---

## 🧠 My Technical Stack

- **Languages:** Python, C++, JavaScript  
- **Tools:** Git, VS Code, Google Colab, Jupyter, Postman  
- **Libraries:** NumPy, Pandas, Matplotlib, Scikit-learn  
- **Platforms:** GitHub, Google Cloud, Firebase, Kaggle  

---

## 🎯 Objective

My goal is to apply my computer science fundamentals to build real-world solutions that scale. Google is the perfect place to achieve that vision. This portfolio reflects my journey and preparation to be part of such a global innovation engine.

---

## 📫 Contact

Let’s connect and build something meaningful together:

- **GitHub:** [github.com/rohitmendigeri](https://github.com/rohitmendigeri)  
- **Email:** rohit.mendigeri@example.com  
- **LinkedIn:** [linkedin.com/in/rohitmendigeri](https://linkedin.com/in/rohitmendigeri)

---

Thanks for checking out my portfolio!
