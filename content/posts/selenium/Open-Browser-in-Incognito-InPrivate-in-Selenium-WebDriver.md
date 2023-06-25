---
title: "Open Browser in Incognito InPrivate in Selenium WebDriver"
date: 2016-09-27
tags: ["selenium", "How-to"]
draft: false
author: "Amol Chavan"
---

# Open Browser in Incognito InPrivate in Selenium WebDriver

---

### How to Open Chrome Browser in Incognito mode using Selenium / WebDriver ?

We will use Chrome Drivers [Capabilities & ChromeOptions](https://sites.google.com/a/chromium.org/chromedriver/capabilities) to open Chrome browser in incognito mode. To be precise, we have to use argument --incognito for ChromeOption as shown in below example-

    import org.openqa.selenium.WebDriver;
    import org.openqa.selenium.chrome.ChromeDriver;
    import org.openqa.selenium.chrome.ChromeOptions;
    import org.openqa.selenium.remote.DesiredCapabilities;

    /**
     * Created by Amol Chavan on 9/19/2016.
     */
    public class PrivateBrowsing {

        public static void main(String args[]){
            createInstance();
        }

        public static WebDriver createInstance(){
            DesiredCapabilities capabilities = DesiredCapabilities.chrome();
            ChromeOptions options = new ChromeOptions();
            options.addArguments("--incognito");
            capabilities.setCapability(ChromeOptions.CAPABILITY, options);
            System.setProperty("webdriver.chrome.driver","C:\\Grid\\chromedriver.exe");
            WebDriver driver = new ChromeDriver(capabilities);
            driver.get("http://www.google.com");
            return driver;
        }
    }

### How to Open Firefox Browser in Incognito / Private mode using Selenium / WebDriver ?

We will use [Firefox Profile](https://seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/firefox/FirefoxProfile.html) to open Firefox in private mode. To be precise, we will set browser.private.browsing.autostart in firefox profile preference.

    import org.openqa.selenium.WebDriver;
    import org.openqa.selenium.firefox.FirefoxDriver;
    import org.openqa.selenium.firefox.FirefoxProfile;

    /**
     * Created by Amol Chavan on 9/19/2016.
     */
    public class PrivateBrowsing {

        public static void main(String args[]){
            createInstance();
        }

        public static WebDriver createInstance(){
            FirefoxProfile firefoxProfile = new FirefoxProfile();
            firefoxProfile.setPreference("browser.private.browsing.autostart",true);
            WebDriver driver = new FirefoxDriver(firefoxProfile);
            driver.get("http://www.google.com");
            return  driver;
        }
    }

### How to Open Internet Explorer (IE) Browser in InPrivate mode using Selenium / WebDriver ?

We will use [IE Driver Capabilities](https://seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/ie/InternetExplorerDriver.html) to open IE in InPrivate mode. To be precise we will use FORCE_CREATE_PROCESS capability along with IE_SWITCHES to which parameter would be -private

    import org.openqa.selenium.WebDriver;
    import org.openqa.selenium.ie.InternetExplorerDriver;
    import org.openqa.selenium.remote.DesiredCapabilities;

    /**
     * Created by Amol Chavan on 9/19/2016.
     */
    public class PrivateBrowsing {

        public static void main(String args[]){
            createInstance();
        }

        public static WebDriver createInstance(){
            DesiredCapabilities capabilities = DesiredCapabilities.internetExplorer();
            capabilities.setCapability(InternetExplorerDriver.FORCE_CREATE_PROCESS, true);
            capabilities.setCapability(InternetExplorerDriver.IE_SWITCHES, "-private");
            System.setProperty("webdriver.ie.driver","C:\\Grid\\IEDriverServer.exe");
            WebDriver driver = new InternetExplorerDriver(capabilities);
            driver.get("http://www.google.com");
            return driver;
        }
    }
