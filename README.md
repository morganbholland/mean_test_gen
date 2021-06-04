# mean_test_gen
 Script and markdown file that randomly generates 40 hypothesis testing problems for the sample mean. 
 In the `src` folder, there is a script `xbarscript.R` and an Rmarkdown file `hypothesis testing worksheet.Rmd`. The script randomly generates the values needed for a hypothesis testing question about the population mean of a random variable The function `testgen` takes as input a random seed and as output returns a list containing the null hypothesis, sample size, sample mean, sample standard deviation, test type (right-side, left-side, or two-sided), the result of the test (reject or fail to reject), and the significance level of the test. The markdown file runs the script 40 times and arranges the results into a worksheet with 40 hypothesis testing problems (with their solutions). The markdown file generates both an HTML and Word version of the worksheet. 
 
 NOTES: At present, the test uses a normal distribution in drawing the sample and the normal distribution in calculating the solution to the test. You will have to modify the script if you want to use the t distribution. Requires `tidyverse` and `glue` packages.

