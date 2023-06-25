---
title: "Exclude JMeter Component at Runtime"
date: 2019-06-23
tags: ["jmeter"]
draft: false
author: "Amol Chavan"
ghcommentid: 1
---

# Exclude JMeter Component at Runtime

---

This post in trying to be answer of one of the [question](https://stackoverflow.com/questions/56545015/jmeter-execute-specific-components-only-on-gui-and-not-cli) on the [stackoverflow](http://www.stackoverflow.com).

As you may already know that, JMeter Scripts are saved with extension as `jmx` which is nothing but a XML in disguise.

I have created sample JMeter Test Plan (also available on GitHub) for demonstration of this POC. Script looks like this -

<center>![JMeter GUI Demo script](/Exclude-JMeter-Component-at-Runtime/jmeter-gui-demo-script.png)_JMeter GUI Demo script_</center>

And below is the JMX structure of it -

![JMeter-jmx-demo-script](/Exclude-JMeter-Component-at-Runtime/JMeter-jmx-demo-script.png)_JMeter jmx demo script_

you can see, all the JMeter components, XML tag highlighted in the picture, have property `enabled` for which `true` and `false` are only two valid values. To see this in action I will disable one of the Thread group of JMeter Script.

![Disabled-threadgroup-in-JMeter-GUI](/Exclude-JMeter-Component-at-Runtime/Disabled-threadgroup-in-JMeter-GUI.png)_Disabled threadgroup in JMeter GUI_

Now see above change is also gets reflected in the `jmx` file in the mentioned `enabled` property for Thread Group in below code

![Disabled-threadgroup-in-JMeter-jmx](/Exclude-JMeter-Component-at-Runtime/Disabled-threadgroup-in-JMeter-jmx.png)_Enabled property is changed got diabaled component in UI to false_

So above simple analysis shows that if we want to toggle script at the runtime execution in CLI mode, we need to make the changes in `jmx` file such that required component must be marked as false for enabled property.

I expect, some of you might also knew this. So to solve the problem at hand, we need to change the flag at run time and for that we can leverage host OS on which script is running or we can use below approach:

To see the required change in effective way, I'm executing above script first in non-gui mode using below command :

    jmeter -n -t .\ExcludeJMeterComponent.jmx -l result.CSV -e -o "Output"

You can see the result generated by the command : all the samplers including JSR and Debug sampler got executed

![APDEX-Result-with-Debug-Sampler](/Exclude-JMeter-Component-at-Runtime/APDEX-Result-with-Debug-Sampler.png)_APDEX Result with Debug Sampler.png_

APDEX result of non-gui execution of demo script

Now, let's go to the actual solution, I will edit the `jmx` script in below way

![Updated jmx file demo script](/Exclude-JMeter-Component-at-Runtime/updated-jmx-file-demo-script.png)_Updated jmx file - demo script_

Debug Sampler and View Result Tree is updated to consume property which can be passed as parameter in non GUI mode

Now I will re-execute the script in non gui mode sending additional property as below

    jmeter -n -t .\ExcludeJMeterComponent.jmx -l result.CSV -e -o "Output" -DenabledDebugComponents=false

APDEX result of non-gui execution of demo script: You can see `Debug sampler` Does not get execute.

![APDEX Result WITHOUT Debug Sampler](/Exclude-JMeter-Component-at-Runtime/APDEX-Result-WITHOUT-Debug-Sampler.png)_APDEX Result WITHOUT Debug Sampler_

Of course, **if you load this script again in JMeter this values going to go away/get override with your next save but if you are using any version control system to keep track of your `jmx` script [which you should] it will be very easy to add this changes in the script again.**

There is one more solution which will be posted shortly to fix this issue but its dirty fix if you are not using CI tool.