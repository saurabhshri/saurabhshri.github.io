---
layout: page
permalink: /gsoc-final-submission/index.html
title: >-
  Google Summer of Code – Final Work Product Submission | CCAligner - Saurabh
  Shrivastava
tags:
  - Google Summer of Code
  - CCAligner
  - Word by Word Audio Subtitle Synchronisation
  - Open Source
  - Submission
  - Saurabh
  - Shrivastava
  - GSoC
chart: true
published: true
description: >-
  CCAligner : Word by Word Audio Subtitle Synchronisation. My project was aimed
  at word level synchronisation  and alignment of subtitles with audio. This
  project was a part of GSoC 2017 Under CCExtractor by  Saurabh Shrivastava.
comments: true
categories:
  - GSoC
featured: true
---
<figure>
  <img src="{{ site.url }}/images/ccextractor_gsoc.png" alt="CCExtractor and Google Summer of Code" style="width:35%;" >
  <figcaption>Google Summer of Code with CCExtractor Development</figcaption>
</figure>

# CCAligner : Word by Word Audio Subtitle Synchronisation Tool and API. 

The aim of my GSoC project was to build a tool for word by word synchronisation of subtitles with audio, present in the video by tagging each individual word as it is spoken, similar to that in karaoke systems. I have named my project CCAligner as it conveniently lays out it’s basic functionality.

<figure>
  <img src="{{ site.url }}/images/ccaligner.png" alt="CCAligner CLI" style="width:35%;" >
  <figcaption>CCAligner</figcaption>
</figure>

The usual subtitle files (such as SubRips) have line by line synchronisation in them i.e. the subtitles containing the dialogue appear when the person starts talking and disappears when the dialogue finishes. This continues for the whole video. For example :

```
1274
01:55:48,484 -> 01:55:50,860
The Force is strong with this one
```

In the above example, the dialogue `#1274` - _The Force is strong with this one_ appears at `1:55:48` remains in the screen for two seconds and disappears at `1:55:50`.

CCAligner makes use of automatic speech recognition to analyse audio and recognise words to perform alignment. 

```
The           [6948484:6948500]
Force         [6948501:6948633]
is            [6948634:6948710]
strong        [6948711:6949999]
with          [6949100:6949313]
```

<figure>
  <img src="{{ site.url }}/images/karaoke.gif" alt="CCAligner Output as karaoke" style="width:35%;" >
  <figcaption>CCAligner Output as karaoke</figcaption>
</figure>

The project comprises of both user friendly tool and developer friendly API.

## Compilation

Make sure you all the dependencies are met (https://github.com/saurabhshri/CCAligner/blob/master/docs/installing_dependencies.adoc). Navigate
to `install/` directory in the project and run `./build.sh`.

Up-to-date instructions can be found at : https://github.com/saurabhshri/CCAligner/blob/master/docs

## Usage

The default output of CCAligner is stored as an XML file. For example, the next command will generate file.xml :

```
./ccaligner -wav /path/to/file.wav -srt /path/to/file.srt
```

For complete list of options and parameters, please read the docs at : https://github.com/saurabhshri/CCAligner/blob/master/docs

## Example Outputs

<div style="position:relative;height:0;padding-bottom:56.25%"><iframe src="https://www.youtube.com/embed/38_27E1PxXA?ecver=2" style="position:absolute;width:100%;height:100%;left:0;max-width:56.25rem;margin-top:0px;margin-right:auto;margin-bottom:2em;margin-left:auto;" width="640" height="360" frameborder="0" allowfullscreen></iframe></div>
<figcaption>CCAligner output as karaoke - Demo 1 : Sitcom</figcaption>

<div style="position:relative;height:0;padding-bottom:56.25%"><iframe src="https://www.youtube.com/embed/6VnhC8u_d40?ecver=2" style="position:absolute;width:100%;height:100%;left:0;max-width:56.25rem;margin-top:0px;margin-right:auto;margin-bottom:2em;margin-left:auto;" width="640" height="360" frameborder="0" allowfullscreen></iframe></div>
<figcaption>CCAligner output as karaoke - Demo 2 : Ted Talk</figcaption>

<div style="position:relative;height:0;padding-bottom:56.25%"><iframe src="https://www.youtube.com/embed/j_zeixo-zJY?ecver=2" style="position:absolute;width:100%;height:100%;left:0;max-width:56.25rem;margin-top:0px;margin-right:auto;margin-bottom:2em;margin-left:auto;" width="640" height="360" frameborder="0" allowfullscreen></iframe></div>
<figcaption>CCAligner output as karaoke - Demo 3 : Cartoon Show</figcaption>

<div style="position:relative;height:0;padding-bottom:56.25%"><iframe src="https://www.youtube.com/embed/8tTDX6NZGsU?ecver=2" style="position:absolute;width:100%;height:100%;left:0;max-width:56.25rem;margin-top:0px;margin-right:auto;margin-bottom:2em;margin-left:auto;" width="640" height="360" frameborder="0" allowfullscreen></iframe></div>
<figcaption>CCAligner output as karaoke - Demo 4 : Discussion Video</figcaption>

<div style="position:relative;height:0;padding-bottom:56.25%"><iframe src="https://www.youtube.com/embed/tFrf0TVnqIQ?ecver=2" style="position:absolute;width:100%;height:100%;left:0;max-width:56.25rem;margin-top:0px;margin-right:auto;margin-bottom:2em;margin-left:auto;" width="640" height="360" frameborder="0" allowfullscreen></iframe></div>
<figcaption>CCAligner Video Transcription Demo : Reality Show</figcaption>

<div style="position:relative;height:0;padding-bottom:56.25%"><iframe src="https://www.youtube.com/embed/km1iHe_mGuo?ecver=2" style="position:absolute;width:100%;height:100%;left:0;max-width:56.25rem;margin-top:0px;margin-right:auto;margin-bottom:2em;margin-left:auto;" width="640" height="360" frameborder="0" allowfullscreen></iframe></div>
<figcaption>Approximate Word by Word Audio Subtitle Synchronization</figcaption>

## Project Related Links

- Project repository on Github: [https://github.com/saurabhshri/CCAligner](https://github.com/saurabhshri/CCAligner)

- Project readme : [https://github.com/saurabhshri/CCAligner/blob/master/README.adoc](https://github.com/saurabhshri/CCAligner/blob/master/README.adoc)

- Project documentation : [https://github.com/saurabhshri/CCAligner/blob/master/docs/](https://github.com/saurabhshri/CCAligner/blob/master/docs/)

- My blog (includes weekly GSoC posts) : [https://saurabhshri.github.io](https://saurabhshri.github.io)

- Milestones and deliverable checklist : [https://saurabhshri.github.io/gsoc/](https://saurabhshri.github.io/gsoc/)

- Project link on official GSoC web-app : [https://summerofcode.withgoogle.com/projects/#5589068587991040](https://summerofcode.withgoogle.com/projects/#5589068587991040)

- Project proposal : [https://github.com/saurabhshri/saurabhshri.github.io/blob/master/GSoC/](https://github.com/saurabhshri/saurabhshri.github.io/blob/master/GSoC/)

- Mentors : [@cfsmp3](https://github.com/cfsmp3) and [@AlexBratosin2001](https://github.com/AlexBratosin2001)

The project was built by me individually. All the external libraries and code used are credited wherever due.

## Technical Documentation

All the technical details are commented in the codes and the documentation is available in the readme of the repository (linked above). Code is properly commented and the variables, classes and other components are named properly in Camel Case for easier understanding of the code. Find compiling, installing, usage instructions and docs here :

```
https://github.com/saurabhshri/CCAligner/blob/master/docs/
```

## Additional Work

In addition to my main project, I also worked on creating a single header SubRip subtitle parser library in C++ and contributing to various open source projects, including, but not limited to CCExtractor, Sample-Platform, AutoEdit2, Rhubarb Lip Sync, CMUSphinx.

1. Created a single header SubRip subtitle parser library in C++. This served as a core in CCAligner subtitle handling. It has very huge number of options available, and is very simple to use.

    - Project repository : [https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp](https://github.com/saurabhshri/simple-yet-powerful-srt-subtitle-parser-cpp)
    - Documentation : [https://github.com/saurabhshri/CCAligner/tree/master/docs](https://github.com/saurabhshri/CCAligner/tree/master/docs)

2. Improving existing CCExtractor features, fixing issues and help in PR and code reviews.

    - All my commits to CCExtractor repository : [https://github.com/CCExtractor/ccextractor/commits?author=saurabhshri](https://github.com/CCExtractor/ccextractor/commits?author=saurabhshri)

3. Improving CCExtractor's sample-platform, fixing and reporting issues, and help in PR and code reviews.

    - All my commits to Sample-Platform repository : [https://github.com/canihavesomecoffee/sample-platform/commits?author=saurabhshri](https://github.com/canihavesomecoffee/sample-platform/commits?author=saurabhshri)

4. Link to my Github profile : [https://github.com/saurabhshri/](https://github.com/saurabhshri/)

## Known Issues and Future Work

The project is in it’s very early stage and is constantly evolving. The available functions, usage instructions et cetera are expected to refactor over time. Feel free to contribute and improve the project. Currently, officially only US English is supported. For other languages and accents, a properly trained acoustic model could be supplied and experimented with. Text tokenisation within the program needs improvement. Feel free to raise any issue in the repository's issue tracker : [https://github.com/saurabhshri/ccaligner/issues](https://github.com/saurabhshri/ccaligner/issues)

## My GSoC Experience

My GSoC experience has been surreal! When I look back at "few months ago" myself and compare it with today me, the difference is HUGE, and in a good way. All thanks to GSoC. Not only has GSoC helped me grow as a developer, but it has also taught me how to work in community, do research, ask for advices, help people, get help from other people, communicate effectively and much more! Many thanks to Google Open Source Office for organising this programme! 😊

I am also super lucky to be a part of CCExtractor organisation. They are extremely humble and modest. The amount of caring and kindness in the community is unbelievable! CCExtractor people are awesome! I have literally zero issues and a million reasons to be happy with. Alex is super-supportive and always encouraging. I feel so honoured, and I am also very proud of him. Willem's awesome to work with. He was the first person I had an actual interaction with, and I love working with him. Even now I try to help him and have fun with Sample Platform. Carlos is the boss! 😎 He seems busy, but is always there to help. The level of trust he drenches upon me is the biggest motivation ever. I have good time working on problems with Evgeny, he's really good with Algorithms. So, so happy to be the part of the family!

Also, huge thanks to [Nickolay Shmyrev](https://github.com/nshmyrev) from CMUSphinx who was always there to answer queries and questions! 😊  

Biggest thanks go to my parents, without whom the completion of project couldn't have been possible. Thanks for so many blessing and care! 🤗

## Read More

More information and news related to project could be found at the links attached above and would be posted from time to time on my blog : [https://saurabhshri.github.io](https://saurabhshri.github.io)

## About Me

My name is Saurabh Shrivastava, and I am a final year Information Technology engineering undergrad. I love working with community to explore problems and develop solutions! At some point in the not-terribly-distant future, I hope to become a good and professional software developer. Open source has been an amazing experience for me so far, and I will continue to contribute and learn as well. Hoping to put my work and skills in good use.

Read more about me at [https://saurabhshri.github.io/about](https://saurabhshri.github.io/about) or follow me on Twitter at [https:twitter.com/saurabhshri_](https:twitter.com/saurabhshri_)

Thank you for taking your time out to read this. Follow the blog to subscribe to my future posts. 

-  
_Saurabh Shrivastava_  
_May The Twenty Fourth Be With You!_
