---
layout: post
title:  "One year of learning from others about their experiences"
date:   2018-10-01 00:00:00 -0500
categories: Projects Voice
---
<img src="/assets/uploads/2017/11/violet.png" alt="violet" width="100"/>

The last year has been a fun ride. Since we open-sourced and started talking about the ideas behind Violet we have been able to learn lessons from the experiences of how some of the best Voice Apps have been built.

Not only have we built these into Violet, but we have also been talking about them at different places.<!--more-->

## A Conversational Flow Language & the VOICE Summit

We learned that the temporal nature of voice and users earlier familiarity with speech means that getting the User Experience right in the Voice world is far harder than in a Mobile or Web world.

Not only do teams need to spend time designing a good voice conversation, but they also need to iterate on the voice scripts once they have it implemented. This iteration can often be hard because of the large amount of state-management code in most Voice Apps.

We noticed that Voice Apps essentially consisted of one of a few 'user-experience design patterns'. These design patterns resulted in us defining an HTML-inspired [Conversational Flow Language](https://helloviolet.ai/docs/conversation-flow-design) (and added support for it into Violet).


## Improved Developer Focus & support beyond Alexa

As we learned of the need to better support Conversation Design, we also realized that most Voice Apps need a significant amount of business logic. We also realized that the code behind a voice app could easily become intertwined and that it would be helpful to allow developers to separate the Conversation Design from the Business Logic.

We have updated Violet's API's to help make such separation of concerns easier. Also, as we received feedback from developers we have improved API documentation as well as now we have a tutorial for [building Voice Apps using the Salesforce API](https://trailhead.salesforce.com/en/content/learn/projects/quickstart-violet).

As we received requests for conversations running on more devices, we added support for Google Dialogflow. This has allowed us to build actions for Google Home as well as provide voice conversations on mobile devices.


## Sharing Learnings

I shared a number of our learnings, in particular on the User Experience side of things at the [VOICE Summit](https://www.voicesummit.ai/) this year. You can find the [slides](https://www.slideshare.net/vineet-sinha/buil ding-great-voice-experiences) as well as see a [video](https://www.youtube.com/watch?v=14L08pg8aK8) of the presentation.

I also presented at Dreamforce again this year in a session focused on helping developers build voice skills on Violet. You can see a [video](https://www.salesforce.com/video/3579625/) of the presentation.

I am going to be sharing more of these lessons here in the upcoming months.

## Thanks!

The learning this year for all of us would not have been possible without the collaboration of a number of people. In particular, I want to thank [Mitchell Harris](https://www.linkedin.com/in/mitchell-harris-6b44b923/) at the [RAIN Agency](https://rain.agency/), [Steve Tingris](https://www.linkedin.com/in/tingiris/) at [Dabble Lab](https://dabblelab.com/), and [Diana Deibel](https://www.linkedin.com/in/diana-deibel-8454b64/) at [Grand Studio](http://grandstudio.com/) for collaborating on these ideas.
