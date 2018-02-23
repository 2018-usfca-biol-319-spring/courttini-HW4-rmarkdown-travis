# Rmarkdown and litterfall module synthesis homework assignment for BIOL319
## Due as a pull request on Monday, February 26, 2017 before 11:59 pm

The **goal of this assignment** is to have you synthesize the analyses and techniques you have learned so far to do a more complex analysis of the NEON litterfall data in the context of nutrient fluxes in ecosystems. You will continue to practice using R and RStudio to analyze and visualize ecological data, doing so in the context of a version-controlled workflow, and submitting your work as a Pull Request on GitHub.

You should feel free to reuse code and writing from your past assignments. You may have to slightly modify your code to fit the specifics of this report. To get full points, you will need to go into more depth in your writing and thinking -- it is not enough to just simply repeat what you have said over the past two weeks, although that would be a great place to start. This is a synthetic assignment, meant to bring together the work we have done with this dataset over the past 3 weeks and continue to refine and elaborate your understanding of it.

**General overview:** Just like last week, you will do all your work for this assignment in the provided `Analysis.Rmd` file. It should read in the `ltr_massdata.csv` file that is in the `data` directory, use the `subset()` function as needed to select subets of that data, and then plot those data using a combination of boxplots and scatterplots (more details below). Finally, you will need to describe the context for the results and interpret your findings in the context of background you read about each of the NEON regions and sites, which is [available here](http://www.neonscience.org/field-sites/field-sites-map/list). For example, [here's a description](http://www.neonscience.org/field-sites/field-sites-map/BART) of the Bartlett Experimental Forest (short ID: BART).

Please follow the instructions carefully and read them all before getting started.

This second assignment will be worth 10 points. The grading breakdown will be as follows:

* 5 points - Completes all required steps (as outlined below)
* 1.5 points - R script is appropriately commented and well organized
* 1.5 points - Appropriate use of git to version control the steps, including adding and committing the appropriate files at the specific steps below, and writing informative and appropriately formatted commit messages and pull request description 
* 2 points - The final commit before the deadline passes Travis-CI checks (successful knitting and code style, details at the bottom of this Readme). Since Travis will only run on your code once you open a pull request (PR), feel free to open your PR well before the deadline to test it out

You must submit your work as a Pull Request to the class organization ('2018-usfca-biol-319-spring') on GitHub by 11:59 pm on Monday, February 26 for full credit. Late assignments will not be accepted, since we will be peer reviewing each other's code after it is submitted.

Steps:

1. Fork this repository to your own GitHub account.
1. On your laptop, in RStudio, select File > New Project...
1. Choose 'Version Control', then 'git', then paste the URL from your fork and hit tab
1. This will autofill the project name, you can choose where this repository folder will be on your laptop
1. Select 'Open in New Session', then 'Create Project'
1. This should download the repository from GitHub and set up a new project for you in RStudio
1. Just like last week, we'll be working in the `Analysis.Rmd` file instead of an R script. So, just open the existing file (look for it in the file browser tab in the lower right-hand corner of RStudio). In this script, in addition to filling out each of the sections (Introduction, Methods, Results, Discussion), you will need to create two figures: an appropriately labeled boxplot comparing mass of one functional group of litter across all sites in the dataset, and a scatterplot of the mass of that same litter functional group from a single site of your choice over time. You can (and absolutely should!) reuse any code and text from previous assignments to complete this report. You can just copy and paste out of the files from past weeks as needed.
  * In your Rmd, you will need to incorporate the appropriate (labelled!) R code chunks to:
    * Read in the `ltr_massdata.csv` dataset from the `data` directory
    * Use the `subset()` function to select all measurements from only one litter type from the following: "Flowers", "Leaves", "Mixed", "Needles", "Other", "Seeds", "Twigs/branches", "Woody material".
    * Create a properly titled and labelled boxplot with the variable `siteID` on the x axis and `dryMass` on the y axis. 
    * Add an R code chunk to apply an appropriate statistical test to determine if there are significant differences in mass of your chosen litter type across NEON sites. You should report the type of test you used, the p-value it returned, and interpretation of what this p-value means about the data you plotted.
    * Choose *one* site of interest - it could be a site with a lot of litter, or one with very little, or somthing in between.
    * Subset out the data for **just your target site and just your target litter functional type** (which should be the same functional type as the type you chose for your boxplot).
    * Create a properly labelled scatterplot with the variable `collectDate` on the x axis and `dryMass` on the y axis. You will need to use the `as.POSIXct()` function like we did in class in order to have the x axis format properly.
1. In the discussion section, explain what you think could be the ecological reason for the differences or lack of differences that you observed between sites, and then infer the reasons for the patterns you observe in your focal site over time, based on your reading of the overview information about each of the sites on the NEON website. The goal is for you to apply ecological thinking to infer why you observe different patterns in the data. Think about type of vegetation that grows at each site, its climate, seasonal patterns, etc.
1. In the Introduction and Methods sections, you should include some background on the NEON project in general, the sites overall, and some additional information on the specific site you are working with. The goal is to give a reader a sense of the diversity of ecosystem types that are represented and where they are located. In the methods, you should very briefly summarize how the data were collected (detailed info is in the 'NEON_litterfall_userGuide_vA.pdf' file in the `data` folder). 
1. Add and commit your Rmd file frequently as you work. Be sure to write [meaningful commit messages](https://chris.beams.io/posts/git-commit/) and a descriptive Pull Request title and description.
1. Knit your Rmd file to a docx using the 'knit' button in RStudio and commit this docx as well.
1. Push your commits back to your repository on GitHub. 
1. Open a pull request back to the class repository to submit your assignment. Make sure the Pull Request (PR) has a useful description of the changes you made. 20% of your points this week will be based on your code passing the automated checks on Travis-CI. This will check for two things: that your Rmd file can be successfully knitted, and that your code follow proper style guidelines. If you want to check for any style errors while you are working on the code, you can install the 'lintr' package by typing the following at the console:

```r
install.packages("lintr")
```

and then whenever you want to check your code you can run at the R console (the command prompt) in RStudio:

```r
lintr::lint(filename = "Analysis.Rmd")
```

Don't hesistate to ask questions on Piazza as you work!

**NOTE:** There are some files in this repository you may not have seen before. They are used for automating testing. 

##### Infrastructure for Automated Software Testing

- `.travis.yml`: a configuration file for automatically running [continuous integration](https://travis-ci.com) checks when you submit your pull request, to verify reproducibility of all `.Rmd` notebooks in the repo.  If all `.Rmd` notebooks can render successfully and pass linting (or code style and syntax checks), then the "Build Status" badge above will be green (`build success`), otherwise it will be red (`build failure`).  
- `.Rbuildignore`: a configuration file telling the build script which files to ignore.
- `DESCRIPTION`: a metadata file for the repository, based on the R package standard. Its main purpose here is as a place to list any additional R packages/libraries needed for any of the `.Rmd` files to run.
- `tests/render_rmds.R`: an R script that is run to execute the above described tests, rendering and linting all `.Rmd` notebooks. 
