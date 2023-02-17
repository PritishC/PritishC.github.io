---
layout: post
title: 'Resources used for GATE'
date: 2021-06-18
permalink: /posts/2021/06/gate-resources/
tags:
  - GATE
  - interviews
---

In this post I will elaborate on what resources I used to prepare for GATE. I get this question a lot, so I figured it's best to put it out somewhere.
Note that the resources I used may not be the right ones for you. Do your due diligence!

You may also want to check [Gokul's list of resources](https://goxul.github.io).

2019 Phase
----------

In this phase, I had to prepare entire subjects from scratch. I had not touched most of these CS books and topics in years, and especially not at the level prescribed by the IITs/IISc. I spent the first 6 of 8 months in making notes and solving half of the GO PDFs, and the remaining 2 months in solving the remaining portion of the GO PDFs. I took only two mock tests near the end, and this turned out to be a big weakness. I followed Bikram Ballav's "What to Read" PDF in searching for resources to make notes from.
I solved PYQs for all subjects, but I specifically mention them in some subjects below because certain kinds of PYQs appear frequently in GATE.

1. Data Structures: Mark Allen Weiss for some topics (AVL trees, general trees, code complexity calculation). Cormen for most other topics like heaps, binary trees. GO Volume 2 PDF for solving previous-year questions (PYQs) on C programming and data structures (no better source than this).
2. Algorithms: Cormen hands down. Covers almost everything you can think of. Sartaj Sahni for some topics like the greedy knapsack problem. Note that PYQs on this topic are a mix of mathematics (combinatorics, probability) and algorithm design. There are some extra topics like the tournament method of finding min-max that are covered best in GO answers.
3. Databases: Korth-Sudarshan for topics like ER diagrams, SQL, relational algebra, a bit of indexing, and concurrency. Navathe for DB normalization. NPTEL videos by Prof PP Chakraborty on some topics like relational calculus.
4. Computer Networks: Kurose and Ross for most topics. Tanenbaum for topics in routing and the various layers.
5. Operating Systems: Galvin for some topics, Stallings for memory management and a bit of synchronization. NPTEL videos by Prof PK Biswas of IIT Kharagpur for topics such as synchronization, file systems.
6. Compiler Design: Mostly the Dragon book. I tried to solve exercise problems by myself and used this [Github repository](https://github.com/fool2fish/dragon-book-exercise-answers) to self-check answers. A background in theory of computation is mandatory.
7. Theory of Computation: NPTEL videos by Prof Kamala Krithivasan of IIT Madras. PYQs in GO PDF Vol 2, of which the majority were problems on regular languages, regular expressions, minimal state automata. Prof Shai Simonson's ADuni videos for decidability. GO for Rice's theorem and some university PDFs on reduction, although Shai's videos have a better way of explaining.
8. Digital Logic: Morris Mano for making notes and some problems. NPTEL lectures by Prof Srinivasan of IITM. Mostly PYQs for problem solving.
9. Computer Organization and Architecture: NPTEL videos by Prof Matthew Jacob of IISc, especially for topics like pipelining and cache memory, although these are _not_ enough. This is a subject that should be covered in depth from standard books and videos. PYQs cover the vast majority of possible question types.
10. Mathematics: Rosen for discrete mathematics concepts and some solved problems. Erwin Kryszig for Linear Algebra. Sheldon Ross for probability. NPTEL videos by Prof Kamala for group theory and some other topics that have appeared in GATE. Some PDFs prepared by Arjun Suresh of GO for topics like combinatorics, graph theory (conceptual understanding) although I don't remember where I found them.

2020 Phase
----------

I analyzed my [2020 exam](https://docs.google.com/spreadsheets/d/1ASbHQNiI_FOvc7nxjxB1khq3HzaSsSQ4p-blUD3yOPM/edit?usp=sharing) and found a number of weaknesses. I wasn't good enough in both regular problem solving and timed problem solving. I had not taken enough mock tests. I aimed to fix these issues. I found [Gatevidyalay](https://www.gatevidyalay.com/) to be a good source for which exercise problems to solve in standard books. In the process I discovered that quite a few GATE questions appear almost directly or with little modification from these books. I also took four different test series this time, of which I found GO's lengthy/tricky tests to be the closest analog to GATE 2021: GO, Applied Course, GATEBook, Testbook. Yes, I did not use any of the popular coaching test series, didn't see the point. I should have solved more from GO!

Do both weekly subject tests as well as full mock tests in the last few months. GATEBook's weekly subject tests covered a lot of tricky concepts and used standard sources as well as the old GRE CS subject tests for problems. I am not going to list subject test contributions below.

1. Data Structures: Mostly a repeat from last year, focussed on PYQ problem solving this time.
2. Algorithms: Mostly a repeat from last year. Covered a few topics like binary search tree range queries from the 2020 paper.
3. Databases: Navathe for concepts and problems from ER modelling, **indexing** (problems come almost verbatim from here!) and a bit of concurrency. Raghu Ramakrishnan for concurrency management and transactions.
4. Computer Networks: Peterson and Davie for exercise problems in the bottom 3 layers. Wikipedia for application layer protocols. Kurose and Ross, Tanenbaum and RFCs for transport layer congestion control.
5. Operating Systems: Tanenbaum for concepts and problem solving in topics like process scheduling, disk scheduling, disk numericals, file systems, memory management (especially multilevel paging). Little Book of Semaphores for a bit of mental mapping in synchronization.
6. Compiler Design: A new chapter was added this year: dataflow analysis and optimization, which I covered from the Dragon Book, but mostly from online notes from [Stanford's class](https://web.stanford.edu/class/archive/cs/cs143/cs143.1128/) (not Alex Aiken) and [these notes](http://user.it.uu.se/~kostis/Teaching/KT1-11/Slides/handout14.pdf).
7. Theory of Computation: I covered all topics except decidability from Peter Linz, and it made a huge difference in my performance. Solving exercise problems gave me in-depth understanding here. Also used Sipser to study about minimum pumping length. In hindsight, should have solved decidability problems from Linz too.
8. Digital Logic: Covered topics such as combinational circuits (especially adders), Booth multiplication, floating point arithmetic from Computer Organization by Carl Hamacher and solved some exercise problems. Rest is a repeat from last year.
9. Computer Architecture and Organization: Studied Hamacher for topics such as datapath, cache memory and other memories, DMA, pipelining and solved exercise questions. Used Hennessy and Patterson for some pipelining concepts such as the speedup formula. Georgia Tech/Udacity COA videos to understand dependencies and hazards.
10. Mathematics: Solved Rosen exercise problems for topics covered in previous phase. Covered concepts and solved lots of problems from topics such as Trees, Graph Theory, Set Theory, Functions, Relations, Combinatorics (all that balls in bins and generating function stuff). Used Prof Gravner's notes for practicing probability (lots of good problems here). JBStatistics Youtube videos for probability distributions. Rest was a repeat from last year.

Additionally, MSQs were introduced this year and they raise the bar a few notches. Make sure to study theory **in depth** for subjects like Operating Systems (Galvin) and Networks to prepare for MSQs. I missed out on this.

I didn't quite get the rank I wanted, but it was enough to apply to MS programs at top IITs.

Interview Preparation
---------------------

I focussed on linear algebra and probability. For this, I used Prof Strang's LA lectures+recitations+problems, and Prof Tsitsiklis's Probability lectures+recitations+problems (upto lecture 9 - ideally the whole course should be covered). If you are aiming for AI/ML (the IITs/IISc call this area Intelligent Systems), then these two subjects are mandatory.
