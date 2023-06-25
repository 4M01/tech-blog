---
title: "Groovy Tutorial: Read JSON file in a Groovy using JSONSlurper"
date: 2020-12-04
tags: ["Groovy","JSON","JSONSlurper","API Testing"]
draft: false
author: "Amol Chavan"
socialshare: true
---
# Groovy Tutorial: Read JSON file in a Groovy using JSONSlurper
---
**TLDR** : I have also created [video](https://youtu.be/s87UbU8z6bg) around this functionality. if you are not into reading and like video, please check it out. 

After going through this post, you will understand how to convert JSON to a Groovy object using [JSONSlurper.](http://docs.groovy-lang.org/2.4.0/html/gapi/groovy/json/JsonSlurper.html)

## Why Groovy in API testing
Understanding [Groovy](https://groovy-lang.org/) is important as it is
used in different API testing clients like [JMeter](https://jmeter.apache.org/), [SoapUI](https://www.soapui.org/) and [Katalon](https://docs.katalon.com/katalon-studio/docs/create_first_api_test_katalon_studio.html#step-5-add-an-existing-request-to-a-test-case)

In API testing or in [Performance testing](https://amol.blog/tags/performance-testing/), often we have to do chaining of multiple API calls. In API chaining, we often need to extract some data or keys from the response of a previous request, manipulate it as per the requirement, and send it in the next request. 

Data manipulation is not always straight-forward, sometimes hard, tedious and error-prone and time-consuming but if we convert JSON to groovy objects it becomes easy. 

## JSON

Most of the modern-day web development frameworks rely on a JSON as a data type to send this data to the client.

Let's understand Groovy's love for a JSON. Groovy comes with integrated support for convertion between Groovy objects and JSON, unlike
other languages, Groovy don't need any third-party dependencies for convertion.
Groovy implicitly support this without any external libraries but if you use Java, you may have to use external libraries and write some specific code
for serialization and deserialization.

For Java, popular libraries are for JSON serialization & de-serialization are -

- [GSON](https://github.com/google/gson)
- [Jackson](https://github.com/FasterXML/jackson)
- [Simple Json](https://www.tutorialspoint.com/json/json_java_example.htm)

For Groovy, you just need to import a package and you are done, no need to add any library to classpath.

`groovy.json package`

With this you save lot of time, writing custom POJOs and mappers.

**Example 1: [Simple example of JSON parsing in Groovy using `JsonSlurper`, Convert text data to JSON](https://www.youtube.com/watch?v=s87UbU8z6bg&t=267s)**

```
import groovy.json.JsonSlurper
String text = '{"Message":"Hello World!","Joe":"How are you doing?"}'
JsonSlurper jsonSlurper = new JsonSlurper()
Object result = jsonSlurper.parseText(text)
println result.getClass()
```

If you [run](https://groovyconsole.appspot.com/script/5174395060355072) the above code, you will see object of type `lazylist`.

**Example 2: [Read text which has Array in a JSON Text in a Groovy](https://www.youtube.com/watch?v=s87UbU8z6bg&t=614s)**
```
import groovy.json.JsonSlurper
JsonSlurper jsonSlurper = new JsonSlurper()
String txt = '{ "myList": [4, 8, 15, 16, 23, 42] }'
Object result1 = jsonSlurper.parseText(txt)
println result1.getClass()
println (result1 instanceof List)
println (result1 instanceof Map)
```
Link to Groovy Console - https://groovyconsole.appspot.com/script/5204430337081344

It is very easy to print the all the keys of json: just like magic, [example](https://groovyconsole.appspot.com/script/5131218861424640) demonstrate different data type and native support. AND YOU CAN CREATE NULL as value for key without fuss:

**Example 4: [We can convert JSON text which has different datatypes to Groovy Object](https://www.youtube.com/watch?v=s87UbU8z6bg&t=614s)** with ease.
```
import groovy.json.JsonSlurper
JsonSlurper jsonSlurper = new JsonSlurper()
String allDataType = '''
{ "simple": 123,
"fraction": 123.66,
"exponential": 123e12,
"null":null,
"boolean":true
}'''

Object result2 = jsonSlurper.parseText(allDataType )
println (result2.keySet())
 ```

**Example 5: We can [read JSON from text file from computer in Groovy](https://www.youtube.com/watch?v=s87UbU8z6bg&t=1171s) and create object and use it in just 2 lines:**

```

import groovy.json.JsonSlurper

def inputFile = new File("D:\\yourPath\\json.txt")
def InputJSON = new JsonSlurper().parseText(inputFile.text)
InputJSON.each{ println it }
```

**Example 6: We can also read the [JSON file from network](https://www.youtube.com/watch?v=s87UbU8z6bg&t=927s) easily in a Groovy.**

```

import groovy.json.JsonSlurper

String JSON_URL = "https://api.carbonintensity.org.uk/intensity"
URL url = new URL(JSON_URL)
InputStream urlStream = null
urlStream = url.openStream()
BufferedReader reader = new BufferedReader(new InputStreamReader(urlStream))
JsonSlurper jsonSlurper = new JsonSlurper()
Object result = jsonSlurper.parse(reader)
println (result.toString())
```
Link to Grovy console - https://groovyconsole.appspot.com/script/4888845266976768


But what if JSON you are reading JOSN is not strict one (like below in example) and dont want your parser very stict about it?
```
{
        /* Information about the book */
        bookDeatils: {
            "Name": 'Harry Potter and the Prisoner of Azkaban',
            'Characters': ["Harry", "Ron", "Hermione"]
        }
         
        # Include more info about the book
        'Author': "J.K. Rowling"
    
}   
```
 Groovy has multiple type of parser that you can use. Set parser level as per your and you are done. You can easily set it to RELAX level using :

 `JsonSlurper jsonSlurper = new JsonSlurper().setType(JsonParserType.LAX);` 

To set parser level to Relax level, you need just an additional import - `import groovy.json.JsonParserType
`

**Example 7: Handling [not so proper JSON (LAX JSON)](https://www.youtube.com/watch?v=s87UbU8z6bg&t=1528s) in a Groovy**

```
import groovy.json.JsonParserType
import groovy.json.JsonSlurper

String JSON_URL = "https://gist.githubusercontent.com/4M01/44afc190ede9c7ffaee50702e75df4d7/raw/887ff0581b1e08580ff3984541d2ac59d3b01664/JsonParserTypeLAX";
URL url = new URL(JSON_URL);
InputStream urlStream = null;
urlStream = url.openStream();
BufferedReader reader = new BufferedReader(new InputStreamReader(urlStream));
JsonSlurper jsonSlurper = new JsonSlurper().setType(JsonParserType.LAX);
Object result = jsonSlurper.parse(reader);
```

I'll be writing follow up post on this about manipulation of JSON file in Groovy.
