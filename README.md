# Saucery
Documentation and examples for Saucery2 and Saucery3 NuGet packages and JUnit 4 implementation.

## General Notes:
On initially cloning this repository and opening either of the solutions, the Activation Dialog should open.  If not, you may need to open the Package Manager Console window under (View > Other Windows > Package Manager Console).  Licence keys can be obtained from http://fullcirclesolutions.com.au

Saucery is compatible with any CI server that the [SauceOnDemand](https://github.com/jenkinsci/sauce-ondemand-plugin) plugin supports. As of January 2016 this is [Jenkins](http://jenkins-ci.org) and [Bamboo](https://www.atlassian.com/software/bamboo).

If you have Resharper installed the Saucery classes will appear in red.  However the solution will still build perfectly well.  This is a Resharper bug over which we have no control.

Note that if you choose to start from scratch (i.e. add Saucery3 OR Saucery3 NuGet package to an empty class library) the following steps will probably be required to make the Activation Dialog appear so you can generate your licence file:

1. Save All Files
2. Close and reopen your solution
3. Open the Package Manager Console if it is not already.


| Platform you wish to target | Write your tests with | Base class you should use |
| --------------------------- | --------------------- | ------------------------- | 
| Desktop browser             | Selenium              | SauceryBase               |
| Android device              | Appium                | SauceryAndroidBase        |
| IOS device                  | Appium                | SauceryIOSBase            |

## [Saucery 2](http://www.nuget.org/packages/saucery2) (for NUnit 2)

In a Jenkins job, execute your test project in a Windows Batch Command step like this:

    "C:\Program Files (x86)\NUnit 2.6.4\bin\nunit-console.exe" <workspace\relative\path\to\my\test.dll> /xml=nunit-selenium-testsuite.xml
    exit %%ERRORLEVEL%%

Publish test results in Jenkins with a Post Build Publish NUnit test result report step specifying nunit-selenium-testsuite.xml (or whatever filename you specified in the command above).

## [Saucery 3](http://www.nuget.org/packages/saucery3) (for NUnit 3)

In a Jenkins job, execute your test project in a Windows Batch Command step like this:

    "C:\Program Files (x86)\NUnit.org\nunit-console\nunit3-console.exe" <workspace\relative\path\to\my\test.dll> --result:nunit-selenium-testsuite.xml;format=nunit2
    exit %%ERRORLEVEL%%

Publish test results in Jenkins with a Post Build Publish NUnit test result report step specifying nunit-selenium-testsuite.xml (or whatever filename you specified in the command above).

SauceryForJUnit is for JUnit 4.12 and is currently available on request.  If there is sufficient demand it will be released on http://bintray.com
