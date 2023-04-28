# Marketing-Mixed-Modelling (MMM)

The following case-study was part of the [HAMS Data Science Challenge](https://github.com/haensel-ams/recruitment_challenge/tree/master/DataScience_202209). The challenge was set in the context of performance marketing and the tasks were to:

* build a Bayesian MMM with the latest [PyMC package](https://www.pymc.io/)
* test it on the given dataset
* interpret the insights from the model
* answer the following questions:

  * How do you model spend carry over?
  * Explain your choice of prior inputs to the model?
  * How are your model results based on prior sampling vs. posterior sampling?
  * How good is your model performing? How you do measure it?
  * What are your main insights in terms of channel performance/ effects?
  * (Bonus) Can you derive ROI (return on investment) estimates per channel? What is the best channel in terms of ROI?

## Dataset MMM_test_data.csv

* start_of_week: first day of the week	
* revenue: revenue generated in this week from sales	
* spend_channel_1..7: marketing cost spend in this week in channel 1..7	

# Summary

We built a mixed-media-model to predict the impact of spends in 7 different marketing channels on our target variable, the revenue. We asssumed that the effect of marketing has a carryover effect, one with a delayed peak modelling using a delayed adstock function. Further, the response to the revenue of the spend does not increase linearly with increasing spend, but rather saturates at high spends, and can even start to show dimishing returns, something that we modelled using a logistic saturation curvature function. Finally, we used as control measurements, an underlying trend, seasonal variations, and exceptional events of peak revenue, that is unlikely to do with marketing spend. We inferred the parameters of this model using a Bayesian framework, where assuming certain prior distributions for these parameters and a Gaussian nature to the noise, we stochastically sampled over the parameter space using an MCMC algorithm.
