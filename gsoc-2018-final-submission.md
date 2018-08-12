---
layout: page
permalink: /gsoc-2018-final-submission/index.html
title: Google Summer of Code, 2018 – Final Work Product Submission | CCExtractor Web - Saurabh Shrivastava
tags:
  - Google Summer of Code
  - CCExtractor Web
  - Extract Subtitles Online
  - Open Source
  - Submission
  - Saurabh
  - Shrivastava
  - GSoC
chart: true
published: true
description: >-
  CCExtractor Web : WebApp for subtitle extraction through CCExtractor. This project was a part of GSoC 2018 Under CCExtractor by Saurabh Shrivastava.
comments: true
categories:
  - GSoC
featured: true
---
<figure>
  <img src="{{ site.url }}/images/ccextractor_gsoc_2018.png" alt="CCExtractor and Google Summer of Code" style="width:35%;" >
  <figcaption>Google Summer of Code with CCExtractor Development</figcaption>
</figure>

# CCExtractor Web : WebApp for subtitle extraction through CCExtractor. 

The aim of the project is to create an easy to use web application that can be hosted on a web-server for subtitle extraction using CCExtractor. The idea is simple – the users do not need to install CCExtractor on their own machine, they can directly use the web application to process their files anytime, anywhere. It would also serve as an easy interface for first time developers (notably GSoC and GCI students) to experience the extraction process.

<figure>
  <img src="{{ site.url }}/images/usage.gif" alt="Extracting Subtitles Using CCExtractor-Web" style="width:50%;" >
  <figcaption>CCExtractor-Web (Full Video: https://youtu.be/0Qw4a0ZzVJc)</figcaption>
</figure>

The high level workflow for this project basically involves obtaining files from user along with suitable parameters, passing them to the CCExtractor , processing the files, obtaining output file and making it available for download. Other things include, but is not limited to, user management, file management, record maintenance, multiple CCExtractor binary options and API.

# Project Related Links

- Project repository on Github: https://github.com/saurabhshri/ccextractor-web

- Project readme : https://github.com/saurabhshri/ccextractor-web/blob/development/README.adoc

- Project documentation : https://github.com/saurabhshri/ccextractor-web/blob/development/docs/

- Project link on official GSoC web-app : https://summerofcode.withgoogle.com/projects/#5789900830408704

- Mentors : [@canihavesomecoffee](https://github.com/canihavesomecoffee) and [@alexbrt](https://github.com/alexbrt)

The project was built by me individually with the invaluable help from my mentors. All the external libraries and code used are credited wherever due.

# Technical Documentation

All the technical details are commented in the codes and the documentation is available in the readme of the repository (linked above). Code is properly commented and the variables, classes and other components are named properly in Camel Case for easier understanding of the code. Find compiling, installing, usage instructions and docs here : https://github.com/saurabhshri/ccextractor-web

# Known Issues and Future Work

The project is in it’s very early stage and is constantly evolving. The available functions, usage instructions et cetera are expected to refactor over time. Feel free to contribute and improve the project. Currently, files could only be uploaded from user's file system. In future I would like to add capability to add files from cloud storage like Google Drive and add batch processing. Feel free to raise any issue in the repository's issue tracker : https://github.com/saurabhshri/ccextractor-web/issues

# About Me

My name is Saurabh Shrivastava, and I am an Information Technology Engineering graduate. I love working with community to explore problems and develop solutions! At some point in the not-terribly-distant future, I hope to become a good and professional software developer. Open source has been an amazing experience for me so far, and I will continue to contribute and learn as well. Hoping to put my work and skills in good use.

Read more about me at https://saurabhshri.github.io/about or follow me on Twitter at https://twitter.com/saurabhshri_ . My Github is https://github.com/saurabhshri/ .

Thank you for taking your time out to read this. Follow the blog to subscribe to my future posts. 

-  
_Saurabh Shrivastava_  
_May The Twenty Fourth Be With You!_