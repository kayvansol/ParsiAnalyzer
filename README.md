# Persian Analyzer For Elasticsearch

# ParsiAnalyzer
ParsiAnalyzer is an analysis plugin for Elasticsearch. Analysis is a process that consists of the following steps:

- Tokenizing a block of text into individual terms
- Normalizing these terms into a standard form

An analyzer is really just a wrapper that combines Character filters, Tokenizer, and Token filters. Elasticsearch provides many Built-in Analyzers but there's still room for improvement especially for Persian language. This plugin provides tools for tokenizing, normalizing and stemming Persian text.

## Key features
- Tokenize Persian text
  - Convert whitespaces to zero width nonjoiner (`نیم‌فاصله`) whenever it is necessary. for example,`می رود` to `می‌رود`.
  - Convert Persian punctuations to their English equivalent. for example,`۳/۱۴` to `۳.۱۴`
  - Tokenize Persian text by whitespaces and punctuations.
  
- Normalize Persian tokens into a single canonical form
  - Transform all forms of Yeh, Kaf, Heh, and Hamza to a unique form. for example,`براي` to `برای`.
  - Convert all Persian and Arabic numbers to their English equivalent. for example,`۱۴۳` to `143`.
  - Remove diacritic (`اِعراب`) from words. for example, `اَرّه` to `اره`.
  - Remove Kashida form words. for example, `بادبــــــادک` to `بادبادک`.
  
- Remove common Persian stop words
  - Persian stop words like `از`, `به` and etc will be removed.
  
- Stem Persian words
  - Remove common Persian suffixes. for example, `ها` or `ان`.
  
## Installation
To install the plugin for Elasticsearch 8.13.4, run this command:

```bin\elasticsearch-plugin install file:///path/to/ParsiAnalyzer.zip```

## Build
If you want to build ParsiAnalyzer for any specific version of Elasticsearch, follow these steps:
1. Make sure you've installed JDK and Maven on your computer
2. Clone project from https://github.com/NarimanN2/ParsiAnalyzer.git
3. Open ```pom.xml```
4. Under dependencies tag, change Elasticsearch version to your desired version
5. Open ```plugin-descriptor.properties```
6. Change elasticsearch.version to your desired version
7. Build and Run maven project with Goals ```package```
8. In the target/releases folder, you’ll now find a zip file. install the plugin using this command:
```bin/elasticsearch-plugin install file:///path/to/ParsiAnalyzer.zip```

