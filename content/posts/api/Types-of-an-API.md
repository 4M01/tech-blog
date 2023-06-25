---
title: "Types of An API"
date: 2020-12-26
tags: ["API","Types of an api","Rest API","API Testing"]
draft: false
author: "Amol Chavan"
socialshare: true
---
# Types of an API

   In the last [post](https://amol.blog/post/api/what-is-an-api/), we covered [what is an API](https://amol.blog/post/api/what-is-an-api/) and why we need an API. 
   
In this post, we will cover :

- [Types of an API](#types-of-an-api)
  - [Types of API based on Usage:](#types-of-api-based-on-usage)
    - [1. Libraries and frameworks as APIs](#1-libraries-and-frameworks-as-apis)
    - [2. Operating systems APIs](#2-operating-systems-apis)
    - [3. Remote APIs](#3-remote-apis)
    - [4. Web APIs](#4-web-apis)
  - [Types of API based on release policies:](#types-of-api-based-on-release-policies)
      - [Private:](#private)
      - [Partner:](#partner)
      - [Public:](#public)
  - [Difference between API, WebService \& REST API:](#difference-between-api-webservice--rest-api)
    - [Difference between API and Web Services](#difference-between-api-and-web-services)
    - [Difference between Web Services and REST APIs](#difference-between-web-services-and-rest-apis)

## Types of API based on Usage:<a name="API-Classification-Based-On-Usage"></a>
<br>
### 1. Libraries and frameworks as APIs

API for an object-oriented language, such as Java, would provide a specification of classes and its class methods. Java SDK also provides lot of API that one can use to build the applications. Selenium Library provides an API for browser automation. The API describes and prescribes the "expected behavior" (a specification) while the library is an "actual implementation" of this set of rules. A single API can have multiple implementations (or none, being abstract) in the form of different libraries that share the same programming interface.

We can import the `java.time` package to work with the date and time API. The package includes many date and time classes.

```visual-basic
import java.time.LocalDate; // import the LocalDate class

public class Main {
  public static void main(String[] args) {
    LocalDate myObj = LocalDate.now(); // Create a date object
    System.out.println(myObj); // Display the current date
  }
}
```

### 2. Operating systems APIs
An API can specify the interface between an application and the operating system. Windows OS provides COM API for WMI and for VBScript

```visual-basic
' List Physical Memory Properties

On Error Resume Next

strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colItems = objWMIService.ExecQuery _
    ("Select * from Win32_PhysicalMemoryArray")

For Each objItem in colItems
    Wscript.Echo "Description: " & objItem.Description
    Wscript.Echo "Maximum Capacity: " & objItem.MaxCapacity
    Wscript.Echo "Memory Devices: " & objItem.MemoryDevices
    Wscript.Echo "Memory Error Correction: " & objItem.MemoryErrorCorrection
Next
```

Output:

>Microsoft (R) Windows Script Host Version 5.812

>Copyright (C) Microsoft Corporation. All rights reserved.

>Description: Physical Memory Array

>Maximum Capacity: 33554432

>Memory Devices: 2

>Memory Error Correction: 3

>***** script completed - exit code: 0 *****

<center>![Windows native OS - COM-API Example](/Windows native OS COM-API Example.png)_Windows native OS - COM-API Example_</center>

### 3. Remote APIs

Remote APIs allow developers to manipulate remote resources through protocols, specific standards for communication that allow different technologies to work together, regardless of language or platform.

For example, the Java Database Connectivity API allows developers to query many different types of databases with the same set of functions.

<center>![Java Database Connectivity API](/Types-of-An-API/Java Database Connectivity API.png)_Java Database Connectivity API. Source: javaguides.com_</center>

### 4. Web APIs

A Web API is an application programming interface for either a web server or a web browser. It is a web development concept. <span style="background-color:yellow">**In a generic sense, an webservice IS a API over HTTP. They often utilize JSON or XML, but there are some other approaches as well.**</span>

<center>![Example of Web API](/Types-of-An-API/Example of Web API.png)_Example of Web API. Source: tutorialsteacher.com_</center>

<a name="API-Classification-Based-On-Release-Policies"></a>
## Types of API based on release policies:

#### Private:
The API is for internal company use only.


#### Partner:
 Only specific business partners can use the API. 
 
 **For example**, vehicle for hire companies such as Uber and Lyft allow approved third-party developers to directly order rides from within their apps. This allows the companies to exercise quality control by curating which apps have access to the API, and provides them with an additional revenue stream.

#### Public: 
The API is available for use by the public. 

**For example**, Microsoft makes the Windows API public, and Apple releases its API Cocoa, so that software can be written for their platforms. Not all public APIs are generally accessible by everybody. For example, Internet service providers like Cloudflare or Voxility, use RESTful APIs to allow customers and resellers access to their infrastructure information, DDoS stats, network performance or dashboard controls. Access to such APIs is granted either by “API tokens”, or customer status validations.
<br> 

## Difference between API, WebService & REST API:

API is overloaded term. <em>Web services, Web APIs and APIs</em> are few of those overlapping tech terms that regularly get confused. Folks used these words interchangeably, but are they even the same  thing? They are not wrong when they call it as an API but it's not precise. Let's try to understand the difference between them.

<a name="Difference-between-API-and-WebServices"></a>
### <u>Difference between API and Web Services</u>
From Stackoverflow:

> An API (Application Programming Interface) is the means by which third parties can write code that  interfaces with other code. A Web Service is a type of API, one that almost always operates over     HTTP (though some, like SOAP, can use alternate transports, like SMTP). The official W3C definition mentions that Web Services don't necessarily use HTTP, but this is almost always the case and is usually assumed unless mentioned otherwise.

> For examples of web services specifically, see [SOAP](http://en.wikipedia.org/wiki/SOAP), [REST](http://en.wikipedia.org/wiki/REST), and [XML-RPC](http://en.wikipedia.org/wiki/XML-RPC). For an example of another type of API, one written in C for use on a local machine, see the Linux Kernel API.

Basically, a webservice is a method of communication between two machines while an API is an exposed layer allowing you to program against something.

The technical definitions (courtesy of Wikipedia) are:

<b>API:</b>

>An application programming interface (API) is a set of routines, data structures, object classes and/or protocols provided by libraries and/or operating system services in order to support the building of applications.

<b>Webservice:</b>

> A Web service (also Web Service) is defined by the W3C as "a software system designed to support interoperable machine-to-machine interaction over a network"


A Web service uses only three styles of use: SOAP, REST and XML-RPC for communication whereas API may use any style for communication.

A Web service always needs a network for its operation whereas an API doesn’t need a network for its operation.
 

<a name="Difference-between-WebServices-And-REST-API"></a>
### <u>Difference between Web Services and REST APIs</u>
From Stackoverflow:

> A typical WebService will be a few methods an [WSDL](https://www.w3.org/TR/wsdl.html) that describes how to call it. There's no real convention for how these should be structured, so you always need lots of API documentation.

> Typically this will be something like (for ASP.NET):

    HTTP POST to mysite.com/products.asmx/ListAllProducts - returns XML list of products
    HTTP POST to mysite.com/products.asmx/GetProduct - returns XML for product based on SOAP XML in the posted content
    HTTP POST to mysite.com/products.asmx/UpdateProduct - changes product based on SOAP XML in the posted content

> REST is more of a convention for structuring all of your methods:

    HTTP GET from mysite.com/products - returns XML or JSON listing all products
    HTTP GET from mysite.com/products/14 - returns XML or JSON for product 14
    HTTP POST to mysite.com/products/14 - changes product 14 to what you post in the HTML form.
    HTTP DELETE to mysite.com/products/14 - removes product 14
    HTTP PUT to mysite.com/products - adds a new product

> So REST works more like you'd expect browser URLs to. In that way it's more natural and as a convention is much easier to understand. All REST APIs work in a similar way, so you don't spend as long learning the quirks of each system

Below picture will help you visualize the relationship between API, Webservice and Rest API.

<center>![API Webservice and Rest API](/Types-of-An-API/Relationship between API Webservice and Rest API.png)
_Relationship between API, Webservice and Rest API._</center>


Now, that we have covered basics of APIs, we will dig deeper in next post about Web APIs and REST APIs.

Cheers!