---
layout: post
title: Integrating Behavior User Studies with Log Analysis
folder: projects
type: project
image: images/log-test.png
excerpt: >-
  This is a UX assessment methodology I co-developed with Dr. Xi Niu at
  University of North Carolina at Charlotte. We have conducted several case
  studies and showed that integrating behavioral user studies with log analysis
  (i.e., http server logs) is an effective way to uncover the contextual
  information of search tasks.
published: true
---


**Method**: Transaction Log Analysis, Log Visualization, Data-driven Task Design, Behavior Observation      
**Tools**: Python, R, SAS, Morae

## Challenge  
The library catalog (or discovery tool) transaction logs are believed as one of the important sources of big data in libraries. Although researchers can mine detailed information about users’ search behavior from logs, one of the obstacles of log analysis is the lack of contextual information such as users’ motivations, information needs, and step-by-step actions. Analyzing logs alone also has the danger of reaching oversimplified conclusions about search behavior without appropriate understanding of the tasks’ contexts and users’ preferences.

## Method  
Through case studies, we have shown that integrating behavioral user studies with log analysis is an effective way to uncover the contextual information of search tasks and drive user interface improvement. We used behavior patterns from log analysis to develop test tasks for user tests so that we can target certan search behavior and task context for observation. 

## Results  
Common findings and behavior patterns on search field usage, facet selections, and query formulations include these: 

1. Users predominantly use keyword search; 
2. Use of facets is low, and nested facet selections are rare;
3. Most search sessions involve fewer than four queries;
4. The average number of words per query is generally less than three;
5. More than half of search sessions reformulate the search by adjusting the original keywords. 

In addition, the content coverage of catalogs and discovery tools can affect users’ search behavior. For example, users of discovery tools tend to have a higher percentage of keyword searches and a lower percentage of title, author, subject, and call number searches. 

## Presentation   
<iframe src="//www.slideshare.net/slideshow/embed_code/key/fXlPFCswa5AvvK" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/jimmie/integrating-behavior-user-studies-with-log-analysis" title="Integrating Behavior User Studies with Log Analysis" target="_blank">Integrating Behavior User Studies with Log Analysis</a> </strong> from <strong><a href="//www.slideshare.net/jimmie" target="_blank">Tao Zhang</a></strong> </div>

## Related Publiations  
Niu, X., Zhang, T., & Chen, H. (2014). [Study of user search activities with two discovery tools at an academic library](http://www.tandfonline.com/doi/abs/10.1080/10447318.2013.873281). *International Journal of Human-Computer Interaction*, 30(5), 422-433.

Zhang, T., Niu, X., Zhu, L. & Chen, H. (2015). [Search in One’s Hand: How Users Search a Mobile Library Catalog](http://link.springer.com/chapter/10.1007/978-3-319-20612-7_24). Paper presented at the *17th International Conference on Human-Computer Interaction*, Los Angeles, CA. August 2-7, 2015.
