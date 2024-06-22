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
bash```bin/elasticsearch-plugin install file:///path/to/ParsiAnalyzer.zip```

## The steps are as the following :

Note : for establish a ELK Stack, refer to my [github](https://github.com/kayvansol/elasticsearch/)

all commands are present  at [commands](https://github.com/kayvansol/ParsiAnalyzer/blob/main/commands.txt)

Change Elasticsearch version to 8.13.4 :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/pom.png?raw=true)

&

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/descriptor.png?raw=true)

**Build** the project :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/build.png?raw=true)

the related packages appear after downloading :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/NewDependency.png?raw=true)

**Run** the app with goal of **package** :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/build1.png?raw=true)

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/build2.png?raw=true)

at final :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/build3.png?raw=true)

the zip file is present at target/releases folder :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/release.png?raw=true)

**upload** zip file inside `elasticsearch` container :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/uploadzip.png?raw=true)

install the plugin for Elasticsearch 8.13.4 inside `elasticsearch` container :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/install.png?raw=true)

test the installed analyzer with `kibana` after restart the elasticsearch container, you can use Elasticsearch's `analyze` API :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/post.png?raw=true)

create your `index` with the analyzer, ParsiAnalyzer can be specified directly in the field mapping as follows :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/createindex.png?raw=true)

insert data to the index :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/insertdata.png?raw=true)

search :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/search.png?raw=true)

get with analyzer :

![alt text](https://raw.githubusercontent.com/kayvansol/ParsiAnalyzer/main/img/getwithanalyzer.png?raw=true)
