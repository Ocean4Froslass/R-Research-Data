sex nested within populations and families. fixed effects and random effects. population and family are considered a replication variable. family as fixed effect? otherwise, as a random variance effect. indicate nested effects. family nested within population. 

Start with ANOVA between M and F traits. Consider t-test analyses initially. 

Timeline for Data Analysis, starting next experiment. Consider replication at the family level? Is there a population or family effect (differ between one another?)? 

Fischer’s exact test? Conversion of \#flower axil data to categorical? (0 \= none, 1 \= alot)?

germ \<- aov(formula \= germination\_date \~ Sex, data \= my\_data)

summary(germ) p-value \= 0.61

infloresence\_date \<- aov(formula \= initial\_inflor\_date \~ Sex, data \= my\_data)

summary(infloresence\_date) p-value \= 0.00718 \>:D

height \<- aov(formula \= plant\_height \~ Sex, data \= my\_data)

summary(height) p-value \= 0.805 

collection \<- aov(formula \= p.h.\_collection \~ Sex, data \= my\_data)  
summary(collection) p-value \= 0.761

inflor\_length \<- aov(formula \= inflor\_length \~ Sex, data \= my\_data)  
summary(inflor\_length) p-value \= 0.607

flowering \<- aov(formula \= flowering\_date \~ Sex, data \= my\_data)  
summary(flowering) p-value \= 3.74e-05 \>:D

leaf\_area \<- aov(formula \= leaf\_area..cm.2. \~ Sex, data \= my\_data)  
summary(leaf\_area) p-value \= 0.415

leaf\_mass \<- aov(formula \= dry\_leaf\_mass..g. \~ Sex, data \= my\_data)  
summary(leaf\_mass) p-value \= 0.314 \| updated p-value \= 0.175 (leaf\_mass \<- aov(formula \= new\_dry\_leaf\_mass \~ Sex, data \= updated\_data))

inflor\_mass \<- aov(formula \= dry\_inflor\_mass..g. \~ Sex, data \= my\_data)  
summary(inflor\_mass) p-value \= 0.73 \| updated p-value \= 0.355 (inflor\_mass \<- aov(formula \= new\_dry\_inflor\_mass \~ Sex, data \= updated\_data)) \*Plot by date of germination by males and females \- also for date for inflorescence development.

above\_veg\_mass \<- aov(formula \= dry\_above\_veg\_mass..g. \~ Sex, data \= my\_data)  
summary(above\_veg\_mass) p-value \= 0.00828 \>:D \| updated p-value \= 0.862 (summary(aov(formula \= new\_dry\_above\_veg \~ Sex, data \= updated\_data))

\*plot by dry\_mass by above\_veg\_mass \-\> run linear regression

roots \<- aov(formula \= dry\_roots..g. \~ Sex, data \= my\_data)  
summary(roots)   p-value \= 0.0584 \| updated p-value \= 0.877 (roots \<- aov(formula \= new\_dry\_roots \~ Sex, data \= updated\_data))

flower\_density \<- aov(formula \= flower\_density\_inflorescence..flowers.2.cm.2. \~ Sex, data \= my\_data)  
summary(flower\_density)   p-value \= 0.332

axil\_flowers \<- aov(formula \= number\_axils\_with\_flowers \~ Sex, data \= my\_data)  
summary(axil\_flowers)   p-value \= \<2e-16 \>:D

SLA \<- aov(formula \= specific\_leaf\_area..cm.2...g. \~ Sex, data \= my\_data)  
summary(SLA)    p-value \= 0.824

Phi2 \<- aov(formula \= Phi.2 \~ Sex, data \= my\_data)  
summary(Phi2) p-value \= 0.793

\*Run model with and without sex present to test whether sex is significant \-

Ex: \# Do H and F flowers have different petal lengths by Dam?  
\# Construct the full linear mixed-effects model  
full\_model \<- lmer(petallength \~ Dam \+ sex \+ Dam\*sex \+ (1 \| plant) ,  
                  data \= oxFL)  
\# Construct a reduced model without the sex variable  
reduced\_model \<- lmer(petallength \~ Dam \+ sex \+ (1 \| plant) ,  
                  data \= oxFL)  
\# Perform likelihood ratio test (ANOVA) to compare the models  
anova\_result \<- anova(full\_model, reduced\_model)  
\# Print the ANOVA result  
print(anova\_result)

1\|mother refers to mother as a random variable \- exclusive of sex.

\*Repeat analyses with exclusion of outliers to determine their significance.

\*For Phi2, consider including covariance as time since data was collected (since it took several hours to collect). \*Plot time by Quantum Yield Efficiency (Phi2). 

Germination date by height plot? \*

Insight into potential biases as to why there may have not been a difference overall? Collection bias or treatment conditions?

full\_model \<- lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|mother) \+ germTime)  
reduced\_model \<- lmer(number\_axils\_with\_flowers \~ (1\|mother) \+ germTime)  
anova\_result \<- anova(full\_model, reduced\_model)  
print(anova\_result)

full\_model \<- lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|Mother) \+ germination\_date \+ Sex\*germination\_date, data \= updated\_data)

\*\*All results showing as statistically significant \- error with mother assignment? Also, need to load lmerTest package to show p-values\!

\*\*\*

Timeline \- Finish initial data analysis by June 10th. Start 2nd experiment by June 15th. Experiment should take \~1-1.5 months.

Separate individual label into 3 columns \- population, mother, individual. Remove spaces within the data table.

height \~ sex \+ (1 \| mother) \* takes into variance based on mother population. Followed by summary() & emmeans(). (restricted maximum likelihood analysis). 

lmer(plant\_height \~ Sex \+ (1 \| Mother), data \= new\_data)

\*Calculate the ratio of time plant was growing \- ratio of time spent germinating to height at plant collection. 

\*Adjust mass by number of days since it has been growing? Dry mass / \# of days growing.

Adjust flowering date by germination date \- i.e., \#days since germination.

1.) Look into restricted maximum likelihood analysis/ 

2.) Take into account different mothers 

Specs analysis (?)

**\*\*\*2 level nesting design in R?\*\*\*** population within mother

Make sure data follows ANOVA model assumptions. 

Create sex ratios for each family. Consider throwing out S1I2 2 samples \- only 2 individuals, both males, might induce bias. 

\*5 treatments for Nitrogen? 10 seeds per family? 300 total? Mixing up fertilizer treatment? Or just dilute an all around fertilizer \- I.E. not just nitrogen but all nutrients?

JUNE 7th \- Done with Initial Data analysis \+ start prepping for Dr. Smith meeting for nutrient experiment stuff. Ordering/deadlines? USE THE MOTHER\!

\*\*\* collection \<- aov(formula \= p.h.\_collection \~ Sex \+ (1 \| Mother), data \= updated\_data)  
Error in 1 \| Mother :   
  operations are possible only for numeric, logical or complex types

R version 4.4.0 (2024-04-24 ucrt) \-- "Puppy Cup"  
Copyright (C) 2024 The R Foundation for Statistical Computing  
Platform: x86\_64-w64-mingw32/x64

R is free software and comes with ABSOLUTELY NO WARRANTY.  
You are welcome to redistribute it under certain conditions.  
Type 'license()' or 'licence()' for distribution details.

R is a collaborative project with many contributors.  
Type 'contributors()' for more information and  
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or  
'help.start()' for an HTML browser interface to help.  
Type 'q()' to quit R.

\[Workspace loaded from \~/.RData\]

\> lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|mother) \+ germTime \+ Sex\*germTime, data \= updated\_data)  
Error in lmer(number\_axils\_with\_flowers \~ Sex \+ (1 \| mother) \+ germTime \+  :   
  could not find function "lmer"  
In addition: Warning messages:  
1: In class(object) \<- "environment" :  
  Setting class(x) to "environment" sets attribute to NULL; result will no longer be an S4 object  
2: In class(object) \<- "environment" :  
  Setting class(x) to "environment" sets attribute to NULL; result will no longer be an S4 object  
3: In class(object) \<- "environment" :  
  Setting class(x) to "environment" sets attribute to NULL; result will no longer be an S4 object  
4: In class(object) \<- "environment" :  
  Setting class(x) to "environment" sets attribute to NULL; result will no longer be an S4 object  
5: In class(object) \<- "environment" :  
  Setting class(x) to "environment" sets attribute to NULL; result will no longer be an S4 object  
6: In class(object) \<- "environment" :  
  Setting class(x) to "environment" sets attribute to NULL; result will no longer be an S4 object  
7: In class(object) \<- "environment" :  
  Setting class(x) to "environment" sets attribute to NULL; result will no longer be an S4 object  
8: In class(object) \<- "environment" :  
  Setting class(x) to "environment" sets attribute to NULL; result will no longer be an S4 object  
\> library(lme4)  
Loading required package: Matrix  
\> library(lmerTest)

Attaching package: ‘lmerTest’

The following object is masked from ‘package:lme4’:

    lmer

The following object is masked from ‘package:stats’:

    step

\> lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|mother) \+ germTime \+ Sex\*germTime, data \= updated\_data)  
Error in eval(predvars, data, env) : object 'mother' not found  
\> lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|Mother) \+ germTime \+ Sex\*germTime, data \= updated\_data)  
Error in eval(predvars, data, env) : object 'germTime' not found  
\> lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|Mother) \+ germination\_date \+ Sex\*germination\_date, data \= updated\_data)  
boundary (singular) fit: see help('isSingular')  
Linear mixed model fit by REML \['lmerModLmerTest'\]  
Formula: number\_axils\_with\_flowers \~ Sex \+ (1 \| Mother) \+ germination\_date \+      Sex \* germination\_date  
   Data: updated\_data  
REML criterion at convergence: 567.0509  
Random effects:  
 Groups   Name        Std.Dev.  
 Mother   (Intercept) 0.000     
 Residual             1.905     
Number of obs: 136, groups:  Mother, 15  
Fixed Effects:  
          (Intercept)                   SexM       germination\_date  SexM:germination\_date    
             19.19747               \-7.65863               \-0.16044                0.05088    
optimizer (nloptwrap) convergence code: 0 (OK) ; 0 optimizer warnings; 1 lme4 warnings   
\> library(lmerTest)  
\> lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|Mother) \+ germination\_date \+ Sex\*germination\_date, data \= updated\_data)  
boundary (singular) fit: see help('isSingular')  
Linear mixed model fit by REML \['lmerModLmerTest'\]  
Formula: number\_axils\_with\_flowers \~ Sex \+ (1 \| Mother) \+ germination\_date \+      Sex \* germination\_date  
   Data: updated\_data  
REML criterion at convergence: 567.0509  
Random effects:  
 Groups   Name        Std.Dev.  
 Mother   (Intercept) 0.000     
 Residual             1.905     
Number of obs: 136, groups:  Mother, 15  
Fixed Effects:  
          (Intercept)                   SexM       germination\_date  SexM:germination\_date    
             19.19747               \-7.65863               \-0.16044                0.05088    
optimizer (nloptwrap) convergence code: 0 (OK) ; 0 optimizer warnings; 1 lme4 warnings   
\> print(lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|Mother) \+ germination\_date \+ Sex\*germination\_date, data \= updated\_data))  
boundary (singular) fit: see help('isSingular')  
Linear mixed model fit by REML \['lmerModLmerTest'\]  
Formula: number\_axils\_with\_flowers \~ Sex \+ (1 \| Mother) \+ germination\_date \+      Sex \* germination\_date  
   Data: updated\_data  
REML criterion at convergence: 567.0509  
Random effects:  
 Groups   Name        Std.Dev.  
 Mother   (Intercept) 0.000     
 Residual             1.905     
Number of obs: 136, groups:  Mother, 15  
Fixed Effects:  
          (Intercept)                   SexM       germination\_date  SexM:germination\_date    
             19.19747               \-7.65863               \-0.16044                0.05088    
optimizer (nloptwrap) convergence code: 0 (OK) ; 0 optimizer warnings; 1 lme4 warnings   
\> summary(SLA)  
             Df Sum Sq Mean Sq F value Pr(\>F)  
Sex           1    129   128.8   0.049  0.824  
Residuals   134 349275  2606.5                 
\> library(emmeans)  
Welcome to emmeans.  
Caution: You lose important information if you filter this package's results.  
See '? untidy'  
\> emmeans(lmer(plant\_height \~ Sex \+ (1 \| Mother), data \= new\_data))  
Error in emmeans(lmer(plant\_height \~ Sex \+ (1 \| Mother), data \= new\_data)) :   
  argument "specs" is missing, with no default  
\>   
\> emmeans(plant\_height \~ Sex \+ (1 \| Mother), data \= new\_data)  
Error in (function (object, at, cov.reduce \= mean, cov.keep \= get\_emm\_option("cov.keep"),  :   
  Can't handle an object of class  “formula”   
 Use help("models", package \= "emmeans") for information on supported models.  
\> aov(formula \= new\_dry\_inflor\_mass \~ Sex, data \= updated\_data)  
Call:  
   aov(formula \= new\_dry\_inflor\_mass \~ Sex, data \= updated\_data)

Terms:  
                        Sex   Residuals  
Sum of Squares  0.000052514 0.008179986  
Deg. of Freedom           1         134

Residual standard error: 0.007813109  
Estimated effects may be unbalanced  
\> inflor\_mass \<- aov(formula \= new\_dry\_inflor\_mass \~ Sex, data \= updated\_data)  
\> summary(inflor\_mass)  
             Df   Sum Sq   Mean Sq F value Pr(\>F)  
Sex           1 0.000053 5.251e-05    0.86  0.355  
Residuals   134 0.008180 6.104e-05                 
\> aov(formula \= new\_dry\_above\_veg \~ Sex, data \= updated\_data)  
Call:  
   aov(formula \= new\_dry\_above\_veg \~ Sex, data \= updated\_data)

Terms:  
                       Sex  Residuals  
Sum of Squares  0.00006643 0.29200586  
Deg. of Freedom          1        134

Residual standard error: 0.04668135  
Estimated effects may be unbalanced  
\> summary(aov(formula \= new\_dry\_above\_veg \~ Sex, data \= updated\_data)  
\+   
\+ as  
Error: unexpected symbol in:  
"  
as"  
\> summary(aov(formula \= new\_dry\_above\_veg \~ Sex, data \= updated\_data))  
             Df  Sum Sq   Mean Sq F value Pr(\>F)  
Sex           1 0.00007 0.0000664    0.03  0.862  
Residuals   134 0.29201 0.0021791                 
\> roots \<- aov(formula \= new\_dry\_roots \~ Sex, data \= updated\_data)  
\>   
\> summary(roots)  
             Df   Sum Sq   Mean Sq F value Pr(\>F)  
Sex           1 0.000003 3.240e-06   0.024  0.877  
Residuals   134 0.018058 1.348e-04                 
\> plot(dry\_above\_veg\_mass..g., new\_dry\_aboe\_veg, pch \= 19, col \= "black")  
Error: object 'dry\_above\_veg\_mass..g.' not found  
\> plot(dry\_above\_veg\_mass..g., new\_dry\_above\_veg, pch \= 19, col \= "black")  
Error: object 'dry\_above\_veg\_mass..g.' not found  
\> plot(dry\_above\_veg\_mass..g., new\_dry\_aboe\_veg, pch \= 19, col \= "black", data \= updated\_data)  
Error: object 'dry\_above\_veg\_mass..g.' not found  
\> plot(dry\_above\_veg\_mass..g., new\_dry\_above\_veg, pch \= 19, col \= "black", data \= updated\_data)  
Error: object 'dry\_above\_veg\_mass..g.' not found  
\> plot(dry\_above\_veg\_mass..g., new\_dry\_above\_veg, pch \= 19, col \= "black", data \= updated\_data)  
Error: object 'dry\_above\_veg\_mass..g.' not found  
\> plot(new\_dry\_above\_veg \~ dry\_above\_veg\_mass..g., pch \= 19, col \= "black", data \= updated\_data)  
\> plot(dry\_above\_veg\_mass..g., germination\_date, pch \= 19, col \= "black", data \= updated\_data)  
Error: object 'dry\_above\_veg\_mass..g.' not found  
\> plot(new\_dry\_above\_veg \~ germination\_date, pch \= 19, col \= "black", data \= updated\_data)  
\> plot(dry\_above\_veg\_mass \~ germination\_date, pch \= 19, col \= "black", data \= updated\_data)  
Error in eval(predvars, data, env) :   
  object 'dry\_above\_veg\_mass' not found  
\> plot(dry\_above\_veg\_mass..g. \~ germination\_date, pch \= 19, col \= "black", data \= updated\_data)  
\> plot(new\_dry\_above\_veg \~ germination\_date, pch \= 19, col \= "black", data \= updated\_data)  
\> plot(dry\_inflor\_mass..g. \~ germination\_date, pch \= 19, col \= "black", data \= updated\_data)  
\> abline(lm(dry\_inflor\_mass..g. \~ germination\_date, data \= updated\_data), col \= "blue")  
\> lm(dry\_inflor\_mass..g. \~ germination\_date, data \= updated\_data)

Call:  
lm(formula \= dry\_inflor\_mass..g. \~ germination\_date, data \= updated\_data)

Coefficients:  
     (Intercept)  germination\_date    
        0.156142         \-0.001499  

\> summary(lm(dry\_inflor\_mass..g. \~ germination\_date, data \= updated\_data))

Call:  
lm(formula \= dry\_inflor\_mass..g. \~ germination\_date, data \= updated\_data)

Residuals:  
      Min        1Q    Median        3Q       Max   
\-0.055679 \-0.023079 \-0.005234  0.014119  0.102916 

Coefficients:  
                   Estimate Std. Error t value Pr(\>\|t\|)      
(Intercept)       0.1561419  0.0378988   4.120  6.6e-05 \*\*\*  
germination\_date \-0.0014993  0.0006957  \-2.155    0.033 \*    
\---  
Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.03181 on 134 degrees of freedom  
Multiple R-squared:  0.03349,	Adjusted R-squared:  0.02628   
F-statistic: 4.644 on 1 and 134 DF,  p-value: 0.03296

\> lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|Mother) \+ germination\_date)  
Error in eval(predvars, data, env) :   
  object 'number\_axils\_with\_flowers' not found  
\> lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|Mother) \+ germination\_date, data \= updated\_data)  
boundary (singular) fit: see help('isSingular')  
Linear mixed model fit by REML \['lmerModLmerTest'\]  
Formula: number\_axils\_with\_flowers \~ Sex \+ (1 \| Mother) \+ germination\_date  
   Data: updated\_data  
REML criterion at convergence: 564.3151  
Random effects:  
 Groups   Name        Std.Dev.  
 Mother   (Intercept) 0.0       
 Residual             1.9       
Number of obs: 136, groups:  Mother, 15  
Fixed Effects:  
     (Intercept)              SexM  germination\_date    
         17.5747           \-4.8980           \-0.1304    
optimizer (nloptwrap) convergence code: 0 (OK) ; 0 optimizer warnings; 1 lme4 warnings   
\> summary(lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|Mother) \+ germination\_date, data \= updated\_data))  
boundary (singular) fit: see help('isSingular')  
Linear mixed model fit by REML. t-tests use Satterthwaite's method \['lmerModLmerTest'\]  
Formula: number\_axils\_with\_flowers \~ Sex \+ (1 \| Mother) \+ germination\_date  
   Data: updated\_data

REML criterion at convergence: 564.3

Scaled residuals:   
     Min       1Q   Median       3Q      Max   
\-2.63705 \-0.62017 \-0.06729  0.71811  2.09081 

Random effects:  
 Groups   Name        Variance Std.Dev.  
 Mother   (Intercept) 0.000    0.0       
 Residual             3.612    1.9       
Number of obs: 136, groups:  Mother, 15

Fixed effects:  
                  Estimate Std. Error        df t value Pr(\>\|t\|)      
(Intercept)       17.57468    2.26442 133.00000   7.761 1.98e-12 \*\*\*  
SexM              \-4.89805    0.32744 133.00000 \-14.959  \< 2e-16 \*\*\*  
germination\_date  \-0.13040    0.04169 133.00000  \-3.128  0.00216 \*\*   
\---  
Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Correlation of Fixed Effects:  
            (Intr) SexM    
SexM        \-0.001         
germintn\_dt \-0.994 \-0.076  
optimizer (nloptwrap) convergence code: 0 (OK)  
boundary (singular) fit: see help('isSingular')

\> summary(lmer(flower\_density\_inflorescence \~ Sex \+ (1\|Mother) \+ germination\_date, data \= updated\_data))  
Error in h(simpleError(msg, call)) :   
  error in evaluating the argument 'object' in selecting a method for function 'summary': object 'flower\_density\_inflorescence' not found  
\> summary(lmer(flower\_density\_inflorescence..flowers.2.cm.2. \~ Sex \+ (1\|Mother) \+ germination\_date, data \= updated\_data))  
Linear mixed model fit by REML. t-tests use Satterthwaite's method \['lmerModLmerTest'\]  
Formula: flower\_density\_inflorescence..flowers.2.cm.2. \~ Sex \+ (1 \| Mother) \+      germination\_date  
   Data: updated\_data

REML criterion at convergence: 606.6

Scaled residuals:   
     Min       1Q   Median       3Q      Max   
\-1.78957 \-0.78306  0.02112  0.66135  2.79276 

Random effects:  
 Groups   Name        Variance Std.Dev.  
 Mother   (Intercept) 0.09817  0.3133    
 Residual             4.88123  2.2094    
Number of obs: 136, groups:  Mother, 15

Fixed effects:  
                  Estimate Std. Error        df t value Pr(\>\|t\|)    
(Intercept)        0.69046    2.66276 132.25056   0.259   0.7958    
SexM               0.32402    0.38254 129.92762   0.847   0.3985    
germination\_date   0.12268    0.04898 132.73715   2.505   0.0135 \*  
\---  
Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Correlation of Fixed Effects:  
            (Intr) SexM    
SexM        \-0.003         
germintn\_dt \-0.994 \-0.073  
\> summary(lmer(flower\_density\_inflorescence..flowers.2.cm.2. \~ Sex \+ (1\|Mother), data \= updated\_data))  
Linear mixed model fit by REML. t-tests use Satterthwaite's method \['lmerModLmerTest'\]  
Formula: flower\_density\_inflorescence..flowers.2.cm.2. \~ Sex \+ (1 \| Mother)  
   Data: updated\_data

REML criterion at convergence: 608.6

Scaled residuals:   
     Min       1Q   Median       3Q      Max   
\-1.70916 \-0.72243  0.01785  0.63636  2.66763 

Random effects:  
 Groups   Name        Variance Std.Dev.  
 Mother   (Intercept) 0.1255   0.3542    
 Residual             5.0548   2.2483    
Number of obs: 136, groups:  Mother, 15

Fixed effects:  
            Estimate Std. Error       df t value Pr(\>\|t\|)      
(Intercept)   7.3181     0.2977  38.8152  24.584   \<2e-16 \*\*\*  
SexM          0.3971     0.3886 130.9148   1.022    0.309      
\---  
Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Correlation of Fixed Effects:  
     (Intr)  
SexM \-0.689  
\> plot(flower\_density\_inflorescence..flowers.2.cm.2. \~ germination\_date, pch \= 19, col \= "black", data \= updated\_data)  
\> lm(flower\_density\_inflorescence..flowers.2.cm.2. \~ germination\_date, data \= updated\_data)

Call:  
lm(formula \= flower\_density\_inflorescence..flowers.2.cm.2. \~   
    germination\_date, data \= updated\_data)

Coefficients:  
     (Intercept)  germination\_date    
          0.6623            0.1264  

\> summary(lm(flower\_density\_inflorescence..flowers.2.cm.2. \~ germination\_date, data \= updated\_data))

Call:  
lm(formula \= flower\_density\_inflorescence..flowers.2.cm.2. \~   
    germination\_date, data \= updated\_data)

Residuals:  
    Min      1Q  Median      3Q     Max   
\-3.8668 \-1.7692  0.0124  1.4492  6.5124 

Coefficients:  
                 Estimate Std. Error t value Pr(\>\|t\|)    
(Intercept)       0.66234    2.65328   0.250   0.8033    
germination\_date  0.12639    0.04871   2.595   0.0105 \*  
\---  
Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 2.227 on 134 degrees of freedom  
Multiple R-squared:  0.04785,	Adjusted R-squared:  0.04074   
F-statistic: 6.733 on 1 and 134 DF,  p-value: 0.01052

Final\_Data \<- read.csv("C:/Users/Ocean/Downloads/Fin\_Data.csv")

\*NEW\*

full\_model \<- lmer(number\_axils\_with\_flowers \~ Sex \+ Treatment \+ Treatment\*Sex \+ (1\|mother) \+ germTime)

plots for each treatment \- treatment by sex? use mother as a random factor. 

\*Treatment by sex interaction \- direct effect of sex. 

No treatment by sex interaction in nature? Since 0% may not be all too common in normal circumstances. Consider philosophy of throwing out outliers \- probably won’t. 

Revisit driving hypotheses in the project. Sexual dimorphisms? Consider reasonings for potential 

Intro \+ Methods/Results by the end of Fall. Have tentative timeline by next meeting\!

RNotebook?

1) Final\_Data\$initial\_inflor\_date \<- as.numeric(as.character(Final\_Data\$initial\_inflor\_date))  
     
   infloresence\_date \<- aov(formula \= initial\_inflor\_date \~ Sex, data \= Final\_Data)  
   

summary(infloresence\_date) p-value \= 0.691

\*\*\* full\_model \<- lmer(initial\_inflor\_date \~ Sex \+ Treatment \+ Sex\*Treatment \+ (1\|Mother) \+ X..Days.growing, data \= Final\_Data, na.action \= na.omit)  
fixed-effect model matrix is rank deficient so dropping 1 column / coefficient  
Type III Analysis of Variance Table with Satterthwaite's method  
                Sum Sq Mean Sq NumDF  DenDF  F value  Pr(\>F)      
Sex                2.7     2.7     1 356.63   0.1602 0.68921      
Treatment        197.8    49.5     4 355.81   2.9181 0.02133 \*    
X..Days.growing 4785.0  4785.0     1 356.50 282.3320 \< 2e-16 \*\*\*  
Sex:Treatment     12.3     4.1     3 357.76   0.2412 0.86757      
\---  
Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1

2) germ \<- aov(formula \= germination\_date \~ Sex, data \= Final\_Data)  
     
   summary(germ) p-value \= 0.817 \*\*\* crit error \- Warning messages:  
   1: In checkConv(attr(opt, "derivs"), opt\$par, ctrl \= control\$checkConv,  :  
     Model failed to converge with max\|grad\| \= 11.7968 (tol \= 0.002, component 1\)  
   2: In checkConv(attr(opt, "derivs"), opt\$par, ctrl \= control\$checkConv,  :  
     Model is nearly unidentifiable: very large eigenvalue  
    \- Rescale variables?  
 


3) height1 \<- aov(formula \= plant\_height\_initial \~ Sex, data \= Final\_Data)  
   summary(height1) p-value \= 0.0238  
   Type III Analysis of Variance Table with Satterthwaite's method  
                   Sum Sq Mean Sq NumDF  DenDF  F value  Pr(\>F)      
   Sex               3512    3512     1 449.09   5.1084 0.02429 \*    
   Treatment       539208  134802     4 448.68 196.0757 \< 2e-16 \*\*\*  
   X..Days.growing    862     862     1 450.60   1.2545 0.26329      
   Sex:Treatment     3374     843     4 450.26   1.2268 0.29861      
   \---  
   Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
     
     
4) height2 \<- aov(formula \= p.h.\_month \~ Sex, data \= Final\_Data)  
     
   summary(height2) p-value \= 0.00139  
   Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF DenDF   F value    Pr(\>F)      
   Sex              251726  251726     1   451  236.4948 \< 2.2e-16 \*\*\*  
   Treatment       4457150 1114287     4   451 1046.8630 \< 2.2e-16 \*\*\*  
   X..Days.growing      93      93     1   451    0.0873    0.7678      
   Sex:Treatment     51984   12996     4   451   12.2096 1.964e-09 \*\*\*  
     
     
5) height3 \<- aov(formula \= p.h.\_collection \~ Sex, data \= Final\_Data)  
     
   summary(height3) p-value \= 0.196  
   Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF DenDF   F value Pr(\>F)      
   Sex                  12      12     1   451    0.0173 0.8955      
   Treatment       7165679 1791420     4   451 2526.9309 \<2e-16 \*\*\*  
   X..Days.growing      14      14     1   451    0.0192 0.8898      
   Sex:Treatment      4250    1062     4   451    1.4987 0.2015  
     
     
6) Final\_Data\$inflor\_length \<- as.numeric(as.character(Final\_Data\$inflor\_length))  
     
   inflor\_length \<- aov(formula \= inflor\_length \~ Sex, data \= Final\_Data)  
     
   summary(inflor\_length) p-value \= 0.188  
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                   Sum Sq Mean Sq NumDF DenDF F value  Pr(\>F)    
   Sex             1112.3 1112.33     1   358  1.3286 0.24983    
   Treatment       8485.1 2121.28     4   358  2.5337 0.04006 \*  
   X..Days.growing  317.4  317.37     1   358  0.3791 0.53849    
   Sex:Treatment    437.3  145.77     3   358  0.1741 0.91388   
     
   fixed-effect model matrix is rank deficient so dropping 1 column / coefficient  
   boundary (singular) fit: see help('isSingular')  
     
7) Final\_Data\$flowering\_date \<- as.numeric(as.character(Final\_Data\$flowering\_date))

	flowering \<- aov(formula \= flowering\_date \~ Sex, data \= Final\_Data)

	summary(flowering) p-value \= 0.67

Type III Analysis of Variance Table with Satterthwaite's method  
                 Sum Sq Mean Sq NumDF DenDF F value  Pr(\>F)    
Sex               9.625   9.625     1   358  0.3203 0.57176    
Treatment        40.835  10.209     4   358  0.3398 0.85107    
X..Days.growing 182.524 182.524     1   358  6.0747 0.01418 \*  
Sex:Treatment    31.681  10.560     3   358  0.3515 0.78811    
\---  
Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1

8) leaf\_area \<- aov(formula \= leaf\_area..cm.2. \~ Sex, data \= Final\_Data)  
     
   summary(leaf\_area) p-value \= 3.7 x 10^-6   
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF  DenDF  F value    Pr(\>F)      
   Sex               83.62   83.62     1 449.35  50.1186 5.605e-12 \*\*\*  
   Treatment       1780.84  445.21     4 448.90 266.8501 \< 2.2e-16 \*\*\*  
   X..Days.growing    2.37    2.37     1 450.80   1.4201  0.234011      
   Sex:Treatment     23.67    5.92     4 450.16   3.5469  0.007296 \*\*   
   \---  
   Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
     
     
9) leaf\_mass \<- aov(formula \= dry\_leaf\_mass..g. \~ Sex, data \= Final\_Data)  
     
   summary(leaf\_mass) p-value \= 2 x 10^-16  
     
   boundary (singular) fit: see help('isSingular')  
     
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                      Sum Sq   Mean Sq NumDF DenDF  F value    Pr(\>F)      
   Sex             0.0077350 0.0077350     1   451 272.9001 \< 2.2e-16 \*\*\*  
   Treatment       0.0089316 0.0022329     4   451  78.7796 \< 2.2e-16 \*\*\*  
   X..Days.growing 0.0000048 0.0000048     1   451   0.1698 0.6805281      
   Sex:Treatment   0.0005560 0.0001390     4   451   4.9044 0.0007034 \*\*\*  
   \---  
   Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
     
10) Final\_Data\$dry\_inflor\_mass..g. \<- as.numeric(as.character(Final\_Data\$dry\_inflor\_mass..g.))  
      
    inflor\_mass \<- aov(formula \= dry\_inflor\_mass..g. \~ Sex, data \= Final\_Data)  
      
    summary(inflor\_mass) p-value \= 0.00468  
      
    fixed-effect model matrix is rank deficient so dropping 1 column / coefficient  
      
    Type III Analysis of Variance Table with Satterthwaite's method  
                      Sum Sq   Mean Sq NumDF  DenDF F value    Pr(\>F)      
    Sex             0.008979 0.0089787     1 356.67  7.7907  0.005534 \*\*   
    Treatment       0.039782 0.0099455     4 355.62  8.6295 1.175e-06 \*\*\*  
    X..Days.growing 0.000512 0.0005125     1 356.51  0.4447  0.505303      
    Sex:Treatment   0.002067 0.0006890     3 357.87  0.5978  0.616780      
    \---  
    Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
      
11) above\_veg\_mass \<- aov(formula \= dry\_above\_veg\_mass..g. \~ Sex, data \= Final\_Data)  
      
    summary(above\_veg\_mass) p-value \= 2.76e-06  
      
    Type III Analysis of Variance Table with Satterthwaite's method  
                     Sum Sq Mean Sq NumDF  DenDF  F value    Pr(\>F)      
    Sex              0.7976 0.79761     1 448.98  32.7426 1.925e-08 \*\*\*  
    Treatment       12.4891 3.12227     4 448.70 128.1728 \< 2.2e-16 \*\*\*  
    X..Days.growing  0.0051 0.00510     1 450.20   0.2093   0.64751      
    Sex:Treatment    0.2810 0.07025     4 450.33   2.8840   0.02227 \*    
    \---  
    Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
      
      
12) roots \<- aov(formula \= dry\_roots..g. \~ Sex, data \= Final\_Data)  
      
    summary(roots) p-value \= 8.31e-10  
      
    Type III Analysis of Variance Table with Satterthwaite's method  
                     Sum Sq Mean Sq NumDF  DenDF F value    Pr(\>F)      
    Sex             0.31105 0.31105     1 449.11 52.0377 2.332e-12 \*\*\*  
    Treatment       1.81470 0.45368     4 448.77 75.8987 \< 2.2e-16 \*\*\*  
    X..Days.growing 0.00887 0.00887     1 450.47  1.4832   0.22391      
    Sex:Treatment   0.07385 0.01846     4 450.35  3.0887   0.01582 \*    
    \---  
    Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
      
13) Final\_Data\$flower\_density\_inflorescence..flowers.2.cm.2. \<- as.numeric(as.character(Final\_Data\$flower\_density\_inflorescence..flowers.2.cm.2.))  
      
    flower\_density \<- aov(formula \= flower\_density\_inflorescence..flowers.2.cm.2. \~ Sex, data \= Final\_Data)  
      
    summary(flower\_density) p-value \= 0.899  
      
    boundary (singular) fit: see help('isSingular')  
      
    Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF DenDF F value  Pr(\>F)    
    Sex              0.166  0.1657     1   358  0.0161 0.89909    
    Treatment       79.029 26.3431     3   358  2.5600 0.05481 .  
    X..Days.growing  7.287  7.2867     1   358  0.7081 0.40063    
    Sex:Treatment   82.671 27.5570     3   358  2.6780 0.04693 \*  
    \---  
    Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
      
    \*\*\* for some treatments, there is a difference but for others there is not.   
      
14) Final\_Data\$number\_axils\_with\_flowers \<- as.numeric(as.character(Final\_Data\$number\_axils\_with\_flowers))  
      
    axil\_flowers \<- aov(formula \= number\_axils\_with\_flowers \~ Sex, data \= Final\_Data)  
      
    summary(axil\_flowers) p-value \= 0.946  
      
    boundary (singular) fit: see help('isSingular')  
      
    Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF DenDF F value Pr(\>F)  
    Sex              0.048  0.0479     1   358  0.0034 0.9537  
    Treatment       30.914 10.3048     3   358  0.7265 0.5367  
    X..Days.growing  3.887  3.8874     1   358  0.2741 0.6009  
    Sex:Treatment   43.541 14.5135     3   358  1.0233 0.3823  
      
15) SLA \<- aov(formula \= specific\_leaf\_area..cm.2...g. \~ Sex, data \= Final\_Data)  
      
    summary(SLA) p-value \= \<2 x 10^-16  
      
    Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF  DenDF  F value  Pr(\>F)      
    Sex             230023  230023     1 448.90 166.7468 \< 2e-16 \*\*\*  
    Treatment       436737  109184     4 448.65  79.1490 \< 2e-16 \*\*\*  
    X..Days.growing     50      50     1 450.06   0.0363 0.84892      
    Sex:Treatment    11488    2872     4 450.27   2.0819 0.08218 .   
      
      
16) Phi2 \<- aov(formula \= Phi.2 \~ Sex, data \= Final\_Data)

	summary(Phi2) p-value \= 0.207

Type III Analysis of Variance Table with Satterthwaite's method  
                  Sum Sq  Mean Sq NumDF  DenDF F value Pr(\>F)  
Sex             0.055951 0.055951     1 449.35  1.7979 0.1806  
Treatment       0.138237 0.034559     4 448.92  1.1105 0.3509  
X..Days.growing 0.001992 0.001992     1 450.79  0.0640 0.8004  
Sex:Treatment   0.071351 0.017838     4 450.17  0.5732 0.6822

17) Growth\_Days \<- aov(formula \= X..Days.growing \~ Sex, data \= Final\_Data)  
      
    summary(Growth\_Days) p-value \= 0.817  
      
18) new\_leaf\_mass \<- aov(formula \= new\_dry\_leaf\_mass \~ Sex, data \= Final\_Data)  
      
    summary(new\_leaf\_mass) p-value \= 0.00116  
      
    Type III Analysis of Variance Table with Satterthwaite's method  
                       Sum Sq   Mean Sq NumDF  DenDF  F value    Pr(\>F)      
    Sex             0.0005850 0.0005850     1 448.98  20.6569 7.073e-06 \*\*\*  
    Treatment       0.0000998 0.0000250     4 448.66   0.8814    0.4749      
    X..Days.growing 0.0085444 0.0085444     1 450.31 301.7306 \< 2.2e-16 \*\*\*  
    Sex:Treatment   0.0001882 0.0000470     4 450.33   1.6611    0.1580      
    \---  
    Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
      
19) Final\_Data\$new\_dry\_inflor\_mass \<- as.numeric(as.character(Final\_Data\$new\_dry\_inflor\_mass))  
      
    new\_inflor\_mass \<- aov(formula \= new\_dry\_inflor\_mass \~ Sex, data \= Final\_Data)  
      
    summary(new\_inflor\_mass) p-value \= 0.781  
      
    fixed-effect model matrix is rank deficient so dropping 1 column / coefficient  
      
    Type III Analysis of Variance Table with Satterthwaite's method  
                      Sum Sq  Mean Sq NumDF  DenDF  F value Pr(\>F)      
    Sex             0.000162 0.000162     1 355.90   0.2870 0.5925      
    Treatment       0.003865 0.000966     4 355.41   1.7141 0.1463      
    X..Days.growing 0.142721 0.142721     1 355.81 253.1812 \<2e-16 \*\*\*  
    Sex:Treatment   0.001764 0.000588     3 356.93   1.0431 0.3735      
    \---  
    Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
      
20) new\_above\_veg\_mass \<- aov(formula \= new\_dry\_above\_veg \~ Sex, data \= Final\_Data)  
      
    summary(new\_above\_veg\_mass) p-value \= 0.0674  
      
    Type III Analysis of Variance Table with Satterthwaite's method  
                     Sum Sq Mean Sq NumDF  DenDF  F value    Pr(\>F)      
    Sex             0.06594 0.06594     1 448.75   4.9800   0.02614 \*    
    Treatment       0.55489 0.13872     4 448.53  10.4762  4.03e-08 \*\*\*  
    X..Days.growing 2.71986 2.71986     1 449.82 205.4012 \< 2.2e-16 \*\*\*  
    Sex:Treatment   0.10967 0.02742     4 450.13   2.0705   0.08368 .    
    \---  
    Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
      
21) new\_roots \<- aov(formula \= new\_dry\_roots \~ Sex, data \= Final\_Data)  
      
    summary(new\_roots) p-value \= 0.0125   
      
    full\_model \<- lmer(new\_dry\_roots \~ Sex \* Treatment \+ (1\|Mother) \+ X..Days.growing, data \= Final\_Data, na.action \= na.omit)  
      
    summary(full\_model)  
  


    Type III Analysis of Variance Table with Satterthwaite's method

                     Sum Sq Mean Sq NumDF  DenDF  F value    Pr(\>F)    

    Sex             0.02505 0.02505     1 449.07   9.0025 0.0028462 \*\* 

    Treatment       0.05240 0.01310     4 448.70   4.7068 0.0009923 \*\*\*

    X..Days.growing 0.42061 0.42061     1 450.50 151.1365 \< 2.2e-16 \*\*\*

    Sex:Treatment   0.02211 0.00553     4 450.32   1.9863 0.0955693 .  

    \---

    Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1

  


1) Final\_Data\$number\_axils\_with\_flowers \<- as.numeric(as.character(Final\_Data\$number\_axils\_with\_flowers))  
     
   full\_model \<- lmer(number\_axils\_with\_flowers \~ Sex \+ Treatment \+ Treatment\*Sex \+ (1\|Mother) \+ X..Days.growing, data \= Final\_Data, na.action \= na.omit)  
   

\*\*\*New ones \- library(lme4)  
library(emmeans)

full\_model \<- lmer(number\_axils\_with\_flowers \~ Sex \+ Treatment \+ Treatment\*Sex \+ (1\|Mother) \+ X..Days.growing, data \= Final\_Data, na.action \= na.omit)

emm \<- emmeans(full\_model, \~ Treatment \* Sex)

tukey\_result \<- pairs(emm, adjust \= "tukey")

summary(tukey\_result)

pairwise tukeys test of 25% to 50%, 50% to 75%, etc. tukeys test for sex by treatment interaction, only for significant ones. fig. 3, M & F responding to the treatments the same (b/c statistics \- sex by treatment \= 0.2015). Substitute x-axis from treatment to nutrient concentrations. refer to Hesse & Pannell \- maybe make a similar figure with the logs \- or use the ratio of inflorescence mass / vegetative mass. reorganize discussion in theoretical aspect? build discussion around bateman, charnov and third paper emphasizing bateman's observations in plants.

install.packages("emmeans")  
library(emmeans)  
emmeans(full\_model, \~ Sex \| Treatment)  
pairs(emmeans(full\_model, \~ Sex \| Treatment))

For the % means between each sex for each treatment,   
library(lme4)  
library(emmeans)  
library(dplyr)  
Do full model above  
emm \<- emmeans(full\_model, \~ Sex \| Treatment)  
emm\_df \<- as.data.frame(emm)  
print(emm\_df)

summary(full\_model)  
Linear mixed model fit by REML \['lmerMod'\]  
Formula:   
number\_axils\_with\_flowers \~ Sex \+ Treatment \+ Treatment \* Sex \+    
    (1 \| Mother) \+ X..Days.growing  
   Data: Final\_Data

REML criterion at convergence: 2004.7

Scaled residuals:   
     Min       1Q   Median       3Q      Max   
\-1.83069 \-0.82830  0.01043  0.79033  1.85815 

Random effects:  
 Groups   Name        Variance Std.Dev.  
 Mother   (Intercept)  0.00    0.000     
 Residual             14.18    3.766     
Number of obs: 367, groups:  Mother, 4

Fixed effects:  
                  Estimate Std. Error t value  
(Intercept)        7.63639    0.61832  12.350  
SexM               0.46766    0.79800   0.586  
Treatment25%       0.45181    0.77334   0.584  
Treatment50%       0.29861    0.75056   0.398  
Treatment75%       0.50719    0.78433   0.647  
X..Days.growing    0.02571    0.04912   0.524  
SexM:Treatment25%  0.08153    1.11603   0.073  
SexM:Treatment50% \-0.38332    1.11266  \-0.345  
SexM:Treatment75% \-1.66062    1.12958  \-1.470

Correlation of Fixed Effects:  
            (Intr) SexM   Trt25% Trt50% Trt75% X..Dy. SM:T25 SM:T50  
SexM        \-0.610                                                   
Treatmnt25% \-0.616  0.470                                            
Treatmnt50% \-0.646  0.485  0.500                                     
Treatmnt75% \-0.633  0.466  0.479  0.495                              
X..Dys.grwn \-0.493  0.047  0.021  0.045  0.074                       
SxM:Trtm25%  0.417 \-0.713 \-0.693 \-0.345 \-0.330  0.005                
SxM:Trtm50%  0.419 \-0.715 \-0.336 \-0.673 \-0.331  0.004  0.512         
SxM:Trtm75%  0.438 \-0.707 \-0.332 \-0.344 \-0.694 \-0.049  0.504  0.505  
optimizer (nloptwrap) convergence code: 0 (OK)  
boundary (singular) fit: see help('isSingular')

TimeLine \- Try to Finish Data Analysis by Halloween. 

Feb. 7 \- Last day for graduate degree candidates to file with the Graduate School an application to graduate.

Feb. 12 \- *(or at least 3 weeks prior to your defense date)* is the last day for Doctoral & Masters students to have their defense notification form submitted by department via Enrollment Services Portal.

March. 28 \- Last day for graduate degree candidates to defend theses/dissertations.

April 4th \- last day to submit a final, committee-approved copy of your thesis or dissertation for review.A final copy of your thesis or dissertation must be submitted in PDF format to the ETD web site within ***two weeks of your defense or no later than the posted date***.

Early march option for defense\!

**Univariate Analysis** \- 

library(lmerTest)

full\_model \<- lmer(plant\_height\_initial \~ Sex \+ Treatment \+ Sex\*Treatment \+ (1\|Mother) \+ X..Days.growing, data \= Final\_Data, na.action \= na.omit)

summary(full\_model)

anova(full\_model) 

\*Least squares mean\! Then, ggplot the results and included error bars. 

Multivariate Options \- 

PCA, MANOVA, \- Weight data for PCA? Interaction between covariates and by treatment, sex and covariates by treatment by sex. 

BOnferonni adjustment for Type 1 error. Crit value / \# tests?

\*Graph notes \- Consider removing the grid lines. Make each treatment line be horizontal next to one another (?). Percentage label should be on the x-axis below the graph. \*consider using libraries aside from ggplot. Put the percentages in order (0% \-\> 100%).   
Add standard error bars for each treatment. 

Post-Hoc Tests \- 

1) LSD (Least Significant Difference)  
2) Tukey Test   
* Add stars for potentially significant p-values following the test. (number of stars change depending on degree of significance). \*Add to the figure if you change the \# of stars.  
* Add lines that connect the means between each treatment.   
* \*\*\* When adding error bars, connecting lines etc to a particular variable, can consider dropping off portions if it becomes too crowded. Might be useful to start with as much as possible.

After the plots are generated, put them in a powerpoint for each analysis. 

To obtain the residuals, can save them from the mixed effect model, and put them in a new column. 

Heteroscedasticity  tests \- Consider the inclusiveness or dropping of 0% treatment if it is relevant. 

ggplot(Final\_Data, aes(x \= Sex, y \= p.h.\_month, group \= Sex, color \= Sex)) \+  
    geom\_line() \+  
    geom\_point() \+  
    facet\_wrap(\~ Treatment) \+  
    labs(title \= "p.h.\_month by Sex for Each Treatment",  
         x \= "Sex",  
         y \= "p.h.\_month") \+  
    theme\_minimal()  
 :)

Residual stuff \- full\_model \<- lmer(flowering\_date \~ Sex \+ Treatment \+ Sex\*Treatment \+ (1\|Mother) \+ X..Days.growing, data \= Final\_Data, na.action \= na.omit)

Final\_Data\$residuals \<- residuals(full\_model)

Final\_Data\$residuals \<- as.numeric(Final\_Data\$residuals)

Final\_Data \<- Final\_Data %\>% filter(Treatment \!= "0%")

Final\_Data \<- Final\_Data %\>% filter(\!is.na(residuals))

residuals\_by\_group \<- Final\_Data %\>%  
\+    group\_by(Sex, Treatment) %\>%  
\+    summarise(mean\_residual \= mean(residuals, na.rm \= TRUE))

print(residuals\_by\_group)

Final\_Data \<- Final\_Data %\>%  
\+    left\_join(residuals\_by\_group, by \= c("Sex", "Treatment"))  
ggplot(Final\_Data, aes(x \= Sex, y \= flowering\_date, group \= Sex, color \= Sex)) \+  
\+    geom\_line() \+  
\+    geom\_point() \+  
\+    geom\_errorbar(aes(ymin \= flowering\_date \- residuals, ymax \= flowering\_date \+ residuals), width \= 0.2) \+  
\+    facet\_wrap(\~ Treatment) \+  
\+    labs(title \= "flowering\_date by Sex for Each Treatment",  
\+         x \= "Sex",  
\+         y \= "flowering\_date") \+  
\+    theme\_minimal()

\*\*\* to get the proper plot order, Final\_Data\$Treatment \<- factor(Final\_Data\$Treatment, levels \= c("25%", "50%", "75%", "100%")) \*\*\*

1) summary\_stats \<- Final\_Data %\>%

  group\_by(Sex, Treatment) %\>%  
  summarise(mean\_flowering\_date \= mean(flowering\_date, na.rm \= TRUE),  
            se\_flowering\_date \= sd(flowering\_date, na.rm \= TRUE) / sqrt(n()))

2) Final\_Data \<- Final\_Data %\>%  
     left\_join(summary\_stats, by \= c("Sex", "Treatment"))  
     
3) ggplot(Final\_Data, aes(x \= Sex, y \= flowering\_date, group \= Sex, color \= Sex)) \+  
       geom\_line() \+  
       geom\_point() \+  
       geom\_errorbar(aes(ymin \= mean\_flowering\_date \- se\_flowering\_date, ymax \= mean\_flowering\_date \+ se\_flowering\_date), width \= 0.2) \+  
       facet\_wrap(\~ Treatment) \+  
      labs(title \= "Flowering Date by Sex for Each Treatment",  
          x \= "Sex",  
            y \= "flowering\_date") \+  
       theme\_minimal()  
     
   Check for Standard Error vs. Standard Deviation  
     
   Plot 95% CI / S.E. on the same graph \- i.e. combining all 4 plots for each treatment together to show relationship over time.  
     
   Look at rate of change relationships between the treatments \- i.e., for p.h. Month, it would seem to have the greatest difference at 75% and the least at 25%. 

asas  
Why would females with thicker leaves be more adaptive than males who grow taller quicker?

Make violin plots\! Put significance stars (1, 2 , 3 to show relative significance). And put % treatment values below the M/F

Write results/methods first\! Also, pull up various articles that are similar to the experiment \- sexual allocation in dioecious plants\!

Introduction \- Summarize with other species\! Categorize \- perennials, insect pollinated, silene latifolia, live fast die young life strategies, life history characteristics (herbaceous perennials, wind-pollinated annuals, etc.). Then, discuss allocation strategies of herbaceous perennials vs wind-pollinated annuals, vs other strategies, etc. 

When a paper refers to someone, check their paper (ideally primary source?). 

Why are males not adapting the female’s strategy or taking longer to grow and thicker leaves/vegetative mass allocation, and vice versa? Discuss from both the female and male perspectives\!

New Graphs \- 

full\_model \<- lmer(number\_axils\_with\_flowers \~ Sex \+ Treatment \+ Treatment\*Sex \+ (1\|Mother) \+ X..Days.growing, data \= Final\_Data, na.action \= na.omit)

summary\_data \<- Final\_Data %\>%  
  group\_by(Treatment, Sex) %\>%  
  summarise(  
    mean\_inflor\_ratio \= mean(inflor\_ratio, na.rm \= TRUE),  
    se\_inflor\_ratio \= sd(inflor\_ratio, na.rm \= TRUE) / sqrt(n())  
  ) %\>%  
  mutate(  
    ci\_lower \= mean\_inflor\_ratio \- 1.96 \* se\_inflor\_ratio,  
    ci\_upper \= mean\_inflor\_ratio \+ 1.96 \* se\_inflor\_ratio,  
    Treatment\_Sex \= paste(Treatment, Sex)  
  )

summary\_data\$Treatment \<- factor(summary\_data\$Treatment, levels \= c("25%", "50%", "75%", "100%"))

summary\_data \<- summary\_data %\>%  
  mutate(  
    Treatment\_Sex \= ifelse(Sex \== "F", as.numeric(Treatment) \+ 0.1, as.numeric(Treatment))  
  )

ggplot(summary\_data, aes(x \= Treatment\_Sex, y \= mean\_inflor\_ratio, group \= Sex)) \+

  geom\_line(color \= "black") \+

  geom\_point(aes(shape \= Sex), size \= 3\) \+

  geom\_errorbar(aes(ymin \= ci\_lower, ymax \= ci\_upper), width \= 0.2) \+

  scale\_x\_continuous(breaks \= c(1, 2, 3, 4), labels \= c("25%", "50%", "75%", "100%")) \+

  scale\_shape\_manual(values \= c("F" \= 16, "M" \= 1)) \+

  labs(

    x \= "Nutrient Concentration",

    y \= "Mean Inflorescence to Total Biomass Ratio"

  ) \+

  theme\_minimal() \+ 

  theme(

    panel.grid.major \= element\_blank(), 

    panel.grid.minor \= element\_blank(),

    axis.line \= element\_line(),

    axis.title \= element\_text(size \= 14),  

    axis.text \= element\_text(size \= 12),   

    legend.title \= element\_text(size \= 14), 

    legend.text \= element\_text(size \= 12\)   

  ) 

Final Step :3

library(magick)

library(cowplot)

 img1 \<- image\_read("C:/Users/Ocean/Downloads/new\_final\_initial\_inflor\_date.PNG")

img2 \<- image\_read("C:/Users/Ocean/Downloads/new\_final\_flower\_density\_inflorescence.PNG")  
img3 \<- image\_read("C:/Users/Ocean/Downloads/new\_final\_inflor\_mass.PNG")  
img4 \<- image\_read("C:/Users/Ocean/Downloads/new\_final\_initial\_inflor\_date.PNG")

img5 \<- image\_read("C:/Users/Ocean/Downloads/new\_final\_flower\_density\_inflorescence.PNG")  
img6 \<- image\_read("C:/Users/Ocean/Downloads/new\_final\_inflor\_mass.PNG")

plot1 \<- ggdraw() \+ draw\_image(img1)  
plot2 \<- ggdraw() \+ draw\_image(img2)  
plot3 \<- ggdraw() \+ draw\_image(img3)  
plot4 \<- ggdraw() \+ draw\_image(img4)  
plot5 \<- ggdraw() \+ draw\_image(img5)  
plot6 \<- ggdraw() \+ draw\_image(img6)

combined\_plot \<- plot\_grid(plot1, plot2, plot3, ncol \= 3\)  
ggsave(

  filename \= "C:/path/to/your/directory/combined\_plot.png",

  plot \= combined\_plot,

  width \= 8,

  height \= 10,

  dpi \= 300

)

 combined\_plot \<- plot\_grid(

  plot1, plot2, plot3, plot4, plot5,

  labels \= c("A", "B", "C", "D", "E"),

  ncol \= 1,

  label\_size \= 14  \# Adjust the label size as needed

)

\*\*\*combined\_plot \<- plot\_grid(

    plot1, plot2, plot3,

    labels \= c("A", "B", "C"),

    ncol \= 1,  \# Set the number of columns to 2

    label\_size \= 40,  \# Adjust the label size as needed

    label\_x \= 0.1,  \# Adjust the x position of the labels

    label\_y \= 0.9   \# Adjust the y position of the labels

)

Graph 1 \- Plant Heights Initial, 1 Month, 2 Months

Graph 2 \- Leaf Mass, Area, SLA

Graph 3 \- Inflorescence Date, Flower Density Inflorescence, Inflorescence Mass, Inflorescence Length

Graph 4 \- Dry Root Biomass, Vegetative Biomass, Phi2, \# Axils w/ Flowers, Flowering Date, Germination Date

OR

Graph 1 \- Germination Date, Inflorescence Date, Flowering Date

Graph 2 \- PH Initial, PH Month, PH Collection

Graph 3 \- Fl

* Look into reasons as to why males are limited/constrained/some other mechanism that prevents them from ‘catching up’ to the females in terms of biomass \- why not produce more flowers, etc. 

* Are females constricted by their growth patterns \- maybe not a male impacted observation?

* Rumex \- where males grow taller than females \- for pollen dispersal advantage b/c wind pollination?  
    
* Mass inflorescence differences \- males lost pollen? Unable to determine relative energy allocation towards pollen and seeds for comparison. 

* At the end of the life cycle (after the heights have equilibrated), the females might just have more resources to make use of said greater resources. 

* Potential benefit of males \- ability to invest in reproduction sooner \- maybe females are more susceptible to disease b/c of longer “investment” time. 

* Environmental limitations \- as desert annuals, maybe males only need 1 rainfall to finish reproductive stage while females may be more constrained.  
    
* Any benefit for seeds produced sooner vs seeds produced later? Can look at different species.   
    
* Plasticity vs genetic basis for variations in the germination rates in fall vs. spring and summer. 

[https\://journals.plos.org/plosone/article?id=10.1371/journal.pone.0009824](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0009824)

[https\://link.springer.com/article/10.1007/s00442-017-3966-5](https://link.springer.com/article/10.1007/s00442-017-3966-5)

[https\://link.springer.com/article/10.1007/s10682-013-9672-9](https://link.springer.com/article/10.1007/s10682-013-9672-9) 

\*For the figures, adjust so that they match the standard in normal journals (i.e., no titles, presence of a legend, add significance asterisks on top of each relevant column, add nothing for insignificant ones rather than a hyphen, etc. Add axis lines for x & y, rather than no line at all.

Add standard error/deviation to the graphs in place of 95% CI. \*Already did\! Is a 

fin\$Treatment \<- factor(fin\$Treatment)  
fin\$Treatment \<- relevel(fin\$Treatment, ref \= "0%")

\*For the graphs, instead of using color, consider using filled and open circles for the mean values (instead..

lmer() function utilizes Restricted Maximum Likelihood (REML), rather than least squares differential (LSD), etc. 

Log Results \+ Code \- 

install.packages("readxl")

library(readxl)

data \<- read\_excel("Final Experiment Data.xlsx")

data\$total\_veg\_mass \<- data\$\`dry\_above\_veg\_mass\` \+ data\$\`dry\_roots\`

male\_data \<- subset(data, Sex \== "M")

female\_data \<- subset(data, Sex \== "F")

male\_model \<- lm(log(\`dry\_inflor\_mass\`) \~ log(total\_veg\_mass), data \= male\_data)

female\_model \<- lm(log(\`dry\_inflor\_mass\`) \~ log(total\_veg\_mass), data \= female\_data)

summary(male\_model)

summary(female\_model)

plot(log(male\_data\$total\_veg\_mass), log(male\_data\$\`dry\_inflor\_mass\`), pch \= 16, xlab \= "Log reproductive biomass (g)", ylab \= "Log vegetative biomass (g)", main \= "Males")  
abline(male\_model, lty \= 2\)

![][image1]

plot(log(female\_data\$total\_veg\_mass), log(female\_data\$\`dry\_inflor\_mass\`), pch \= 16, xlab \= "Log reproductive biomass (g)", ylab \= "Log vegetative biomass (g)", main \= "Females")  
abline(male\_model, lty \= 2\)

![][image2]

Residuals:

    Min      1Q  Median      3Q     Max 

\-1.8980 \-0.2330  0.1122  0.3584  0.7367 

Coefficients:

                    Estimate Std. Error t value

(Intercept)         \-2.43306    0.06272 \-38.790

log(total\_veg\_mass)  0.20088    0.08603   2.335

                    Pr(\>\|t\|)    

(Intercept)           \<2e-16 \*\*\*

log(total\_veg\_mass)   0.0207 \*  

\---

Signif. codes:  

0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.5135 on 174 degrees of freedom

Multiple R-squared:  0.03038,	Adjusted R-squared:  0.02481 

F-statistic: 5.452 on 1 and 174 DF,  p-value: 0.02069

log(*R*)=−2.33+0.30log(*V*),*R*  
2  
\=0.04

Residuals:

    Min      1Q  Median      3Q     Max 

\-1.4222 \-0.2445  0.1157  0.3457  0.7024 

Coefficients:

                    Estimate Std. Error t value

(Intercept)         \-2.32799    0.04582  \-50.81

log(total\_veg\_mass)  0.29917    0.11420    2.62

                    Pr(\>\|t\|)    

(Intercept)          \< 2e-16 \*\*\*

log(total\_veg\_mass)  0.00951 \*\* 

\---

Signif. codes:  

0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.4418 on 189 degrees of freedom

Multiple R-squared:  0.03504,	Adjusted R-squared:  0.02993 

F-statistic: 6.863 on 1 and 189 DF,  p-value: 0.009514

Roots \+ Inflor new logs 

\# Load necessary library  
install.packages("readxl")  
library(readxl)

\# Read the data  
data \<- read\_excel("Final Experiment Data.xlsx")

\# Calculate total vegetative mass  
data\$total\_veg\_mass \<- data\$\`dry\_above\_veg\_mass\` \+ data\$\`dry\_roots\`

\# Calculate allocation towards roots  
data\$allocation\_roots \<- data\$\`dry\_roots\` / data\$total\_veg\_mass

\# Subset data by sex  
male\_data \<- subset(data, Sex \== "M")  
female\_data \<- subset(data, Sex \== "F")

\# Create linear models  
male\_model \<- lm(log(allocation\_roots) \~ log(total\_mass), data \= male\_data)  
female\_model \<- lm(log(allocation\_roots) \~ log(total\_mass), data \= female\_data)

\# Summarize models  
summary(male\_model)  
summary(female\_model)

\# Plot allocation towards roots against total biomass for males  
plot(log(male\_data\$total\_mass), log(male\_data\$allocation\_roots), pch \= 16,   
     xlab \= "Log total biomass (g)", ylab \= "Log allocation towards roots", main \= "Males")  
abline(male\_model, lty \= 2\)

\# Plot allocation towards roots against total biomass for females  
plot(log(female\_data\$total\_mass), log(female\_data\$allocation\_roots), pch \= 16,   
     xlab \= "Log total biomass (g)", ylab \= "Log allocation towards roots", main \= "Females")

abline(female\_model, lty \= 2\)

\# Calculate allocation towards inflorescences  
data\$allocation\_inflor \<- data\$\`dry\_inflor\_mass..g.\` / data\$total\_veg\_mass

\# Subset data by sex  
male\_data \<- subset(data, Sex \== "M")  
female\_data \<- subset(data, Sex \== "F")

\# Create linear models  
male\_model \<- lm(log(allocation\_inflor) \~ log(total\_mass), data \= male\_data)  
female\_model \<- lm(log(allocation\_inflor) \~ log(total\_mass), data \= female\_data)

\# Summarize models  
summary(male\_model)  
summary(female\_model)

\# Plot allocation towards inflorescences against total biomass for males  
plot(log(male\_data\$total\_mass), log(male\_data\$allocation\_inflor), pch \= 16,   
     xlab \= "Log total biomass (g)", ylab \= "Log allocation towards inflorescences", main \= "Males")  
abline(male\_model, lty \= 2\)

\# Plot allocation towards inflorescences against total biomass for females  
plot(log(female\_data\$total\_mass), log(female\_data\$allocation\_inflor), pch \= 16,   
     xlab \= "Log total biomass (g)", ylab \= "Log allocation towards inflorescences", main \= "Females")

abline(female\_model, lty \= 2\)

[image1]: <data:image/png;base64,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>

[image2]: <data:image/png;base64,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>