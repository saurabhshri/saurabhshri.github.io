---
layout: post
published: true
mathjax: false
featured: false
comments: true
title: 'Google Summer of Code : Mid Term Evaluations!✍️ ’
description: >-
  Here I talk about how my mid term evaluation went, and what I am planning
  ahead.
categories:
  - GSoC
tags: gsoc open-source subtitles weekly-updates evaluations
---
With the ending of eight week of Google Summer of Code, second phase of conding is almost complete. This meant that it's time for mid term evaluations, which would judge whether I will be continuing the program or fail. 

> I successfuly passed my mid term evaluations, thankfully, leaving my mentors happy with my work. Though initially I hit a bump, but later on, I passed with flying colours. 😊

This was the last week of second phase of coding period. In the previous 4 weeks I began full blown ASR work and integrated it with the work built during the first phase. That involved couple of things like using PocketSphinx to perform speech recognition, generating language model, grammars, dictionaries et cetera from the subtitles followed by actually performing alignement using fuzzy comparision and window based search. The fourth week was reserved as buffer week to meet the missed milestones, complete the documentation and all the remaining things. By the end of second phase, I met the following deliverables : 

- [x] Word recognition and timed transcription.
- [x] Tuned language models and dictionaries.
- [x] Adaptation script and implementation for custom models and dictionaries based on subtitles.
- [x] Exporting result with colored identification of recognised/ non recognised words. (Just for demonstration purpose)

When we began evaluation, with the first sample, output of ccaligner was mostly rubbish with no relevance to the actual subtitles. The sample was from one the daily soap operas. Turns out that the subtitle etracted from that vides were roll-up subtitles and had delayed timing, resulting in different recognition then expected, as the expected format is a SubRip.

Next we tried another sample from the same genere, and this time, the program kind of froze. It kept on trying to understand the utterance, but kept failing. After debugging, I found out that the subtitle had some emojis in it, which wern't being handled correctly. This resulted in corrupted grammar and language model leading to the freeze. It was a rather quick fix, but Carlos ultimately decide to shift the _actual_ evaluation later, so that I can do a bit more testing. Wise decision, as I found out that when the audio had no speech as opposed to the indictaion present in subtitle and flase positive from VAD, the decoder crashed.

After handling non ASCII characters and fixing the crash, I added the transcribe option in which the decoder does the alignment irrespective of subtitle timings. It still uses subtitle file to create language model, but marks the utterances on it's own and gives word by word timed transcription along with confidence score.

Two days later, at night, I found out that Carlos is free and we _re-attempted_ the evaluations. This time it worked flawlessly and I think I met all his expectations! 😊 He was happy with the output, and 
he proceeded to tell me that I passed, and said, that I did a good job! I was very happy to hear this after hitting that bump before, and kind of not meeting his expectations in the first evaluations.

Few days later I received the official email from Google Open Source Office, declaring me passed in the mid term evaluations. In the official feedback he mentioned about completing documentation as well and giving credits everywhere (which, I thankfully did throughout)!

> Looks like the hardest parts are done and working reasonably well. Important missing thing is documentation (good one, both technical and informative). Your blogs are well written though so I don't think this is going to be a problem. When you document, remember to mention all dependencies, too. Also if code was taken from any other project, give credit.

Here's the screenshot of the same : 

![mid_term_evaluation_gsoc2017.png]({{site.baseurl}}/images/posts/mid_term_evaluation_gsoc2017.png)

I’ll continue to improve myself and learn more, as I have learned from this evaluation.

Thank you Carlos and Alex for being my mentor, and for passing me in the second evaluations! 😊 

### What’s next?

Now I will begin working on implementing phoneme recognition in the tool. This involves using phoneme decoder, generating phonetic language model and implementing it in CCAligner. This will be followed by all sorts of refining and handling output. Logging, error handling, external documentation shall be of utmost importance as well. The next month will be super busy as it's high time in college too.

I hope other students have passed their evaluations as well and are enjoying working. I can not express how amazing the experience has been so far. It's almost surreal. Hope to complete the project within the timeline. See you in the next one! 🍀


