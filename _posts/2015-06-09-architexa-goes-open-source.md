---
layout: post
title:  "Architexa goes Open Source"
date:   2015-06-09 00:00:00 -0500
categories: projects architexa
---
The dream behind Architexa started when I was working on my PhD. I realized that as programmers, we often have to look at a lot of code. And, that if we have tools to help experienced programmers get a better view of the code (and in particular its architecture), we could save them a lot of time.

The underlying stats are shocking – coders spend 5x as much time modifying code than writing new code and 3x as much time understanding code than modifying code (more – When Understanding means Rewriting). With that, the work started first as a tool (Relo) to create box-and-arrow diagrams (like class-diagrams) using the code as a guide. It then added another tool (Strata) to guesstimate a layered-architectural-diagram using code dependencies with heuristics for breaking cycles. And, finally with Architexa we added a tool to show run time information in code using sequence diagrams.

While we added the above, we got a lot of great feedback – and even got love letters! The Architexa team grew to over 10 people, and we eventually even got some investors. However, growing the business was hard for a number of reasons, and we realized that we would not be able to build Architexa as-is into something that every developer would want to use. We really had to choose between focusing on premium work that was often framework-specific or rebuilding from scratch to have something that might not have all the benefits of Architexa but would be something that a developer could benefit from quickly.

As part of that we decided to open source Architexa. You can see the best version that we could share at: https://github.com/i3labs/architexa

Over the next little bit, I will be polishing the repository and including licensing information. The code will be licensed primarily as AGPL, and we will also work to have a more appropriate license for anyone wanting it and support towards commercial applications. Beyond this, I will be phasing out the forums (feel free to ask questions on Stack Overflow) and will look forward to any Pull Requests (especially those that align with the Roadmap).

Beyond the administrative tasks, the short term roadmap for Architexa includes adding automated tests and making it compatible with Eclipse Luna. Longer term features will depend on those that are willing to support the contributed code, but it will be great to have a stand alone version of Architexa, integration into other code editors, increased support for JVM languages and frameworks, and finally support for non-Java languages.

Let me know what you think.

