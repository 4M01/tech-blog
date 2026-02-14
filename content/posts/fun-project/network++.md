# What this extensio does?

Advanced API inspector for DevTools: edit & replay requests, JSONPath queries, GraphQL support saved collections. Essentailly Network++ is attemp to supercharge Chrome DevTools with powerful API inspection tools that developers/tester actually need.



# Why I Built This Chrome Extension:

While working on a JMeter script, instead of recording the flow using a JMeter plugin and proxy, we relied heavily on **Chrome Developer Tools** — specifically the **Network** tab — to inspect request and response details.

Whenever we needed to correlate something from a response, we had to use **JSONPath**. There’s a website, [jsonpath.com](https://jsonpath.com), where you can write JSONPath queries to extract values from a payload. The same functionality is available out of the box in JMeter.

However, the friction was real.

## The Correlation Problem

For every request we wanted to correlate, we had to:

1. Copy the response from the Network tab.
2. Paste it into jsonpath.com.
3. Write the JSONPath extraction logic.
4. Copy the JSONPath expression back into JMeter.

This repetitive process slowed down script creation significantly. I knew it was inefficient, but I hadn’t thought deeply about solving it until recently.

Over the past couple of weeks, I worked on testing features that heavily relied on server responses. Since we are using **GraphQL**, the response payloads were quite large.

Navigating through those responses to find specific values — especially when the same field appeared inside multiple nested arrays — became very difficult.

Copying 1,000+ lines of JSON, pasting it into jsonpath.com, and manually searching for specific IDs inside arrays was painful and time-consuming.

That’s when I decided to solve this problem — and that’s why I created this extension.

---

## The API Retry Problem

There was another friction point during API testing in JMeter.

When correlating values, we often needed to:

- Extract a value,
- Modify some request parameters,
- Retry the API call.

The usual workflow looked like this:

1. Copy the request as cURL.
2. Paste it into Notepad or another editor.
3. Modify headers, request body values, or endpoint paths.
4. Execute the call again.

To do this properly, we also needed valid authorization headers.

On Windows, this added extra friction because cURL is not natively supported like it is on macOS or Ubuntu. That meant either installing it manually or using a tool like Postman, which can be heavy on system resources.

Again — unnecessary friction.

---

## What This Extension Solves

This extension provides two core features:

### 1️⃣ In-Browser JSONPath Extraction
Extract values directly from responses without switching tools or copying large payloads.

### 2️⃣ Edit and Send Functionality
Modify and resend requests directly from the browser — with headers and authorization intact.

---

## The Goal

Reduce context switching.  
Eliminate unnecessary copy-paste.  
Speed up JMeter script creation and front end developement, espcailly working GraphQL
This extension is built to remove friction from API testing workflows.


You can download the extension from (here)[https://drive.google.com/file/d/1DFR5EUbu5c5inXTDmK4uB8wBOhbzXIL8/view?usp=sharing] 

## Load ZIP Chrome Extension (Unpacked) — Quick Steps

- Chrome doesn’t load .zip directly. Extract first.
- Unzip the file.
- Ensure manifest.json is at the root of the extracted folder.
- Open Chrome → `chrome://extensions/`
- Enable Developer mode (top-right).
- Click Load unpacked → select the extracted folder.

Done. Extension available as extra tab in developer tool 
