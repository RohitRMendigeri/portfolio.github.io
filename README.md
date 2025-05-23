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

We cam use **informed heuristics** that are both fast and realistic:

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
