---
permalink: /research/
title: "Research"
excerpt: "Research on non-blocking data structures and safe memory reclamation"
author_profile: true
---

My research is in computer systems, with an emphasis on concurrent and parallel computing. I study how non-blocking data structures interact with safe memory reclamation: the machinery that decides when removed objects can be freed or reused without allowing another thread to access invalid memory.

This problem matters because non-blocking algorithms can avoid lock-related delays, but their performance and correctness depend on how memory is managed. My work connects algorithm design, correctness and progress reasoning, and experimental systems evaluation.

<div class="research-block" markdown="1">

### RRR-SMR: safe and efficient node reuse

RRR-SMR provides a methodology for copy-free node reuse and transfer in recyclable lock-free data structures. The work addresses explicit node ownership, the ABA problem, and two-phase deletion in queues, linked lists, and Natarajan-Mittal trees. The evaluation studies both throughput and memory use on a 128-core AMD EPYC system.

**Publication:** PLDI 2025  
**Resources:** [Paper](https://doi.org/10.1145/3729337) · [Artifact](https://doi.org/10.5281/zenodo.15258497) · [Code](https://github.com/rusnikola/rrr-smr) · [Slides](https://rusnikola.github.io/files/rrr-pldi25-slides.pdf)

</div>

<div class="research-block" markdown="1">

### SCOT: memory reclamation for optimistic traversal

Some non-blocking data structures use optimistic traversals that follow pointers without announcing every node to the memory reclaimer. This creates a difficult compatibility problem for robust reclamation schemes. SCOT modifies the data structure rather than the reclamation API. It provides correct versions of the original Harris linked list and Natarajan-Mittal tree under hazard pointers, hazard eras, interval-based reclamation, and Hyaline.

**Publications:** SPAA 2025 brief announcement and PPoPP 2026 full paper  
**Resources:** [PPoPP paper](https://doi.org/10.1145/3774934.3786455) · [SPAA brief announcement](https://doi.org/10.1145/3694906.3743348) · [Artifact](https://doi.org/10.5281/zenodo.17707898) · [Code](https://github.com/rusnikola/scot) · [Slides](https://rusnikola.github.io/files/scot-ppopp26-slides.pdf)

</div>

<div class="research-block" markdown="1">

### R-SCOT: recyclable optimistic-traversal structures

R-SCOT brings node recycling and optimistic traversal into one design. It uses differentiated tag increments to preserve local recovery and efficient traversal in recyclable linked lists and trees. The work shows that recyclable optimistic-traversal structures can remain competitive across several memory-reclamation schemes.

**Publication:** SPAA 2026 brief announcement  
**Resources:** [Paper](https://doi.org/10.1145/3816782.3819211) · [Code](https://github.com/rusnikola/r-scot)

</div>

## Future directions

My planned work grows directly from these results while opening broader systems questions:

1. **Reusable concurrent components.** Build a library that makes RRR-SMR and SCOT techniques easier to apply, test, and compare across data structures.
2. **Stronger traversal guarantees.** Develop wait-free traversal methods for tree structures while preserving practical performance.
3. **Clearer interfaces.** Design portable interfaces that expose the information memory reclamation needs without tightly coupling one data structure to one reclamation scheme.
4. **Student-centered systems research.** Create projects at several levels, from reproducible benchmarking and testing to algorithm design and correctness reasoning.

I welcome conversations about concurrent data structures, memory reclamation, multicore performance, and opportunities for student collaboration.

