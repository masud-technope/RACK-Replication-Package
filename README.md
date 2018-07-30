RACK-Replication-Package
====================================================
Replication package of RACK--Query Reformulation for Code Search using Crowdsourced Knowledge


Abstract
-------------------------------------------
Traditional code search engines (e.g., Krugle) often do not perform well with natural language queries. They mostly apply keyword matching between query and source code. Hence, they need carefully designed queries containing references to relevant APIs for the code search. 
Unfortunately, preparing an effective search query is not only challenging but also time-consuming for the developers according to existing studies.
In this article, we propose a novel query reformulation technique--RACK--that suggests
a list of relevant API classes for a natural language query intended for code search. Our technique offers such suggestions by exploiting keyword-API associations from the questions and answers of Stack Overflow (i.e., crowdsourced knowledge). We first motivate our idea using an exploratory study with 19 standard Java API packages and 344K Java related posts from Stack Overflow.
Experiments using 175 code search queries randomly chosen from three Java tutorial sites show that our technique recommends correct API classes within the Top-10 results for 83% of the queries, with 46% mean average precision and 54% recall, which are 66%, 79% and 87% higher respectively than that of the state-of-the-art. 
Reformulations using our suggested API classes improve 64% of the natural language queries and their overall accuracy improves by 19%.
Comparisons with three state-of-the-art techniques demonstrate that RACK outperforms them in the query reformulation by a statistically significant margin. Investigation using three web/code search engines shows that our technique can significantly improve their results in the context of code search.

Accepted Papers
-----------------------------------------
```
- M. Masudur Rahman, C.K. Roy and David Lo, "RACK: Automatic API Recommendation using Crowdsourced Knowledge", In Proceeding of The 23rd IEEE International Conference on Software Analysis, Evolution, and Reengineering (SANER 2016), pp. 349--359, Osaka, Japan, March 2016
- M. Masudur Rahman and C.K. Roy and David Lo, " RACK: Code Search in the IDE using Crowdsourced Knowledge", In Proceeding of The 39th International Conference on Software Engineering (ICSE 2017), pp. 51--54, Buenos Aires, Argentina, May, 2017
```

