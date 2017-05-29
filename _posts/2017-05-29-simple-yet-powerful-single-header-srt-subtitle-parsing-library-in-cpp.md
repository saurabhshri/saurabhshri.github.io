---
layout: post
published: true
mathjax: false
featured: true
comments: true
date: '2017-05-29 11:11:00 +0530'
title: Simple yet powerful single header srt subtitle parsing library in cpp
description: >-
  srtparser.h is a single header simple to use powerful subtitle parsing  C++
  library.
categories:
  - GSoC
tags: GSoC open-source Subtitles Parser C++ SRT
---
Srtparser.h : Simple, yet powerful single header C++ SRT Subtitle Parser Library. 💖

This is a follow-up blog post to my [previous post](https://saurabhshri.github.io/2017/05/gsoc/creating-a-full-blown-srt-subtitle-parser), where I began implementing a fully functional but simple to use subtitle parser in C++ for my [GSoC project](https://saurabhshri.github.io/2017/05/gsoc/accepted-in-google-summer-of-code-2017).

I am happy to announce that the subtitle parser is ready. **You may access it here** : https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp

I have tried my best to document it in the Github repo, and it should be fairely easy to use. But in case you have any doubt or you need any help, feel free to contact me or raise an issue in that Github repo, I will be happy to help. 😁

The parser is super easy to use and has tons of features ✨ : 

- It is a single header C++ (CPP) file, and can be easily used in any project.
- It is focused on portability, efficiency and simplicity and has no external dependency.
- Wide variety of functions at programmers' disposal to parse srt file as per need.
- Some amazing and useful capabilities such as :
	- extracting and stripping HTML and other styling tags from subtitle text.
    - extracting and stripping speaker names.
    - extracting and stripping non dialogue texts.
    - extracting words as list.
    - get time in both string and in milliseconds.
- It is super easy to extend and customize.

I could not find any other subtitle parser / parsing library which was apt for my usage and I ended up creating one myself. Hope this is helpful to other developers as well. This is definitely one of the best ones out there. Feel free to use it.

# How to use srtparser.h subtitle parser

1. Include the header file in your program.

```cpp
	#include "srtparser.h"
```
2. Create SubtitleParserFactory object. Use this factory object to create SubtitleParser object.

```cpp
    SubtitleParserFactory *subParserFactory = new SubtitleParserFactory("inputFile.srt");
    SubtitleParser *parser = subParserFactory->getParser();
```
3. Use the parser. 😉

```cpp
    std::vector<SubtitleItem*> sub = parser->getSubtitles();
    long int startTime = sub→getStartTime();
```


**Read more about the available functions in this easy to read and explanatory table** : [https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp#parser-functions](https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp#parser-functions) .

You may also checkout a demo program using this library in `example/` directory.

### Elements present in subtitle - item

Following is the list of all fields present in subtitle item :
```cpp

	long int _startTime;                    //in milliseconds
    
    long int _endTime;
    
    std::string _text;                      //actual line, as present in subtitle file
    
    long int timeMSec(std::string value);   //converts time string into ms

    int _subNo;                              //subtitle number
    
    std::string _startTimeString;           //time as in srt format
    
    std::string _endTimeString;
    
    bool _ignore;                           //should subtitle be ignore; used when the subtitle is empty after processing
    
    std::string _justDialogue;              //contains processed subtitle - stripped style, non dialogue text removal etc.
    
    int _speakerCount;                      //count of number of speakers
    
    std::vector<std::string> _speaker;      //list of speakers in a single subtitle
    
    int _nonDialogueCount;                  //count of non spoken words in a subtitle
    
    std::vector<std::string> _nonDialogue;  //list of non dialogue words, e.g. (applause)
    
    int _wordCount;                         //number of words in _justDialogue
    
    std::vector<std::string> _word;         //list of words in dialogue
    
    int _styleTagCount;                     //count of style tags in a single subtitle
    
    std::vector<std::string> _styleTag;     //list of style tags in that subtitle
    
```    

### Downloading the header file.

You may download the header file in any way desireable. 

- Simply clone the repo using 

	git clone https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp.git

- Download the zip file from 

	[https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp/archive/master.zip](https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp/archive/master.zip)

### License

srtparser.h library is licensed under MIT License (find it here). Feel free to use it in your  application. :) Happy development!

### Contribution and Feature request/ Bug

Feel free to raise an issue or make a feature request [here](https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp/issues).

Also, feel free to contribute to the project. Your help would highly be appreciated! 😀
