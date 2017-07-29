---
title: APIs for Scholarly Resources
permalink: p/apis-for-scholars
layout: default
category: software
---

GOAL: Write a program that automatically maintains a database of metadata for research articles published in the UC Berkeley College of Chemistry.

Relevant APIs
-------------

-   [MIT Libraries: APIs for Scholarly Resources](http://libguides.mit.edu/apis)
-   [Berkeley Libraries: APIS for Scholarly Resources](http://guides.lib.berkeley.edu/information-studies/apis)
-   [StackExchange: Open database APIs for journal article metadata](http://opendata.stackexchange.com/questions/638/open-database-apis-for-journal-article-metadata)
-   [Springer BioMedCentral APIs](https://dev.springer.com/)
-   [Elsevier ScienceDirect APIs](http://dev.elsevier.com/)
-   [Mendeley APIs](http://dev.mendeley.com/)

### Web of Science

Does Web of Science have an API? [Yes](http://wokinfo.com/products_tools/products/related/webservices/). [FAQ](http://wokinfo.com/products_tools/products/related/webservices/ws_faq/). It uses a [SOAP protocol](https://en.wikipedia.org/wiki/SOAP). Can I access it?

`"Web of Science Web Services is freely available to every Scientific and Scholarly Research customer that subscribes to Web of Science Core Collection.  The data the customer can extract are limited to the databases and file depths of the subscription. Only systems requesting use of the service will be entitled. In most instances, that will be only one IP address, though there may be cases where multiple IP addresses will be entitled."`

When you download a .tsv of the search results, the 'field tag' headers are described here: <https://images.webofknowledge.com/WOK46/help/WOS/h_fieldtags.html>

### Scopus

<http://dev.elsevier.com/>

`"Anyone can obtain an API Key and use the APIs free of charge, provided that our policies for using APIs and the data are honored. Furthermore, full API access is only granted to clients that run within the networks of organizations with Sciencedirect and/or Scopus subscriptions. Clients without content subscriptions have access to limited basic metadata for most publications and citation records, as well as to basic search functionality. Content published by Elsevier under Open Access licenses is fully available."`

Previous Projects
-----------------

-   [SAGE: Smarter Academic Graph Explorer](http://sage-search.appspot.com/) ([project details](http://www.cs.princeton.edu/~edwardz/333.html))- always appears to time out :(
-   [ProgrammableWeb: 46 Research APIs](http://www.programmableweb.com/news/46-research-apis-dataunison-mendeley-lexisnexis-and-zotero/2012/04/24)
