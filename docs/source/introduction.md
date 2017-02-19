Introduction
============
**Elasticsearch** is a search engine based on [Lucene](http://lucene.apache.org/core/). Its an open source, distributable, Scalable and schema-free full text search engine written in java. In Elasticsearch each indexed document is conceptually a JSON document and it can be accessible from RESTful web service interface.


<div style="background-color: #f2f2f2">
 <b> what is lucene? </b>
 <br>
	Apache Lucene is a high-performance, full-featured text search engine library written entirely in Java. It provides reached searching algorithms like ranked searching, fielded searching, sorting by specific field, multiple-index searching etc.
</div>
<br>
<div style="background-color: #f2f2f2">
	<b> what is schema-free database? </b>
	<br>
	A schema free DB is also known as NOSQL database. It can store data without a previous structure. There is no prefixed structure. You can alter is very easily and store any kind of data.
</div>

Use case
---------
Elasticsearch provides you various types of inbuilt text matching algorithms. You can do full-text or partial-text matching with just typing small queries. You need to type small [mappings](https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping.html) to analyse and organise your data before you start storing your data.

One of the best use case of elasticsearch is to build your own search engine. A commonly-requested feature in search applications is **autocomplete** or **search suggestions**. The key idea is to provide users instant suggestions based on different parameters, while they are typing the queries. These parameters can be user’s **search history**, **generally popular queries**, **top results**, **trending topics**, **spelling mistakes**, etc.

Suppose you have the data of checkins according to the city. You Want to build a search bar which will take city name as an input and provides you data of checkins. When the user enters full-text based queries any document based database is capable to give the perfectly matched documents. However, an autocomplete query will not contain complete words. As the user types New York, your search application might receive queries for N, Ne, New.. Etc. We need to implement separate mechanism which will analyze the stored data and will give you the similar outputs.

To implement autocomplete like feature we can use **prefix matching** algorithm. Prefix algorithm works by looking for all terms in the index that match the given prefix. If there are a lot of terms in your index, this query can become quite **unwieldy** and eventually result in a **too many clauses** error. Also, the Prefix based search engine does not allow matching in the middle of words. **Like**, York query should match with New York data.	



The another approach is based on **N-Grams**. You can break your data and can store sub part of it. There are several tokenizers and token filters that come with elasticsearch that will break words up into n-grams.
Like break New York into ‘N’, ‘e’, ‘w’, ‘Y’, ‘o’, ‘r’, ‘k’, ‘York’, ‘Ne’, ‘New’, ‘New ’.. Etc. tokens.
N-grams allow matching in the middle of words at the cost of more tokens and a larger index.

elasticsearch has a **Multi Field** type that supports indexing a field multiple ways. This handy feature can be used to index a field **normally(Full-text)** and also as n-grams. 

In this way Elasticsearch provides you a great way to implement search engines without an AI recommendation filter.
