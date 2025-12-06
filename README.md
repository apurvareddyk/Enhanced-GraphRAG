# PROPEX-RAG: Prompt-Driven GraphRAG for Multi-Hop QA — Overview

<img width="720" height="480" alt="image" src="https://github.com/user-attachments/assets/21093997-7c3d-47c2-97ee-e3757376782d" />

## Paper Description
**PROPEX-RAG** presents a training-free approach to multi-hop question answering that combines a **symbolic, entity-centric knowledge graph** with small, auditable **prompt policies**. Rather than relying on heavy retriever fine-tuning, it focuses on pulling the **right evidence early** (high Recall@k) and feeding the generator compact, grounded context for **reproducible, cited answers**.

The method operates in two phases. **Offline**, a symbolic graph is built from the corpus using extracted entities and fact triples, with conservative synonym/context links to avoid noisy hops. **Online**, a brief prompt filters candidate facts, seeds key entities, and triggers a short **Personalized PageRank (PPR)** traversal; passages are then **re-ranked by symbolic overlap** with entities/facts before generation. Empirically, this design yields strong results on multi-hop benchmarks (e.g., HotpotQA, 2WikiMultiHopQA) without complex training.


<img width="720" height="520" alt="image" src="https://github.com/user-attachments/assets/b681006b-f52c-4f17-85a5-39ae4deb0bc1" />


Architecture of the retrieval-augmented QA framework. Phase I constructs a symbolic knowledge graph from LLM-extracted entities and facts triples. Phase II performs PPR-based traversal using query-aligned seeds and filtered facts to retrieve and re-rank passages for grounded answer generation.

## Architecture at a Glance
- **Offline:** Build an entity-centric graph (entities, fact triples, synonym/context edges).  
- **Online:** Prompt-filter → seed entities → short PPR traversal → symbolic overlap re-rank → send top passages to the LLM.  
- **Why it works:** Structure + controllable prompts concentrate retrieval on the right subgraph, improving early evidence and stabilizing answers.

## Read / Watch
- **Medium article:** https://medium.com/@apurva.karne/propex-rag-c67d4e6a1aa9  
- **Paper (arXiv PDF):** https://arxiv.org/pdf/2511.01802  
- **YouTube presentation:** https://youtu.be/9NR4oWL8Nso  
- **SlideShare deck:** https://www.slideshare.net/slideshow/propex-rag-prompt-driven-graphrag-for-multi-hop-qa/284501869

## Acknowledgments
All claims, numbers, and the original diagram are drawn from **“PROPEX-RAG: Enhanced GraphRAG using Prompt-Driven Prompt EXecution.”**  
**Authors:** Tejas Sarnaik, Manan Shah, and Ravi Hegde (IIT Gandhinagar, India).  
We thank the authors for their excellent work and open dissemination.

## Citation
Sarnaik, T., Shah, M., & Hegde, R. (2025). *PROPEX-RAG: Enhanced GraphRAG using Prompt-Driven Prompt EXecution.* arXiv:2511.01802. https://arxiv.org/pdf/2511.01802

## License
This summary and accompanying assets are released under the **MIT License**. See [LICENSE](LICENSE).
