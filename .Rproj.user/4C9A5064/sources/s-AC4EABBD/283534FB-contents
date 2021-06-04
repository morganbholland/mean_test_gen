
testgen <- function(seed){
  require(tidyverse)
  require(glue)
  set.seed(seed) 
  #Set the seed for r's random number generator. Uncomment the line above to generate the same test every time. Once the line is uncommented, you can change the number to manually generate different tests.
  
  n <- round(runif(1, min = 50, max = 500)) # Set the sample size, drawn from uniform distribution and rounded to nearest integer
  
  mu <- sample(1:100,1) 
  sd <- sample(5:50,1)  # Set the population mean and sd.
  
  X <- rnorm(n,mean = mu, sd = sd) #sample is drawn from a normal distribution. It's not necessary to draw from a normal distribution, but you will have to modify the code if you want to try a different one. 
  
  xbar <- round(mean(X),2)
  s <- round(sd(X),2)
  se <- s/sqrt(n)

  muho <- xbar + round(rnorm(1, mean = 0, sd = se*2)) # Add some random noise to the sample mean to come up with a null hypothesis mean. 
  
  alpha <- sample(c(0.01, 0.05, 0.10),1) # Randomly select the alpha level of the test.
 
  if (muho > xbar){
    hset <- c("less", "two-sided")
  }else{
    hset <- c("greater","two-sided")
  } # The possible types of alternative hypotheses are different depending on which side of xbar the null mu is.
  
  alt <- sample(hset,1) # Randomly select the type of test based on the alternative hypothesis. 
  
  ts = (xbar - muho)/se
  
  if (alt == "less"){
    testtxt = glue(">")
    cv = qnorm(alpha)
    p = pnorm(ts)
    cilower = xbar - abs(cv)*se
    ciupper = Inf
    
  }else if (alt == "greater"){
    testtxt = glue("<")
    cv = qnorm(1-alpha)
    p = pnorm(1-ts)
    cilower = -Inf
    ciupper = xbar + abs(cv)*se
  }else {
    testtxt = glue("=")
    cv = qnorm(alpha/2)
    p = if_else(ts <= 0, 2*pnorm(ts), 3*pnorm(-ts))
    cilower = xbar - abs(cv)*se
    ciupper = xbar + abs(cv)*se
  }
  
  ci = c(cilower,ciupper) #Calculated, but not returned. Add this to the list below if you want R to return the confidence interval.
  
  result = if_else(p < alpha, "reject", "cannot reject")
  
  return(list('mu' = muho, 'n' = n, 'xbar' = xbar, 's' = s, 
              'testtxt' = testtxt, 'result' = result, 'alpha' = alpha))
}



