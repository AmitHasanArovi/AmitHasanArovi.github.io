---
permalink: /research/
title: "Research"
excerpt: "Research on non-blocking data structures and safe memory reclamation"
author_profile: true
---

My research is in computer systems, with a focus on concurrent and parallel computing, non-blocking data structures, and safe memory management. I study how threads can safely access, remove, and reuse shared memory while preserving correctness and progress guarantees. My work focuses on dynamically allocated data structures in C and C++, where programmers directly control memory allocation and object lifetime.

Modern multicore systems allow many threads to work at once, but those threads often coordinate through shared queues, lists, and trees. A lock can protect these structures, but a delayed thread holding the lock can prevent others from proceeding. Lock-free data structures guarantee system-wide progress even when a thread is delayed. Wait-free operations provide a stronger guarantee: each operation completes within a bounded number of its own steps despite interference from other threads. Maintaining these guarantees requires careful coordination between the data structure and its memory management.

One challenge arises when a thread removes a node while another thread still holds a pointer to it. Freeing the node immediately can cause an invalid memory access. Safe memory reclamation (SMR) addresses this problem by delaying deallocation until the node can no longer be accessed. However, reclamation alone does not make it safe to reuse the node or move it to another structure. Direct reuse can avoid allocation and copying, but it also changes the node's links and role. An older reference may therefore become misleading even though the memory remains allocated.

A related challenge concerns optimistic traversal, which allows searches to pass logically deleted nodes without immediately unlinking them. Some reclamation schemes support this behavior but allow memory awaiting reclamation to grow without a fixed bound when a thread stalls. Robust reclamation schemes limit this memory retention, but protecting the current node does not necessarily make the next node safe to access. A search must also validate that its path remains safe to follow.

My dissertation, *Bridging the Gap Between Safe Memory Management and Non-Blocking Data Structures*, connects these problems. I develop methods that coordinate node ownership, deletion, reuse, and traversal while preserving the reclamation scheme's existing interface and guarantees. My work combines algorithm design with correctness and progress arguments. I also build reproducible C and C++ research artifacts and evaluate throughput and memory use on multicore hardware.

The following three projects form the core of my dissertation research.

<div class="research-block" markdown="1">

### RRR-SMR: Recyclable Non-Blocking Data Structures

RRR-SMR allows the same node to move between non-blocking data structures without copying its data or freeing and reallocating the node. For example, a task node can move from a run queue to a wait queue and later return. When the node is no longer needed, it can still be retired through the chosen memory reclamation scheme.

Making this reuse safe requires coordinating version checks, ownership, and physical removal. Version checks help detect changes caused by concurrent updates and reuse. Ownership rules identify the thread responsible for deciding whether to retire or reuse a node. Other threads may help remove it, but they do not independently claim it. Before the node is transferred, the removal protocol ensures that it has been fully unlinked from the original structure.

I developed recyclable implementations of a specialized Michael-Scott queue, a Harris-Michael-style linked list, and the Natarajan-Mittal tree. I evaluated them using C++ benchmarks on a 128-core AMD EPYC system, varying thread count, payload size, and the proportion of operations that recycled nodes. The experiments measured throughput and memory retained in retired nodes awaiting reclamation.

**Publication:** PLDI 2025  
**Resources:** [Paper](https://doi.org/10.1145/3729337) · [Artifact](https://doi.org/10.5281/zenodo.15258497) · [Code](https://github.com/rusnikola/rrr-smr) · [Slides](https://rusnikola.github.io/files/rrr-pldi25-slides.pdf)

</div>

<div class="research-block" markdown="1">

### SCOT: Safe Concurrent Optimistic Traversals

SCOT makes optimistic traversal compatible with robust memory reclamation. The difficulty arises when a search passes through nodes being deleted. Protecting the current node keeps that node allocated, but another thread may unlink the deleted chain and reclaim its successor. The protected node's link can remain unchanged, so checking that link alone does not establish that the search can safely continue.

SCOT addresses this problem by changing how the data structure protects nodes and validates relationships along the search path. These checks allow a search to detect when concurrent unlinking has invalidated its path. It can then recover locally when possible or restart when necessary. The reclamation scheme retains its existing interface and guarantees.

I applied SCOT to Harris' original optimistic linked list and the Natarajan-Mittal tree with hazard pointers, hazard eras, interval-based reclamation, and Hyaline-1S. I also developed a linked-list extension in which threads can help complete another thread's search. This makes read-only search wait-free: each search completes within a bounded number of its own steps, while insertion and deletion remain lock-free.

**Publications:** SPAA 2025 brief announcement and PPoPP 2026 full paper  
**Resources:** [PPoPP paper](https://doi.org/10.1145/3774934.3786455) · [SPAA brief announcement](https://doi.org/10.1145/3694906.3743348) · [Artifact](https://doi.org/10.5281/zenodo.17707898) · [Code](https://github.com/rusnikola/scot) · [Slides](https://rusnikola.github.io/files/scot-ppopp26-slides.pdf)

</div>

<div class="research-block" markdown="1">

### R-SCOT: Recyclable Optimistic-Traversal Data Structures

R-SCOT combines RRR-SMR's safe node reuse with SCOT's optimistic traversal. Bringing these methods together requires a search to remain correct when a node leaves a structure and later returns with different links. Keeping the node allocated is not enough because reuse can change where those links lead.

The design coordinates the version checks used for reuse with the validation needed for traversal. It uses different version-tag increments for ordinary updates and logical deletion. This allows a search to recover locally after benign changes and restart conservatively when a change may invalidate its path. The ownership rules and checks needed for safe reuse remain part of the design.

Using R-SCOT, I developed a recyclable version of Harris' original optimistic linked list and extended the recyclable Natarajan-Mittal tree from epoch-based reclamation to robust reclamation schemes. In the tree, searches protect both ordinary nodes and the separate blocks that hold child pointers. These changes allow node reuse and optimistic traversal to work together safely.

**Publication:** SPAA 2026 brief announcement  
**Resources:** [Paper](https://doi.org/10.1145/3816782.3819211) · [Code](https://github.com/rusnikola/r-scot)

</div>
