---
title: "Highlight Element in Selenium WebDriver"
date: 2017-08-29
tags: ["selenium", "How-to"]
draft: false
author: "Amol Chavan"
---

# Highlight Element in Selenium WebDriver

---

I [missed](http://amolchavan.space/post/selenium/object-repository-in-selenium-webdriver/) highlighting object feature of QTP when I used to debug my selenium API call on webelement. Number of times I wondered, why didn't by default any method is provided to perform highlight action. But I no longer wish for the same as I have found work around.

Remember this - _‘JavaScript comes in handy to perform any fancy tasks on DOM.’_

#### **Logic to perform highlight `WebElement` in Selenium WebDriver:-**

To create highlight effect, as in QTP, we don't just need to highlight the element but also have to de-emphasize/play down the same element. Highlighting element once is not enough, as the operation would be fast and we may don't realize highlighting effect. Better we break down logic as in below steps:-

1. Highlight element using javascript
2. Play-down same element using javascript
3. Perform above two actions in a loop for significant time.

Below code demonstrate use of [JavascriptExecutor](https://seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/JavascriptExecutor.html) to perform highlight element in Selenium WebDriver.

    public void highlightElement(WebElement element) {
      for (int i = 0; i < 5; i++) {
        WrapsDriver wrappedElement = (WrapsDriver) element;
        JavascriptExecutor driver = (JavascriptExecutor)
                  wrappedElement.getWrappedDriver();
        driver.executeScript("arguments[0].setAttribute('style',arguments[1]);",
                  element, "color: green; border: 5px solid green;");
        driver.executeScript("arguments[0].setAttribute('style',arguments[1]);",element, "");
      }
    }

As you can see in the above code, method highlightElement accepts WebElement as parameter and perform highlight operations for 5 seconds [i<5].

This is all for now.

Cheers!!
