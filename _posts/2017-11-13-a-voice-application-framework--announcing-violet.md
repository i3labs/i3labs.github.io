---
layout: post
title:  "A Voice Application Framework: Announcing Violet"
image:  "/assets/uploads/2017/11/violet.png"
date:   2017-11-13 00:00:00 -0500
categories: Projects Voice Development
author: Vineet Sinha
---
<img src="/assets/uploads/2017/11/violet.png" alt="violet" width="100"/>

For the greater part of this last year, I have had the pleasure of building a lot of Voice prototypes. These have included Alexa skills, actions for Google Home, as well as building standalone devices (powered by AVS) with custom wake-words and voices.

When building such Voice Apps/Skills, I quickly noticed the need for programming with a fairly powerful yet low-level platform-specific API's. It reminded me of the first Web apps that I built, where we needed to program to the different DOM API of Netscape Navigator and Internet Explorer. <!--more-->

The amount of technology behind smart speakers is incredible. On top of that, Amazon and Google have not only been able to simplify that power in building devices for our homes - Amazon Echo and Google Home respectively - but have also been able to build API for developers to build Skills that run on them.

These Skills, unfortunately, do require developers to track where a conversation is for every single user. Doing this makes it hard for developers to focus on the actual conversation use-case, the script design, and the business logic to support the skill.

[Violet](https://helloviolet.ai/) is an Open-Source Node.js based framework that focused on helping developers build Voice Apps. It started as a reusable-library for prototypes that I have been building and after over a dozen iterations it has become something that others have found helpful.

Violet is built on the [alexa-app](https://www.npmjs.com/package/alexa-app) package. It makes it easy to build and test conversations locally. It has primitives to automate state-management of conversations using the  goals backed by a per-user stack. It also includes a plugin framework with plugins to access various parts such as data access to PostgreSQL and Salesforce.

We were excited to talk about it at Dreamforce this week. And we were fortunate to get some really good feedback. We would love to hear about your thoughts. In particular, how can a framework help you build great Voice Apps? Are there common aspects that you have found when building a Voice App that you would like to see in an App Framework like Violet?
