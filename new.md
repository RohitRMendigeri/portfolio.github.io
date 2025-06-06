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
## 📌 Case Study :  
 # GPU Allocation in a Colab-Style Environment

A very simple scheduler matches user requests (Free, Pro, Pro+) to available GPUs (K80, T4, V100, A100) using:

1. Two priority queues (High and Low)  
2. A sorted list of idle GPUs  
3. A “best-fit” rule to pick the smallest GPU that meets each user’s need

---

## 1. Queues and GPU List

### 1.1. High-Priority Queue (`HEAP_HIGH`)
- Holds only **Pro+** users  
- Ordered by the time they requested a GPU (earliest first)  
- Each entry contains:
  - `user_id`  
  - `min_gpu_rank` (1=small job, 2=medium, 3=large)  
  - `arrival_time`  

### 1.2. Low-Priority Queue (`HEAP_LOW`)
- Holds **Pro** and **Free** users  
- Within this queue, Pro users go before Free users; among the same type, earlier requests go first  
- Each entry contains:
  - `user_id`  
  - `min_gpu_rank` (1=small, 2=medium, 3=large)  
  - `arrival_time`  

### 1.3. Idle GPUs List (`IDLE_LIST`)
- A list of all currently free GPUs, **sorted from lowest to highest rank**:
  1. K80 → rank 1  
  2. T4  → rank 2  
  3. V100 → rank 3  
  4. A100 → rank 4  
- Each entry shows:
  - `gpu_id`  
  - `gpu_type`  
  - `rank`  

---

## 2. How It Works

### 2.1. When a User Requests a GPU
1. User clicks **“Enable GPU.”**  
2. Collect the user’s:
   - `user_id`  
   - `tier` (Free / Pro / Pro+)  
   - `job_size` (small / medium / large)  
   - `arrival_time` (timestamp)  
3. Decide `min_gpu_rank` based on `job_size`:
   - small → 1  
   - medium → 2  
   - large → 3  
4. Put the request into:
   - **`HEAP_HIGH`** if the user is **Pro+**  
   - **`HEAP_LOW`** if the user is **Pro** or **Free** (Pro before Free)  
5. Show the user: “Waiting for GPU.”

### 2.2. When a GPU Becomes Free
1. Add the freed GPU into `IDLE_LIST` in the correct spot so it stays sorted by rank.  
2. Decide which queue to take from:
   - If `HEAP_HIGH` is not empty, pop its earliest entry.  
   - Otherwise, pop the earliest entry from `HEAP_LOW`.  
   - If both are empty, stop (no one is waiting).  
3. Take the popped request’s `min_gpu_rank` and scan `IDLE_LIST` from lowest rank to highest:
   - As soon as you find a GPU whose rank ≥ `min_gpu_rank`, assign that GPU to the user and remove it from `IDLE_LIST`.  
   - If you reach the end without finding a match (all ranks are too low), put the request back into its original queue.  
4. Repeat whenever another GPU opens up or a new request arrives.

---

**End of Document**  




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
