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

These heuristics help guide the search efficiently while adapting to **real-world constraints**.


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
## 📌 Case Study 3: KD-Trees for Location-Based Search at Google

###  Challenge in Real-Time Systems  
Quickly finding the nearest locations (e.g., businesses, data centers, delivery points) based on a user's current position.

###  Solution Overview: Using KD-Tree (K-Dimensional Tree)  
A **KD-Tree** is a space-partitioning data structure used to organize points in a K-dimensional space (e.g., latitude and longitude for K=2). It enables efficient **nearest-neighbor** and **range queries** — perfect for location-aware services.

-  **Maps:** Find nearby places like ATMs, cafés, or gas stations.  
-  **Delivery/Logistics:** Assign nearest delivery partners.  
-  **Cloud Infrastructure:** Locate closest servers or CDN nodes for users.

###  Data Structures Used  
- **KD-Tree:** For organizing geo-locations in K-dimensional space.  
- **Max Heap:** To maintain top-K closest locations during queries.  

###  Algorithm – K-Dimensional Search (e.g., K = 2 for lat/lon)  
1. **Build:** Recursively split points by cycling through K dimensions (e.g., lat → lon → lat…).  
2. **Query:** Compare user location across K axes; traverse and backtrack if needed.  
3. **Track:** Use Max Heap to maintain top-K nearest neighbors.

###  Time & Space Complexity  

| Operation         | Time Complexity | Space Complexity |
|-------------------|------------------|------------------|
| Build Tree        | O(N log N)       | O(N)             |
| Nearest Neighbor  | O(log N) avg     | O(K)             |

*Where:*  
- N = number of locations, K = number of dimensions (e.g., 2 for lat/lon)

###  Usage 
-  **Maps & Search:** Find nearby POIs based on GPS.  
-  **Logistics:** Match users with nearest drivers.  
-  **CDNs & Edge Networks:** Route traffic to the closest server node.

KD-Trees enable **real-time**, **location-aware intelligence** — crucial for enhancing user experience in mapping, search, and cloud systems.


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

#### 1. **Watch-Time Analysis**  
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

#### 2. **Suspicious Behavior Detection**  
Sliding windows also help detect bots:
- If an account likes/comments on hundreds of videos in a short span, it's flagged using a **behavioral sliding window**.
- Similar to Gmail’s usage, but with a focus on action frequency in **video sessions**.



###  Uses Cases Sliding Windows

- **Google Trends**: Detects search bursts within moving 5-minute or 1-hour windows.
- **Google Safe Browsing**: Monitors URL visit frequency in short windows to assess phishing threats.



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
# 📌 Case study 14 : How Google Spanner Stores Data – Internals, Data Structures, and Algorithms



##  Overview of Data Storage in Spanner

**Google Spanner** is a globally distributed SQL database that unifies:

- **Relational models** (tables, transactions)
- **Distributed systems** (sharding, replication)
- **Consensus protocols** (Paxos)
- **Synchronized clocks** (TrueTime API)

It stores structured data using **automatic sharding**, **interleaved tables**, and **replicated tablets**, all while ensuring **strong consistency** and **global scalability**.



##  Physical Storage Structure

### 1. Tablet and Split Architecture
- Tables are automatically partitioned into **key ranges** known as **splits**.
- Each split is managed by a **tablet**.
- Tablets are distributed and **replicated** across 3–5 nodes.
- Each tablet belongs to a **Paxos group** which handles replication and consistency.

### 2. Directory-Based Sharding
- Spanner groups rows by common **directory prefixes** in their primary keys.
- These directories are the unit of load balancing and movement across servers.
- This method improves **locality** and simplifies re-sharding.



##  Data Layout

### Interleaved Table Storage
- Tables can be **interleaved** within parent-child hierarchies.
- Rows from a child table are stored **physically close** to their parent rows.
- This reduces I/O and improves range query performance on related data.



##  Algorithms Used in Spanner

###  1. Paxos (Leader-Based Consensus)
Used for:
- Replication of write operations.
- Leader election and coordination.
- Ensuring all replicas agree on the same commit log.

 Guarantees **one-copy equivalence**: the system behaves like a single-node database even though it is distributed.


###  2. TrueTime API
Used for:
- Assigning globally consistent timestamps.
- Preventing write-write conflicts across distributed replicas.

TrueTime provides a **bounded uncertainty interval**: TT.now() → [earliest, latest]
Spanner **waits for the uncertainty window** to pass before committing transactions, ensuring **external consistency** (linearizability).



###  3. MVCC (Multi-Version Concurrency Control)
- Each write creates a **new version** of a row with a unique commit timestamp.
- **Readers** can view a consistent snapshot without blocking writers.
- **Writers** commit only at timestamps **after** all previously committed versions.


###  4. B-Tree or LSM Tree Variants
Internally used in tablets for:
- Efficient **key-value lookups**.
- Fast **range scans**.
- High-throughput **inserts and deletes**.
- **Compaction** to manage multiple versions and reduce storage bloat.


###  5. Background Compaction Algorithms
Spanner runs background processes to:
- Merge older row versions.
- Apply **garbage collection** to expired data.
- Rebuild **indexes** where necessary.
- Optimize read performance by reducing storage fragmentation.


##  Life of a Write Operation

1. A transaction starts on the client.
2. Spanner assigns a **commit timestamp** using the TrueTime API.
3. The **Paxos leader** for the tablet initiates replication to its followers.
4. If a **quorum** (majority) acknowledges the write, it is considered committed.
5. The write is stored in:
   - **Write-ahead logs** for durability.
   - **In-memory buffers**, then flushed to disk storage.


##  Life of a Read Operation

1. A client issues a read request, optionally specifying a timestamp (for snapshot consistency).
2. If the read timestamp is earlier than the current **safe time** (from TrueTime), any replica can serve it.
3. Otherwise, the **leader** serves the read.
4. Spanner retrieves data using **MVCC** to construct a consistent snapshot based on the timestamp.



##  Time Complexity

| Operation                  | Time Complexity     | Description                                      |
|----------------------------|---------------------|--------------------------------------------------|
| Write                      | O(log n)            | Due to index updates + Paxos logging             |
| Read (Point Lookup)        | O(log n)            | B-Tree / LSM lookup                              |
| Range Scan                 | O(k + log n)        | k = rows returned                                |
| Paxos Replication          | O(R)                | R = number of replicas (3–5 typically)           |
| Snapshot Reads (MVCC)      | O(1) per version    | Timestamp-based version selection                |


 Space Complexity   : O(n)   : Includes data + version history + replication   





##  Applications within Google

- **Google Ads**: Ensures accurate billing and auction metadata with strong consistency.
- **Gmail**: Stores mailbox metadata like labels and threading.
- **Google Cloud Platform (GCP)**: Offers Spanner as a service for enterprise applications.
- **Google Photos & Play Store**: Use Spanner for consistent metadata access across the globe.


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
