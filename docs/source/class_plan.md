# Teaching Plan: 5-Minute Videos & 30-Minute Classes

---

## Detailed Scripts

These are fully developed scripts for teaching demonstrations, ready to be converted into presentation slides.

---

# 📹 CPU SCHEDULING — 5-Minute Video Script

## Opening Hook (0:00 - 0:30)

**[SLIDE 1: Title - "CPU Scheduling: Who Gets the Processor Next?"]**

> "Your computer is running Spotify, Chrome with 20 tabs, VS Code, and a Zoom call — all 'at once.' But here's the secret: your CPU can really only run ONE thing at a time."

**[VISUAL: Multiple applications competing for a single CPU]**

> "So how does the operating system decide which process gets the CPU next? That's CPU scheduling — and getting it wrong means laggy apps, frozen screens, and frustrated users."

---

## Part 1: Why Scheduling Matters (0:30 - 1:00)

**[SLIDE 2: CPU-I/O Burst Cycle]**

> "Every process alternates between two phases: CPU bursts — doing actual computation — and I/O bursts — waiting for disk, network, or keyboard input."

**[VISUAL: Timeline showing CPU burst → I/O wait → CPU burst → I/O wait]**

> "When a process is waiting for I/O, the CPU sits idle unless we schedule another process. Good scheduling keeps the CPU busy and users happy."

**[SLIDE 3: Key Metrics]**

> "We measure scheduling quality by:
> - **Waiting time**: How long processes sit in the ready queue
> - **Turnaround time**: Total time from arrival to completion
> - **Response time**: Time until first response (crucial for interactive apps)"

---

## Part 2: Non-Preemptive Scheduling (1:00 - 2:15)

**[SLIDE 4: FCFS - First Come First Serve]**

> "The simplest algorithm: First Come, First Serve. Processes run in arrival order — like a queue at a bank."

**[VISUAL: Gantt chart with P1=24ms, P2=3ms, P3=3ms arriving in order]**

```
| P1 (24ms)                  | P2 | P3 |
0                           24   27   30
```

> "If P1 arrives first, P2 and P3 wait 24ms and 27ms respectively. Average wait: 17ms."

**[SLIDE 5: The Convoy Effect]**

> "But what if P2 and P3 arrived first?"

```
| P2 | P3 | P1 (24ms)                  |
0   3    6                            30
```

> "Now average wait is only 3ms! Same total work, but short jobs finish much faster. This is the convoy effect — one slow process blocks everyone."

**[SLIDE 6: SJF - Shortest Job First]**

> "Shortest Job First solves this: always run the shortest job next."

**[VISUAL: Gantt chart with P4=3, P1=6, P3=7, P2=8]**

```
| P4 | P1    | P3      | P2        |
0   3       9        16          24
```

> "Average wait drops from 10.25ms (FCFS) to just 7ms! SJF is provably optimal for minimizing average wait time."

> "The catch? You need to know how long each job will take — which in reality, you don't. Operating systems estimate using exponential averaging of past bursts."

---

## Part 3: Preemptive Scheduling (2:15 - 3:30)

**[SLIDE 7: Preemptive vs Non-Preemptive]**

> "So far, once a process starts, it runs until it finishes or blocks. That's non-preemptive. But what if a more important process arrives?"

> "Preemptive scheduling can interrupt a running process and switch to another. Essential for responsive systems!"

**[SLIDE 8: SRTF - Shortest Remaining Time First]**

> "SRTF is preemptive SJF: if a new process arrives with a shorter remaining time, preempt the current one."

**[VISUAL: Gantt chart with arrivals at different times]**

```
Process | Arrival | Burst
P1      | 0       | 8
P2      | 1       | 4
P3      | 2       | 9
P4      | 3       | 5

| P1 | P2    | P4      | P1           | P3              |
0   1      5        10              17                 26
```

> "At t=1, P2 arrives with burst 4. P1 has 7 remaining. Since 4 < 7, we preempt P1 and run P2!"

> "Average wait: 6.5ms — even better than non-preemptive SJF's 7.75ms."

**[SLIDE 9: Round Robin]**

> "Round Robin gives everyone a fair share. Each process gets a fixed time quantum — say 4ms — then goes to the back of the queue."

**[VISUAL: Circular queue with time quantum = 4]**

```
| P1 | P2 | P3 | P1 | P3 | P1 | P3 | P1 | P1 | P1 |
0   4    7   10  14  17  21  24  28  30
```

> "With P1=24ms, P2=3ms, P3=3ms and quantum=4: P2 and P3 finish quickly, while P1 makes steady progress."

> "Trade-off: Small quantum = more responsive but more context switch overhead. Large quantum degrades to FCFS."

---

## Part 4: Putting It All Together (3:30 - 4:30)

**[SLIDE 10: Comparison Table]**

| Algorithm | Preemptive? | Pros | Cons |
|-----------|-------------|------|------|
| **FCFS** | No | Simple, fair | Convoy effect, poor wait times |
| **SJF** | No | Optimal avg wait | Must predict burst lengths |
| **SRTF** | Yes | Best avg wait | Overhead, starvation risk |
| **Round Robin** | Yes | Fair, responsive | Higher turnaround time |

**[SLIDE 11: Real-World: Multi-Level Feedback Queues]**

> "Real operating systems like Linux and Windows use multi-level feedback queues: multiple queues with different priorities and algorithms."

**[VISUAL: Pyramid of queues - Interactive at top (RR, small quantum), Batch at bottom (FCFS)]**

> "New processes start at high priority. If they use their full quantum, they drop to a lower queue. I/O-bound interactive processes stay high; CPU hogs sink to the bottom."

> "This adapts automatically without needing to know burst times in advance!"

---

## Part 5: AI Connection & Closing (4:30 - 5:00)

**[SLIDE 12: Connection to AI/ML]**

> "Why does this matter for AI? GPU cluster scheduling uses these same concepts! SLURM and Kubernetes schedule ML training jobs using priority queues, fair-share algorithms, and preemption."

**[VISUAL: GPU cluster with multiple jobs waiting]**

> "And here's a fun fact: Google's research shows that better scheduling can reduce energy consumption by 20-40% — the same algorithms that make your laptop responsive also make AI more sustainable."

**[SLIDE 13: Key Takeaways]**

> "To recap:
> 1. CPU scheduling decides which process runs next
> 2. FCFS is simple but suffers from convoy effect
> 3. SJF minimizes wait time but needs burst predictions
> 4. Round Robin provides fairness and responsiveness
> 5. Real systems combine these in multi-level feedback queues"

**[SLIDE 14: Thank You]**

> "CPU scheduling: the unsung hero that keeps your computer from freezing. Any questions?"

---

---

# 📹 WORD EMBEDDINGS — 5-Minute Video Script

## Opening Hook (0:00 - 0:40)

**[SLIDE: Show a simple question]**

> "Quick question: Which of these is more similar to 'dog' — 'cat' or 'democracy'?"

*Obvious, right? Cat! But here's the thing — to a computer, 'dog', 'cat', and 'democracy' are just... strings of characters. There's no inherent notion of meaning or similarity.*

**[SLIDE: Three words represented as random strings]**

> "So how do we teach machines to understand that 'dog' and 'cat' are related concepts while 'democracy' is something completely different?"

**[SLIDE: Title - "Word Embeddings: Teaching Machines the Meaning of Words"]**

> "The answer is word embeddings — one of the most elegant ideas in modern AI."

---

## Part 1: The Problem with Traditional Representations (0:40 - 1:30)

**[SLIDE: One-hot encoding visualization]**

> "Traditionally, we represented words as 'one-hot vectors'. If our vocabulary has 10,000 words, each word becomes a vector with 10,000 dimensions — all zeros except for a single 1."

**[VISUAL: Show "cat" = [0,0,0,1,0,...,0] and "dog" = [0,1,0,0,0,...,0]]**

> "The problem? To a computer, the distance between 'cat' and 'dog' is exactly the same as between 'cat' and 'democracy'. Every word is equally different from every other word!"

**[SLIDE: Distance comparison diagram]**

> "This is clearly wrong. We need a smarter representation that captures meaning."

---

## Part 2: The Big Idea (1:30 - 2:45)

**[SLIDE: Quote by J.R. Firth]**

> "The solution comes from a beautiful linguistic insight from the 1950s: 'You shall know a word by the company it keeps.'"

**[SLIDE: Example sentences]**

> "Think about it — where do you typically see the word 'dog'? In sentences like 'The dog barked', 'Feed the dog', 'Walk the dog'. And 'cat'? 'The cat purred', 'Feed the cat', 'Pet the cat'."

**[VISUAL: Words with overlapping context clouds]**

> "Words that appear in similar contexts tend to have similar meanings! This is called the distributional hypothesis."

**[SLIDE: Word2Vec training concept]**

> "Word embeddings like Word2Vec learn by predicting context. Given millions of sentences, the algorithm learns to represent each word as a dense vector — say, 300 numbers — where similar words end up close together in this 300-dimensional space."

**[VISUAL: t-SNE visualization showing clusters]**

> "When we visualize this space, something magical happens — animals cluster together, countries cluster together, verbs cluster together... all learned automatically from text!"

---

## Part 3: The Magic of Vector Arithmetic (2:45 - 4:00)

**[SLIDE: The famous analogy]**

> "But here's where it gets really mind-blowing. These embeddings capture more than just similarity — they capture relationships."

**[VISUAL: King - Man + Woman = Queen equation with vectors]**

> "The most famous example: If you take the vector for 'king', subtract 'man', and add 'woman'... you get something remarkably close to 'queen'!"

**[ANIMATION: Showing the parallelogram in 2D projection]**

> "The 'royalty' direction and 'gender' direction are encoded separately in this space. We can do arithmetic with meaning!"

**[SLIDE: More examples]**

> "Paris - France + Italy ≈ Rome. Walking - Walk + Swim ≈ Swimming. These relationships emerge naturally from the training process!"

---

## Part 4: Why It Matters (4:00 - 4:45)

**[SLIDE: Applications cascade]**

> "Word embeddings revolutionized NLP. Suddenly, machines could understand that 'happy' and 'joyful' are synonyms, that 'bank' can mean a financial institution or a river's edge depending on context."

**[VISUAL: Timeline from Word2Vec to GPT]**

> "This idea — representing words as meaningful vectors — laid the foundation for everything that followed: ELMo, BERT, GPT, and all the large language models we use today."

**[SLIDE: Key takeaway]**

> "The genius of embeddings? Instead of telling a computer what words mean, we let it discover meaning from patterns in language."

---

## Closing (4:45 - 5:00)

**[SLIDE: Summary]**

> "To recap: Word embeddings transform words into vectors where proximity reflects similarity. They're learned from context, and they capture rich semantic relationships. It's how we gave machines their first glimpse of what words actually mean."

**[SLIDE: Thank you with key equation: Meaning = Context]**

---

---

# 📚 PAGERANK — 30-Minute Class Script

## Introduction & Hook (0:00 - 3:00)

**[SLIDE 1: Title - "PageRank: How Google Organized the World's Information"]**

> "Good morning! Today we're going to explore one of the most influential algorithms in computing history — an algorithm that helped two Stanford PhD students build a trillion-dollar company and fundamentally changed how we access information."

**[SLIDE 2: The Pre-Google Problem]**

> "Let me take you back to 1997. The internet has about 100 million web pages. You want to find information about... let's say, 'jaguar'. You type it into AltaVista or Yahoo."

**[VISUAL: Search results chaos]**

> "What do you get? A random jumble — car websites, animal pages, Mac OS versions, sports teams, and spam. The search engines of that era used keyword matching. If 'jaguar' appeared 50 times on a page, that page ranked higher. Easily gamed, completely unreliable."

**[SLIDE 3: The Question]**

> "The fundamental question Larry Page and Sergey Brin asked was: How do you measure which page is genuinely important?"

---

## Part 1: The Core Insight (3:00 - 7:00)

**[SLIDE 4: Citation Analogy]**

> "Page and Brin borrowed an idea from academia. How do we judge the importance of a research paper? By counting citations! A paper cited by many others is probably important."

**[VISUAL: Academic citation network]**

> "But here's the clever twist — not all citations are equal. A citation from a highly-cited paper should count more than a citation from an obscure one."

**[SLIDE 5: The Web as a Graph]**

> "They applied this to the web. Think of every web page as a node. Every hyperlink is a directed edge — a 'vote' from one page to another."

**[VISUAL: Small web graph with 5-6 pages and directed links]**

> "A page is important if it's linked to by other important pages. Notice the recursion? This is the key insight!"

**[SLIDE 6: Fun Fact]**

> "Quick trivia: The name 'PageRank' is a pun — it's both about ranking web 'pages' AND named after Larry Page himself!"

---

## Part 2: The Random Surfer Model (7:00 - 12:00)

**[SLIDE 7: Random Surfer Concept]**

> "Let me give you an intuitive way to understand PageRank. Imagine a random web surfer — let's call her Alice."

**[VISUAL: Stick figure Alice on a web graph]**

> "Alice starts on a random page. At each step, she randomly clicks one of the links on that page. She keeps doing this for a very, very long time."

**[SLIDE 8: Question]**

> "Question: After billions of clicks, on which page is Alice most likely to be found?"

**[Pause for thinking]**

> "The answer gives us PageRank! Pages where Alice spends more time are more important. They're 'central' in the web's link structure."

**[SLIDE 9: Interactive Demo — Small Graph]**

**[VISUAL: Animated random walk on a 6-node graph]**

> "Let's watch this in action. Here's a small web with 6 pages. Watch Alice's random walk... notice how she keeps returning to certain nodes? Those are the high-PageRank pages!"

**[SLIDE 10: The Damping Factor]**

> "But wait — there's a problem. What if Alice reaches a page with no outgoing links? She's stuck! Or what if there's a cycle she can never escape?"

**[VISUAL: Dangling node and cycle examples]**

> "The solution: with probability 0.15, Alice gets 'bored' and teleports to a completely random page. The remaining 0.85 probability, she follows a link normally. This 0.85 is called the damping factor d."

---

## Part 3: The Mathematical Formulation (12:00 - 18:00)

**[SLIDE 11: The Equation]**

> "Let's formalize this. For a page A, its PageRank is:"

$$PR(A) = \frac{1-d}{N} + d \sum_{i \in M(A)} \frac{PR(T_i)}{L(T_i)}$$

**[Walk through each term]**

> "Where:
> - N is the total number of pages
> - d is the damping factor (typically 0.85)
> - M(A) is the set of pages that link TO page A
> - L(Ti) is the number of outgoing links from page Ti"

**[SLIDE 12: Intuition Behind the Formula]**

> "The first term (1-d)/N represents the teleportation — the random jumps. The second term is the sum of 'votes' from linking pages, where each page's vote is its PageRank divided by how many links it has."

> "Think about it — if a page with PageRank 0.5 has 10 outgoing links, each link passes 0.05 of its importance."

**[SLIDE 13: Worked Example]**

**[VISUAL: Simple 4-page example from Wikipedia]**

> "Let's work through this. Four pages: A, B, C, D. 
> - B links to A and C
> - C links to A
> - D links to A, B, and C"

**[Step-by-step calculation]**

> "Starting with all pages having PageRank 0.25...
> After iteration 1... After iteration 2... The values converge!"

**[SLIDE 14: Matrix Formulation]**

> "For those who like linear algebra, PageRank is actually an eigenvector problem!"

$$\mathbf{r} = M\mathbf{r}$$

> "The PageRank vector r is the principal eigenvector of the transition matrix M with eigenvalue 1. We find it using power iteration — repeatedly multiply until convergence."

**[SLIDE 15: Convergence]**

> "How fast does this converge? The original Google paper reported that 322 million pages converged in just 52 iterations. The algorithm scales beautifully!"

---

## Part 4: Implementation Insights (18:00 - 22:00)

**[SLIDE 16: The Power Iteration Algorithm]**

```python
def pagerank(M, d=0.85, epsilon=1e-8):
    N = M.shape[0]
    r = np.ones(N) / N  # Start uniform
    
    while True:
        r_new = (1-d)/N + d * M @ r
        if np.linalg.norm(r_new - r) < epsilon:
            return r_new
        r = r_new
```

> "The algorithm is remarkably simple! Initialize uniformly, apply the formula, repeat until convergence."

**[SLIDE 17: Handling Edge Cases]**

> "Real-world considerations:
> 1. **Dangling nodes** (no outlinks): Distribute their PageRank evenly to all pages
> 2. **Spider traps** (self-loops or small cycles): The damping factor prevents getting stuck
> 3. **Sparse matrix storage**: The web is sparse — most pages link to only a few others"

**[SLIDE 18: Scale]**

> "In 1998, Google indexed 24 million pages. Today? Over 30 billion! The algorithm's efficiency and parallelizability were crucial to Google's success."

---

## Part 5: Applications Beyond Search (22:00 - 26:00)

**[SLIDE 19: Beyond the Web]**

> "The beautiful thing about PageRank is that it works on ANY directed graph where you want to find important nodes!"

**[SLIDE 20: Academic Citations]**

> "Remember where we started — academic citations! PageRank has been adapted for measuring paper and researcher influence. It's fairer than just counting citations."

**[SLIDE 21: Social Networks]**

> "Twitter uses personalized PageRank for 'Who to Follow' recommendations. The algorithm finds users who are well-connected to people you already follow."

**[SLIDE 22: Biology & Neuroscience]**

> "In biology, PageRank identifies essential proteins in interaction networks. In neuroscience, it correlates with neuron firing rates! The math transcends domains."

**[SLIDE 23: Sports Rankings]**

> "Fun application: PageRank has been used to rank NFL teams based on who-beat-whom networks. It captures strength of schedule automatically!"

---

## Part 6: Limitations & Evolution (26:00 - 28:00)

**[SLIDE 24: Limitations]**

> "PageRank isn't perfect:
> - **Topic-agnostic**: A high-PageRank page about cats won't help you if you're searching for dogs
> - **Favors old pages**: New pages haven't accumulated links yet
> - **Gaming**: Link farms and paid links tried to manipulate rankings"

**[SLIDE 25: Modern Search]**

> "Today, Google uses over 200 ranking signals. RankBrain and BERT add machine learning. But PageRank remains a foundational signal — the backbone on which everything else is built."

---

## Conclusion & Summary (28:00 - 30:00)

**[SLIDE 26: Key Takeaways]**

> "Let's recap what we've learned:
> 1. PageRank defines importance recursively — important pages link to important pages
> 2. The random surfer model provides intuition: PageRank = probability of being on a page after infinite random walks
> 3. Mathematically, it's the principal eigenvector of the web's transition matrix
> 4. The algorithm is simple, scalable, and converges quickly
> 5. The idea extends far beyond web search"

**[SLIDE 27: The Bigger Picture]**

> "PageRank represents a fundamental shift in thinking — from content-based to structure-based analysis. The links between things often tell us more than the things themselves."

**[SLIDE 28: Questions?]**

> "That's PageRank — an algorithm that turned the chaos of the early web into the organized information universe we navigate today. Any questions?"

---

---

# � CPU SCHEDULING — 5-Minute Video Script

## Opening Hook (0:00 - 0:30)

**[SLIDE 1: Title - "CPU Scheduling: Who Gets the Processor Next?"]**

> "Your computer is running Spotify, Chrome with 20 tabs, VS Code, and a Zoom call — all 'at once.' But here's the secret: your CPU can really only run ONE thing at a time."

**[VISUAL: Multiple applications competing for a single CPU]**

> "So how does the operating system decide which process gets the CPU next? That's CPU scheduling — and getting it wrong means laggy apps, frozen screens, and frustrated users."

---

## Part 1: Why Scheduling Matters (0:30 - 1:00)

**[SLIDE 2: CPU-I/O Burst Cycle]**

> "Every process alternates between two phases: CPU bursts — doing actual computation — and I/O bursts — waiting for disk, network, or keyboard input."

**[VISUAL: Timeline showing CPU burst → I/O wait → CPU burst → I/O wait]**

> "When a process is waiting for I/O, the CPU sits idle unless we schedule another process. Good scheduling keeps the CPU busy and users happy."

**[SLIDE 3: Key Metrics]**

> "We measure scheduling quality by:
> - **Waiting time**: How long processes sit in the ready queue
> - **Turnaround time**: Total time from arrival to completion
> - **Response time**: Time until first response (crucial for interactive apps)"

---

## Part 2: Non-Preemptive Scheduling (1:00 - 2:15)

**[SLIDE 4: FCFS - First Come First Serve]**

> "The simplest algorithm: First Come, First Serve. Processes run in arrival order — like a queue at a bank."

**[VISUAL: Gantt chart with P1=24ms, P2=3ms, P3=3ms arriving in order]**

```
| P1 (24ms)                  | P2 | P3 |
0                           24   27   30
```

> "If P1 arrives first, P2 and P3 wait 24ms and 27ms respectively. Average wait: 17ms."

**[SLIDE 5: The Convoy Effect]**

> "But what if P2 and P3 arrived first?"

```
| P2 | P3 | P1 (24ms)                  |
0   3    6                            30
```

> "Now average wait is only 3ms! Same total work, but short jobs finish much faster. This is the convoy effect — one slow process blocks everyone."

**[SLIDE 6: SJF - Shortest Job First]**

> "Shortest Job First solves this: always run the shortest job next."

**[VISUAL: Gantt chart with P4=3, P1=6, P3=7, P2=8]**

```
| P4 | P1    | P3      | P2        |
0   3       9        16          24
```

> "Average wait drops from 10.25ms (FCFS) to just 7ms! SJF is provably optimal for minimizing average wait time."

> "The catch? You need to know how long each job will take — which in reality, you don't. Operating systems estimate using exponential averaging of past bursts."

---

## Part 3: Preemptive Scheduling (2:15 - 3:30)

**[SLIDE 7: Preemptive vs Non-Preemptive]**

> "So far, once a process starts, it runs until it finishes or blocks. That's non-preemptive. But what if a more important process arrives?"

> "Preemptive scheduling can interrupt a running process and switch to another. Essential for responsive systems!"

**[SLIDE 8: SRTF - Shortest Remaining Time First]**

> "SRTF is preemptive SJF: if a new process arrives with a shorter remaining time, preempt the current one."

**[VISUAL: Gantt chart with arrivals at different times]**

```
Process | Arrival | Burst
P1      | 0       | 8
P2      | 1       | 4
P3      | 2       | 9
P4      | 3       | 5

| P1 | P2    | P4      | P1           | P3              |
0   1      5        10              17                 26
```

> "At t=1, P2 arrives with burst 4. P1 has 7 remaining. Since 4 < 7, we preempt P1 and run P2!"

> "Average wait: 6.5ms — even better than non-preemptive SJF's 7.75ms."

**[SLIDE 9: Round Robin]**

> "Round Robin gives everyone a fair share. Each process gets a fixed time quantum — say 4ms — then goes to the back of the queue."

**[VISUAL: Circular queue with time quantum = 4]**

```
| P1 | P2 | P3 | P1 | P3 | P1 | P3 | P1 | P1 | P1 |
0   4    7   10  14  17  21  24  28  30
```

> "With P1=24ms, P2=3ms, P3=3ms and quantum=4: P2 and P3 finish quickly, while P1 makes steady progress."

> "Trade-off: Small quantum = more responsive but more context switch overhead. Large quantum degrades to FCFS."

---

## Part 4: Putting It All Together (3:30 - 4:30)

**[SLIDE 10: Comparison Table]**

| Algorithm | Preemptive? | Pros | Cons |
|-----------|-------------|------|------|
| **FCFS** | No | Simple, fair | Convoy effect, poor wait times |
| **SJF** | No | Optimal avg wait | Must predict burst lengths |
| **SRTF** | Yes | Best avg wait | Overhead, starvation risk |
| **Round Robin** | Yes | Fair, responsive | Higher turnaround time |

**[SLIDE 11: Real-World: Multi-Level Feedback Queues]**

> "Real operating systems like Linux and Windows use multi-level feedback queues: multiple queues with different priorities and algorithms."

**[VISUAL: Pyramid of queues - Interactive at top (RR, small quantum), Batch at bottom (FCFS)]**

> "New processes start at high priority. If they use their full quantum, they drop to a lower queue. I/O-bound interactive processes stay high; CPU hogs sink to the bottom."

> "This adapts automatically without needing to know burst times in advance!"

---

## Part 5: AI Connection & Closing (4:30 - 5:00)

**[SLIDE 12: Connection to AI/ML]**

> "Why does this matter for AI? GPU cluster scheduling uses these same concepts! SLURM and Kubernetes schedule ML training jobs using priority queues, fair-share algorithms, and preemption."

**[VISUAL: GPU cluster with multiple jobs waiting]**

> "And here's a fun fact: Google's research shows that better scheduling can reduce energy consumption by 20-40% — the same algorithms that make your laptop responsive also make AI more sustainable."

**[SLIDE 13: Key Takeaways]**

> "To recap:
> 1. CPU scheduling decides which process runs next
> 2. FCFS is simple but suffers from convoy effect
> 3. SJF minimizes wait time but needs burst predictions
> 4. Round Robin provides fairness and responsiveness
> 5. Real systems combine these in multi-level feedback queues"

**[SLIDE 14: Thank You]**

> "CPU scheduling: the unsung hero that keeps your computer from freezing. Any questions?"

---

---

# �📚 HASH TABLES / HASHMAP — 30-Minute Class Script

## Introduction & Hook (0:00 - 3:00)

**[SLIDE 1: Title - "Hash Tables: The Secret Behind Lightning-Fast Lookups"]**

> "Let me start with a challenge. I have a phonebook with 1 million entries. I give you a name — say, 'Sharma, Priya' — and you need to find her phone number."

**[SLIDE 2: The Challenge]**

> "If the phonebook is unsorted, you might have to check all 1 million entries. That's O(n) — linear time. Even if it's sorted and you use binary search, that's O(log n) — about 20 comparisons."

**[VISUAL: Comparison of search times]**

> "But what if I told you that Python's dictionary finds any value in essentially ONE step, regardless of whether it has 100 entries or 100 million? That's the magic of hash tables!"

**[SLIDE 3: Where Hash Tables Live]**

> "Hash tables power:
> - Python's `dict` and `set`
> - Java's `HashMap` and `HashSet`  
> - JavaScript objects
> - Database indexes
> - Caching systems
> - Your browser's local storage"

> "They're arguably the most useful data structure in all of computer science. Let's understand how they work!"

---

## Part 1: The Core Idea (3:00 - 8:00)

**[SLIDE 4: Arrays — The Fastest Data Structure]**

> "First, let's remember why arrays are fast. If I have an array and I want element at index 42, I can compute its memory address directly: base_address + 42 × element_size. One step! O(1)."

**[VISUAL: Array memory layout]**

> "Arrays give us constant-time access... but only if we have integer indices. What if our keys are strings like names?"

**[SLIDE 5: The Hash Function Idea]**

> "The brilliant idea: What if we could convert ANY key into an integer? Then we could use that integer as an array index!"

**[VISUAL: String → Hash Function → Integer → Array Index]**

> "This conversion function is called a hash function. It takes a key of any type and produces an integer."

**[SLIDE 6: Hash Function Example]**

> "Let's see a simple example. For a string, we might:
> 1. Take ASCII values of characters
> 2. Combine them somehow (add, multiply, etc.)
> 3. Take modulo of array size"

```python
def simple_hash(key, table_size):
    total = 0
    for char in key:
        total = (total * 31 + ord(char))
    return total % table_size
```

**[Work through example]**

> "Hash('Priya', 10) might give us 7. So we store Priya's number at index 7!"

**[SLIDE 7: The Hash Table in Action]**

**[VISUAL: Animation of insert and lookup]**

> "Insert 'Priya': hash('Priya') → 7 → store at index 7
> Lookup 'Priya': hash('Priya') → 7 → retrieve from index 7
> Both operations: O(1)!"

---

## Part 2: The Collision Problem (8:00 - 14:00)

**[SLIDE 8: The Inevitable Problem]**

> "But wait — here's the issue. We have infinite possible keys (all possible strings) but finite array slots (say, 100). By the pigeonhole principle, multiple keys MUST map to the same index!"

**[VISUAL: Two keys pointing to same slot]**

> "This is called a collision. hash('Priya') = 7 and hash('Rahul') = 7. Now what?"

**[SLIDE 9: Collision Resolution Strategy 1 — Chaining]**

**[VISUAL: Linked lists at each array slot]**

> "Solution 1: At each array index, instead of storing one item, store a linked list of all items that hash to that index."

> "Insert: Hash to find slot, append to the list
> Lookup: Hash to find slot, search through the list
> Delete: Hash to find slot, remove from the list"

**[SLIDE 10: Chaining Analysis]**

> "If we have n items in a table of size m, the average list length is α = n/m. This is called the load factor."

> "Average lookup time: O(1 + α)
> If α = 2, we check about 2-3 items on average — still excellent!"

**[SLIDE 11: Collision Resolution Strategy 2 — Open Addressing]**

> "Alternative: Don't use linked lists. Instead, if your slot is taken, probe for the next empty slot."

**[VISUAL: Linear probing animation]**

> "Linear probing: If slot i is full, try i+1, then i+2, etc."

```
Insert 'Priya' → hash=7 → slot 7 empty → place at 7
Insert 'Rahul' → hash=7 → slot 7 full → try 8 → empty → place at 8
Lookup 'Rahul' → hash=7 → slot 7 has 'Priya' → try 8 → found!
```

**[SLIDE 12: Open Addressing Variants]**

> "Probing strategies:
> - **Linear probing**: i, i+1, i+2, ... (simple but causes clustering)
> - **Quadratic probing**: i, i+1², i+2², ... (reduces clustering)
> - **Double hashing**: i, i+h₂(key), i+2h₂(key), ... (best distribution)"

**[SLIDE 13: Chaining vs Open Addressing]**

| Aspect | Chaining | Open Addressing |
|--------|----------|-----------------|
| Implementation | Simpler | More complex |
| Memory | Extra pointers | Compact |
| Cache performance | Worse (pointer chasing) | Better (sequential) |
| Load factor tolerance | Can exceed 1 | Must stay below 1 |
| Deletion | Easy | Tricky (tombstones) |

> "Python uses open addressing. Java HashMap uses chaining. Both work well!"

---

## Part 3: Load Factor & Resizing (14:00 - 19:00)

**[SLIDE 14: The Load Factor Problem]**

> "What happens as we insert more items? The load factor α = n/m grows. Collisions become more frequent. Performance degrades."

**[VISUAL: Graph showing lookup time vs load factor]**

> "For chaining: Still okay even at α = 2 or 3
> For open addressing: Performance crashes as α approaches 1!"

**[SLIDE 15: Dynamic Resizing]**

> "Solution: When load factor exceeds a threshold (typically 0.75), we resize!"

**[VISUAL: Resizing animation]**

> "Steps:
> 1. Create a new array (usually 2× the size)
> 2. Rehash ALL existing elements (because hash depends on table size!)
> 3. Insert into new table
> 4. Discard old table"

**[SLIDE 16: The Amortization Argument]**

> "Wait — rehashing takes O(n) time! Isn't that bad?"

> "Not when amortized! We only resize when we've inserted n elements since last resize. That O(n) work is 'spread' over those n inserts."

**[VISUAL: Amortized analysis diagram]**

> "Each insert 'pays' for a small piece of the future resize. On average, insert is still O(1)!"

**[SLIDE 17: Shrinking]**

> "Some implementations also shrink when load factor drops too low (say, below 0.25), to save memory. Same amortized analysis applies."

---

## Part 4: Hash Function Design (19:00 - 23:00)

**[SLIDE 18: What Makes a Good Hash Function?]**

> "A good hash function should:
> 1. **Be deterministic**: Same input always gives same output
> 2. **Be fast**: O(key length) is ideal
> 3. **Distribute uniformly**: All buckets equally likely
> 4. **Minimize patterns**: Similar keys shouldn't map to similar indices"

**[SLIDE 19: Bad Hash Function]**

> "Example of a BAD hash: Just return the first character's ASCII value"

```python
def bad_hash(s): return ord(s[0]) % table_size
```

> "All names starting with 'A' go to the same bucket! Terrible distribution."

**[SLIDE 20: Polynomial Rolling Hash]**

> "Common good approach — treat string as a polynomial:"

$$h(s) = s[0] \cdot p^0 + s[1] \cdot p^1 + ... + s[n-1] \cdot p^{n-1}$$

> "Where p is a prime (often 31 or 37). This gives excellent distribution."

```python
def poly_hash(s, table_size, p=31):
    h = 0
    for i, char in enumerate(s):
        h += ord(char) * (p ** i)
    return h % table_size
```

**[SLIDE 21: Cryptographic Hash Functions]**

> "For some applications, we use cryptographic hashes like SHA-256:
> - Extremely uniform distribution
> - Collision-resistant (hard to find two inputs with same hash)
> - But slower — use only when security matters"

---

## Part 5: Real-World Applications (23:00 - 27:00)

**[SLIDE 22: Application 1 — Caching]**

> "Hash tables are perfect for caches. Given a request, hash it to check if result is cached. O(1) lookup — essential for performance!"

**[VISUAL: Web cache / memoization example]**

**[SLIDE 23: Application 2 — Database Indexing]**

> "Databases use hash indexes for equality queries. SELECT * FROM users WHERE email='x@y.com' — O(1) with hash index vs O(log n) with B-tree!"

**[SLIDE 24: Application 3 — Deduplication]**

> "Finding duplicates: Hash each item, check if hash exists. Used in:
> - Detecting duplicate files
> - Database join operations  
> - Compiler symbol tables"

**[SLIDE 25: Application 4 — Counting]**

> "Word frequency counting is classic:"

```python
counts = {}  # Hash table!
for word in text.split():
    counts[word] = counts.get(word, 0) + 1
```

> "Without hash tables, this would be O(n²). With hash tables: O(n)!"

**[SLIDE 26: Behind Your Favorite Language]**

> "When you use these in different languages:
> - Python: `dict`, `set` — open addressing with custom probing
> - Java: `HashMap` — chaining with trees for long chains
> - C++: `unordered_map` — chaining
> - JavaScript: Objects — highly optimized hash tables"

---

## Part 6: Analysis & Common Pitfalls (27:00 - 29:00)

**[SLIDE 27: Time Complexity Summary]**

| Operation | Average | Worst Case |
|-----------|---------|------------|
| Insert    | O(1)    | O(n)       |
| Lookup    | O(1)    | O(n)       |
| Delete    | O(1)    | O(n)       |

> "Worst case happens when ALL elements hash to the same bucket — essentially a linked list. But with a good hash function, this is astronomically unlikely."

**[SLIDE 28: Common Pitfalls]**

> "Watch out for:
> 1. **Mutable keys**: If a key changes after insertion, you'll never find it again!
> 2. **Bad hash functions**: Can degrade to O(n)
> 3. **Hash collisions attacks**: Attackers craft inputs to cause O(n²) behavior
> 4. **Not overriding hashCode with equals (Java)**: Two 'equal' objects with different hashes cause bugs"

---

## Conclusion (29:00 - 30:00)

**[SLIDE 29: Key Takeaways]**

> "Hash tables give us:
> - O(1) average case for insert, lookup, delete
> - Trade space for time — extra memory enables speed
> - Two main collision strategies: chaining and open addressing
> - Dynamic resizing maintains performance as data grows
> - Good hash function design is critical"

**[SLIDE 30: The Bigger Picture]**

> "Hash tables embody a fundamental CS principle: clever indexing beats searching. Instead of looking through data to find what you want, compute exactly where it should be."

> "Any questions?"

---

---

## Old Overview
Structured teaching approaches for 8 selected computer science concepts across traditional CS fundamentals and advanced ML/NLP topics.

---

## **1. LLM Decoding Strategies**

### **5-Minute Video Structure:**
1. **Hook (30s)**: Show same prompt generating 3 different outputs - creative story, factual answer, concise response
2. **Core Concept (2min)**: 
   - LLMs predict probability distribution over next token
   - Decoding = choosing which token to actually generate
   - Show temperature slider: low (0.1) → deterministic, high (1.5) → creative
3. **Visual Demo (1.5min)**: Live demo with "Once upon a time" showing:
   - Greedy decoding (always pick highest probability)
   - Top-k sampling (random from top 5 tokens)
   - Temperature effect on distribution
4. **Takeaway (1min)**: Different tasks need different strategies - translation needs precision (low temp), creative writing needs variety (high temp)

### **30-Minute Class Structure:**
1. **Introduction (5min)**: Problem setup - why can't we just pick the highest probability token always?
2. **Greedy Decoding (5min)**: 
   - Algorithm walkthrough
   - Limitations: repetition, lack of diversity
   - When it works: factual QA, code generation
3. **Beam Search (7min)**:
   - Keep top-k hypotheses at each step
   - Example with beam width = 3
   - Computational cost vs. quality tradeoff
4. **Sampling Methods (8min)**:
   - **Temperature**: Softening/sharpening probability distribution
   - **Top-k sampling**: Sample from k most likely tokens
   - **Top-p (nucleus) sampling**: Sample from smallest set with cumulative probability p
   - Mathematical formulation and intuition
5. **Practical Guidelines (5min)**:
   - Task-specific recommendations
   - Interactive demo showing parameter effects
   - Recent trends: structured generation, constrained decoding

---

## **2. PageRank**

### **5-Minute Video Structure:**
1. **Hook (45s)**: "How does Google decide which of 1 billion pages to show first?"
2. **Intuition (2min)**:
   - Web as a graph: pages = nodes, links = edges
   - Key insight: Important pages are linked by other important pages (recursive!)
   - Random surfer analogy: where would a random clicker end up?
3. **Visual Animation (1.5min)**: 
   - Small graph (5-6 nodes)
   - Show surfer randomly walking
   - Node sizes grow with visit frequency
   - Scores converge
4. **Takeaway (45s)**: PageRank = stationary distribution of random walk. Still powers search today (with modifications)

### **30-Minute Class Structure:**
1. **Motivation (5min)**: 
   - Pre-PageRank era: keyword matching, easily gamed
   - Link analysis idea: "democratic voting by links"
   - Historical context: Brin & Page, 1998
2. **Algorithm Intuition (7min)**:
   - Random surfer model
   - Transition probability matrix
   - Initial uniform distribution → iterative updates
   - Convergence concept
3. **Mathematical Formulation (10min)**:
   - Basic equation: $PR(A) = (1-d)/N + d \sum_{i} PR(T_i)/C(T_i)$
   - Damping factor $d$ (typically 0.85) - teleportation probability
   - Matrix formulation: $\mathbf{r} = M\mathbf{r}$ (eigenvector with eigenvalue 1)
   - Power iteration algorithm
4. **Implementation & Issues (5min)**:
   - Handling dangling nodes (no outlinks)
   - Personalized PageRank
   - Computational considerations for web-scale graphs
5. **Extensions (3min)**: 
   - Modern search uses 200+ signals
   - Social network influence
   - Citation networks (h-index connection)

---

## **3. Attention Mechanism**

### **5-Minute Video Structure:**
1. **Hook (30s)**: "How does a translation model know that 'bank' means river-bank vs. financial-bank?"
2. **Problem Setup (1.5min)**:
   - Seq2seq with fixed-length bottleneck fails for long sequences
   - Encoder compresses everything into single vector → information loss
3. **Attention Solution (2min)**:
   - Decoder can "look back" at all encoder states
   - Visual: translating "I am a student" → "Je suis un étudiant"
   - Heat map showing which source words decoder attends to for each target word
   - "am" → "suis" gets high attention weight
4. **Impact (1min)**: Revolutionized NLP → Led to Transformers → GPT, BERT, everything modern

### **30-Minute Class Structure:**
1. **Context: Seq2Seq Limitations (5min)**:
   - Review RNN encoder-decoder architecture
   - Bottleneck problem: compressing variable-length input into fixed vector
   - Performance degrades with sequence length (show empirical plot)
2. **Attention Mechanism (12min)**:
   - **Core Idea**: Weighted combination of all encoder hidden states
   - **Alignment Scores**: How relevant is each encoder state to current decoder state?
     - $e_{ij} = a(s_{i-1}, h_j)$ - score function
     - Common: $a(s, h) = v^T \tanh(W_1s + W_2h)$ (Bahdanau attention)
   - **Attention Weights**: $\alpha_{ij} = \text{softmax}(e_{ij})$
   - **Context Vector**: $c_i = \sum_j \alpha_{ij} h_j$
   - **Decoder Update**: Uses both previous state AND context vector
   - Mathematical walkthrough with concrete example
3. **Variants (5min)**:
   - Bahdanau (additive) vs. Luong (multiplicative) attention
   - Global vs. local attention
   - Self-attention preview (leads to Transformers)
4. **Visualization & Interpretation (5min)**:
   - Attention weight heat maps
   - What patterns emerge? (diagonal for translation, specific alignments)
   - Interpretability: Are attention weights explanations?
5. **Impact (3min)**:
   - Breakthrough paper: "Neural Machine Translation by Jointly Learning to Align and Translate" (2014)
   - Path to Transformers: "Attention is All You Need" (2017)
   - Applications beyond NLP: Vision (ViT), multimodal models

---

## **4. Word Embeddings**

### **5-Minute Video Structure:**
1. **Hook (30s)**: Show 3D projection of word space with "king", "queen", "man", "woman" forming a parallelogram
2. **The Problem (1min)**:
   - Computers don't understand words, need numbers
   - One-hot encoding: [0,0,1,0,...,0] - no notion of similarity
   - "cat" and "dog" should be closer than "cat" and "democracy"
3. **Solution: Embeddings (2min)**:
   - Map words to dense vectors (e.g., 300 dimensions)
   - Similar words → similar vectors
   - Show t-SNE visualization: animals cluster, countries cluster, verbs cluster
   - Famous example: $\vec{king} - \vec{man} + \vec{woman} \approx \vec{queen}$
4. **Takeaway (1.5min)**: Learn from context: "You shall know a word by the company it keeps". Foundation for modern NLP.

### **30-Minute Class Structure:**
1. **Motivation & History (4min)**:
   - One-hot encoding problems: high dimensionality, no similarity
   - Distributional hypothesis: Words in similar contexts have similar meanings
   - Evolution: LSA → neural embeddings
2. **Word2Vec: Skip-gram Model (10min)**:
   - **Task**: Given center word, predict context words
   - **Architecture**: Input word → embedding layer → output layer (softmax over vocabulary)
   - **Example**: "The quick brown fox jumps" - if center = "fox", predict {brown, jumps}
   - **Loss Function**: $-\log P(w_{context}|w_{center})$
   - **Training Tricks**:
     - Negative sampling (avoid computing full softmax)
     - Subsampling frequent words
   - Mathematical formulation: $P(w_O|w_I) = \frac{\exp(v_{w_O}^T v_{w_I})}{\sum_{w=1}^W \exp(v_w^T v_{w_I})}$
3. **CBOW Variant (3min)**:
   - Reverse task: predict center from context
   - Faster to train, works better for frequent words
   - Skip-gram better for rare words
4. **Properties & Analogies (5min)**:
   - Linear relationships in embedding space
   - Vector arithmetic: king - man + woman = queen
   - Semantic relations: capital("France") = Paris
   - Syntactic relations: plural(cat) = cats
   - Why does this work? Geometric interpretation
5. **Alternatives & Modern Context (5min)**:
   - **GloVe**: Global matrix factorization approach
   - **FastText**: Character n-grams, handles OOV words
   - **Contextualized Embeddings**: ELMo, BERT (same word, different contexts → different embeddings)
   - Comparison: Static vs. contextual embeddings
6. **Practical Demo (3min)**:
   - Using pre-trained embeddings (word2vec, GloVe)
   - Finding similar words with cosine similarity
   - Applications: document similarity, recommendation systems

---

## **5. Hash Tables / HashMap**

### **5-Minute Video Structure:**
1. **Hook (30s)**: "How does Python's dict find a value in a billion-item dictionary instantly?"
2. **The Problem (1min)**: 
   - Array with index: O(1) lookup BUT need integer keys
   - Need to store {"alice": 98, "bob": 87, ...} - string keys!
3. **Hash Function Magic (1.5min)**:
   - Convert any key to integer: hash("alice") → 17, hash("bob") → 42
   - Use as array index
   - Animation showing: insert("alice", 98) → hash → index 17 → store
4. **Collision Handling (1.5min)**:
   - Problem: hash("alice") and hash("alicia") might both → 17
   - Solution preview: chaining (linked list at each slot)
5. **Takeaway (30s)**: O(1) average case for insert, lookup, delete. Powers dictionaries, sets, database indexes.

### **30-Minute Class Structure:**
1. **Motivation (3min)**:
   - Abstract Data Type: Map/Dictionary
   - Operations: insert, lookup, delete
   - Alternatives: Array (O(1) but integer keys), Binary Search Tree (O(log n))
   - Goal: O(1) with arbitrary keys
2. **Hash Function (5min)**:
   - Definition: h: Universe → {0, 1, ..., m-1}
   - Properties needed: deterministic, uniform distribution, fast to compute
   - Examples:
     - Division method: h(k) = k mod m
     - Multiplication method
     - String hashing: polynomial rolling hash
   - Perfect vs. non-perfect hashing
3. **Collision Resolution (12min)**:
   - **Chaining**:
     - Each slot points to linked list
     - Insert: compute hash, append to list
     - Search: compute hash, traverse list
     - Analysis: Average case O(1 + α) where α = n/m (load factor)
   - **Open Addressing**:
     - Store everything in array itself
     - Linear probing: h(k), h(k)+1, h(k)+2, ... until empty slot
     - Quadratic probing, double hashing
     - Deletion complications (tombstones)
     - Clustering problems
   - Comparison of methods
4. **Load Factor & Resizing (5min)**:
   - Performance degrades when α = n/m gets large
   - Dynamic resizing: when α > threshold (e.g., 0.75), double array size
   - Rehashing all elements: O(n) operation, but amortized O(1) per insert
   - Amortized analysis sketch
5. **Applications & Practical Considerations (5min)**:
   - Python dict, Java HashMap, C++ unordered_map
   - Database indexing
   - Caching (LRU cache implementation)
   - Security considerations: cryptographic hash functions
   - Real-world performance tips

---

## **6. Quicksort**

### **5-Minute Video Structure:**
1. **Hook (30s)**: "How does your phone sort 10,000 contacts in a blink?"
2. **The Idea (1.5min)**:
   - Divide and conquer approach
   - Pick a pivot element (say, middle value)
   - Partition: elements < pivot | pivot | elements > pivot
   - Recursively sort left and right parts
3. **Visual Animation (2min)**:
   - Array: [8, 3, 1, 7, 0, 10, 2]
   - Pick pivot = 3
   - Show partitioning step by step
   - Recursion on subarrays
   - Final sorted result
4. **Why "Quick"? (1min)**: O(n log n) average case, in-place sorting, cache-friendly. Used in most standard libraries.

### **30-Minute Class Structure:**
1. **Sorting Problem & Landscape (3min)**:
   - Review: Bubble sort O(n²), Merge sort O(n log n)
   - Quicksort: Another O(n log n) but often faster in practice - why?
2. **Algorithm (8min)**:
   - **Partition Function** (most critical part):
     - Choose pivot (strategies: first, last, median, random)
     - Two-pointer approach: 
       - Left pointer scans for element > pivot
       - Right pointer scans for element < pivot
       - Swap and continue until pointers cross
     - Return pivot position
   - **Recursive Quicksort**:
     ```
     quicksort(A, low, high):
         if low < high:
             pi = partition(A, low, high)
             quicksort(A, low, pi-1)
             quicksort(A, pi+1, high)
     ```
   - Detailed walkthrough with example array
3. **Complexity Analysis (8min)**:
   - **Best/Average Case**: O(n log n)
     - Partition divides roughly in half each time
     - Height of recursion tree = log n
     - Work at each level = O(n)
   - **Worst Case**: O(n²)
     - When pivot is always smallest/largest (already sorted array!)
     - Unbalanced partitions: n + (n-1) + (n-2) + ... = O(n²)
     - Recurrence relation analysis
   - **Randomized Quicksort**: Random pivot → expected O(n log n) even for worst-case input
4. **Pivot Selection Strategies (5min)**:
   - First/last element: Simple but vulnerable to already-sorted data
   - Random: Probabilistic guarantee
   - Median-of-three: First, middle, last → practical compromise
   - True median: Median-of-medians algorithm (deterministic O(n log n))
5. **Practical Considerations (4min)**:
   - **In-place sorting**: O(log n) space for recursion stack vs. merge sort's O(n)
   - **Cache performance**: Sequential access patterns in partition
   - **Hybrid approaches**: Switch to insertion sort for small subarrays (< 10 elements)
   - **Three-way partitioning**: Handle duplicate keys efficiently (Dutch National Flag)
6. **Comparison with Merge Sort (2min)**:
   - Quicksort: Faster average case, in-place, not stable
   - Merge sort: Guaranteed O(n log n), stable, requires extra space
   - When to use which?

---

## **7. Binary Search Tree (BST)**

### **5-Minute Video Structure:**
1. **Hook (30s)**: "How would you find a name in a 1000-page phone book?" → Binary search on sorted list
2. **From Arrays to Trees (1.5min)**:
   - Sorted array: Search is O(log n), but insert is O(n) (shifting elements)
   - Linked list: Insert is O(1), but search is O(n)
   - Can we get O(log n) for both? → BST!
3. **BST Structure (1.5min)**:
   - Each node: left child < parent < right child
   - Visualization: Insert 5, 3, 7, 1, 9 → show tree building
   - Search animation: Finding 7 in the tree
4. **The Catch (1min)**: If you insert sorted data (1,2,3,4,5...), you get a linked list! → Need balancing (preview of AVL/Red-Black trees)
5. **Takeaway (30s)**: Foundation for balanced trees, database indexes, file systems.

### **30-Minute Class Structure:**
1. **Motivation (4min)**:
   - Need for dynamic set operations: insert, delete, search, min, max
   - Array vs. Linked List tradeoffs
   - BST property: Maintains sorted order while allowing efficient operations
2. **Structure & Operations (12min)**:
   - **BST Property**: For every node: left subtree < node < right subtree
   - **Search** (4min):
     - Start at root, compare with target
     - Go left if target smaller, right if larger
     - Pseudocode and example
     - Complexity: O(h) where h = height
   - **Insert** (4min):
     - Search for position where key should be
     - When you hit NULL, insert there
     - Example: Insert into existing tree
     - Maintains BST property
   - **Delete** (4min):
     - **Case 1**: Leaf node → simply remove
     - **Case 2**: One child → replace with child
     - **Case 3**: Two children → replace with inorder successor (or predecessor)
       - Inorder successor = leftmost node in right subtree
     - Detailed walkthrough of each case
3. **Traversals (5min)**:
   - **Inorder** (Left-Root-Right): Produces sorted sequence!
   - **Preorder** (Root-Left-Right): Copy tree
   - **Postorder** (Left-Right-Root): Delete tree
   - Recursive implementation
   - Applications of each traversal
4. **Complexity Analysis (4min)**:
   - All operations: O(h) where h = height
   - **Best case**: Balanced tree → h = log n → O(log n)
   - **Worst case**: Skewed tree (sorted insertion) → h = n → O(n)
   - Visualization: Balanced vs. skewed BSTs
5. **Limitations & Solutions (5min)**:
   - BST can degenerate to linked list
   - Need for self-balancing: AVL trees, Red-Black trees
   - Brief overview:
     - AVL: Strict balancing, height difference ≤ 1
     - Red-Black: Looser balancing, faster insertions
     - Both guarantee O(log n) operations
   - Modern implementations: C++ map/set use Red-Black trees

---

## **8. Dynamic Programming**

### **5-Minute Video Structure:**
1. **Hook (45s)**: Calculate Fibonacci(40) - naive recursion takes minutes, DP takes milliseconds. Why?
2. **The Problem (1.5min)**:
   - Show recursion tree for Fib(5): F(3) computed twice, F(2) computed three times
   - Redundant computation explodes exponentially
3. **DP Solution (2min)**:
   - **Memoization**: Store results in a table, look up before computing
   - Show same tree with checkmarks: "Already computed!"
   - **Bottom-up**: Build table from base cases upward
   - Visual: Fib table filling: F(0)=0, F(1)=1, F(2)=1, F(3)=2, ...
4. **Takeaway (45s)**: "Remember the past to build the future". Trading space for time. Used in: route planning, text editing, bioinformatics, AI.

### **30-Minute Class Structure:**
1. **Introduction & Philosophy (5min)**:
   - **Core Idea**: Break problem into overlapping subproblems, solve each once
   - **Requirements**:
     - Optimal substructure: Optimal solution contains optimal solutions to subproblems
     - Overlapping subproblems: Same subproblems solved multiple times
   - Contrast with Divide & Conquer (non-overlapping subproblems)
   - When to suspect DP: "Count number of ways", "Find optimal", "Min/Max"
2. **Fibonacci Example (5min)**:
   - **Naive Recursion**: T(n) = T(n-1) + T(n-2) → O(2ⁿ)
   - **Memoization (Top-Down)**:
     - Add cache dictionary
     - Check cache before computing
     - O(n) time, O(n) space
   - **Tabulation (Bottom-Up)**:
     - Build array from base cases
     - No recursion overhead
     - Code walkthrough
3. **Classic Problem: 0/1 Knapsack (10min)**:
   - **Problem**: n items (weight, value), knapsack capacity W. Maximize value.
   - **Recursive Structure**:
     - For item i: Either take it or leave it
     - K(i, w) = max(K(i-1, w), value[i] + K(i-1, w-weight[i]))
   - **DP Table**:
     - 2D table: rows = items, columns = capacities
     - Fill cell-by-cell with recurrence
     - Visual walkthrough with example
   - **Complexity**: O(nW) time, O(nW) space
   - **Backtracking**: Which items were selected?
4. **Longest Common Subsequence (6min)**:
   - **Problem**: Find longest subsequence common to two strings
   - Example: "ABCDGH" and "AEDFHR" → "ADH"
   - **Recurrence**:
     - If X[i] == Y[j]: LCS[i][j] = 1 + LCS[i-1][j-1]
     - Else: LCS[i][j] = max(LCS[i-1][j], LCS[i][j-1])
   - **Table Filling**: Show matrix construction
   - **Applications**: diff tools, bioinformatics (DNA alignment)
5. **DP Patterns & Tips (4min)**:
   - **Identify State**: What parameters uniquely describe a subproblem?
   - **Recurrence Relation**: How to compute state from smaller states?
   - **Base Cases**: What are the simplest subproblems?
   - **Order of Computation**: What order ensures prerequisites are computed first?
   - **Common Patterns**: 
     - 1D DP (Fibonacci, climbing stairs)
     - 2D DP (Knapsack, LCS, edit distance)
     - State machines (buy/sell stock)
   - Practice problems overview

---

## **Summary Table: Key Teaching Points**

| Topic | Core Insight | Visual Element | Common Pitfall to Address |
|-------|--------------|----------------|---------------------------|
| **LLM Decoding** | Different tasks need different randomness levels | Temperature effect on probability distribution | Assuming greedy is always best |
| **PageRank** | Importance is recursive and link-based | Random walker animation | Thinking it's just link counting |
| **Attention** | Weighted combination solves bottleneck | Attention heat map for translation | Confusing attention with interpretation |
| **Word Embeddings** | Context creates meaning in vector space | t-SNE clusters + analogies | Thinking embeddings are semantic features |
| **HashMap** | Hash function + collision handling = O(1) | Collision resolution animation | Ignoring worst-case and resizing |
| **Quicksort** | Partition-based divide & conquer | Partition process visualization | Forgetting worst case O(n²) |
| **BST** | Binary property enables O(log n) search | Balanced vs. skewed tree comparison | Assuming always O(log n) |
| **Dynamic Programming** | Trade space for time via memoization | Recursion tree with redundancy highlighted | Not identifying overlapping subproblems |

---

## Pedagogical Notes

Each lesson follows the structure: **Problem → Intuition → Algorithm → Analysis → Practice**

### General Teaching Principles:
- Start with a relatable hook to capture attention
- Use visual demonstrations wherever possible
- Address common misconceptions explicitly
- Connect to real-world applications
- Balance mathematical rigor with intuitive understanding
- Provide concrete examples before abstract generalizations
- End with actionable takeaways

### For the 5-Minute Videos:
- Focus on ONE core idea
- Prioritize visualization over equations
- Leave them curious to learn more
- Use animations and live demos

### For the 30-Minute Classes:
- Build complexity gradually
- Include interactive moments (questions, small exercises)
- Provide both top-down and bottom-up explanations
- Connect to students' existing knowledge
- Reserve time for questions and clarifications
