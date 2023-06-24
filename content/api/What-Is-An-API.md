---
title: "What is An API"
date: 2020-12-11
tags: ["API","What is an api","Rest API","API Testing"]
draft: false
author: "Amol Chavan"
socialshare: true
---
# What is an API?

In this post you will also understand:

1. What is an API? 
2. What are  the relatable examples of an API?
3. Why we need an API?

    

This post focuses on the general term API and not on webservices or REST API . Here is the outline of the article.
### Table of Contents
1. [An Application](#Application)
2. [An Interface](#Interface)
3. [Application Interface](#ApplicationInterface)
4. [API: Context about Programming](#APIcontext)
5. [Simple Example of an API](#SimpleExampleOfAnAPI)

## API - Application Programming Interface

You may already know the acronym of API, but do you understand all those terms?  I'll explain each term, not in the same order.

## An Application <a name="Application"></a>
- What does an application mean to you?
- What kind of picture comes to your mind while using this word?

Application is nothing but any program running [or you can run] on a computer. In turn, a program is nothing but a set of instruction given to a computer in a language that computer understand to perform some task. This is almost true and you can imagine <span style="background-color:yellow">**task manger and each processes running on a computer as an applications.**</span>

You are reading this post in a browser running on the computer or mobile [also small pc], the browser is an application.

You can divide applications into various categories depending upon the criteria. Simple classification criteria we can use whether the application is a desktop-based app [aka native app] like a browser, Microsoft paint, excel or browser-based apps like YouTube, Twitter or CITI  bank application that you use to transfer the fund.  

- In case of **Web Application**, though you are using it in a browser, you are just accessing it through the browser, the application runs on some another machine[called as a server]
- The **Desktop application** runs on your machine and you can close at any point of a time [most of] unlike a web-application which you stop using for yourself but it keeps running on the server.

<center>![Examples of Desktop Applications & Web Applications](/What-is-an-API/ExamplesOfDesktopApplicationsWebApplications.png)_Examples of Desktop Applications & Web Applications_</center>

***Examples of Desktop Applications & Web Applications***

Applications can also be divided into other categories depending on their intend and use.

1. **Efficiency**:

    <ins>Example:</ins>  Phone banking app.

2. **Communication/Collaboration:**

     <ins>Example:</ins> Whatsapp

3. **Information Distribution:**

     <ins>Example:</ins> New York post website

4. **Fun:**

     <ins>Example:</ins> Games

You can group most of the apps in one or more categories mentioned above. An application can belong to multiple groups.

<center>![Applications categories depending on their intend and use](/What-is-an-API/ApplicationsCcategoriesDependingOnTheirIntendUse.png)_Applications categories depending on their intend and use_</center>


I hope this gives you context about the term application, we will also try to group application using one more criteria in the latter part.

## An Interface <a name="Interface"></a>

let's try to understand interface as a general term, afterwards we will use it from the context of computing.

<center>![Bing Search results for term Interface](/What-is-an-API/BingSearchresultsfortermInterface.png)_Bing Search results for term Interface_</center>



<p>An interface is something with which we interact as a user.</p>


<center>![Interface Example - Electric Switch](/What-is-an-API/InterfaceExampleElectricSwitch.png)_Interface Example - Electric Switch_</center>



Everyday, we interact with electric switches which are great examples of an interface.

Essentially,  using electric switch you just close the circuit.

<center>![Example Open and Close Circuit](/What-is-an-API/ExampleOpenANDCloseCircuit.png)_Example Open and Close Circuit_</center>


1. In case of electric switch, you know how to use it.  But you don't need to understand how it works - it just gets your work done - light up the bulb.
2. Also how it is designed and implemented is up to the vendor, you have been provided with the common understanding of how to use it.
3. It can have different form and do the exact same thing or have a different form for a different objectives. In Example, image above of electric switch, You can have it for electric socket

## Application Interface <a name="ApplicationInterface"></a>

Now, let's try to understand the interface from the computing perspective. 

Earlier, we categorized applications using criteria as kind of applications(web/native) and purpose of an application.  Now, let's categorized application from perspective how end-user consumes application, how one interacts with the application:

<center>![How end user interacts with applications using GUI & CLI](/What-is-an-API/HowEndUserInteractsWithApplicationsUsingGUI&CLI.png)_How end user interacts with applications using GUI & CLI_</center>



In computing, the <span style="background-color:yellow">**Interface is something we use to exchange the information with an application**</span> or in some case libraries which may not be running until you run it. 

1. **Graphical User Interface (GUI):**

    A GUI is a system of interactive visual components for computer software. According to [wiki](https://en.wikipedia.org/wiki/Graphical_user_interface) -

    > The graphical user interface is a form of user interface that allows users to interact with electronic devices through graphical icons and audio indicator such as primary notation, instead of text-based user interfaces, typed command labels or text navigation.

    Example : Google Search. You are provided with Text Box were you type-in your query and hit on Search Button or hit/tap on Enter/Search Key. Everything is intuitive for end user and using GUI you exchange information with Application. More than 99.9% of applications are created for end user are GUI application

2. **Command Line Interface:**

    Terminal or Command prompt like applications where user exchange information through series of text command provided by application. According to [wiki](https://en.wikipedia.org/wiki/Command-line_interface) - 

    > A command-line interface (CLI) processes commands to a computer program in the form of lines of text. The program which handles the interface is called a command-line interpreter or command-line processor

    Example : [curl](https://curl.se/) - exchange of information over multiple protocol.

Application like git client does provide both GUI and CLI so that user can use any kind of exchange he/she  prefers. 

## API: Context about Programming <a name="APIcontext"></a>

All the applications created suppose to do information exchange because they are created with the at least one of the intent mentioned earlier. 

In a way, it is required to have at least one kind of interface available so information exchange happens. We went through the two kind of interfaces in previous section - GUI & CLI

Let's discuss about API now.  **APIs are developed so they will get consumed in some other program(s) as per the need. APIs, almost all the time, are never meant for end user interaction.**


From [MDN](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Introduction)

> Application Programming Interfaces (APIs) are constructs made available in programming languages to allow developers to create complex functionality more easily. They abstract more complex code away from you, providing some easier syntax to use in its place.
As a real-world example, think about the electricity supply in your house, apartment, or other dwellings. If you want to use an appliance in your house, you simply plug it into a plug socket and it works. You don't try to wire it directly into the power supply — to do so would be really inefficient and, if you are not an electrician, difficult and dangerous to attempt.

<center>![Electric Plug as an example of the API](/What-is-an-API/ElectricPlugAsAnExampleOfTheAPI.png)_Electric Plug as an example of the API_</center>
<a name="SimpleExampleOfAnAPI"></a>
### Simple example of an API for visualization 

Below diagram can be used to visualize the API in a simple way. Here one application(producer) exposing interface so that another application(consumer) can use it(consume it). 

Just like the switch shown in above diagram, its upto us which application(consumer) we want to use to consume the information. Of course, Most of the time, there will be some protocols[http], preferred programming lanauages that one need to use as consumer so they can use the API.

<center>![Electric Plug as an example of the API](/What-is-an-API/Simple-API-Example.png)_Simple API Example to visualize what is an API_</center>


## Why we need an API:

 1. API provides way to excahnge information with a program. 

    This is the sole purpose of any kind of interface be it, GUI, CLI or API.

 
 2. API provides abstraction around complex functionality.

    Example: Going to restaurant and ordering a food. You just need to convey your order to waiter and he will provide that information to chef in a kitchen. Chef will prepare your ordered dish and it can be very complex/simple dish to prepare based on your order. Once dish is prepared, waiter will serve ordered dish on your table. Just like how API works, you dont need to understand what are the ingredients required for food, how to prepare it and how much time it will take. All this information and implementation is hidden from end user.

3. API also helps in [modular programming](https://en.wikipedia.org/wiki/Modular_programming) [We will cover this as separate posts.] and API enables different programs to communicate each other.
    
    Example: Do you recall you can login on multiple web applications using your Google or Facebook credenatils? API enabled the application you were using to talk to Google and Facebook and authenticate you. 

4. API can be used to extend the functionality of existing program. 

    Example: Browser extensions. JIRA plugins.

    
Hope this helps.

Cheers!


P.S. Next follow up post in the API testing series is - [Types of an API.](http://amolchavan.space/post/api/type-of-an-api/) 