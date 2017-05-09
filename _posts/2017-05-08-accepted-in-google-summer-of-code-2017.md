---
layout: post
published: true
mathjax: false
featured: true
comments: true
title: Accepted in Google Summer of Code 2017!
description: >-
  I got accepted into Google Summer of Code 2017 for my project - CCAligner :
  Word by Word Audio Subtitle Synchronization with CCExtractor Development |
  Saurabh Shrivastava.
categories:
  - GSoC
tags: GSoC open-source CCExtractor FOSS Subtitles
imagefeature: posts/Accepted_in_GSoC.png
---
My proposal _CCAligner - Word by Word Subtitle Synchronization_ with CCExtractor Development has been accepted for Google Summer of Code (GSoC) 2017!

>If you are reading this, chances are, you already know what's GSoC. In case you don't, here's official link to the same : [http://g.co/gsoc](http://g.co/gsoc) . 

I am very happy to announce that my proposal to build a tool for word by word audio subtitle synchronization has been selected for Google Summer of Code. I will be working with the organization [CCExtractor Development](https://ccextractor.org "CCExtractor Website.") which made the de-facto subtitle extraction tool - [CCExtractor](https://github.com/CCExtractor/ccextractor "CCExtractor on Github."). I am super excited to work with my mentors [Carlos Fernandez Sanz](https://github.com/cfsmp3 "Carlos' Github profile.") (who originally built CCExtractor) and [Alex Bratosin](https://github.com/AlexBratosin2001 "Alex's Github profile.") (CCExtractor GCI 2016 Winner).

### What is my project about?

I have named my project **CCAligner** as it conveniently lays out it's basic functionality and also adheres to the name of it's parent tool CCExtractor. So, what generally happens is that the usual subtitle files (such as SubRips) have line by line synchronization in them i.e. the subtitles containing the dialogue appear when the person starts talking and disappears when the dialogue finishes. This continues for the whole video. For example :

1274  
01:55:48,484 -- 01:55:50,860  
The Force is strong with this one  

In the above example, the dialogue #1274 - _The Force is strong with this one_ appears at `1:55:48` remains in the screen for two seconds and disappears at `1:55:50`.

The aim of the project is to tag the word as it is spoken, similar to that in karaoke systems.

E.g.

The---------[6948484:6948500]  
Force------[6948501:6948633]  
is------------[6948634:6948710]  
strong-----[6948711:6949999]  
with--------[6949100:6949313]    

In the above example each word from subtitle is tagged with beginning and ending timestamps based on audio.

### Why is this useful?

While watching a video, it makes sense to have a whole / part of sentence displayed on screen rather than individual words as they are spoken. But there are cases where having timing information of each word is very important. Think of a scenario where you have to tag an occurrence of an event, marked by a special word, then having the information about when the word was spoken is what we need. This is a very basic example to just give you an idea. I have written about various possible applications of this tool in my proposal, and do give it a read if you are interested.

I really hope by the end of summer, the tool gets ready to be used. The basic flow of usage would be really simple. Just call the tool, pass the audio file, the subtitle file, choose the mode, the output type and the result should be word by word subtitle synchronization.

### What am I doing right now?

Right now, it's community bonding period. I just finished my exams and returned home. As mentioned in the timeline, I will be spending this month fine-tuning my deliverables by discussing with my mentors, and also making a sample repository for me to test the tool.

### The GSoC result was announced on 4th, why such a late post? Am I lazy?

While I might be lazy, which I most certainly am, it has nothing to do with me being late. I fell in love with open-source ever since I made my first contribution, and I extremely excited for this GSoC. I was amidst my semester examinations when the result was announced. I had already intimidated my mentors about the same and they themselves advised me to prioritize exams. I will be publishing few more posts about the same later on.

### Where's the proof of selection and my proposal?

I am including this, only to show-off my name on GSoC website :P .
This is the official link about my project on Google Summer of Code website - [https://summerofcode.withgoogle.com/projects/#5589068587991040](https://summerofcode.withgoogle.com/projects/#5589068587991040 "CCAligner - Word by Word Subtitle Synchronization | Google Summer of Code Project by Saurabh Shrivastava") . I shall also soon add myself on CCExtractor's website. 

![My Project listed on GSoC website.]({{site.baseurl}}/images/posts/accepted_proof.PNG)

About my proposal, you may find my GSoC 2017 proposal for CCExtractor Development [here](https://drive.google.com/file/d/0B7xAF1f7vzYzOE1LY21pZjdSTW8/view?usp=sharing "GSoC Proposal - CCAligner") and in case that link doesn't work (please comment about the same, I shall replace it), here's the [mirror](https://github.com/saurabhshri/saurabhshri.github.io/blob/master/GSoC/5565268630700032_1490805743_Word_by_Word_Subtitle_Sync_by_Saurabh_Shrivastava_CCExtractor.pdf "Mirror of my GSoC proposal on Github.").

Follow this blog to read my future posts. Thank you for reading. Feel free to comment with your views, questions and criticism, if any. I would love to discuss them. :)
