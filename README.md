# Selenium-Zephyr-CrossBrowserTesting-example
In this repository, we will highlight an example of integrating test management, cross browser testing with Selenium, Jira, and Jenkins CI. 

Test Management and Cross Browser Testing are done using two world-class SmartBear solutions; Zephyr for Jira and CrossBrowserTesting.

### CrossBrowserTesting
Ditch your VMs and Device Lab. Easily run Manual, Visual, and Selenium Tests in the cloud on 2050+ real desktop and mobile browsers.
https://crossbrowsertesting.com/

### Zephyr for Jira
The #1 Agile Test Management Solution in Jira, perfect for teams focusing on Test Design, Execution, and Test Automation
https://marketplace.atlassian.com/apps/1014681/zephyr-for-jira-test-management?hosting=cloud&tab=overview

### Workflow
With these solutions, we can seamlessly execute a Jenkins CI job with a selenium test executing on a real machine from CrossBrowserTesting and results automatically synchronized into Jira via a Zephyr test cycle. This workflow requires being an active user on both tools. 

Step 1 - Install the CrossBrowserTesting Jenkins plugin 
https://help.crossbrowsertesting.com/selenium-testing/continuous-integration/installing-jenkins/

Step 2 - Download Selenium Tests (selenium_test.py) and Zephyr for Jira Synchronize Script (sync_z4j.py) example from this repo

Step 3 - Fill out parameters in config.json file to be authenticated into Zephyr for Jira https://zephyrdocs.atlassian.net/wiki/spaces/ZFJCLOUD/pages/1686798372/A.T.O.M+API+Documentation

Step 4 - Set up Jenkins Job with both tools
  a. Enable CrossBrowserTesting.com in Build Environment according to above docs. Select desired OS, Browser, and Resolution
  https://help.crossbrowsertesting.com/wp-content/uploads/2019/06/Build_Environment_1.png
  
  b. Set up first build step to run selenium tests and execute junit xml file as the report
      
      Note: This can be done in many ways. During the webinar, I used the shining panda jenkins plugin with the pytest module to do this. 
      Sample Command - py.test --junitxml "/Results/results.xml" "selenium_test.py"
  
  c. Set up execution for Z4J Sync scriptas a build or post-build action
      
      Sample Command - python sync_z4j.py
 

You can see this in action during our SmartBear Webinar - Test, Track, and Analyze: Scaling Test Automation Effectively in Agile
https://smartbear.com/resources/webinars/scaling-test-automation-in-agile/



## Configuration Instructions
config.json file is required in the same directory as the migration script. 

Example config can be found 

ACCESS_KEY: Output Directory for Reports.

SECRET_KEY: Vendor ID issued by Atlassian.

ACCOUNT_ID: ID of Vendor Add-on

PROJECT_ID: Email of account with Reporting Permissions to Vendor Account.

REPORT_DIRECTORY: Password of account with Reporting Permissions to Vendor Account.

RESULT_FILE: Array(List) of files that contain search text *NOTE Files should be single column csv with search terms.

All fields are required. 


## Execution Instructions

Execute script 
`python email_lookup.py`
