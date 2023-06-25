---
title: "Object Repository in Selenium WebDriver"
date: 2016-07-11
tags: ["selenium", "How-to"]
draft: false
author: "Amol Chavan"
---

# Object Repository in Selenium WebDriver

---

**Update : This is old post. I wrote this when I was learning Java and WebDriver. Now that I have seen enough I know, `Object Repository` has nothing to do with Selenium WebDriver**

---

From last 6 month or so, I am happily playing with Selenium API. Earlier, I invested more than 3 years in [QTP](https://en.wikipedia.org/wiki/HP_QuickTest_Professional)/[UFT](http://www8.hp.com/us/en/software-solutions/unified-functional-automated-testing/). After spending that much of time in QTP, it’s very obvious that moving to selenium is not easy game and you cannot help yourself but compare this two things. You missed a lot of things from QTP when you move to Selenium, I can enlist few of those as follows:-

1. Actions
2. Datatables
3. Checkpoints
4. Smart Identifications
5. Recovery scenarios
6. Readily available test execution results and
7. Object Repository and OR Manager

This is not the complete list but still this are the majors which I have missed.

_“Journey becomes easy and better when you have good companion_.” I went through many forums to find out good companion for learning selenium and finally settled on a book [Selenium Testing Tools Cookbook](https://www.amazon.in/Selenium-Testing-Cookbook-Unmesh-Gundecha-ebook/dp/B00AC1HDJI/ref=as_sl_pc_tf_cw?&linkCode=waf&tag=httpwwwugacha-21) by [Unmesh Gundecha](https://unmesh.me/). When I started to learn selenium, I thought of creating Object Repository in selenium. The book by Unmesh, itself was presented with recipe of implementation of Object Repository [OR]. I have done some changes in implementation as per need which we will discuss in this post.

### **What is Object Repository (OR) anyway?**

Object Repository is a mechanism to store objects information from application under test for performing action on those objects in a test script, it acts as interface between Test script and application in order to identify the objects during the execution.

### **Setting Up Object Repository for Selenium WebDriver**

\We know that, QTP internally uses XML to store object repository. For Selenium Context,someone already answered on [\*\*stackoverflow](http://stackoverflow.com/questions/26758299/object-repository-in-xml-file-for-selenium-webdriver-framework-with-java-and-tes) \*\* and answer shows use of XML as object repository for Webdriver. Personally, I prefer to use properties files as they are more readable than XML files. As you might aware, property file uses key-value pair format. You must decide the format for your properties file, I am using it in following way:-

`[logical_name]=[locator_type]~[locator_value]`

Where -

`[logical_name]`:Logical Name generally would be label of element.[As it displayed on the UI]

`[locator_type]`:Locator type must be one from the following- `id, name, className, linkText, partialLinkText, cssSelector, xpath, tagName`

`[locator_value]`:Locator value - Value of locator_type

Sample property file screenshot-

![](https://lh6.googleusercontent.com/kmLNEVS-H6WWmjvdyCv3F3fX2G68TWhjy7LF8Y5P8YddPSyQQJLw7azjDtoidcvWGX3Epb9BwOUgBOw7hB7yp7O2bwPNbuVyRGPey9giGerXEcuGSwXaWpDiHDSkuOVYA4YKfnya)

## **Fetching objects from the Object Repository:-**

Now that we have created properties file (OR), we need to have mechanism in a place to fetch this objects in our test script. Let's design a class which will help us to achieve the following objectives.:-

1. Get WebElement as mentioned in our properties file.[method `getElement()`]
2. Get Locator as mentioned in our properties file. [method `getLocator()`]
   ```java

   import org.openqa.selenium.By;
    import org.openqa.selenium.WebElement;
   import java.io.FileInputStream;
   import java.io.IOException;
   import java.util.Properties;


   public class ObjectMap extends ActionUtilities{
     Properties properties;

     /**
     * This is Constructor Method accepts Absolute path of object map file and load it into memory.
     * @param mapFilePath
     */
     public ObjectMap(String mapFilePath){
       properties = new Properties();
       try {
         FileInputStream fileInputStream = new FileInputStream(mapFilePath);
         properties.load(fileInputStream);
         fileInputStream.close();
       }catch (IOException e) {
         System.out.println(e.getMessage());
       }
   }

   /**
   * This is Method accepts LogicalElementName present in object map file and returns By of type webdriver.
   * @param logicalElementName
   */
     public By getLocator(String logicalElementName) {
     try {
       String locator = properties.getProperty(logicalElementName);
       String locatorType = locator.split("~")[0];
       String locatorValue = locator.split("~")[1];

       switch (locatorType.toUpperCase()) {
         case "ID":
         return By.id(locatorValue);
         case "NAME":
         return By.name(locatorValue);
         case "CLASSNAME":
         return By.className(locatorValue);
         case "TAGNAME":
         return By.tagName(locatorValue);
         case "LINKTEXT":
         return By.linkText(locatorValue);
         case "PARTIALLINKTEXT":
         return By.partialLinkText(locatorValue);
         case "CSSSELECTOR":
         return By.cssSelector(locatorValue);
         case "XPATH":
         return By.xpath(locatorValue);
         default:
         return null;
       }
     }catch (NullPointerException e){
       System.out.println(e.getMessage());
       return null;
     }
   }

     /**
     * This is Method accepts LogicalElementName present in object map file and returns webelement of type webdriver.
     * @param logicalElementName
     */
     public WebElement getElement(String logicalElementName){
       return driver.findElement(getLocator(logicalElementName));
     }

     /**
     * Property getter
     * @param propertyName
     */
     public String getProperty(String propertyName){
       return  properties.getProperty(propertyName);
     }

     /**
     * Property setter.
     */
     public void setProperty(String key, String value) {
        properties.setProperty(key,value);
     }

   }

   ```

### **Using Object Repository in Selenium WebDriver script:-**

Now let us try to automate the scenario of login to application which uses Login `OR` [Login.properties file as shown in image], `ObjectMap` class.

    import com.utilities.ObjectMap;
    import org.openqa.selenium.firefox.FirefoxDriver;

    /**
     * Created by Amol Chavan on 11-07-2016.
     */
    public class TestRunner {
      public static void main(String[] args){
          ObjectMap objectMap = new ObjectMap("Login.properties");
          FirefoxDriver driver = new FirefoxDriver();
          driver.get("https://wordpress.com/wp-login.php");
          driver.findElement(objectMap.getLocator("Username")).sendKeys("MyUserName");
          driver.findElement(objectMap.getLocator("Password")).sendKeys("MyPassword");
          driver.findElement(objectMap.getLocator("StaySignedIn")).click();
          driver.findElement(objectMap.getLocator("Login")).click();
      }
    }

Above script demonstrate login to wordpress. It uses getLocator method from the class ObjectMap. This is very straightforward example of OR, it does not uses [Page Object Model](http://qaperspective.blogspot.in/2016/06/page-object-model.html) or TestNG. If you notice, we have not used getElement method from the ObjectMap class and used one OR in a script like [shared OR](http://www.guru99.com/quick-test-professional-qtp-tutorial-23.html). May be in future, I will post related articles which will show use of OR as Local OR along with Page Object.
