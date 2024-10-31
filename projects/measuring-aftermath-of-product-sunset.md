---
title: "Measuring the Aftermath of a Product Sunset"
# subtitle: "Generalized from application at Research & Development department, Mendix, Siemens."
image: 
  path: /images/analytics-to-decisions.webp
  thumbnail: /images/analytics-to-decisions.webp
  caption: "A representation by DALL-E"
# tags:
#   - product analytics
#   - statistics
#   - projects
# collection: projects
taxonomy: articles
---
Experiments are a great way to measure what will change. To measure what has changed, (in absence of, or in addition to experiment results) we need a comparative analysis of the before vs after periods with respect to the sunset event, that is, we need to conduct counterfactual analyses.  
There are 2 approaches to apply counterfactual analysis for this scenario:  
*Notation: O(v) is observed values, E(v) is expected value.*
* Testing for significant difference between the observed values: O(metrics pre-sunset) vs O(metrics post-sunset). In shorthand, O(pre) vs O(post).  
This method is quicker but less robust.
* Comparing expected value to observed values:  E(metrics post-sunset) vs O(metrics post-sunset). In shorthand, E(post) vs O(post).  
Here, E(v) are predicted to estimate a scenario where the sunset event never occurred. But, since the sunset event did occur, the difference of the E(v) from the O(v) explains the change after product sunset. This method is relatively more time-consuming but is also more robust.  

Both approaches have their advantages and disadvantages. 

|                           | Approach 1: O(pre) vs O(post) | Approach 2: E(post) vs O(post) |
|---------------------------|-------------------------------|--------------------------------|
| Feature <br>selection*    | **Feature-agnostic**: This method is suitable to be applied to a wide variety of metrics (or features) like, cross-sectional data (example: absolute count of active days per user), time-series data and pooled time series data (example: average or median active days across all users per month). | **Time-series and pooled time-series only**: Since this method involves predicting future values of a feature, this can only be done with time-series data or pooled time-series data (where a feature distribution is aggregated per time period).  
Furthermore, since no aggregate (average, median, etc.) is single-handedly representative of the complete distribution, selecting this approach involves the risk of losing useful information. |
| Robustness <br>of results | What this approach offers in breath of feature selection, it fails to offer in depth of robust findings.   
This can be compensated for by manually segmenting the data based on expected differentiators and, running significance tests for each segment (in addition to the whole distribution).   
However, the practicality of this is subject to the ease of proactively judging these segments from the dataset, and the increased risk of operating with confirmation bias. | This approach of counterfactual analysis offers more depth of information to characterize significant differences between expected and observed results along a spectrum, rather than a single data point like in approach 1.   
One may, for instance, discover that not only is there significant difference but it occurs more in peak months of activity, compared to slump months of the product usage cycle. |
| Time <br>investment       | This approach is relatively quicker to execute and, can be an optional first step to approach 2, to get a feel of the underlying dataset & patterns. | Fitting a time series model to each feature*, especially, for a new dataset, is usually more time consuming. |

**Here and onward, feature is used to mean variables/metrics in the data model (data science terminology), and not features of a product (product terminology).*