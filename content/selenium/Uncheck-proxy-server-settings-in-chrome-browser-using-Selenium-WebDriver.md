---
title: "Uncheck Proxy Server Settings in Chrome Browser Using Selenium WebDriver"
date: 2017-09-16
tags: ["selenium", "How-to"]
draft: false
author: "Amol Chavan"
---

# Uncheck Proxy Server Settings in Chrome Browser Using Selenium WebDriver

---

If you have read my past [posts](http://qaperspective.blogspot.in/2016/08/how-can-i-enhanceimprove-my-selenium.html), you might know that I follow a lot of forums to understand what type of issues are faced by the community. This helps me to broaden my knowledge. Couple of days ago, I stumbled upon this [question](https://www.facebook.com/groups/Testingridewithautomation/permalink/1770893919843998/) on a such forum on Facebook.

Question was- _“How to uncheck proxy server settings in chrome browser using selenium Code ?”_ with Below image.

![](https://lh4.googleusercontent.com/Xf2yjoweeIu1ZlGguokE6izcOD2Ss0l80u9z0baYc3o1qmmVMd_41yhotb8EQ8J1kHvzCU1SbxKk8uWU5aR8DIt9GeC19sRAIygijJx7NhyVcpWbH4qywIq6lCMjwFlSc5yrjRHi)

That was really interesting question and Thanks for this question ‎[Roby Chauhan](https://www.facebook.com/profile.php?id=100007029078193).

Defining problem statement:- Uncheck proxy setting while invoking Chrome browser using Selenium WebDriver.

Understanding Problem Statement:-

I first tried to solve this question manually and realized once again that proxy setting that you applied in one browser are not just that browser specific but it OS specific.

That means if you set proxy in one browser it is applicable to all browsers. If you set wrong proxy in one browser you would not able to connect to the internet using any browser. Refer image below for more understanding. Image taken from [Chrome support group for education and help](https://support.google.com/chrome/a/answer/187202?hl=en&rd=1).

![](https://lh4.googleusercontent.com/wwEoZ9xKLSEej3vpiP9KaHJOr1fuNRyr4cv5Xq8WH4P9MVDP3GNB9YDXjsa073Ll-3X6eds_yO0W2lM9oHjB-eRc3YPpmRWnQ-spwKRyfL_kZQbslc12lUo9_e1ED69OIgawRC4a)

So basically we are talking about this red box, where we doing some setting which we need to overcome while invoking chrome using Selenium WebDriver.

Solution:-

After a lot of searching on Google, I found solution somewhere on the internet, we need to below use [Capabilities & ChromeOptions](https://sites.google.com/a/chromium.org/chromedriver/capabilities).

`options.addArguments("--no-proxy-server");`

Please check working code snippet below:-

    import org.openqa.selenium.WebDriver;
    import org.openqa.selenium.chrome.ChromeDriver;
    import org.openqa.selenium.chrome.ChromeOptions;
    import org.openqa.selenium.remote.DesiredCapabilities;

    /**
     * Created by Amol Chavan on 9/10/2016.
     */

    public class DriverFactory {
       public static WebDriver createInstance(){
            DesiredCapabilities capabilities = DesiredCapabilities.chrome();
            ChromeOptions options = new ChromeOptions();
            options.addArguments("--no-proxy-server");
            capabilities.setCapability(ChromeOptions.CAPABILITY, options);
            System.setProperty("webdriver.chrome.driver","C:\\Grid\\chromedriver.exe");
            WebDriver driver = new ChromeDriver(capabilities);
            driver.get("http://www.google.com");
            return driver;
        }
    }

This is all for now.

Cheers!!
