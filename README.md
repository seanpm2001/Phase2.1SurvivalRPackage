# Phase2.1SurvivalRPackage 

R code to run, validate, and submit the analysis for the Phase2.1 Temporal Trend project and additional results for Phase1.1 paper revision. Please note it will take about 30 minutes to finish running the analysis. Thank you for your patience!

# Docker Users

## 1. Make sure you are using the latest version of Docker. 

## 2. Always RESTART your R session before installing or re-installing the package!

## 3. Run the following scripts in R:

```
devtools::install_github("https://github.com/covidclinical/Phase2.1SurvivalRPackage", subdir="FourCePhase2.1Survival", upgrade=FALSE)
library(FourCePhase2.1Data)
library(FourCePhase2.1Survival)
library(icd)
currSiteId = getSiteId()
runAnalysis(currSiteId)
```

## 4. Two ways to submit the results:
1. Submit via GitHub. 
+ (1) Share with @Chuan your GitHub accountname via direct message on Slack channel so you can be added as contributor to the repository. 
+ (2) Note that you would need to use a token to access private repos, see here (https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token). Briefly, to generate a new token, go to your GitHub settings -> Developer settings -> Personal access tokens -> Generate.
+ (3) Submit the result files in your output directory to the branch named topic-[YourSiteId] in GitHub repo Phase2.1SurvivalRSummariesPublic by running the following scripts in R:
```
submitAnalysis()
```

2. Submit via Slack channel. Alternatively, if somehow submitAnalysis() didn’t allow you to upload the results to Phase2.1SurvivalRSummariesPublic, you can share the results file with @Chuan via the direct message on Slack channel.

# Non-Docker Users
## Please refer to branch no-docker: https://github.com/covidclinical/Phase2.1SurvivalRPackage/tree/no-docker

# VA Users

## 1. Download the zip of the github repo
<img width="483" alt="Screen Shot 2021-04-14 at 12 45 19 AM" src="https://user-images.githubusercontent.com/9748986/114655686-b33e8080-9cba-11eb-93f7-2756436a2605.png">
. 

## 2. Upload files to VINCE
Unzip the file downloaded from the github repo, upload the files under "FourCePhase2.1Survival/R" and "FourCePhase2.1Survival/data" to VINCI.

## 3. Set up directory at VINCI
Create a folder named "[YourPath]/FourCePhase2.1Survival" in your own folder at VINCI, and move the files from UPLOAD to this folder. You should have subfolders R, data, and Output. 

## 4. Set up directory in R
Set the working directory to "[YourPath]/FourCePhase2.1Survival", and set the output directory. Please note fail to set the right working and output directories will lead to error when running the code.

```
setwd("[YourPath]/FourCePhase2.1Survival")
dir.output="[YourPath]/FourCePhase2.1Survival/Output" ### 
```

## 5. Run the following scripts in R:

```
library(RODBC)
files.sources = list.files("R")
sapply(paste0("R\\",files.sources), function(x) source(x))
currSiteId = "VA1" ### you may change to "VA2", ..., "VA5" as needed
runAnalysis_VA(currSiteId, dir.output)
```
## 6. Two ways to submit the results
There should be three files in the output folder: VA_Result.Rdata, VA_Result_R1.Rdata, and VA_log.txt. You can choose either of the following way to submit the results.

1. Submit via GitHub. 
+ (1) Share with @Chuan your GitHub accountname via direct message on Slack channel so you can be added as contributor to the repository. 
+ (2) Note that you would need to use a token to access private repos, see here (https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token). Briefly, to generate a new token, go to your GitHub settings -> Developer settings -> Personal access tokens -> Generate.
+ (3) Submit the result files in your output directory to the branch named topic-VA in GitHub repo Phase2.1SurvivalRSummariesPublic 
https://github.com/covidclinical/Phase2.1SurvivalRSummariesPublic/tree/topic-VA

2. Submit via Slack channel. Alternatively, if somehow Github didn’t allow you to upload the results to Phase2.1SurvivalRSummariesPublic, you can share the results file with @Chuan via the direct message on Slack channel.



