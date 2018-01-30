---
layout: post
title: Information retrieval and Estimation
---

   Chapter 1 and 5.1 mainly talks about boolean retrieval mechanism and two laws of estimating vocabulary size or distribution of
terms.  The basic information retrieval(IR) idea is finding information in a cluster of unstructured documents or files which contains
your goal. In the early year, boolean retrieval model is the most popular and accurate one. The core idea is retrieval information in
boolean expression, like (search AND  engine). For boolean query views each document as a set of words, we introduced
incidence matrix to represent if the document contains the specific terms or not. For example, D1’s content is what can you learn
from search engine, D2 is what can you learn from web application and D3 is what can you learn from computer vision. For every
terms in these documents, let 1 indicates it exists in certain documents and 0 not, just as table1shows. Then we got vector for
each document and each terms respectively. For example, D1 = 11111110000 and term application = 010. This is easy for
resolving boolean retrieval query. For the query (search AND engine), it returns 100 & 100 = 1, which means D1 document. It is easy
to get aimed documents through vector and boolean function &, | and ~.
![avatar](/image/read1)
   As we can see, the incidence matrix is a sparse matrix, the useless 0s will occupy lots of memory. To make it space efficient, we
optimize the matrix to a “hash table and linkedlist” like matrix. For the example above, we first sort terms alphabetically and record
the document id this terms belong to, that is application-2, can-1, can-2, can-3, computer-2, engine-1, from-1, from-2, from-3,
learn-1, learn-2, learn-3, search-1, vision-3, web-2, you-1, you-2, you-3. If there are any same terms in the same document, we
only keep one of them; if there are any same terms in the different documents, we group them. At last, we build hash table
linkedlist matrix. That is: application ->2, can->1->2, can->3, computer->2, engine->1, from->1->2 ->3, learn->1, learn->2 ->3,
search->1, vision->3, web->2, you->1->2->3. This is called inverted matrix, the terms are called dictionary and the list called
position list. We can use it to resolve the boolean retrieval as well. The (search AND engine) could be the result of merging “search”
and “engine” positions list, that is 1, too.

   The boolean query operators include AND, OR and NOT. Different order to retrieval documents may lead to different time
cost and space efficiency. We can apply this arbitrary to do query optimization. For example, (term1&term2&term3) and
(term1&term2)&term3 may have different operation time if term1 has very small document frequency. For (term1&term2)&term3, we
can limit the results to a very small range if term1 has smallest document frequency, which means it has smallest position list.
Users may use free text queries, systems need to decide the best match document. A extended boolean retrieval model need to be
used, which include additional operators like approximate operator and so on.

   And 5.1 talks about two laws - Heap’s law and Zipf’s law. Heap’s law is helping estimates how many the distinct words are
when we know the number of tokens(document length). The function is , k is often 10~100, T is the number of tokens and b is often
0.4~0.5. And the Zipf’s law gives the distribution of terms. The function is . cf is the collection frequency of the  rank, C is a
constant and i is the  rank, k is -1, and this is a power law equation. So it can be described as , which means rank is inverse to
collection frequency. If the second top rank term’s collection frequency is the half of the most top one. Though these two laws’
results are only approximate statistics, they give us a general sense how huge data we are dealing with and their rough distribution.
