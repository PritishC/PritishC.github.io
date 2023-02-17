---
layout: post
title: Second Semester Review
date: 2022-05-31
permalink: /posts/2022/05/second-sem-review/
tags:
  - IITB
  - MS
---

This post will follow the same format as the first semester review. With this semester ends one year of the program taken fully online, and I willl be heading to campus in June. Life circumstances made this semester a bit more difficult than it should have been, but it is what it is...

CS726: Advanced Machine Learning
--------------------------------

Run by [Prof. Sunita Sarawagi](https://www.cse.iitb.ac.in/~sunita/cs726/) and truly an advanced level course. You may come across other reviews of this course by undergrads on their respective DAMP websites. You will find that they mention that the course requires a significant amount of effort to keep up - and having taken it, I believe this to be true on average. The instructor covers probabilistic graphical models and some generative models in the first half, and interesting topics from recent deep learning papers in the second half (Gaussian processes, energy based models, causality, normalizing flows, time-series forecasting with Gaussian copula, etc) plus sampling. Classes were taken on Teams, and there were also some interesting guest lectures by researchers from the industry (think Google Research etc).

There was one theory assignment, weekly quizzes which could be taken only once and had greater weightage than the assignment, two exams and one course project. There were sample questions for almost every lecture, but understanding how the answers came about took a while initially. Questions in the quizzes, assignment and exams did require some thought, in increasing order of magnitude. One would greatly benefit if they possess a good background in probability before starting this course. Some knowledge of graph theory and deep learning basics would also be helpful. Form a study group with atleast one good student in it so that you can discuss whatever was taught and clear your doubts. Take conceptual help from the TAs too - I want to add that Lokesh, a PhD student in the instructor's group, was particularly helpful to me.

For the PGMs portion, there is enough material available online (some of which I can recommend are [Stanford](https://ermongroup.github.io/cs228-notes/), [CMU](http://www.cs.cmu.edu/~guestrin/Class/10708/), this helpful resource on [d-separation by MIT](http://web.mit.edu/jmn/www/6.034/d-separation.pdf), the Koller-Friedman book and any other material one can google on Bayesian networks). For generative models like the VAE and GAN, the prof. provided us with lecture notes. For the second half, too, we were given lecture notes, resources, and sample questions crafted by the instructor.

The project was an interesting experience. I got to choose a topic that interested me, which I proposed to my team and then led the charge. This was a first for me wrt ML projects. We attempted a modification of this ICLR workshop paper on [graph energy based models](https://arxiv.org/abs/2102.00546), where we tried to learn one part of the GEBM architecture with a [linear-additive neural network](https://towardsdatascience.com/interpretable-neural-networks-with-pytorch-76f1c31260fe). We had to then defend our design choices during the final presentation for the [project](https://github.com/PritishC/cs726-project).

Everything I want to say for this course has already been said in earlier DAMP reviews. Note that a sizeable number of undergrads took the course this time, and this affected grading. Take the quizzes seriously and don't dip on any of the exams, or your final grade may be affected.


CS769: Optimization in Machine Learning
---------------------------------------

Run by [Prof. Ganesh Ramakrishnan](https://www.cse.iitb.ac.in/~ganesh/cs769/), earlier CS709. This course is a bit different from standard convex optimization courses, in that it reduces coverage of KKT and duality in favour of submodular optimization in the second half. The first half covers convexity theory and the linear algebra and multivariate calculus involved, upto the analysis of vanilla gradient descent. The second half largely covers the various kinds of gradient descent, upto projected and proximal gradient descent, makes a detour to cover KKT and its relation to the proximal operator (with an aside on the duality gap), and then dives into submodular optimization. Classes were taken on Teams. Since I had come across submodularity in prior research work/readings, I was interested in taking this.

This course forced me to practice and get better at multidim functions and calculus, and see ML functions in that light, for which I used a set of notes provided by the instructor as well as [this book](https://mml-book.github.io/book/mml-book.pdf), particularly the vector calculus chapter. I've seen mild complaints on previous iterations of this course alleging that the instructor spent too much time on the math basics. It did not feel that way in this iteration, although they did emphasize on solving questions (each lecture had ungraded HW questions). I also used various online resources, such as Stanford etc. and the book by Boyd and Vandenberghe for topics I had doubts in. The Moodle for this course was packed with content, including lecture videos from previous iterations of this course, the instructor's notes, and other resource pdfs. The course consisted of two assignments (both included programming questions), two exams, two paper readings (report + ppt) and a course project (report + ppt + code). Questions in both the assignments and the exams required a bit of thought but were well-made and focused on application of concepts.

In the course project, I proposed a re-implementation of this paper on [document summarization](https://aclanthology.org/P11-1052.pdf). My teammate implemented a performance review on multiple hyperparameter configs and I tried to implement a [deep submodular function](https://arxiv.org/abs/1701.08939) for doc summarization. The latter didn't work out, but I documented what I tried and where it failed. This helped us a lot during the presentation, which the instructor himself took and asked many questions.

This course covered a lot of material and you have to put in some time to get a hang of everything, similar to 726. Taking both 726 and 769 together probably wasn't a great idea in hindsight, because there was a lot of pressure in the last month with the end semester exams, presentations, research work and seminar. But if you feel you can handle it, you end up gaining a lot of knowledge and maybe even some ideas for your future research.


CS899: Communication Skills
---------------------------

Run by [Prof. Varsha Apte](https://www.cse.iitb.ac.in/~varsha/index.php), and is a core pass/no-pass course with separate allocation of credits. I'm a bit conflicted about this course, mainly because of the amount of time it demanded in an already packed semester. The time requirement is similar to or maybe a little less than CS699 from the first semester. I did learn a few things, such as making worthwhile presentations, how to write survey reports, how to read papers, how to look up whether a conference is worth your time in your field, etc. so I cannot completely discount its usefulness.

People tend to take this course lightly and there have been reports of plagiarism. Don't do that. There were warnings from DDAC (disciplinary action committee) and if a report goes to them, you will end up in trouble. My batchmates and I never plagiarized but also didn't think that these warnings would be anything more than that. Turns out that there are some people who got reported, and I don't know what became of them. There are also people who didn't follow the guidelines for the final mini-seminar talk/presentation and ended up having to retake the course in the summer, which is a bit painful.


MS RnD II
---------

I continued with my guide from the previous semester as we explored a variant of the earlier problem. We had a different undergrad on the project this time and him and I collaborated a lot. I got to see what the full lifecycle looks like, from wrangling with theory to coding up a full experiment pipeline and was a bit more confident than last time.

Note that your research work will clash with your coursework and you either have to take courses that aren't all heavy, or have to be able to handle the madness that ensues. There is also no guarantee that you'll be ready in time for a conference submission. Many things can happen - the pressure becomes crazy, people may leave, etc. You have to pick yourself up and keep going even when the stream is going against you.

It helps to implement ML models and other algorithms by yourself as a way of supplementing your background knowledge.

As before, this course culminated in a project presentation in the presence of an external professor, and the submission of a report.


Seminar
-------

A core course that is common to MTech and MS students. You are supposed to pick a guide to explore your future thesis with, and the seminar is supposed to be a literature review for this purpose. In my case, I read up on literature broadly within the scope of information diffusion. I discovered a few new interests I didn't think I'd have, esp. the field of geometric deep learning and the effect of geometries on ML architectures.

My guide was the same as my RnD guide, and we had weekly meetings where I would present a bunch of papers that I had read, and he would make suggestions about possible future work. We progressed in this manner until he was satisfied that I had covered enough material, and then focused on RnD instead as that took up more of our time.

I had to write a seminar report and make a presentation similar to RnD, and presented it to the same external professor. The things I learned from CS899 helped here during the presentation. Once again, seminar and RnD together could take a toll on your course selection, so be wary of that.

As an ending note, you have to take a minimum total of 58 credits worth of courses in the MS program if you are a TA, so you cannot skip any the five electives given in the [program structure](https://www.cse.iitb.ac.in/academics/ms-detailed-structure.php). The "*" beside an elective denotes that that elective is mandatory for that semester, and that you can't move it to another semester. So if you plan to retag some courses to additional learning and vice-versa (for e.g. to boost your CPI), make sure that you have taken enough courses to be able to do so.
