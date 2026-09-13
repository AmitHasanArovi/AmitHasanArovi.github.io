---
permalink: /
title: ""
excerpt: "Md Amit Hasan Arovi - computer systems researcher and educator"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---
{% include base_path %}

<section class="profile-hero">
  <p class="eyebrow">Computer systems · concurrency · memory management</p>
  <h1>Building safer and faster concurrent software.</h1>
  <p class="hero-lead">I am an Assistant Teaching Professor in Computer Science and Engineering at New Mexico Tech. My research is in computer systems, with a focus on concurrent and parallel computing, non-blocking data structures, and safe memory management.</p>
  <div class="hero-actions">
    <a class="button button--primary" href="{{ base_path }}/research/">Research</a>
    <a class="button button--secondary" href="{{ base_path }}/publications/">Publications</a>
    <a class="button button--secondary" href="{{ base_path }}/files/CV_MdAmitHasanArovi.pdf">Download CV</a>
  </div>
</section>

## About me

I earned my Ph.D. (Summer 2026) and M.S. (Spring 2025) in Computer Science and Engineering from The Pennsylvania State University, advised by Professor [Ruslan Nikolaev](https://rusnikola.github.io/). I received my Bachelor of Science in Computer Science and Engineering from Islamic University of Technology (IUT), Bangladesh, in 2015.

My dissertation, *Bridging the Gap Between Safe Memory Management and Non-Blocking Data Structures*, examines how concurrent data structures can safely remove, reclaim, and reuse shared memory. I design algorithms, analyze their correctness and progress guarantees, and develop reproducible C and C++ research artifacts. I evaluate these systems on multicore hardware to study the tradeoffs among memory use, robustness, and performance.

Before graduate school, I spent more than six years in the software industry building and maintaining production web systems.

<!--
<div class="card-grid card-grid--three">
  <article class="info-card">
    <p class="card-kicker">RRR-SMR</p>
    <h3>Safe memory reuse</h3>
    <p>Copy-free reuse and transfer of nodes across recyclable lock-free queues, linked lists, and trees.</p>
  </article>
  <article class="info-card">
    <p class="card-kicker">SCOT</p>
    <h3>Robust traversal</h3>
    <p>Data-structure adaptations that make optimistic traversals compatible with robust memory reclamation.</p>
  </article>
  <article class="info-card">
    <p class="card-kicker">R-SCOT</p>
    <h3>Recyclable structures</h3>
    <p>A unified approach to node recycling and efficient optimistic traversal in non-blocking data structures.</p>
  </article>
</div>
-->

<h2 id="highlights">Highlights</h2>

<div class="highlights-scroll" tabindex="0" role="region" aria-labelledby="highlights">
  <div class="highlight-list">
    {% for highlight in site.data.highlights %}
    <article class="highlight-item">
      <span class="highlight-date">{{ highlight.date | escape }}</span>
      {{ highlight.text | markdownify }}
    </article>
    {% endfor %}
  </div>
</div>

## Selected publications

<div class="publication-list">
  <article class="publication-card">
    <p class="publication-meta">PPoPP 2026</p>
    <h3>Fixing Non-Blocking Data Structures for Better Compatibility with Memory Reclamation Schemes</h3>
    <p><strong>Md Amit Hasan Arovi</strong> and Ruslan Nikolaev.</p>
    <p class="link-row"><a href="https://doi.org/10.1145/3774934.3786455">Paper</a><a href="https://doi.org/10.5281/zenodo.17707898">Artifact</a><a href="https://github.com/rusnikola/scot">Code</a><a href="https://rusnikola.github.io/files/scot-ppopp26-slides.pdf">Slides</a></p>
  </article>
  <article class="publication-card">
    <p class="publication-meta">PLDI 2025</p>
    <h3>RRR-SMR: Reduce, Reuse, Recycle: Better Methods for Practical Lock-Free Data Structures</h3>
    <p><strong>Md Amit Hasan Arovi</strong> and Ruslan Nikolaev.</p>
    <p class="link-row"><a href="https://doi.org/10.1145/3729337">Paper</a><a href="https://doi.org/10.5281/zenodo.15258497">Artifact</a><a href="https://github.com/rusnikola/rrr-smr">Code</a><a href="https://rusnikola.github.io/files/rrr-pldi25-slides.pdf">Slides</a></p>
  </article>
</div>

<p class="section-link"><a href="{{ base_path }}/publications/">View all publications →</a></p>

## Teaching

At New Mexico Tech, I teach introductory computing, programming fundamentals in C, and assembly language and machine organization. In Spring 2027, I will teach Object-Oriented Programming in C++, Computer Architecture, and Systems Programming. Previously, I served as a teaching assistant for systems programming and operating systems at Penn State.

<p class="section-link"><a href="{{ base_path }}/teaching/">Read more about my teaching →</a></p>
