# Fact-Extraction-and-Verification

This is the repository for the task of Fact Extraction and Verification described in the NAACL2018 paper: : [FEVER: A large-scale dataset for Fact Extraction and VERification.]()

>Unlike other tasks and despite recent interest, research in textual claim verification has been hindered by the lack of large-scale manually annotated datasets. In this paper we introduce a new publicly available dataset for verification against textual sources, FEVER: Fact Extraction and VERification. It consists of 185,441 claims generated by altering sentences extracted from Wikipedia and subsequently verified without knowledge of the sentence they were derived from. The claims are classified as Supported, Refuted or NotEnoughInfo by annotators achieving 0.6841 in Fleiss κ. For the first two classes, the annotators also recorded the sentence(s) forming the necessary evidence for their judgment. 

## Download Wikipedia data

Download the FEVER dataset from the [website](http://fever.ai/data.html) into the data directory

    mkdir data
    mkdir data/fever-data
    
    # We use the data used in the baseline paper
    wget -O data/fever-data/train.jsonl https://s3-eu-west-1.amazonaws.com/fever.public/train.jsonl
    wget -O data/fever-data/dev.jsonl https://s3-eu-west-1.amazonaws.com/fever.public/paper_dev.jsonl
    wget -O data/fever-data/test.jsonl https://s3-eu-west-1.amazonaws.com/fever.public/paper_test.jsonl
    
The data preparation consists of three steps: downloading the articles from Wikipedia, indexing these for the Evidence Retrieval and performing the negative sampling for training.  

Download the pre-processed Wikipedia articles from [the website](https://sheffieldnlp.github.io/fever/data.html) and unzip it into the data folder.
    
    wget https://s3-eu-west-1.amazonaws.com/fever.public/wiki-pages.zip
    unzip wiki-pages.zip -d data
    
Wiki-pages data is in the dictionary form. The keys are "id", "text" and "lines" that mean the wiki-page URL, content of the wiki-page and each sentence in the content. Note that the sentence is seperated by \n and the marking number starts from 0. 

## Read Data
Use the fever_io.py to read the fever project dataset. You may also refer to [https://github.com/sheffieldnlp/fever-naacl-2018/tree/master/src/scripts](https://github.com/sheffieldnlp/fever-naacl-2018/tree/master/src/scripts).


## Find Out More

 Visit [http://fever.ai/2018/task.html](http://fever.ai/2018/task.html) to find out more about the shared task.
