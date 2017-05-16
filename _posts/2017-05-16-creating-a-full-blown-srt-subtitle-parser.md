---
layout: post
published: true
mathjax: false
featured: false
comments: true
title: 'Creating a full blown (SRT) Subtitle Parser '
description: >-
  I am creating a full blown, simple yet powerful SRT subtitle parser in C++ .
  It will be the first step in my GSoC 2017 project pipeline.
categories:
  - GSoC
tags: GSoC open-source Subtitles Parser C++ SRT
---
Creating a C++ subtitle parsing library to fetch and process subtitle file easily and efficiently.

For my GSoC 2017 project, [CCAilgner - Word by Word Audio Subtitle Synchronization Tool](https://saurabhshri.github.io/2017/05/gsoc/accepted-in-google-summer-of-code-2017), the very first step required is processing of subtitle to extract primarily two things - the words those are being spoken, and time duration in which they are being spoken. 

A usual SubRip (SRT) subtile file has 4 basic components :

1. A number indicating which subtitle it is in the sequence.
2. The time that the subtitle should appear on the screen, and then disappear.
3. The subtitle itself.
4. A blank line indicating the start of a new subtitle.

All of these, of course are textual.

E.g. 

```

1
00:00:00,520 --> 00:00:03,536
Chris Anderson: Elon, hey, welcome back to TED.

2
00:00:03,560 --> 00:00:04,936
<i>(Applause)</i>

3
00:00:04,960 --> 00:00:06,536
Elon Musk: Thanks for having me.

4
00:00:06,560 --> 00:00:09,416
CA: So, in the next half hour or so,

```

Now as you can see, a subtitle file may also include some text in the text field which is not actually _spoken_ but is there to convey some information. The second subtitle is a perfect example of this. The words `(applause)` are not spoken but are present in text field. Moreover, styling tags may also be associated as they are valid in SubRip (SRT) format. The `<i> .. </i>` for example, denotes  that the line is to be displayed in italics.

My project (CCAligner), as per plan, should take two files as input - the video/audio file itself and it's  subtitle file. In order to perform alignment, the tool needs to read subtitle file and extract meaningful data in required format. This requires parsing i.e. the tool, needs to _parse_ the subtitle file and present / extract data in suitable format. In order to do so, I am creating a parser which shall perform this task for me.

All in all, the subtitle (SRT) parser must have at least following functionalities :

1. Should be written in C++ (CPP) language, as my tool will primarily be in C++.
2. Should be capable of returning starting time, ending time and actual subtitle text with simple function calls.
3. Should be able to extract and strip HTML and other styling tags (e.g. <i> hello </i> to hello).
4. Should be able to extract and strip speaker names (e.g. Elon: Hi to Hi).
5. Should be able to extract and strip non dialogue elements (e.g. (applause) to {blank}).
6. Should be easy to use and efficient in functioning.

One of the major advantages of Open-Source is, that one does not need to reinvent the wheel. :) So obviously before head-diving into writing the code I did a bit of search to see what work is already been done. There are not a lot of SRT parser I could find which were written in C++, but I found a one in which there is a base, but everything is very raw and perfect for adding onto. Obviously I wasn't expecting to find a parser exactly as per my need. [Here's](github.com/young-developer/subtitle-parser) the repository. 

I have already begun working on it. The original parser could only return starting and ending time (in ms) and subtitle text. I have modified it to be capable of performing the functionalities I listed above. The work is still raw, but I am sure it should come out great.

Right now my srt parser successfully does the following : 

1. Return timestamps in both string format and in ms.
2. Capable of strippin style tags, non dialogue data, speaker names.
3. Extract speaker names.

But there are some issues, after all I have only just begun working on it. These issues are expected to be resolved soon.

1. Style tags and non dialogue texts are stripped but not stored.
2. Only single-name speaker name is extracted, i.e. works for `Elon: Hi` but only extracts last name for `Elon Musk: Hi`. I'll add a check to extract both.
3. To convert time to ms, I am currently usin regex, which I do not like. Plus it os only available in C++ 11 and above. So, I have to write an alternative for that.

I am also planning to make this parser a single header library. After solving the above issues I'll work on that and upload it as an entirely new repository.

# Current Parse Output : 

I have implemented a lot of functions in my SRT parser,here's a demo of some of them :

```
for(SubtitleItem * element : sub)
    {
        myfile<<"start : "<<element->getStartTime()<<endl;
        myfile<<"end : "<<element->getEndTime()<<endl;
        myfile<<"text : "<<element->getText()<<endl;
        myfile<<"justDialogue : "<<element->getDialogue()<<endl;
        myfile<<"speakerCount : "<<element->getSpeakerCount()<<endl;

        if(element->getSpeakerCount())
        {
            std::vector<std::string> name = element->getSpeakerNames();
            for(std::string display : name)
                myfile<<"speakers : "<<display<<", ";
            myfile<<endl;
        }
        myfile<<"ignore : "<<element->getIgnoreStatus()<<endl;
        myfile<<"____________________________________________"<<endl<<endl;
    }
```

For the input : 

```
1
00:00:00,520 --> 00:00:03,536
Chris Anderson:
Elon, hey, welcome back to TED.

2
00:00:03,560 --> 00:00:04,936
It's great to have you here.

3
00:00:04,960 --> 00:00:06,536
Elon Musk: Thanks for having me.

4
00:00:06,560 --> 00:00:09,416
CA: So, in the next half hour or so,
```

I recieved the following output :

```
start : 520
end : 3536
text : 
Chris Anderson:
Elon, hey, welcome back to TED.


justDialogue : 
Chris 
Elon, hey, welcome back to TED.


speakerCount : 1
speakers : Anderson, 
ignore : 0
____________________________________________

start : 3560
end : 4936
text : 
It's great to have you here.


justDialogue : 
It's great to have you here.


speakerCount : 0
ignore : 0
____________________________________________

start : 4960
end : 6536
text : 
Elon Musk: Thanks for having me.


justDialogue : 
Elon Thanks for having me.


speakerCount : 1
speakers : Musk, 
ignore : 0
____________________________________________

start : 6560
end : 9416
text : 
CA: So, in the next half hour or so,


justDialogue : 
So, in the next half hour or so,


speakerCount : 1
speakers : CA, 
ignore : 0
____________________________________________
```

Looks good, right? :)

Of course there's a lot of work left. I will also spend quite a time in optimizing the performance and documenting it so that other people can also use it. 

If you guys have any suggestions for the parser, or would like to request a feature, feel free to post in the comments or mail me. I will be adding link to the repository as soon as I upload it.



