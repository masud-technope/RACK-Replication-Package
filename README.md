Automatic Query Reformulation for Code Search using Crowdsourced Knowledge
==================================================== 


**Abstract:** Traditional code search engines (e.g., Krugle) often do not perform well with natural language queries. They mostly apply keyword matching between query and source code. Hence, they need carefully designed queries containing references to relevant APIs for the code search. Unfortunately, preparing an effective search query is not only challenging but also time-consuming for the developers according to existing studies. In this article, we propose a novel query reformulation technique--RACK--that suggests
a list of relevant API classes for a natural language query intended for code search. Our technique offers such suggestions by exploiting keyword-API associations from the questions and answers of Stack Overflow (i.e., crowdsourced knowledge). We first motivate our idea using an exploratory study with 19 standard Java API packages and 344K Java related posts from Stack Overflow.
Experiments using 175 code search queries randomly chosen from three Java tutorial sites show that our technique recommends correct API classes within the Top-10 results for 83% of the queries, with 46% mean average precision and 54% recall, which are 66%, 79% and 87% higher respectively than that of the state-of-the-art. Reformulations using our suggested API classes improve 64% of the natural language queries and their overall accuracy improves by 19%. Comparisons with three state-of-the-art techniques demonstrate that RACK outperforms them in the query reformulation by a statistically significant margin. Investigation using three web/code search engines shows that our technique can significantly improve their results in the context of code search.

Accepted Papers (3)
-----------------------------------------
```
M. Masudur Rahman, Chanchal K. Roy and David Lo, "Automatic Query Reformulation for Code Search using 
Crowdsourced Knowledge", Journal of Empirical Software Engineering (EMSE), 56 pp.
```
**Download this paper:**  [<img src="http://homepage.usask.ca/~masud.rahman/img/pdf.png"
     alt="PDF" heigh="16px" width="16px" />](https://doi.org/10.1007/s10664-018-9671-0)
```
M. Masudur Rahman, Chanchal K. Roy and David Lo, "RACK: Automatic API Recommendation using Crowdsourced 
Knowledge", In Proceeding of The 23rd IEEE International Conference on Software Analysis, Evolution, and 
Reengineering (SANER 2016), pp. 349--359, Osaka, Japan, March 2016
```
**Download this paper:**  [<img src="http://homepage.usask.ca/~masud.rahman/img/pdf.png"
     alt="PDF" heigh="16px" width="16px" />](http://homepage.usask.ca/~masud.rahman/papers/masud-SANER2016.pdf)
```
M. Masudur Rahman, Chanchal K. Roy and David Lo, "RACK: Code Search in the IDE using Crowdsourced 
Knowledge", In Proceeding of The 39th International Conference on Software Engineering (ICSE 2017), 
pp. 51--54, Buenos Aires, Argentina, May, 2017
```
**Download this paper:**  [<img src="http://homepage.usask.ca/~masud.rahman/img/pdf.png"
     alt="PDF" heigh="16px" width="16px" />](http://homepage.usask.ca/~masud.rahman/papers/masud-ICSE2017.pdf)
     
**Do you want to check [NLP2API](https://github.com/masud-technope/NLP2API-Replication-Package) also?**
----------------

Materials Included
----------------------------------------
**Tool Installation & Run**

- ```rack-exec``` is the functional prototype of RACK, our proposed query reformulation technique. The '0.0.0' version is deprecated (SANER 2016 version). 
We also include ```rack-running-snapshot``` for RACK.
- [**```SOURCE CODE``` of RACK can be found here**](https://github.com/masud-technope/RACK-Server). Go ahead and extend from here.
- ```database/``` contains the keyword--API database constructed from 344K Java related questions and answers of Stack Overflow. 
Originally, we used MSSQL; but we provide SQLite database for the sake of portability. 
Unfortunately, the same queries are providing slightly different results with SQLite.
- ```models/``` contains the trained models needed for POS tagging by Stanford POS tagger.
- ```stopword/``` contains the stop words used by RACK
- ```sample-queries``` for RACK
- ```sample-output``` produced by RACK
- ```NL-Queries-&-Oracle```: A utility file for the tool's run.

**Experimental Dataset: Queries & Results**

- ```EMSE2018-Dataset``` contains experimental data reported on EMSE 2018
   - ```NL Queries & Oracle```: 175 natural language queries & corresponding ground truth.
   - ```RACK-Suggested-API-Classes```: 175 natural language queries and API classes suggested by RACK
   - ```RACK-Suggested-API-Classes-KAC```: API classes suggested by RACK when only KAC heuristic is used.
   - ```RACK-Suggested-API-Classes-KKC```: API classes suggested by RACK when only KKC heuristic is used.		
   - ```RACK-Suggested-API-Classes-KPAC```: API classes suggested by RACK when only KPAC heuristic is used.
   - ```RACK-Suggested-API-Classes-NN```: API classes suggested by RACK when only noun keywords are used.
   - ```RACK-Suggested-API-Classes-VB```: API classes suggested by RACK when only verb keywords are used.
- ```SANER2016-Dataset``` contains experimental results for 150 queries, published in SANER 2016

**License & Others**

- ```README```
- ```LICENSE```

System Requirements
---------------------------
- JDK: RACK was built with **JDK 1.8.0_74**. Please use at least JDK 1.8.* for the successful execution/run.
- Operating System: Only tested on *Windows 10*, but the tool is supposed to be *cross-platform*.
- If any file path contains *space* or *special characters*, the path should be **"double quoted"**.

Available Operations
----------------------------
- ```suggestAPI``` :  Returns a list of API classes for one or more NL queries.
- ```evaluateAPISuggestion``` :  Evaluates the accuracy of suggested API classes against ground truth. 
- ```evaluateCodeSearch``` :  Evaluates the code retrieval performance of queries.
- ```evaluateQE``` :  Evaluates improvement, worsening and preserving of baseline queries by RACK.

Required parameters for the operations
-----------------------------------------------
-  **-K** : expects the number of suggested API classes or code segments (e.g., default: **10**)
-  **-query** : expects a natural language query
-  **-queryFile** : expects the file containing several natural language queries (e.g., deafult: ```./sample-queries.txt```). 
Please note that the **queries should be on the odd lines**.
-  **-resultFile** : stores the API classes suggested by RACK
-  **-task** : expects a task to be performed.


Getting Started
==================================================

Q.1: How to install the RACK tool?
--------------------------------------------------
- Execute ```git clone https://github.com/masud-technope/RACK-Replication-Package.git RACK```
- Run the tool from within the ```RACK``` directory.


Q.2: How to reformulate a given NL query or a file containing all the queries?
-----------------------------------------------------------------------------------
Reformulate a single query
```
java -jar rack-exec.jar -K 10 -task suggestAPI -query "How do I send an HTML email?"
```

Reformulate all queries stored in a file
```
java -jar rack-exec.jar -K 10 -task suggestAPI -queryFile ./sample-queries.txt -resultFile ./sample-output.txt
```

Please note that each NL query is followed by ground truth API classes in the next line (e.g., ```NL-Queries-&-Oracle```). That is, the queries should be 
on the odd lines in the query file. The next line will be either ground truth or simply blank. 

Query File format
--------------------------
- NL Query: How do I send an HTML email?
- **BLANK** or Ground Truth: Properties Session Message MimeMessage InternetAddress


Q.3: How to determine API suggestion performance?
-------------------------------------------------------
```
java -jar rack-exec.jar -K 10 -task evaluateAPISuggestion -resultFile ./EMSE2018-Dataset/RACK-Suggested-API-Classes.txt
```

This command reports Top-10 accuracy, MRR@10, MAP@10, and MR@10 for API suggestion

Q.4: How to get retrieval performance of the reformulated queries?
--------------------------------------------------------------------------
```
java -jar rack-exec.jar -K 10 -task evaluateCodeSearch -resultFile ./EMSE2018-Dataset/RACK-Suggested-API-Classes.txt
```

This commands reports Top-10 accuracy and MRR@10 of code segment retrieval by RACK

Q.5: How to determine query improvement and worsening ratios of the reformulated queries?
---------------------------------------------------------------------------------------------
```
java -jar rack-exec.jar -K 10 -task evaluateQE -resultFile ./EMSE2018-Dataset/RACK-Suggested-API-Classes.txt
```

This commands reports query improvement, worsening, preserved ratios and mean rank differences with the initial queries.


Please cite our work as
------------------------------------------------------------
```
@INPROCEEDINGS{emse2018masud,
author={Rahman, M. M. and Roy, C. K. and Lo, D.},
booktitle={EMSE}, 
title={Automatic Reformulation of Query for Code Search using Crowdsourced Knowledge},
year={2018},
pages={1--56} 
}
```
**Download this paper:**  [<img src="http://homepage.usask.ca/~masud.rahman/img/pdf.png"
     alt="PDF" heigh="16px" width="16px" />](https://doi.org/10.1007/s10664-018-9671-0)
```
@INPROCEEDINGS{saner2016masud,
author={Rahman, M. M. and Roy, C. K. and Lo, D.},
booktitle={Proc. SANER}, title={{RACK}: {A}utomatic {API} {R}ecommendation using {C}rowdsourced {K}nowledge},
year={2016},
pages={349--359} 
}
```
**Download this paper:**  [<img src="http://homepage.usask.ca/~masud.rahman/img/pdf.png"
     alt="PDF" heigh="16px" width="16px" />](http://homepage.usask.ca/~masud.rahman/papers/masud-SANER2016.pdf)
```
@INPROCEEDINGS{icse2017masud,
author={Rahman, M. M. and Roy, C. K. and Lo, D.},
booktitle={Proc. ICSE}, title={RACK: Code Search in the IDE using Crowdsourced Knowledge},
year={2017},
pages={51--54} 
}
```
**Download this paper:**  [<img src="http://homepage.usask.ca/~masud.rahman/img/pdf.png"
     alt="PDF" heigh="16px" width="16px" />](http://homepage.usask.ca/~masud.rahman/papers/masud-ICSE2017.pdf)
     
--------------------------------------------

Something not working as expected?
------------------------------------

Please contact **Masud Rahman** (masud.rahman@usask.ca) or [create a new issue](https://github.com/masud-technope/RACK-Replication-Package/issues/new) for further information.









