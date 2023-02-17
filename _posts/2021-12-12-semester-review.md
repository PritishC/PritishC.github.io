---
layout: post
title: 'First Semester Review'
date: 2021-12-12
permalink: /posts/2021/12/semester-review/
tags:
  - IITB
  - MS
---

2021 has gone by rather fast, and sometimes I still can't believe I've made it this far. It feels like just last week when I was under immense pressure and held great expectations in the run up to GATE.

There was a lot of stress in the aftermath as well, as some of the questions were heavily disputed on GateOverflow and we didn't know how many marks we would get. And then there were the tests and interviews once we knew how far our scores would take us. I'm kinda glad I gave myself the experience of taking atleast one national level exam successfully, what with all the thrill and exasperation that ensued. I hope this experience will pay itself off many times in the future and even if not, it's been worth it.

It took some time to adjust and get past the initial shock of assignments, quizzes and projects. The MS program focuses mainly on research, and in a move not seen in other institutions, IITB's MS includes a core RnD course in the first semester itself. Juggling that along with course commitments took a while to get used to, since I was completely new to ML. I learned a ton from my peers as well.

Here, I write about the courses that I took this semester and what to look out for. For the MS program, you have to take atleast one elective that is related to your stream - for e.g. CS725 for Intelligent Systems, CS744 for Systems, and so on. The rest can be as per your choice. The TA and RA/RAP program structures are different and can be found in the MS rule-book.

CS601: Algorithms and Complexity
--------------------------------

Run by [Prof. Rohit Gurjar](https://www.cse.iitb.ac.in/~rgurjar/CS601/). Covers basics, divide and conquer, greedy algorithms and dynamic programming in the first half. There is an emphasis on proofs in the greedy portion and intuition on how to frame the problem in the dynamic programming portion. Multiple different problems are covered in divide and conquer (e.g. integer squaring) and DP (margin slack). In the second half, covers some parts remaining in greedy/DP and substantial ground in bipartite matching (taxi scheduling/augmenting paths), randomization algorithms (Karger's min cut, reservoir sampling), k-approximation algorithms (load balancing) and complexity classes/reduction. Classes were taken on Zoom/Webex.

There are two theory assignments and two programming assignments, one in each half. All of them have interesting problems and may take days to solve fully. The midsem and endsem exams were proctored remotely using CodeTantra and submissions made on SAFE. Both exams were divided into two halves and a 10min break given in between. The questions consist of scenarios related to what is taught in class - if you're able to understand what is being asked, you'll do fine.

Pace of instruction is slightly slow but this is not an issue with recordings available. Prof takes doubts in the class and is available on Teams for discussion. He was very helpful in resolving some cribs I raised in both exams.

I took this course as **additional learning**, meaning that while its grade appears on the transcript, it does not count in the final CPI. I might retag it later (we have the flexibility to do that later in the program). Take this course if you're interested in algorithms or you feel that it may be relevant to your research.

CS725: Foundations of Machine Learning
--------------------------------------

Run by [Prof. Preethi Jyothi](https://www.cse.iitb.ac.in/~pjyothi/). Provides an introduction to several key topics in ML. Starts with basics in linear algebra and probability, and then covers ML basics (bias-variance tradeoff, regularization, MAP vs MLE, basis functions), linear and logistic regression, Naive Bayes, perceptrons and decision trees in the first half. Covers deep neural nets, SVMs, kernels, K-means clustering, dimensionality reduction (PCA, LDA), Adaboost and applications in the second half. Misses out on Gaussian mixtures, bagging and random forests which can be covered separately.

Books and online resources may be needed for a deeper understanding in some topics, as this is an introductory course. Prof provides supplementary material for every week's topics and that was very helpful. For e.g., Nielsen's book for neural nets and the backprop process, Mitchell's book for decision trees, Bishop and ESL for multiple ML concepts, Andrew Ng's notes for SVMs and kernels. There was one programming assignment on linear regression and gradient descent and one course project, to be done in teams (which my team used to explore GANs for doodling).

There were proctored quizzes in both halves that were harder than the corresponding exams. Some amount of mathematical maturity is needed (calculus, probability and linear algebra), but that should be expected in any serious ML course. A good team can help you sail through the practical parts of the course and I was very fortunate to be in one. If you're an absolute beginner to ML, you will struggle a bit but it will all come together with some persistence. One thing I noticed my more knowledgeable peers do is try to implement every concept that they were taught and I will try to imbibe this.

Prof was very helpful and always available on Teams for discussion. I resolved some of my doubts, for e.g. on Mercer's conditions for kernels this way. I took this course as an elective, but it was mandatory due to my choice of MS stream. It is also a prerequisite for CS726.


CS635: Web Search and Mining
----------------------------

Run by [Prof. Soumen Chakrabarti](https://www.cse.iitb.ac.in/~soumen/teach/2013.2A.CS635/). Covers a wide variety of topics related to information retrieval, and although I've linked to an older version of the course, it gives a fair idea of the syllabus. I took this course because of the graphs component and mild interest in the other components, but that is only one small part (if you are interested in graphs and have a bit of ML experience, take CS768).

Lecture material often touched on relevant research papers, for e.g. in topics such as learning to rank and graph analysis. It may feel somewhat disconnected from the bookish basics of IR which are tested in quizzes and exams, but the topics covered are interesting in their own right. Students are implicitly expected to cover the meat of the stuff from books (Stanford's IR book being most relevant, and Bishop's ML book being the next). Some other resources I found relevant were Stanford's Mining Massive Datasets book (for LSH) and Barabasi's networks book. Online resources were also important. It took me a while to realize all this though.

There were two programming assignments, one on coding schemes (Gamma, Golomb, arithmetic) and one on Naive Bayes text classification using multinomial and Poisson models. It's worth noting that on the second assignment, I had a valuable back-and-forth with the prof on email and he was very encouraging and gave me tips to deal with some implementation problems that I was facing. He even showed interest in the results that I obtained and these little gestures stay with you long after the course is over.

All this being said, take this course only if you're already comfortable with the IITB system and have sufficient mathematical maturity (or equivalently, have a decent background in machine learning). I've noticed grad students (including me) struggle with this course and senior undergrads having the time of their lives. I say this because the exams - and there are _three_ of them - involve interesting math/ML/datastructure questions where those who have been solving such problems in other courses already greatly benefit. Those who have implemented a bit of ML (played with tensor ops atleast) also benefit. This may not always be true for fresh grad students. If you do take this course, make sure to request the TAs for past exams for practice. Questions never repeat in these exams but concepts may.

I took this course as an elective. It also used to be a prereq for CS728, but that may have changed - you'd have to confirm this with the instructor.

CS699: Software Lab
-------------------

Run by [Prof. Kavi Arya](https://cs699-iitb.github.io/CS699-Autumn-2021/), organized by the TAs. Unlike the others, this is a core course with a greater number of credits assigned to it. Covers a variety of topics in software development, scripting, and scientific computing. The variety may seem overwhelming and the need for such a course may even seem debatable (and infact, there has already been a lot of [pondering on this](http://abhinavmaurya.blogspot.com/2010/08/iit-bombay-cs-699-software-laboratory.html) in the past). It worked out well for me in the end though, and I did pick up a few skills (like LaTeX).

I should add that I've spent some time in the industry and so this course didn't give me any trouble. Your experience/mileage depends heavily on the TAs. On average, they did their best to accommodate us but this may vary from person to person, so I can't really make a blanket statement. It seems clear to me now that this course was introduced keeping in mind the large population of recent undergrad passouts who join via GATE. If you join directly from a tier 3 college (I graduated years ago), you may not have sufficient programming experience (CP is not programming experience) or experience with tools.

Includes a course project to be done as a team, and my team made a web scraping project for this. Project is a substantial portion of the grade so it needs to be taken seriously. The lab assignments were divided such that the ones before the midsem were to be done individually, and the ones after were to be done in teams.

This course in addition to others does make your course structure heavy, so plan on the courses you take wisely.

CS777: MS R&D
-------------

Not really a "course", but graded like one. Also a core course with greater credits. You're supposed to pick an advisor in your stream and work with them on a research problem. I went with [Prof. Abir De](https://abir-de.github.io/) as I'm interested in graph mining, graph ML and network science. As part of the problems we explored in information diffusion, we also collaborated with a prof from another IIT - "we" meaning me, our prof and a senior undergraduate.

I felt completely out of my depth for the first half of the semester and I guess that's normal for a rookie like me. I tried to gather background knowledge (for e.g., Jure Leskovec's CS224W) with enthusiasm but initially it didn't stick as much because I was very new. With time and work (and collaborating with the undergrad), things began to make much more sense.

Final deliverables included a report and a presentation (atleast in my case). The presentation was graded by an external professor chosen by the advisor. Make sure that you know what you're talking about in sufficient depth and can answer follow-up questions. The external professor was satisfied with my answers.

It's rather clear that one needs to balance their courses against their research, esp. in the earlier semesters. In the later semesters of the MS program one focuses solely on research so course pressure is not an issue. Had I taken a lighter courseload I could have picked up things during RnD more quickly. However, I don't regret all the knowledge I gained, all things considered.

Hopefully this helps the next batch of MS entrants!
