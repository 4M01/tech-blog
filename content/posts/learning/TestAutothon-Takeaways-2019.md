---
title: "Takeaways from Autothon 2019"
date: 2019-10-08
tags: ["TestAutothon"]
draft: false
author: "Amol Chavan"
---

# Takeaways from Autothon 2019.

---

Every year, from last few years, Step-in Forum organizes a dedicated conference in Pune about the upcoming trends in Software Testing where industry leaders talk about their experiences that can help a software testing community. As part of this event, one day is dedicated to [TestAutoThon](https://testautothon.org/). This year we aced the competition and with this post, I'm trying to reflect on things that helped us.

Just to clarify, the problem statement was given on the same day at the same time to all participant teams and it was expected to be solved in 4 hours.

Here is the list of my takeaways :

1. Failure teaches us more than success.
2. Winners are not always smartest people in the room but they are better prepared.
3. In any "team" collaboration and trust is more important than just a technical aspect.
4. Mobile Automation Setup for Appium is hard for a beginner.
5. Be prepared for more.

I'm trying to keep post small but I'll write about some learning as entire new posts.

## 1. Failure teaches us more than success.

We also participated in the last edition of TestAutoThon In Pune but we were not able to do justice to our talent. What was hard for us to understand what really went wrong and how we could have avoided being in a state that we were in. Once it was clear that we were going to participate in this edition as well, we sat for some time to retrospect and find out a better plan. Here is the image of our last year takeaways which are not verbose and may not make sense out of context:

![Not-To-Do List](/Takeaways-Autothon-2019/Not-To-Do List.png)_Not-To-Do List_

This list seems very shallow now, just like an autopsy of any other failure. This approach did not help us right away but it sets us on the right track.

> 👉 Failure won't give any magical formula for success, it will give a list of things not to do.

## 2. Winners are not always smartest people in the room but they are better prepared.

Once we were ready with our **NOT to-do list**, we had regular weekly meeting as a team to decide the direction both from a technical perspective and from a collaboration perspective. We knew as none of us has worked with Appium for longer/significant tenure, we knew the risk involved. We set a new goal to understand the basics of the tool. This helped us in preparation for the battle. We were confident, as everyone in a team was able to invoke mobile app, a desktop browser without an issue on their machine. Thus we tried to minimize the unknown at D-day. When we interacted with other teams during competition, we got to meet many smart folks.

> 👉 Be prepared for the knowns, it will help you to minimize the unknowns.

## 3. In any "team" collaboration and trust is more important than just a technical aspect.

I was lucky to work with Pratik, Sachin, Jyoti and Bharat. As a team, we were sure each one of us can solve complex test automation problem but the question was as a team can we solve the problem within a given interval. We practiced collaboration and trusted each other that they would complete the subtask assigned to them without a doubt. We also practiced asking for help. I guess this set up us for success.

> 👉 The team need to practice to behave like a team. Collaboration and trust won't come out of the blue.

## 4. Mobile Automation Setup for Appium is hard for a beginner.

There I said it. Even if you are a seasonal QA engineer and expect to set up mobile automation checks with Appium, its very unlikely that you will able invoke the app in one go. You will face some problems and you will learn the setup hard way. So even if you are good at problem-solving and expect that you will make sure everything work without fuss in less time, I'm warning you.

Here is an example, if you happen to invoke native app on android then you need to set `appActivity` and `appPackage` in `[Capability](http://appium.io/docs/en/writing-running-appium/caps/)` of an app(AUT). That means you need to know the basics of [adb](https://developer.android.com/studio/command-line/adb) so you can find the required details. So you have to do googling which may take time to find the required details. Anyway short answer I found out is -

Package Name / Activity Name

Get Activity Name and Package: `dumpsys window windows | grep -E <app name>`

Package Name / Activity Name for Youtube app :​

![adb-get-android-package-name-main-activity-name](/Takeaways-Autothon-2019/adb-get-android-package-name-main-activity-name.png)_adb-get-android-package-name-main-activity-name_

> 👉 Assumptions are dangerous, just like having an assumption while testing of an application, we need to test assumption about our skills and problem-solving abilities beforehand. Do the risk analysis.

## 5. Be prepared for more

We were prepared for solving the problem and we solved it in a stipulated amount of time, that's great. In the final presentation, we have to face two tough questions:

1. What is 'X-factor' of your team?
2. What changes or modification you will do if you been granted 8 more hours?

We answered those questions, the best we could.

> 👉 Presentation means you are trying to sell something, be prepared for more, Have a roadmap ready for your customer/ stakeholders because you are answerable to them.

![Testaholic-Team](/Takeaways-Autothon-2019/Testaholic-Team.jpg)_Testaholic Team (from L-R) : - Bharat, Sachin, Amol, Pratik and Jyoti_

Of course, this win could not have been possible without our amazing mentors- Prakash and Malayaj.

P.S. : Opinions expressed are solely my own and do not express the views of my team mates.
