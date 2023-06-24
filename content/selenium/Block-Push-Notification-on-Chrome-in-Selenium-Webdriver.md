---
title: "Block Push Notification on Chrome in Selenium Webdriver"
date: 2016-06-23
tags: ["Selenium", "How-to"]
draft: false
author: "Amol Chavan"
---

# Block Push Notification on Chrome in Selenium Webdriver

---

Many of you might already know that Chrome browser supports push notification almost on all platforms from version [42](https://developers.google.com/web/updates/2015/03/push-notifications-on-the-open-web?hl=en) and many sites including Facebook and Google+ have already started delivering push notification for end users. So when it comes to automating such sites/apps first thing that you notice is browser asking permission to deliver push notification.

![Facebook asking to allow permission to show Notifications](https://lh3.googleusercontent.com/IVt4JDjdHn6VU-M_I4x-40BaVmcK8upDfgJfJApnEr9l4qCPR5HGdwBXcKs1suENuIH3d0dH4phPzSOADJCBfM7PnmjLhOyduzIZhNa9kWxDQieaSRlqUmGnQ1LixUFuODZpC_DW)_Facebook asking to allow permission to show Notifications_

**Problem Statement:-**

As you can observe in above image that it would be impossible to perform immediate next action in browser after login as it’s been blacked-out. Chrome driver will wait for sometime (implicit wait) and then try to perform next step in browser, whatever it may be, it will fail and if you missed the step in execution which might cause failure of next step and result would be failed test/test suite.

Also push notification badges are not getting displayed as part of web document, so clicking on those button displayed is not possible through selenium.

Workaround - when you Not to Block Push Notification on Chrome in Selenium Webdriver:-

Simple thing to do, is find body element of page [which exist for all the pages :-) ], and perform double click on it. But as mentioned, it would be just workaround.

```java
public void doDoubleClick(){
    WebElement body = driver.findElement(By.tagName("body"));
    Actions actions= new Actions(driver).doubleClick(body);
    actions.build().perform();
}
```

Perform double click on page to get the page back from blacked-out state when notification poped-up.

### **Better Approach:- How to** Block Push Notification on Chrome in Selenium Webdriver

What you would have done if you have to do same thing again and again manually in this case? Consider testing ten different app and login scenarios for them. Any sane person would have searched for [how to do the same manually](https://support.google.com/chrome/answer/3220216?hl=en).

![](https://lh3.googleusercontent.com/8UuffqvZBS24ZtwgNG1WU0DlCli8_5ZNHPLSe9-qQ8s4uuD4mJ0FpEFNGcjoD-gNZo8gS4l46MA0tCPNir5CSrDkjcgoMoeKNPtviiddtArH-6iSk91yXYIemR1l_hQ_qMAJ8TCM)

Manually disable/block Push Notification in Chrome

Whatever you would have done manually, would it be possible to set this up while invoking chromedriver instance? Yes, This is where chromedriver [Capabilities and ChromeOptions](https://sites.google.com/a/chromium.org/chromedriver/capabilities) comes into the picture.

Almost for each user customizable setting there is ChromeOption available. You can check all options [here](http://www.assertselenium.com/java/list-of-chrome-driver-command-line-arguments/). Now to prevent or block push notifications on Chrome we can use disable-notifications option.

```java
public class DriverFactory {
      public static WebDriver createInstance(){
        DesiredCapabilities capabilities =             DesiredCapabilities.chrome();
        ChromeOptions options = new ChromeOptions();
        options.addArguments("disable-notifications");
        capabilities.setCapability(ChromeOptions.CAPABILITY,             options);
        WebDriver driver = new ChromeDriver();
        return driver;
      }
}
```
