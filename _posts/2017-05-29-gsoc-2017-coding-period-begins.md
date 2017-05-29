---
layout: post
published: true
mathjax: false
featured: false
comments: true
title: 'GSoC 2017, Coding Period Begins! ⚡'
description: >-
  My experience and work  during community bonding period of GSoC 2017 with
  CCExtractor
headline: GSoC with CCExtractor | Saurabh Shrivastava
categories:
  - GSoC
tags: GSoC CCExtractor project update srt subtitles
imagefeature: posts/header_cb.jpg
modified: ''
---
This marks the ending of a month long community bonding period. Fine-tuning deliverable, setting up timeline, early coding and much more, here's my GSoC 2017 community bonding experience with CCExtractor Development. 😊

> As it turns out, the little backstory written below is not _little_ afterall. 😛 [Click here](#communinty-bonding-period "Community Bonding Period") to skip it and jump to later portion.

### A little backstory

I began preparing for GSoC in November and at it took me no time to decide that CCExtractor is the one I would love to work with. It was one of the first orgs I researched about and I immediately liked them. They were amidst Google Code-In and it was actually pretty awesome to watch the participants and mentors working together. 

I distinctly remember the starting few days. Though I had joined CCExtractor's discussion group on Slack, I did not say anything in the beginning. I only stayed their and read their conversations. It was not because I didn't have anything to say or that I did not want to introduce myself, but because I was hesitant. I had never done this before. I was dead scared, and nervous. But then I saw how lovely the community is. The Code-In participants were in the age group of 13-18 and seeing them work together gave me a boost in confidence. The mentors were super - supportive. Even when someone was being PITA they handled it pretty flawlessly. So, I thought, if these kids can do it, why can't I (though in reality, they were completing Code-In taks and I was merely trying to introduce myself 😛). So, I introduced myself with my first PR which was a mere correction of a typo in a readme file. I was surprised to see how welcoming everyone was. Not only the mentors, even the participants gave me warm welcome. My hesitation went from 100% to 0% in no time.

That was it. From that moment I actively started participating in the discussions, code reviews, random chats and what not. I started contributing and also helped the code-in students in verifying their code and helping them test things. Along with the main CCExtractor tool, I also had a lot of fun working on Sample-Platform! Also, contributing to sample-platform taught me a great deal of things - not just talking about code - but other important things like open-source ethics, working with people, making good PRs, asking good and quality questions, doing research, proper version control et cetra. Thank you Carlos and Willem, I can not thank you both enough! During this period I also became good friends with Alex and Evgeny who were code-in participants (and winners) and now GSoC mentors. It's super-fun to work with all of these guys and its awesome to be a part of the community!

### Communinty Bonding Period 

The amazing news of [my proposal getting selected](https://saurabhshri.github.io/2017/05/gsoc/accepted-in-google-summer-of-code-2017) for this GSoC was announced on 4th of May which also marked the begining of community bonding period. Community bonding is basically a month allocated to learn about one's organization's processes - release and otherwise - developer interactions, codes of conduct, et cetera. What once choose to do during this period varies.

Since I was already active in the community since quite some time, I was already familiar with most of the people and with the general practices. I have two mentors - [Carlos Fernandez Sanz](https://github.com/cfsmp3) (who originally built CCExtractor) and [Alex Bratosin](https://github.com/AlexBratosin2001) (CCExtractor GCI 2016 Winner).

So here are the things I did during the community bonding period.

1. Set-up a blog.  

	This was actually quite important. To note down my GSoC progress and to keep mentors and everyone in the loop, I created this blog. It's actually a simple Jekyll blog hosted on Github Pages. 
    
    Blog link : [https://saurabhshri.github.io/](https://saurabhshri.github.io/).
    
    Additionally I decided that it would be easier for my mentors and me to keep a check on work if we have a detailed checklist of the tasks which is to be done. My mentors agreeed, and hence I am maintaining the milestones and deliverable in the form of a checklist as Github Gist, so that it's easily embeddable. 
    
    Milestones/Weekly deliverable checklist : [https://saurabhshri.github.io/gsoc/](https://saurabhshri.github.io/gsoc/) .
    
    Till now I have written about three posts (fourth including this) about my GSoC work on the blog the first being [announcement of me getting accepted](https://saurabhshri.github.io/2017/05/gsoc/accepted-in-google-summer-of-code-2017). All my GSoC work progress and related work is tagged under the "Gsoc" category.
    
    Category wise posts : [https://saurabhshri.github.io/categories/](https://saurabhshri.github.io/categories/) .
    
	![]({{site.baseurl}}/images/posts/blog_screenshot.PNG)
    _Screenshot of one of the blog posts_

2. Brought myself a chair.  

	Students participating in GSoC are expected to work at least 40 hours a week, and never having done anything for such a long time before, it was an easy realization that a proper chair is a must. I brought a nice ergonomic chair with lambar support and adjustable height and it really helps in the backpain caused due to bending in front of laptop. I think it was worth an investment.
    
3. Completed GSoC formalities including setting up Payoneer account.

	This took more efforts than I originally expected. Setting up mode of payment (i.e. deciding to recieve money in USD or INR) took some significant amount of time. I visited several banks to enquire about their fees. Plus when I decided and set-up the method, it was chosen wrongly dure to some error on Payoneer's end. I had to again send some documents and information to them on email, after around two weeks of email interchanges the account was finally set-up.
    
    ![]({{site.baseurl}}/images/posts/payoneer.PNG)  
    _Google added as funding source in Payoneeer account_
    
    I will post a detailed post about setting up payment process to help future students sometime soon.
    
4. Fine tuning deliverable.

	I spent a lot of time reading about the techniques I might incorporate while doing the project. Though I had made a pretty detailed plan while making the proposal, I fine tuned the deliverable for first phase. They can be found in the checklist I mentioned above.
    
5. Creating sample repository.

	The kind of samples that are required for my tool are a bit restrcitive. Two of the primary conditions are : 
    
	 a. 	samples must have subtitles  
	 b. 	samples must have clear speech audio
 
 	To find such samples I enquired various people like creator of Kaldi based forced-aligner Gentle and CMUSphinx community. Nikolay from CMUSphinx gave me a very good idea to use Ted Talks as sample. They fit both my primary requirements and are easily available to download as well.
    
  ![]({{site.baseurl}}/images/posts/sample.PNG)  
  _Some Ted samples_
    
    Also, Carlos is sending a 2 TB disk loaded with transport streams recorded from various TV stations. Let's see when I get to recieve that.
    
6. Started coding early. 

	I decided to start coding early and hence started to work on a subtitle parser which is one of the primary requirement of my tool. I have already completed it (at least the part required in my project).
    
    ![]({{site.baseurl}}/images/posts/srtparser.PNG)  
    _Subtitle Parser_

	Link to parser : [https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp](https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp) .
    
    Link to relevant blog posts :
    
  - [Creating a full blown (SRT) Subtitle Parser ](https://saurabhshri.github.io/2017/05/gsoc/creating-a-full-blown-srt-subtitle-parser)
  
  - [Simple yet powerful single header srt subtitle parsing library in cpp](https://saurabhshri.github.io/2017/05/gsoc/simple-yet-powerful-single-header-srt-subtitle-parsing-library-in-cpp)
  
  I have also begun working on setting up testing scripts which will help me during coding period.
  
7. Researching

	This is something which I will need to do throughout. A lot of things which I am planning to do in my project like VAD, ASR, Phoneme Recognition, LM Training et cetera are something which are new to me. It'll be interesting to learn about them and implement them. I am quite excited and a little nervous about them. :)
    
8. Setting up development environement.

	I inititally hoped to recieve a seperate server to work upon, but I understand that it is not entirely possible to give me my own separate server. I will be working on the gsocdev3 server on which I used to work before. It's an excellent machine. The internet is quite good and it has huge sample collection. I also have my laptop with several VMs all ready to test the code I write. I have also enrolled myself in AWS free tier in case I need it.


### What's next?

The coding period officially commences from 30th May. I will stick to the timeline and work to tick those square boxes in the checklist. I will try to complete the tasks ahead of time in order to save time in case I get stuck at some point (which is often the case developing something new). Also, first phase evaluations begin on 26 June.

I wish all the participants a fun and productive summer. 🙋

    