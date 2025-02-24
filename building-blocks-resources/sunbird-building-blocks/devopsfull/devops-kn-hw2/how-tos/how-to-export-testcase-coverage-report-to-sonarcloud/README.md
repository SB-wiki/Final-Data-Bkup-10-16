---
icon: folder-open
---

# 1How-to-export-Testcase-coverage-report-to-SonarCloud

We're using jacoco.xml to export code coverage report to sonarqube.

To check everything working fine, you can have a local sonarqube running and test against that.

### Steps to deploy a local sonarqube:

docker run --rm -d --name sonarqube -p 9000:9000 sonarqube

open browser → localhost:9000 → click on login

initial _username_ and _password_ will be **admin**

Click on the create new project

![](<../../../../../../.gitbook/assets/image2019-11-26\_11-6-24 (1).png>)

Give a name for your project and click setup

![](<../../../../../../.gitbook/assets/image2019-11-26\_11-7-37 (1).png>)

Generate a token

![](<../../../../../../.gitbook/assets/image2019-11-26\_11-8-37 (1).png>)

Select your language

![](<../../../../../../.gitbook/assets/image2019-11-26\_11-11-27 (1).png>)

copy the above command and run it in your project(above example is for maven projects)

After that you should see something like this, if your project is analysed properly

Note: you might have to refresh the page

![](<../../../../../../.gitbook/assets/image2019-11-26\_11-13-55 (1).png>)

If you want to export a specific coverage report

```
mvn verify sonar:sonar \
-Dsonar.projectKey=data-pipeline \
-Dsonar.host.url=http://localhost:9000 \
-Dsonar.login=ed6b5431870626331d3c47e9f8240431d2843ade \
-Dsonar.coverage.jacoco.xmlReportPaths=/home/circleci/dp/data-pipeline/telemetry-location-updater/target/coverage-reports/jacoco-ut/jacoco.xml,/home/circleci/dp/data-pipeline/telemetry-validator/target/coverage-reports/jacoco-ut/jacoco.xml,/home/circleci/dp/data-pipeline/de-duplication/target/coverage-reports/jacoco-ut/jacoco.xml
```

**Adding SonarCloud Badge in the Github Repo:**

Click on **Get project badges**

![](<../../../../../../.gitbook/assets/image2019-12-16\_12-54-25 (1).png>)

Copy the URL and paste it in the Github repository README file.

![](<../../../../../../.gitbook/assets/image2019-12-16\_12-52-33 (1).png>)

***

\[\[category.storage-team]] \[\[category.confluence]]
