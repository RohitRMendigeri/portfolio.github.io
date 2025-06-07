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
## 📌 Case Study 1:  trie Powers in Google Systems

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
## 📌 Case Study 2: How A* Search Optimizes Google Maps Navigation

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
# 📌Case Study 3: KD-Trees for Location-Based Search at Google

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
## 📌 Case Study 4: Huffman Encoding for Efficient Data Compression at Google

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

## 📌 Case Study 5: Segment Trees in Google Analytics

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
## 📌 Case Study 6: Persistent Segment Trees in Workspace & Analytics

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

## 📌 Case Study 7: Mo's Algorithm in Query Optimization

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
## 📌 Case Study 8: Deferred Acceptance Algorithm

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
## 📌 Case Study 9: Uniform Cost Search (UCS) in Resource Optimization

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
## 📌 Case Study 10: Modular Multiplicative Inverse (MMI) in Secure Computation

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
## 📌 Case Study 11: Skip Lists for Efficient Ordered Data Access

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
## 📌 Case Study 12: Sliding Window Algorithm in Gmail and YouTube

###  The Challenge  
At massive scale, Google services like **Gmail** and **YouTube** face a common problem: making real-time decisions from fast, continuous streams of data. Gmail must filter spam the moment an email arrives. YouTube needs to track engagement patterns and detect suspicious activity from billions of viewers.

But scanning entire datasets every second is too costly. Enter: the **Sliding Window Algorithm** — a powerful approach to manage time-sensitive insights efficiently.



###  The Algorithm: Sliding Window Approach  
Sliding Window is a technique where a **subset of data** (the "window") is analyzed while moving through a larger dataset, step-by-step. It ensures:
- **Constant-time updates** (as old data exits and new enters)
- **Memory efficiency** (since only the window is stored)
- **Real-time insights** (without reprocessing everything)



###  In Gmail: Detecting Spam in Real-Time

#### 1. **Spam Phrase Detection**  
A window slides over email content to detect repeated suspicious phrases. This is often combined with:
- **Rabin-Karp Algorithm**: Uses a rolling hash (sliding window of characters) to match known spam patterns(words sentences).
- **Aho-Corasick Algorithm**: For multi-pattern matching, speeding up detection of multiple blacklisted phrases in a single scan.

#### 2. **Sender Behavior Monitoring**  
Gmail can monitor how many emails a user sends, and if it exceeds a certain threshold, the user and their emails may be flagged for further review.

It can be a time-based sliding window, like rate limiting or the Token Bucket method, to help Gmail detect sudden bursts of activity without blocking normal short-term spikes.

###  In YouTube: Engagement and Anomaly Detection

#### **Watch-Time Analysis**  
YouTube tracks where users **stop watching** a video. A sliding window moves through time-stamped engagement logs:
- If many users drop off between `00:45`–`01:15`, this part is flagged as potentially boring or irrelevant.
- Creators get feedback based on **aggregated sliding windows**, allowing them to improve content pacing.

YouTube can use a sliding window approach to analyze real-time data during a live stream. This can help in:
- Identifying the timestamp of peak viewership during a live stream.

- Detecting spikes in subscriber growth over time.

- Tracking when the most viewers liked and subscribed to the channel.

- Analyzing the frequency of interactions to gain deeper insights into user behavior.

- Deciding the optimal time to display ads, based on viewer engagement patterns.

By continuously calculating these metrics within a sliding time window, YouTube can make smarter, data-driven decisions in real time.


###  Algorithmic Details

####  Core Data Structures Used

| Data Structure      | Purpose                                           |
|---------------------|---------------------------------------------------|
| **Deque**           | Efficiently track max/min within a sliding window |
| **HashMap**         | Count occurrences, manage frequency windows       |
| **Rolling Hash**    | Used in Rabin-Karp for fast substring comparisons |


#### 🔗 Common Algorithm Pairings

| Algorithm            | Use Case with Sliding Window                         |
|----------------------|------------------------------------------------------|
| **Rabin-Karp**       | Rolling hash for substring matching                  |
| **Aho-Corasick**     | Multiple pattern string matching                     |
| **Token Bucket**     | Rate-limiting over a sliding time window             |



###  Final Impact  
The Sliding Window technique powers Gmail’s real-time spam detection and YouTube’s dynamic user engagement tracking. By focusing only on the **most recent and relevant** data, Google avoids performance bottlenecks while ensuring responsive, personalized experiences across its platforms.

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
# # 📚 Case Study: Google Drive – Distributed Cloud Storage, Synchronization, and Collaboration

---

## 🧩 Problem Statement

Google Drive is a cloud-based file storage, synchronization, and collaboration platform that serves **over a billion users** (individuals, enterprises, and educational institutions). It must:

- **Store** petabytes (exabytes) of user data (documents, images, videos, binaries, etc.).
- Provide **low-latency access** to files from anywhere in the world.
- Support **real-time synchronization** between multiple devices and collaborators.
- Handle **concurrent edits** (e.g., Google Docs, Sheets) while preserving consistency.
- Offer **versioning**, **offline access**, and **robust conflict resolution**.
- Maintain **data integrity**, **deduplication**, and **efficient bandwidth usage**.

Traditional single-server or monolithic file‐storage architectures cannot scale to these requirements. Google Drive’s design relies on a combination of specialized distributed file systems, scalable metadata stores, efficient synchronization algorithms, and conflict‐resolution mechanisms.

---

## 🧠 Solution Overview

Google Drive’s overall architecture can be thought of as four major layers:

1. **Physical & Distributed Storage Layer**  
   - Built on top of Google’s internal distributed file system (**Colossus**, the successor to GFS).  
   - Stores file “chunks” (fixed-size blocks) across many data centers, replicated for durability and high availability.

2. **Metadata & Indexing Layer**  
   - Maintains per-file and per-chunk metadata (ownership, permissions, versions, pointers to chunk locations).  
   - Uses a highly scalable key‐value store (originally Bigtable; now largely backed by Spanner/Megastore) to index metadata and directory hierarchies.

3. **Synchronization & Diffing Layer**  
   - Detects file changes on client devices using a **ranged‐checksum algorithm** (rsync‐style rolling checksums).  
   - Communicates deltas (changed chunks) to Drive servers, reducing bandwidth by only uploading modified blocks.  
   - Uses **Merkle trees** or **rolling‐checksum trees** to identify changed regions efficiently.

4. **Collaboration & Conflict‐Resolution Layer**  
   - For collaborative editing (Docs, Sheets, Slides), employs **Operational Transformation (OT)** or **CRDTs (Conflict‐free Replicated Data Types)** to merge concurrent changes in real time.  
   - Maintains a **version‐history tree** per document, enabling undo/redo and historical retrieval.

Below, we examine each layer in detail, highlighting the **data structures** and **algorithms** at work.

---

## 🚀 Layer 1: Physical & Distributed Storage

### 1.1 Colossus / GFS‐Derived Chunk Storage

- **Files are chunked** into fixed‐size blocks (e.g., 64 MB). Each chunk has a unique 64-bit identifier.  
- **Colossus** stores chunks in **replicated “chunk shards”** across multiple machines and data centers.  
  - Each chunk is stored on **three or more servers** (replica set) for redundancy.  
  - A **master/chubby‐coordinated service** keeps track of which chunk servers hold which chunk replicas.  

#### Data Structures:

- **Hash Tables** (in the master):  
  - Key: `chunk_id` → Value: list of `chunk_server_locations`.  
  - Allows O(1) lookup of where to retrieve or write a given chunk.

- **B-Trees / SSTables** (on each chunk server):  
  - Each chunk server manages many chunks on disk. Internally, they use **SSTable‐like sorted string tables** (or B-Tree variants) for on‐disk storage of chunk files and their checksums.

- **Write-Ahead Log (WAL)** / Commit Log:  
  - Each chunk server writes an incoming mutation (write) to a local WAL before applying it to the chunk file itself, ensuring durability. On crash, the WAL can be replayed.

#### Algorithms:

- **Consistent Hashing** (for initial chunk router placement—not strictly Dynamo-style, but similar concepts):  
  - Distributes incoming chunk‐writes / new chunk creations evenly across chunk‐server clusters.  
- **Replication Protocol** (Paxos‐inspired or Raft-inspired within Colossus):  
  - Ensures at least 2/3 (or majority) of replicas agree on the chunk’s latest version before acknowledging a write.  
  - Guarantees “one‐copy equivalence” for chunk data.

#### Time & Space Complexity:

- **Chunk Lookup**:  
  - O(1) to query master’s hash table → O(log n) on chunk server’s SSTable to read the data.  
- **Write**:  
  - O(1) to stage in WAL + O(log n) to append to SSTable.  
- **Replication**:  
  - O(R) to replicate to R replicas (R = 3–5 typically).  

---

## 🗄 Layer 2: Metadata & Indexing

### 2.1 Drive Metadata Store

All file‐ and folder‐metadata (file IDs, parent relationships, access control lists, timestamps, version history pointers) are stored in a **globally distributed, strongly consistent key‐value store**:

- **Backend**: Early versions used **Bigtable**; newer versions use **Spanner / Megastore** to provide global ACID transactions for metadata operations.  

#### Data Structures:

- **Directory Hierarchy**:  
  - Stored as a mapping:  
    ```
    (parent_folder_id, file_name) → child_file_id
    ```
  - Implemented as a **B-Tree or LSM Tree** inside Bigtable/Spanner for ordered scans (e.g., “List all files in folder X”).

- **File Metadata Record**:  
  - Key: `file_id` → Value: {owner_id, ACLs, size, chunk_ids[], latest_version, creation_time, modification_time, is_directory, mime_type, etc.}  
  - Stored in a row in the metadata table; uses **Wide‐column layout** (Bigtable/Spanner) so that each attribute can be accessed or updated independently.

- **Version History Index**:  
  - For each `file_id`, multiple versions exist, each keyed by a strictly increasing `version_id` or `timestamp`.  
  - Use of **multi‐versioned rows** via MVCC:  
    ```
    (file_id, version_timestamp) → metadata_snapshot
    ```
  - Allows O(log v) retrieval of a specific version (v = # versions).

- **Inverted Index for Search** (Drive’s built-in search):  
  - Maintains:  
    ```
    (token) → list of file_id where token appears (filename, content, metadata).
    ```
  - Data structure: **Inverted index** implemented on top of Bigtable or an internal search‐engine cluster (similar to Google Search’s index).  
  - Enables near-real-time “Search Drive” queries.

#### Algorithms:

- **B-Tree / LSM‐Tree Operations**:  
  - Insertion / Update: O(log n) per metadata attribute change.  
  - Range scan (list folder contents): O(log n + k), where k = # of entries in that folder.

- **Global Transaction Protocol (via Spanner / Paxos)**:  
  - Two‐phase commit + TrueTime to assign globally ordered timestamps.  
  - Guarantees ACID on metadata updates (e.g., moving a file from one folder to another).  

- **Search Query Processing**:  
  - **Tokenization** of filenames and (if applicable) document contents.  
  - **Inverted index lookup**: O(1) to locate postings list, then O(k) to scan results (k = # matching files or top-K returned).

#### Time & Space Complexity:

- **Metadata Read (point lookup by file_id)**: O(log N), N = total number of files.  
- **List Folder (range scan by parent_folder_id)**: O(log N + k), k = items in folder.  
- **Version Fetch**: O(log V), V = # versions per file.  
- **Search (per token)**:  
  - Lookup: O(1) to find postings via key‐value store.  
  - Merge: O(k) to merge multiple postings lists (k = sum of sizes of postings for user query).

---

## 🔄 Layer 3: Synchronization & Differential Updates

### 3.1 Rsync-Style Rolling Checksum & Chunking

When a user modifies a file locally, the Drive client must synchronize changes to the cloud **without re-uploading the entire file**. Google Drive uses a **rolling checksum algorithm** (inspired by rsync) to detect changed byte ranges:

1. **Chunk Division (Fixed-Size or Variable‐Size)**  
   - The file is logically divided into **fixed‐size blocks** (e.g., 8 KB).  
   - Each block is assigned a **weak checksum** (e.g., Adler-32 or a simple rolling Adler) and a **strong checksum** (e.g., MD5 or SHA-256) for verification.

2. **Rolling Checksum Computation**  
   - As the client reads the modified file, it continuously computes the checksum over a sliding window of block size.  
   - **Rolling‐checksum update**:  
     \[
     \text{new\_checksum} = (\text{old\_checksum} - \text{old\_byte}) / B + \text{new\_byte} \times B^{k-1} \bmod M
     \]
     where B is a base (e.g., 256), k is block length, M is a modulus.

3. **Match & Delta Identification**  
   - For each rolling‐checksum match (weak checksum matches a stored block), the client verifies with the **strong checksum**.  
   - If both match, that block is unchanged; otherwise, it is flagged as changed.

4. **Delta Transfer**  
   - Only the **changed blocks** (and any partially overlapping blocks at boundaries) are sent to the server.  
   - Server reconstructs the new file by reassembling unchanged stored blocks + newly uploaded blocks.

#### Data Structures:

- **Block Lookup Table** (client & server side):  
  - Key: `weak_checksum` → Value: list of `(strong_checksum, block_id)`.  
  - When a rolling checksum matches `weak_checksum`, the client queries this table to confirm with `strong_checksum`.  
  - On the server: stores a mapping of `(file_id, block_checksum)` → location of that block in chunk store.

- **Merkle Tree (for full - file integrity check)**  
  - A **binary hash tree** where:  
    - **Leaf nodes**: hash of each fixed‐size block.  
    - **Internal nodes**: hash of concatenation of their children’s hashes.  
  - Allows O(log n) verification that two file versions share common subtrees (blocks).  
  - Used primarily for **end‐to‐end integrity** and possibly for cross-file deduplication.

#### Algorithms:

- **Rsync Rolling Checksum Algorithm**:  
  - Time: O(n) to scan an n-byte file to compute rolling checksums over every byte position (in practice, block‐aligned).  
  - Space: O(b) for maintaining the current window (b = block size).

- **Delta Reconstruction (on Server)**:  
  - For each block in the updated file:  
    1. If `block_checksum` exists in server’s table → reuse existing chunk.  
    2. Else → store new chunk.  
  - Time: O(m log C), where m = # changed blocks, C = total chunk entries (for lookup). Strong checksums stored in a hash table ⇒ O(1) average lookup.

- **Merkle Tree Verification**:  
  - Build Merkle tree: O(n) to hash all blocks; height = O(log n).  
  - Compare roots: if equal, files are identical; otherwise, traverse down (O(log n) to find first differing block).

---

## 🔄 Layer 4: Collaboration & Conflict Resolution

### 4.1 Operational Transformation (OT) – Real-Time Docs Collaboration

For Google Docs, Sheets, and Slides (which are “stored” in Drive), Drive must manage **real-time collaborative edits** by multiple users on the same document:

- **Operational Transformation (OT)** ensures that concurrent operations (inserts, deletes, formatting changes) commute to a consistent final state.  

#### Core Components:

1. **Operation Buffer & History**  
   - Each client sends edits as **operations** (e.g., Insert(“abc”, pos=5), Delete(3, pos=8)).  
   - The server maintains a **total‐ordered buffer** of applied operations with timestamps.

2. **Transformation Function**  
   - When a new operation **Opₙ** arrives but another operation **Opₘ** (with earlier timestamp) has already been applied locally, Drive computes:  
     \[
     \text{Opₙ}' = \mathrm{Transform}( \text{Opₙ},\, \text{Opₘ} )
     \]
   - Ensures:  
     \[
     \text{Apply}( \text{Opₘ},\, \text{Apply}( \text{Opₙ},\, S )) = \text{Apply}( \text{Opₙ}',\, \text{Apply}( \text{Opₘ},\, S ))
     \]
   - Guarantees **convergence** (all replicas end up in the same state).

3. **Version Vectors / Timestamps**  
   - Each operation carries a **Lamport‐style timestamp** or **vector clock** to track causal ordering.  
   - Server assigns a **global sequence number** via a Paxos‐style consensus for OT operations.

4. **State Machine Replication**  
   - OT is performed on a **replicated state machine** so that all participants see the same total order of operations.  
   - Under‐the-hood, this leverages a **Raft/Paxos-inspired protocol** to ensure all replicas apply updates in the same order.

#### Data Structures:

- **Operation Log**:  
  - An **ordered list** of (op_id, client_id, timestamp, operation_details).  
  - Stored in a **durable state machine log** (often implemented on top of Bigtable or Spanner for persistence).

- **Character / Object Trees** (CRDT Variant in some clients)  
  - To optimize per-document replication and OT, Drive may represent document state as a **tree or sequence CRDT** (e.g., RGA, LSEQ).  
  - Each node: character or element with a unique identifier.  
  - Facilitates O(log n) insertion/deletion in the sequence.

#### Algorithms:

- **OT Transform Function**:  
  - For two operations **A** and **B**: compute `A' = Transform(A, B)` or `B' = Transform(B, A)`.  
  - Typical time: O(1) for simple insert/delete, O(l) if scanning a sequence of length l to adjust indices. In practice, OT implementations maintain indexing structures to reduce this to **O(log n)**.

- **CRDT Insertion/Deletion** (if used in some Drive clients):  
  - Insert: O(log n) to locate correct position in a balanced tree.  
  - Delete: O(log n) to mark a node as tombstone.  
  - Guarantees eventual consistency without central coordination (though server‐side OT is more common in Google Docs).

---

## 🔃 End‐to‐End “Open File” Workflow (Read & Sync)

1. **Client Requests File Metadata**  
   - Client fetches file_id → queries metadata store (Spanner): O(log N).  
   - Receives: latest_version_id, list of chunk_ids.

2. **Client Requests Chunks from Colossus**  
   - For each chunk_id:  
     - Query master’s hash table for chunk_server_locations (O(1)).  
     - Read chunk from one of the replica chunk servers (O(log C) on server’s SSTable).

3. **Assemble File Locally**  
   - Client concatenates chunks in chunk_id order. If file is large, streams chunks as needed.

4. **Client Watches for File Changes**  
   - Client maintains a **long-poll / watch** on metadata (via a push queue service).  
   - When metadata “version” changes, client re-fetches changed chunk_ids or diffs.

5. **Client Applies Differential Update**  
   - Uses rolling checksum to detect which blocks changed since last sync.  
   - Only uploads new/modified blocks.  
   - Server reassembles new version by merging unchanged blocks (O(m) block writes, with m = # modified blocks).

---

## 🔍 End‐to‐End “Collaborative Edit” Workflow (Google Docs)

1. **Client Sends Operation**  
   - User types “a” at position 5: client generates Insert(“a”, 5) with local timestamp.  

2. **Server Assigns Global Sequence**  
   - Operation is sent to a **Drive collaboration server** (backed by Spanner for durability).  
   - Server assigns a **global sequence number** via Paxos/TrueTime to this operation.

3. **Server Transforms & Broadcasts**  
   - The server transforms the incoming operation against any concurrent operations it has previously queued (OT transform).  
   - Broadcasts the transformed op to all connected clients.

4. **Clients Apply Operation**  
   - Each client applies the operation in global sequence order to its local document state.  
   - UI updates in real time; clients send acknowledgments back to the server.

5. **Persistence**  
   - Every operation is appended to an **operation log** (Spanner/Megastore).  
   - Periodic checkpoints (snapshots) collapse the operation log for faster document loading.

---

## ⏱️ Time & Space Complexity Summary

| Workflow / Operation       | Algorithm / Data Structure                   | Time Complexity              | Notes                                                           |
|----------------------------|-----------------------------------------------|------------------------------|-----------------------------------------------------------------|
| **Chunk Lookup**           | Hash Table + SSTable (Colossus)              | O(1) + O(log C)               | C = # chunks per server                                          |
| **Chunk Read/Write**       | SSTable write/read + replication (Paxos)     | O(log C) + O(R)               | R = # replicas                                                   |
| **Metadata Lookup**        | B-Tree/Spanner point lookup                  | O(log N)                     | N = # total files                                                |
| **List Folder**            | B-Tree/Spanner range scan                    | O(log N + k)                 | k = # items in folder                                            |
| **Rolling Checksum**       | Rsync Algorithm (block‐aligned)              | O(file_size / block_size)    | Scans entire file once                                           |
| **Merkle Tree Build**      | Hash over blocks                             | O(n) + O(log n) tree ops     | n = # blocks                                                     |
| **OT Transform**           | OT transformation (index correction)         | O(log L)                     | L = length of document (with balanced sequence CRDT)             |
| **CRDT Insert/Delete**     | Tree insertion/deletion                      | O(log L)                     | L = sequence length in document                                   |
| **Search (Inverted Index)**| Hash table lookup + posting merge            | O(1) + O(k)                   | k = # matching files                                              |

---

## ⚙️ Key Benefits of Drive’s Approach

- **Bandwidth Efficiency**:  
  - Rolling checksum + delta transfers minimize upload/download of unmodified data.  
  - Merkle/Strong checksums ensure integrity with minimal overhead.

- **Low-Latency Access**:  
  - Colossus distributes chunks to edge caches (Colossus near users) for fast reads.  
  - Metadata lookups are constant or logarithmic, backed by Spanner’s global consistency.

- **Strong Consistency & ACID Metadata**:  
  - Spanner (TrueTime + Paxos) ensures that file‐rename, move, share‐permissions changes are immediately and consistently visible globally.

- **Scalable Collaboration**:  
  - OT/CRDT approach allows thousands of simultaneous collaborators on a document while guaranteeing convergence.  
  - Per‐document operation logs scale horizontally across servers.

- **Versioning & History**:  
  - Multi‐version metadata allows “undo,” “version history,” and “restore” operations in O(log V) time.  
  - Efficient snapshotting via background compaction and checkpointing.

- **Fault Tolerance & Durability**:  
  - Triple/chunk replication in Colossus + WAL ensures zero data loss even if multiple nodes fail.  
  - Metadata persisted in globally replicated Spanner ensures no single point of failure.

---

## 📚 References

- **Bigtable & Spanner**  
  - “Bigtable: A Distributed Storage System for Structured Data” (OSDI ’06)  
  - “Spanner: Google’s Globally Distributed Database” (OSDI ’12)

- **Colossus (GFS successor)**  
  - “Colossus: Bigtable Filesystem at Exabyte Scale” (Google Tech Talk, 2014)

- **Rsync & Rolling Checksums**  
  - “The rsync algorithm” (Project Rsync, Technical Report)

- **Operational Transformation**  
  - “Implementing Real-Time Collaborative Editors: Operational Transformation and CRDTs” (SIGMOD Tutorials)

- **Crash Recovery & WAL**  
  - “The Google File System” (SOSP ’03) (foundation for WAL practices)

- **Merkle Trees**  
  - “A Secure and Efficient File System” (Early Merkle Tree usage in distributed storage)




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
