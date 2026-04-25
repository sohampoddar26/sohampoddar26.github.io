# Research Contributions - Video Script (5 Minutes)

**Duration:** ~5 minutes (approximately 750 words at conversational pace)

---

## OPENING (30 seconds)

Hello, I'm Soham Poddar. I recently completed my PhD from IIT Kharagpur under the guidance of Professor Saptarshi Ghosh, and I'm currently a Research Intern at Hewlett Packard Enterprise Labs.

Over the past six years, my research has spanned two major themes: understanding public health discourse through social media, and making AI systems more energy-efficient. Today, I'd like to walk you through these contributions and their impact.

---

## PhD THESIS: VACCINE DISCOURSE ANALYSIS (2 minutes)

My PhD began in 2020—right when the COVID-19 pandemic started and vaccines were under development. This made vaccines a critically important research topic, especially given the growing vaccine hesitancy despite mass-vaccination and herd immunity being crucial to controlling the pandemic.

My thesis provides the first comprehensive multi-year computational analysis of how a major global event transformed vaccine discourse on social media. We developed highly accurate classifiers to categorize vaccine stance of Twitter users and discovered something that challenged conventional assumptions: the pandemic caused massive opinion shifts. Previously pro-vaccine users began expressing anti-vaccine sentiments. This work, published at ICWSM 2022, has since gathered over 60 citations.

But we also realized that the traditional binary categories—pro-vaccine and anti-vaccine—had diverged into different shades of viewpoints. Saying someone is "anti-vaccine" doesn't tell us *why*.

So we created CAVES—the first dataset of its kind with 10,000 tweets annotated across 12 fine-grained concerns: side effects, rushed development, political agendas, conspiracy theories, and more. What makes CAVES unique is that it provides span-level explanations—highlighting exactly which words express which concern. This was published at SIGIR 2022 and has over 40 citations.

Using Transformer-based classifiers trained on CAVES, we analyzed over five years of tweets revealing critical insights: vaccine concerns became significantly more diverse after COVID—making traditional vaccine-promotion strategies obsolete; concerns about COVID vaccines transferred to traditional vaccines like flu shots, MMR, and HPV; and trust in healthcare systems eroded substantially. This longitudinal work appeared at ICWSM 2024 and ACM Transactions on the Web, presented at WWW 2025.

---

## ENERGY EFFICIENCY OF LLMs (1.5 minutes)

Generative AI is transforming nearly every sector. But there's a hidden cost. The deployment of these systems requires substantial energy—billions of daily queries consuming tens of gigawatts. Yet this area remains remarkably understudied.

We conducted the first comprehensive benchmarking of LLM inference energy consumption—testing across diverse NLP tasks, different models, and various system configurations. Our findings, published at NAACL 2025, revealed actionable insights for energy-efficient deployment while maintaining reasonable performance.

But here's what really surprised us: LLMs generate unnecessarily verbose responses, even for simple factual questions. We pioneered the formal characterization of energy-utility trade-offs. We introduced a six-category taxonomy of information types—minimal answer, additional context, reasoning steps, conversational fillers, redundant content, and irrelevant information—and showed distinct patterns across different LLM families.

Through prompt engineering strategies, we achieved 25 to 60 percent energy savings while preserving the core information users actually need. This work appeared at ACL 2025 Findings and forms the foundation for my future research on sustainable AI.

---

## INDUSTRIAL RESEARCH (30 seconds)

At HPE Labs, I'm addressing a critical challenge in enterprise AI: memory fragmentation. In real-world agentic systems, information is scattered across prior conversations, technical documents, company policies, and more—leading to ineffective utilization.

I developed and benchmarked multi-agent LLM frameworks with hierarchical memory architecture. Autonomous agents decide what information to retain, where to store it, and when to retrieve it. This approach demonstrates improved context utilization across memory operations, conversations, and multi-document reasoning tasks.

---

## OTHER CONTRIBUTIONS (30 seconds)

Beyond these main thrusts, I've contributed to several other areas. During my MTech, I worked on Legal NLP—summarizing Indian and UK Supreme Court judgements. This work won the Best Student Paper Award at ICAIL 2021 and has over 100 citations, with a follow-up at AACL-IJCNLP 2022 gathering over 150 citations.

I've also worked on flood detection from social media images during my BTech, understanding transport grievances in Indian cities, and multilingual claim identification—with publications at ICACCP, SNAM, and ICPR.

---

## CLOSING (15 seconds)

In summary, my research combines rigorous empirical analysis with practical system building—from understanding vaccine hesitancy to making AI sustainable. These experiences have shaped my vision for building AI systems that are not just capable, but responsible and efficient.

Thank you.

---

**Total word count:** ~750 words  
**Estimated duration:** 5 minutes at conversational pace

---

## DELIVERY NOTES

- Emphasize "2020" and the pandemic context—it grounds your PhD motivation
- Mention citation counts with slight pride but not arrogance ("has since gathered over 60 citations")
- Slow down when explaining CAVES and the taxonomy—these are key contributions
- "Tens of gigawatts" is a striking number—pause slightly after saying it
- For HPE Labs, "memory fragmentation" is a good hook—emphasize it
- The closing should feel like a natural summary, not rushed
- Consider slides showing: CAVES taxonomy, energy benchmarking graphs, memory architecture diagram
