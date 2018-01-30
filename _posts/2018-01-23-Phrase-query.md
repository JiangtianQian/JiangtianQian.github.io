---
layout: post
title: Phrase query
---

   Sometimes, the search query can be complex, like names and term in computer science. These words are phrase and their lengt
is more than 2. In the most situation, users can surround the phrase with “ ” to do the exact search.  And there are two another
ways to get reasonable search result. The first and the most common one is positional indexes. We use inverted matrix to record
every term’s collection frequency, documentary ID and position in these documentary. If we want to search “search engine is fun”,
we need firstly find position lists of  “search”, “engine” and “fun”.  We should go through the position lists which contains both
three words and then check whether there is a document in which “search” is one word former than “engine”, “engine” is one word
former than “fun” and “search” is two words former than “fun”. So, positional index could be the near K query as well.

   Another useful but not that common mechanism is biword query. The key idea is treating every two successive words as
phrase.By doing this, we can break long sentence to lots of two-words phrase and do the IR. The nouns is important in the query, suitable query nouns can lead to good query result. In the real world sentence, nouns are always separate by adverb, adjective and so on.

   We let X or * to represent these non-nouns words and N to represent nouns, and treat sentence like NX*N as a biword. Though
biword may increase query accuracy, in some situation, it could be worse. For example, “parent power and out home”. The biword
may separate it to “parent power” + “power out” + “out home”. Apparently, it is much better use the whole sentence than add
“power out” in the query. And there is another disadvantages,  every two words we build a position list will occupy lots of space.
And we can combine these two methods to over come their disadvantages. For some certain phrase use biword and phrase query,
the other use positional index query.
