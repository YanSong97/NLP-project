### Comment on [how to make binary data file](https://github.com/rohithreddy024/Text-Summarizer-Pytorch/blob/master/make_data_files.py)

refer to `rohithreddy024/Text-Summarizer-Pytorch/make_data_files.py`

#### Required Paths 

There are 3 paths required to be stated at the begining of the codes `finished_path`, `unfinished_path` and `chunk_path`.
In the sample codes uploaded, I use my own repository but you can change it to yours. You have to upload the data into `data/unfinished` file. But for the rest two, `data/finished` and `data/chunked`, you dont have to create the file, the codes will create for you! 

#### Where do we collect our vocabulary from? 

The codes first collect all volcabulary from the training ariticle file and training summary file. And pick up the most common `VOCAB_SIZE = 200000` words as our finalised vocabulary. We could modify this size by ourselves. 

#### What about chunking file? 

Say you have 1000 articles in your dataset and you want to saparate them into several subfiles. That is what chunking does. By defining the number of articles contained in a single chunk, `CHUNK_SIZE = 1500`, we should take this size into consideration based on the number of articles contained in our dataset. Because, **WikiHow**, **BigPatent** dataset have more articles than CNN/Daily Mails dataset. 


