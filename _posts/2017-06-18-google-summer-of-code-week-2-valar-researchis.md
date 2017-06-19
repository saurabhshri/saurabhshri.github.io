---
layout: post
published: true
mathjax: false
featured: false
comments: true
title: 'Google Summer of Code, Week 2 : Valar Researchis! ⚔'
description: >-
  The second week of Google Summer of Code just wrapped up. This week was spent
  on adding support for managing timestamps for each word, improving Approx
  Aligner, printing result as SRT, revising Game of Thrones and doing a lot of
  reading and researching. The first evaluations are due in two weeks.
headline: GSoC with CCExtractor | Saurabh Shrivastava
categories:
  - GSoC
tags: gsoc open-source subtitles srt ApproxAligner read weekly-updates
---
The second week of Google Summer of Code just wrapped up. This week was spent on adding support for managing timestamps for each word, improving Approx Aligner, printing result as SRT, revising Game of Thrones and doing a lot of reading and researching. The first evaluations are due in two weeks.

> I had imagined that the Approx Aligner would be far from accurate, the results are definitely not bad. I have attached the demo later on in this post.

The first evaluations are even more close as the third week of coding period begins. Since the beginning of the program I am properly (rather ahead atm) on the [timeline](https://saurabhshri.github.io/gsoc/) I proposed. Hence, I did not write _much_ code in this week, but instead I spent the time learning few things which will be helpful for the project later on. Another reason for that was the fact that I was sick (fever) for a while. 🤒 

Here's the summary of things I did in the second week : 

1. Added support for managing the timestamps of individual words.

	The parser was modified to add the support of storing the start-time and end-time of each word ad accessing it. The time values are stored as a vector of `long int` and there are functions to get these values both as vector or individual values by index.
    
    ```
    
    //Relevent Data Members : 
    
    std::vector<std::string> _word;         //list of words in dialogue
    std::vector<long int> _wordStartTime;   //start time of each word in dialogue
    std::vector<long int> _wordEndTime;     //end time of each word in dialogue
    std::vector<long int> _wordDuration;    //actual duration of each word without silence
    
    //Relevent Member Functions : 
    
    std::vector<std::string> getIndividualWords(); //return string vector of individual words
    std::string getWordByIndex(int index);       //return word stored at 'index'
    std::vector<long int> getWordStartTimes();   //return long int vector of start time of individual words
    std::vector<long int> getWordEndTimes();     //return long int vector of end time of individual words
    long int getWordStartTimeByIndex(int index); //return the start time of a word based on index
    long int getWordEndTimeByIndex (int index);  //return the end time of a word based on index
    ```
    This makes things very easy. For example printing the words and their timestamps in SRT format is now as easy as doing : 

	```
    //converting STARTING timestamp (in milliseconds) to hh:ss:mm,ms
    ms_to_srt_time(_sub->getWordStartTimeByIndex(i),&hh1,&mm1,&ss1,&ms1);
    
    //converting ENDING timestamp (in milliseconds) to hh:ss:mm,ms
    ms_to_srt_time(_sub->getWordEndTimeByIndex(i),&hh2,&mm2,&ss2,&ms2); 
    
    //arranging the timestamps in SRT style
    sprintf(timeline, "%02d:%02d:%02d,%03d --> %02d:%02d:%02d,%03d\n", 
    		hh1, mm1, ss1, ms1, hh2, mm2, ss2, ms2);
            
    out<<timeline;
    out<<_sub->getWordByIndex(i)<<"\n\n";
    ```

2. Improving the Approx Aligner and making output as SRT

	Using the word weight to find it's approximate timeframe is bound to have errors. I spent the time in figuring out how can I still improve it and if its even possible. After a lot of experimentation it hit me - apart from the words, the one other thing that makes a difference in actual speech is the "silence" between those words which I was not considering at all. So, using word weight and finding the duration of each word, I split the remaining time into the silence between each word being spoken. One more addition could be a more emphasis on silence  in presence of punctuation, but this is difficult to calculate as it hugely varies from speaker to speaker and situation to situation (well, so does other things).
    
    Anyway, after making changes, I also added the option to print the result as an SRT file so that I can actually see the results and verify them. I will make a report on it's accuracy once I run it across all the samples. The disk containing samples will reach to me soon. The results right now, surprisingly, **are not bad at all!**
    
    I tested it on couple of samples, and it was pretty great given that the method uses 0% audio processing and how fast it is and that it's entirely based on probability and approximation! Here's a quick screengrab demostrating the result : 
    
    <div style="position:relative;height:0;padding-bottom:56.25%"><iframe src="https://www.youtube.com/embed/km1iHe_mGuo?ecver=2" style="position:absolute;width:100%;height:100%;left:0" width="640" height="360" frameborder="0" allowfullscreen></iframe></div>
    
    You can see the results yourself too. Here are the video sample and it's _word by word synced_ subtitles generated using Approx Aligner. :)
    
    - Video File 	: [ElonMusk2017.mp4](http://gsocdev3.ccextractor.org/~saurabhshri/repository/ted/ApproxAligner/ElonMusk2017.mp4)    
    - Subtile File 	: [ElonMusk2017.srt](http://gsocdev3.ccextractor.org/~saurabhshri/repository/ted/ApproxAligner/ElonMusk2017.srt)
    
    This is actually pretty good, because now we will be able to have a window (say +- {ms} of this timestamp) where the word will actually be present and hence we can focus our ASR to detect the word in this range rather than trying to guess it over a period of time.  

3. Loads of reading and researching 📑

	I did not want to waste any time just because I was sick. So, I got few research papers in the field of Forced Aligners and ASR printed and spent time reading them. Also, I read the code of the programs using these ASRs to see in what ways people are using them to accomplish their tasks.
    
    I now have an even better picture of how and what I am going to do in phase two. Also, I already have the capability to perform VAD and read audio samples implemented ahead of time which is a plus.
    
### What's next?

I will be implementing the various other output options, such as JSON and XML. Also, I'll refactor somme code and write documentation on using the Approx Aligner. The tool is in the form of libraray currently and it makes sense to also provide an interface so that it can be used directly as well (i.e. without writing code), after all - it's a _tool_. I should have the disk containing samples soon - so I'll have to process it to get audio in the required format from them and also work on some batch scripts to automatically run test over all of them. 

This time of summer is quite daunting here in India. It's hot, but worse, it's humid. My eyes need a checkup as well - I am often having headaches and blurry vision (not a good sign I know). I hate spectacles and definitely don't want them. The last time I had check-up, the doctor pointed out that my right eye needs a glass of 0.5 power. But given my hatred towards them I did not get my glasses made. I sincerely hope it's not worsened.

Anyway, I hope everyone's having fun and the other participants are having great time building their projects. ⛱