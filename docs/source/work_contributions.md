**Vaccine Discourse Analysis During COVID-19**

My PhD thesis provides the first comprehensive multi-year computational analysis of how the COVID-19 pandemic transformed vaccine discourse on social media. We developed a high-precision classifier (97% accuracy) to categorize anti- and pro-vaccine users on Twitter, demonstrating that the pandemic caused massive opinion shifts—with previously pro-vaccine users expressing anti-vaccine sentiments; and thus challenging assumptions about fixed vaccine opinions.

Recognizing that binary labels were insufficient, we created CAVES—the first large-scale dataset with 10K tweets annotated across 12 fine-grained vaccine concerns (side-effects, rushed development, political agenda, conspiracy theories), uniquely providing span-level explanations for transparent multi-label classification. Using Transformer-based classifiers trained on CAVES, we analyzed 5+ years of tweets revealing critical insights: vaccine concerns became significantly more diverse post-COVID, concerns about COVID vaccines transferred to traditional vaccines (Flu, MMR, HPV), and trust in healthcare systems eroded substantially. We also developed novel approaches for explainable classification through models jointly performing multi-label classification and rationale extraction.

This research led to publications at ICWSM 2022, SIGIR 2022, ICWSM 2024, and ACM TWEB 2024 (presented at WWW 2025).

**Energy Efficiency of Large Language Models**

My second research thrust addresses the underexplored area of LLM inference energy consumption. We conducted the first comprehensive benchmarking across diverse NLP tasks, models, and system configurations, revealing key insights: energy scales linearly with input size despite quadratic attention complexity; maximizing batch size substantially reduces energy consumption; and quantization with targeted prompting significantly improves efficiency.

We also demonstrated that LLMs generate unnecessarily long responses even for simple queries, pioneering the formal characterization of energy-utility trade-offs. We introduced a six-category taxonomy of information types (minimal answer, additional information, reasoning, conversational enhancements, redundant content) showing distinct patterns across LLM families. Through prompt engineering strategies—including length-constrained generation and target-length prediction—we achieved 25-60% energy savings while preserving core information.

This research led to publications at NAACL 2025 and ACL 2025 Findings.

**Other Research Contributions**

As a Research Intern at Hewlett Packard Enterprise Labs (2025-present), I developed multi-agent LLM frameworks with hierarchical memory architecture (short-term context, episodic memory, semantic memory). Autonomous agents decide what information to retain, where to store it, and when to retrieve it, demonstrating improved context utilization across memory operations, conversational QA, and multi-document reasoning tasks.

During my MTech and beyond, I worked on Legal NLP, specifically summarizing Indian and UK Supreme Court judgements. We developed an unsupervised Linear Programming-based approach incorporating domain knowledge from legal experts to create summaries with appropriate proportions of rhetorical roles (facts, statutes, precedents, final judgement). This research led to publications at ICAIL 2021 (Best Student Paper Award) and AACL-IJCNLP 2022.

