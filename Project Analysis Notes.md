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

\> library(lme4)

\> library(lmerTest)

\> lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|mother) \+ germTime \+ Sex\*germTime, data \= updated\_data)

\> lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|Mother) \+ germTime \+ Sex\*germTime, data \= updated\_data)

\> lmer(number\_axils\_with\_flowers \~ Sex \+ (1\|Mother) \+ germination\_date \+ Sex\*germination\_date, data \= updated\_data)

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

\# linear mixed model fit for 1 of the 17 observed traits, number of axils with flowers. Repeated for all traits to establish residual results.

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

1) Final\_Data\$initial\_inflor\_date \<- as.numeric(as.character(Final\_Data\$initial\_inflor\_date))  
     
   infloresence\_date \<- aov(formula \= initial\_inflor\_date \~ Sex, data \= Final\_Data)  
   

summary(infloresence\_date) p-value \= 0.691

\*\*\* full\_model \<- lmer(initial\_inflor\_date \~ Sex \+ Treatment \+ Sex\*Treatment \+ (1\|Mother) \+ X..Days.growing, data \= Final\_Data, na.action \= na.omit)

1) germ \<- aov(formula \= germination\_date \~ Sex, data \= Final\_Data)  
     
   summary(germ) p-value \= 0.817 \*\*\* crit error  
     
1) height1 \<- aov(formula \= plant\_height\_initial \~ Sex, data \= Final\_Data)  
   summary(height1) p-value \= 0.0238  
   Type III Analysis of Variance Table with Satterthwaite's method  
                   Sum Sq Mean Sq NumDF  DenDF  F value  Pr(\>F)      
   Sex               3512    3512     1 449.09   5.1084 0.02429 \*    
   Treatment       539208  134802     4 448.68 196.0757 \< 2e-16 \*\*\*  
   X..Days.growing    862     862     1 450.60   1.2545 0.26329      
   Sex:Treatment     3374     843     4 450.26   1.2268 0.29861      
   \---  
   Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
     
     
1) height2 \<- aov(formula \= p.h.\_month \~ Sex, data \= Final\_Data)  
     
   summary(height2) p-value \= 0.00139  
   Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF DenDF   F value    Pr(\>F)      
   Sex              251726  251726     1   451  236.4948 \< 2.2e-16 \*\*\*  
   Treatment       4457150 1114287     4   451 1046.8630 \< 2.2e-16 \*\*\*  
   X..Days.growing      93      93     1   451    0.0873    0.7678      
   Sex:Treatment     51984   12996     4   451   12.2096 1.964e-09 \*\*\*  
     
1) height3 \<- aov(formula \= p.h.\_collection \~ Sex, data \= Final\_Data)  
     
   summary(height3) p-value \= 0.196  
   Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF DenDF   F value Pr(\>F)      
   Sex                  12      12     1   451    0.0173 0.8955      
   Treatment       7165679 1791420     4   451 2526.9309 \<2e-16 \*\*\*  
   X..Days.growing      14      14     1   451    0.0192 0.8898      
   Sex:Treatment      4250    1062     4   451    1.4987 0.2015  
1) Final\_Data\$inflor\_length \<- as.numeric(as.character(Final\_Data\$inflor\_length))  
     
   inflor\_length \<- aov(formula \= inflor\_length \~ Sex, data \= Final\_Data)  
     
   summary(inflor\_length) p-value \= 0.188  
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                   Sum Sq Mean Sq NumDF DenDF F value  Pr(\>F)    
   Sex             1112.3 1112.33     1   358  1.3286 0.24983    
   Treatment       8485.1 2121.28     4   358  2.5337 0.04006 \*  
   X..Days.growing  317.4  317.37     1   358  0.3791 0.53849    
   Sex:Treatment    437.3  145.77     3   358  0.1741 0.91388   
1) Final\_Data\$flowering\_date \<- as.numeric(as.character(Final\_Data\$flowering\_date))

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

1) leaf\_area \<- aov(formula \= leaf\_area..cm.2. \~ Sex, data \= Final\_Data)  
     
   summary(leaf\_area) p-value \= 3.7 x 10^-6   
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF  DenDF  F value    Pr(\>F)      
   Sex               83.62   83.62     1 449.35  50.1186 5.605e-12 \*\*\*  
   Treatment       1780.84  445.21     4 448.90 266.8501 \< 2.2e-16 \*\*\*  
   X..Days.growing    2.37    2.37     1 450.80   1.4201  0.234011      
   Sex:Treatment     23.67    5.92     4 450.16   3.5469  0.007296 \*\*   
   \---  
   Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
     
1) leaf\_mass \<- aov(formula \= dry\_leaf\_mass..g. \~ Sex, data \= Final\_Data)  
     
   summary(leaf\_mass) p-value \= 2 x 10^-16  
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                      Sum Sq   Mean Sq NumDF DenDF  F value    Pr(\>F)      
   Sex             0.0077350 0.0077350     1   451 272.9001 \< 2.2e-16 \*\*\*  
   Treatment       0.0089316 0.0022329     4   451  78.7796 \< 2.2e-16 \*\*\*  
   X..Days.growing 0.0000048 0.0000048     1   451   0.1698 0.6805281      
   Sex:Treatment   0.0005560 0.0001390     4   451   4.9044 0.0007034 \*\*\*  
   \---  
   Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
     
1) Final\_Data\$dry\_inflor\_mass..g. \<- as.numeric(as.character(Final\_Data\$dry\_inflor\_mass..g.))  
     
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
1) above\_veg\_mass \<- aov(formula \= dry\_above\_veg\_mass..g. \~ Sex, data \= Final\_Data)  
     
   summary(above\_veg\_mass) p-value \= 2.76e-06  
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF  DenDF  F value    Pr(\>F)      
   Sex              0.7976 0.79761     1 448.98  32.7426 1.925e-08 \*\*\*  
   Treatment       12.4891 3.12227     4 448.70 128.1728 \< 2.2e-16 \*\*\*  
   X..Days.growing  0.0051 0.00510     1 450.20   0.2093   0.64751      
   Sex:Treatment    0.2810 0.07025     4 450.33   2.8840   0.02227 \*    
   \---  
   Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
     
1) roots \<- aov(formula \= dry\_roots..g. \~ Sex, data \= Final\_Data)  
     
   summary(roots) p-value \= 8.31e-10  
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF  DenDF F value    Pr(\>F)      
   Sex             0.31105 0.31105     1 449.11 52.0377 2.332e-12 \*\*\*  
   Treatment       1.81470 0.45368     4 448.77 75.8987 \< 2.2e-16 \*\*\*  
   X..Days.growing 0.00887 0.00887     1 450.47  1.4832   0.22391      
   Sex:Treatment   0.07385 0.01846     4 450.35  3.0887   0.01582 \*    
   \---  
   Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
1) Final\_Data\$flower\_density\_inflorescence..flowers.2.cm.2. \<- as.numeric(as.character(Final\_Data\$flower\_density\_inflorescence..flowers.2.cm.2.))  
     
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
1) Final\_Data\$number\_axils\_with\_flowers \<- as.numeric(as.character(Final\_Data\$number\_axils\_with\_flowers))  
     
   axil\_flowers \<- aov(formula \= number\_axils\_with\_flowers \~ Sex, data \= Final\_Data)  
     
   summary(axil\_flowers) p-value \= 0.946  
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                   Sum Sq Mean Sq NumDF DenDF F value Pr(\>F)  
   Sex              0.048  0.0479     1   358  0.0034 0.9537  
   Treatment       30.914 10.3048     3   358  0.7265 0.5367  
   X..Days.growing  3.887  3.8874     1   358  0.2741 0.6009  
   Sex:Treatment   43.541 14.5135     3   358  1.0233 0.3823  
     
1) SLA \<- aov(formula \= specific\_leaf\_area..cm.2...g. \~ Sex, data \= Final\_Data)  
     
   summary(SLA) p-value \= \<2 x 10^-16  
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                   Sum Sq Mean Sq NumDF  DenDF  F value  Pr(\>F)      
   Sex             230023  230023     1 448.90 166.7468 \< 2e-16 \*\*\*  
   Treatment       436737  109184     4 448.65  79.1490 \< 2e-16 \*\*\*  
   X..Days.growing     50      50     1 450.06   0.0363 0.84892      
   Sex:Treatment    11488    2872     4 450.27   2.0819 0.08218 .   
     
1) Phi2 \<- aov(formula \= Phi.2 \~ Sex, data \= Final\_Data)

	summary(Phi2) p-value \= 0.207

Type III Analysis of Variance Table with Satterthwaite's method  
                  Sum Sq  Mean Sq NumDF  DenDF F value Pr(\>F)  
Sex             0.055951 0.055951     1 449.35  1.7979 0.1806  
Treatment       0.138237 0.034559     4 448.92  1.1105 0.3509  
X..Days.growing 0.001992 0.001992     1 450.79  0.0640 0.8004  
Sex:Treatment   0.071351 0.017838     4 450.17  0.5732 0.6822

1) new\_leaf\_mass \<- aov(formula \= new\_dry\_leaf\_mass \~ Sex, data \= Final\_Data)  
     
   summary(new\_leaf\_mass) p-value \= 0.00116  
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                      Sum Sq   Mean Sq NumDF  DenDF  F value    Pr(\>F)      
   Sex             0.0005850 0.0005850     1 448.98  20.6569 7.073e-06 \*\*\*  
   Treatment       0.0000998 0.0000250     4 448.66   0.8814    0.4749      
   X..Days.growing 0.0085444 0.0085444     1 450.31 301.7306 \< 2.2e-16 \*\*\*  
   Sex:Treatment   0.0001882 0.0000470     4 450.33   1.6611    0.1580      
   \---  
   Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1  
1) Final\_Data\$new\_dry\_inflor\_mass \<- as.numeric(as.character(Final\_Data\$new\_dry\_inflor\_mass))  
     
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
1) new\_above\_veg\_mass \<- aov(formula \= new\_dry\_above\_veg \~ Sex, data \= Final\_Data)  
     
   summary(new\_above\_veg\_mass) p-value \= 0.0674  
     
   Type III Analysis of Variance Table with Satterthwaite's method  
                    Sum Sq Mean Sq NumDF  DenDF  F value    Pr(\>F)      
   Sex             0.06594 0.06594     1 448.75   4.9800   0.02614 \*    
   Treatment       0.55489 0.13872     4 448.53  10.4762  4.03e-08 \*\*\*  
   X..Days.growing 2.71986 2.71986     1 449.82 205.4012 \< 2.2e-16 \*\*\*  
   Sex:Treatment   0.10967 0.02742     4 450.13   2.0705   0.08368 .    
1) new\_roots \<- aov(formula \= new\_dry\_roots \~ Sex, data \= Final\_Data)  
     
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

\# Final steps for graph generation \- 

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

