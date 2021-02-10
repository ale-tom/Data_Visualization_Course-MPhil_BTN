This data was derived from:

Baker, M. (2016). 1,500 scientists lift the lid on reproducibility. Nature, 533(7604), 452–454. https://doi.org/10.1038/533452a

I extracted the following columns and renamed their column names:

responseid	
respid
In your current role do you carry out primary research?
Have you published a manuscript in the past 3 years?
How familiar are you with the term reproducibility?
Which of the following statement regarding a†'crisis or reproducibility' within the science community†do you agree with?
Is a 'crisis of reproducibility' something you have heard of before, as an issue in science?
To what extent do you feel that the crisis in reproducibility is suitably flagged?
In your opinion, what proportion of published results in your field are reproducible? i.e. the results of a given study could be replicated exactly or reproduced in multiple similar experimental systems with variations of experimental settings such as materials and experimental model)
Please complete the following sentence:"In my opinion, the level of reproducibility in my field is":
Which, if any, of the following have you done?


I have created dummy data using the following code:
N = as.vector((baker2016 %>% group_by(baker2016$What.is.your.age.) %>% summarise(n = n()))$n)
rand_mean = c(20,30,40,50,60,70,18)
dummy_age = unlist(sapply(1:length(N),function(i) rnorm(N[i],rand_mean[i], 4)))

rand_mean = c(1,1.2,1.3,2,2.5,3,0.8)
rand_sd = c(2,2.5,3,2.1,1,1,1)
dummy_dat2 = unlist(sapply(1:length(N),function(i) rnorm(N[i],rand_mean[i], 1)))

baker2016 = baker2016[order(baker2016$What.is.your.age.),]
baker2016$dummy_age = dummy_age
baker2016$dummy_dat2 = dummy_dat2

set.seed(100)
baker2016$dummy_group = sample(rep(c(1,2), each=dim(baker2016)[1]/2))
