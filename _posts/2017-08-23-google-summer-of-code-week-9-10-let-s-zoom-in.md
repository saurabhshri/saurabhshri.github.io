---
layout: post
published: true
mathjax: false
featured: false
comments: true
title: 'Google Summer of Code, Week 9 & 10 : Let''s Zoom In! '
description: This post covers the work done in week 9 and 10 of Google Summer of Code 2017.
categories:
  - GSoC
tags: gsoc open-source subtitles weekly-updates evaluations
---
Almost two weeks have passed since the second evaluations and my last blog post. This blog post lays down the summary of work I’ve done in past two weeks.

> The task checklist with deliverables is located here : [https://saurabhshri.github.io/gsoc/](https://saurabhshri.github.io/gsoc/) . 

The major work during these two weeks were to implement phoneme recognition. This involved generating phonetic language model with the help of corpus. The challenging task here was to convert text corpus into phonetic corpus.

```
<s> princeton </s>
<s> a fine institution </s>


IL P R IH N S IY T AH N SIL
SIL AH F AY N IH N S T AY T UW SH AH N SIL
```

While creating dictionary, I am using seq2seq to generate the phonemes from words which is trained on CMUDict. But this process is extremely slow and prooved not fesiable for large corpus. So, the alternative was to use fixed sets of rules to perform the conversion. Of course this isn't going to be as accurate as the one generated from seq2seq, but since this corpus's primary aim is to generate language model, it was the way to go. 

Thankfully, these rules were compiled into C++ rules by [Daniel S. Wolf](github.com/DanielSWolf/) in his project [Rhubarb Lip Sync](github.com/DanielSWolf/rhubarb-lip-sync), and I modified it's G2P file to perfrom corpus to phonetic corpus conversion. 

On the left are the result of the tool that uses tensorflow to learn the rules using a dictionary (very slow) and on the right are the results obtained using the script I made which follows the rules I found above.

> america     |     AH M EH R AH K AH       |     AE M EY R AY K AE
> hypocrit    |     HH IH P IH K R IH T     |     HH AY P AA K R IH T
> trump       |     T R AH M P              |     T R AH M P
> saurabh     |     S AO R AE B             |     S OW R AE B HH

This corpus is then used to generate phonetic language model which is fed to phonetic decoder to perform phoneme recognition. Performing phoneme recognition slows down the process relatively as it adds an extra cost to compute those terms.

I also encountered an interesting bug during this. If the corpus contained dual whitespaces, the language model generated was in corrupt form. But the error was not properly reported by SphinxBase and upon reporting, a fix was pushed for the same.

I then proceeded to add deep level logging throughout the program which should aid in debugging. The logging is implemented through a variadic function which is invoked through a defined macro. Similarly, I implemented a function and macro for handling cases for fatal cases with defined error codes. These can be found in `/src/lib_ccaligner/commons.h`.

```
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 249 | Wave File chunkID verification successful
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 253 | Begin decoding wave file
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 108 | File format is identified as WAV
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 115 | Finding FMT and DATA subchunks
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 130 | FMT index : 12 , DATA index :70
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 153 | PCM : True
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 162 | MONO : True
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 171 | Sample Rate 16KHz : True
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 184 | BitRate 16 bits/sec : True
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 202 | Number of samples : 34543104
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 203 | Reading samples
[INFO] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/read_wav_file.cpp : 257 | File decoded successfully
```

and

```
[ERROR] /Users/saurabhshri/Desktop/try/ccaligner/src/lib_ccaligner/params.cpp : 127 
		 -oFormat requires a valid output format!
```

In the following weeks I'll implement the unified output handler for all possible situtations -  continuous mode, complete mode or transcribing mode. I'll also remove deprecated code, organise and refactor the remaining code while completing the documentation. Memory leak fixes, further optimisation et cetera shall also be done next week.

Hoping everyone's having fun! See you in the next one! 🙏🏻