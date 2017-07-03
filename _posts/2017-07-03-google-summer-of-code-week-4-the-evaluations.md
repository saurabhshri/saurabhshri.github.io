---
layout: post
published: true
mathjax: false
featured: false
comments: true
title: 'Google Summer of Code, Week 4 : The Evaluations! ⚰💀'
description: >-
    The fourth week ended on 29th of June marking the end of Phase 1 of coding period. 
    The week also comprised of the first evaluations, which would judge 
    whether I will be continuing the program or fail. 💀
headline: GSoC with CCExtractor | Saurabh Shrivastava
categories:
  - GSoC
  - News
tags: gsoc open-source subtitles  weekly-updates evaluations
---
The fourth week ended on 29th of June marking the end of Phase 1 of coding period. The week  also comprised of the first evaluations, which would judge whether I will be continuing the program or fail. 💀

> I passed my evaluations! My mentor already told me about it during the evaluations, I received the official email from GSoC team on 30th declaring that I am eligible to continue through the next rounds.

This was the last week of first phase of coding period. In the previous 3 weeks I spent time building a the nitty-gritty of the tool upon which now I will continue the work. That involved [building a robust subtitle parser](https://saurabhshri.github.io/2017/05/gsoc/creating-a-full-blown-srt-subtitle-parser), [creating approx aligner](https://www.youtube.com/watch?v=km1iHe_mGuo), building test environment (which included collecting samples), [ability to read and process audio](https://github.com/saurabhshri/CCAligner/blob/master/src/lib_ccaligner/read_wav_file.cpp), [voice activity detection](https://github.com/saurabhshri/CCAligner/tree/master/demo/VAD) and a lot of reading. The fourth week was reserved as buffer week to meet the missed milestones, complete the documentation and all the remaining things.

In the fourth week I added the capability to read wave files from stream/pipe. Till now the  files that were present on the disk were read. Now it is possible to simply pipe the wave file into the program. It was comparatively challenging as the specifications needed to be decoded on the go. It would have been easy if I were only reading raw samples, but reading the wave file and verifying to make sure the wave file is of proper format needed a lot of precision.

There are 3 modes in which wave files can be read.

- File is present on disk. This is the most common usage scenario when the file is present in the disk. If filename is passed to `WaveFileReader` constructor then it uses this method.

```
	WaveFileData * file = new WaveFileData(argv[1]);	//supply filename
    file->read();
    std::vector<int16_t> samples = file->getSamples();	//return samples
```
    
    For example : `./ccaligner input.wav`
    
- Data is piped/streamed. This is helpful when the wave file is not present butis being generated. This helps in making the tool capable of fitting into pipelines.

```
	WaveFileData * file = new WaveFileData();	//will read from pipe or stream
    file->read();
    std::vector<int16_t> samples = file->getSamples();	//return samples
```
    
    For example : `ffmpeg [arguments] | ./ccaligner`
    
- Data is piped/streamed and is first stored in buffer and then processed. This is helpful when we need to ensure that we have complete data before proceeding. This too helps in making the tool capable of fitting into pipelines.

```
	//readStreamIntoBuffer is an enum decalared in read_wave_file.h
    WaveFileData * file = new WaveFileData(readStreamIntoBuffer); 
    file->read();
    std::vector<int16_t> samples = file->getSamples();  //return samples
```
    
    For example : `ffmpeg [arguments] | ./ccaligner -useBuffer`
    
The interface was modified to bring this change in place. You can try the various modes of reading in the VAD demo present in the `/demo` directory.

Though I try to document the code as I write it, there was still a way to improve it even more. I spent some time documenting the code, as well as the repository. I hope it is now even more easier to read and comprehend my code.

### How did the evaluations go?

The highlight of this week were the very first evaluations of my Google Summer of Code project. The evaluations window opened on 26th and were to remain open till 30th. Carlos (CCExtractor Org Admin, my mentor) alloted 28th as the day for my evaluations. My another mentor Alex is on his GCI trip to Google Office, SF.

This was the first time I was going to experience something like this, and no matter how much I researched or read about it, there's no telling how the evaluations are gonna proceed and what is it going to involve. It basically just bottles down to mentor slash project slash work.

So, my evaluation began on 29th past Midnight (IST), i.e. 28th Morning at my mentor's place. I must confess, I was super-nervous (which totally got reflected in my evaluations). So, Carlos sent me a DM on slack asking if I am ready for the evaluations, and I replied that I need few mins to push the final documentation that I wrote prior that day.

Within a span of 2 or 3 minutes I replied him back and the evaluation began. Carlos began by asking where can he obtain the binaries. I told him that he can compile his own (as I made sure it's buildable across all platforms) or I can send him. He chose the first option and I told him how can he compile his own binaries, which basically boiled down to clonning the repo, and using make to build the `ccaligner` executable.

Now, I had a bit different picture about evaluations then what happened next. Sure, I expected him to test the code but I expected that more time would be spent on checking how the code actually is. Meaning, I was naive enough to expect that he'll go through code file by file and see how things work, and is it good or not. I spent an awful amount of time making the code as flexible and adaptable as possible.

After building the tool, he chose a random sample from the HD he sent to us (with all the video samples), and run it against it. The tool worked as expected. But since it did not involve any audio processing (note : only approx aligner is implemented till this time in the interface), he asked me about it. I told him that the audio analysis part is being worked upon and he can try the components stored separetely (VAD) in the demo dir. He built the VAD demo and fed it the wave file obtained from the video file using FFmpeg and it gave the output in stdout with time frames and binary values - 0 for voice absent and 1 for voice present.

Then he proceeded to ask me if I have covered all the milestones I listed in my proposal and the checklist ([http://saurabhshri.github.io/gsoc/](http://saurabhshri.github.io/gsoc/)). I gave him a brief overview against all the listed tasks in checklist and assured him that I have met them all. I asked him to be brutally honest because I wanted, rather I needed to hear what my mentor thinks about it.

This is what my mentor responded :

> I expected to see a bit more to be honest, but don't be worried about it. If all the "cool previews" happen at stage 2 that's fine. Your code quality is good, blog is good, communication is good... so no problems. OK, so eval done. you passed, so just continue working 🙂

So, as you can see, though I passed my evaluations, I need to work even harder. I am happy that my mentor expects a lot from me and I hope in next evaluations I work upto his expectations.

![Official First Evaluations Result]({{site.baseurl}}/images/posts/first_evaluations_result.png)


In the official feedback, my mentor wrote : 

>Code quality is good, however it would be useful to build in a way that allow to have good demos as work progresses. Building "completely horizontally" doesn't allow to preview functionality. We're betting on things working well at the end. Love the blog.

I'll continue to improve myself and learn more, as I have learned from this evaluation. 

Thank you Carlos and Alex for being my mentor, and for passing me in the first evaluations! 😊 Let's have another fun month of some open-source goodiness.

### How about the stipend?

Ah well, looks like I was not very lucky at the stipend front 😛. Google was super-quick to release the stipend on 30th itslef. But for some reason, the payment for me got cancelled with the status _"Transfer rejected by processor."_ . Since it was weekend already, their support ass unavailable. Also, since it's US holiday on 3rd and 4th, I can only hope that their Indian support is available on Monday. I emailed them about the issue and also sent and email to the GSoC team.

Looks like they were available on Monday, as the previous transaction was totally cancelled  and a new transaction was made. I received an email that the money is sent to the bank, and shall be deposited within 4 to 5 days. Let's hope for the best! 🙂

![gsoc_stipend_payoneer.jpg]({{site.baseurl}}/images/posts/gsoc_stipend_payoneer.jpg)


### What's next?

Now I will begin working on implementing ASR in the tool. I am using CMU's Pocketsphinx as it is light, portable and has great and active community. Plus, it's in C, so should be easier to integrate it with my tool. Another possibility was to use Kaldi, but Kaldi in general is pretty resource demanding. Maybe I'll add Kaldi support post GSoC. I have already started working on using Pocketsphinx's API. I was successfully able to compile it using CMake with my tool and supply samples obtained from `read_wave_file.cpp` .

This time I might not make a very extensive task list as I made last time because this time I need to figure things on the go. I'll keep posting the updates in this very blog.

I hope other students have passed their evaluations as well and are enjoying working. Remember guys, it can be frustrating at times and there will be a lot of factors trying to make your morale down. Fight it and you'll emerge a winner. I hope I am able to do so as well. See you in the next one! 🎭