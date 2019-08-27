---
layout: post
title:  "Getting Inputs for your Voice App"
image:  "/assets/uploads/2017/11/violet.png"
date:   2019-03-09 00:00:00 -0500
categories: Voice
author: Vineet Sinha
---
<img src="/assets/uploads/2017/11/violet.png" alt="violet" width="100"/>

You have built a Voice App and it works well. You needed to use voice to expose data that you already had. It took a few iterations, but now users are happy with it. Your next challenge is needing to having your Voice App get data from the user.

If you are using the [Violet](https://helloviolet.ai/) framework then collecting data from users should not be hard. If you need an intro to Violet, see the article on [Building a Voice App in 30 minutes]({% post_url 2019-02-02-building-a-voice-app-in-30-minutes %}). We will build on top of that article here.<!--more-->


## Getting a Single Input from Users

The easiest way to get input from your users is in getting a single value during a conversation. Lets say that you wanted to allow:

> User: What game nights have already been planned for **Friday**?  
> App: Let me see.  
> App: There are no game nights planned for **Friday**. Would you like to add one?  
> User: No.

To build this out, we will need to first tell the framework that we need to accept an input of type `date`.

```javascript
violet.addInputTypes({
  "plannedDayQuery": "date"
});
```

In this case, we are calling the parameter `plannedDayQuery`, and once we have declared it to the framework we can use it anywhere in our conversations.

Building out the above conversation examples gives us the following conversation flow:

```html
<!-- -->
<choice>
  <expecting>What game nights have already been planned for
                [[plannedDayQuery]]?</expecting>
  <say>Let me see.</say>
  <resolve value="app.getGameNightsForDate(response)"/>
</choice>
<!-- -->
```

With the app logic looking something like:

```javascript
var app = {
  // ...
  getGameNightsForDate: (response)=>{
    var dateToQuery = response.get('plannedDayQuery');
    // ,,,
  }
}
```

## Custom Types

Often one of the predefined types do not work for us. In such situations we can define a custom type. For example, if we wanted to only accept a week day, we could do somehting like:

```javascript
violet.addInputTypes({
  "plannedDayQuery": {
    type: "dayOfWeekType",
    values: ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"]
  },
  // ...
});
```

## Thinking about Multiple Inputs

We are now able to get a single input from the user. The big challenge in collecting data however if that we often need multiple inputs from the user for a task - you know where we use Form's in web and mobile apps.

We can definitely do this by having nested `decision` elements, with each having an `ask` and one or more `expecting` elements. However, this does get a little verbose.

In the Voice world, support for these Voice Forms, is provided by what is often referred to as 'muli-turn conversations' or 'dialogs'.

You can do this in Violet by crating a `dialog` element consisting of multiple `item` that can to be provided by the user. Items are unique in that like decisions they consist of an `ask` element to prompt the user, as well as similar to choices they consist of in that they consist of an `expecting` element that defines what the user can say. The dialog prompts users based on the items returned by the `elicit` attribute, and the provided `dialog.nextReqdParam()` implements requesting all the items that have been tagged as `required`.

## Designing our Voice Form

So lets get back to adding data to our Game Night App. We likely want to see something like:

> User: I'm looking to organize a game night.  
> App: What day would you like it to be on?  
> User: I'd like it to be this Thursday.  
> App: How long would you like it to be?  
> User: 3 hours.  
> App: What would you like the main game to be?  
> User: Chess.  
> App: Do you want snacks, lunch, or dinner?  
> User: Dinner.  
> App: Let me see what I can do.
> App: Great, you are all set.

In the above the day, the duration, the game, and the food would be items. Creating a conversation flow from the above, we get:

```html
<app>
  <!-- ... -->
  <dialog id="create" elicit="dialog.nextReqdParam()">
      <expecting>I'm looking to organize a game night</expecting>
      <item name="day" required>
        <ask>What day would you like it to be on?</ask>
        <expecting>I'd like it to be this [[day]]</expecting>
      </item>
      <item name="duration" required>
        <ask>How long would you like it to be?</ask>
        <expecting>[[duration]] hours</expecting>
      </item>
      <item name="game" required>
        <ask>What would you like the main game to be</ask>
        <expecting>[[game]]</expecting>
      </item>
      <item name="food" required>
        <ask>Do you want snacks, lunch or dinner?</ask>
        <expecting>[[food]]</expecting>
      </item>
      <say>Let me see what I can do.</say>
      <resolve value="app.createGameNight(response)">
        <say>Great, you are all set</say>
      </resolve>
    </dialog>
</app>
```

Now, all we need to do is implement `createGameNight`. A simple implementation looks like:

```javascript
// ...
var app = {
  // ...
  createGameNight: (response)=>{
      var dt = calcDateInFuture(response.get('day'),
                                response.get('time'));

      model.futureGameNights.push({
        startTime: dt,
        duration: parseInt(response.get('duration')),
        game: response.get('game'),
        food: response.get('food')
      });

    }
}
```

## Onwards

Hope you found this helpful. I will love to hear ([@VineetSinha](https://twitter.com/VineetSinha)) what you build and how it goes. Feel free to reach out if you are stuck.

If you are looking for a version of this article for the Salesfore platform - there is trailhead Quick Start on [Violet](https://trailhead.salesforce.com/en/content/learn/projects/quickstart-violet).

See the code for this project here: [gameNight.js](https://github.com/vineet-sinha/violet-trailhead/blob/master/gameNight.js)

**Updated:** 22nd Aug - minor details to align with the Violet 1.0 release.
