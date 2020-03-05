### Comment on [how to make binary data file from raw txt data](https://github.com/rohithreddy024/Text-Summarizer-Pytorch/blob/master/make_data_files.py)

refer to `rohithreddy024/Text-Summarizer-Pytorch/make_data_files.py`

#### Required Paths 

There are 3 paths required to be stated at the begining of the codes `finished_path`, `unfinished_path` and `chunk_path`.
In the sample codes uploaded, I use my own repository but you can change it to yours. You have to upload the data into `data/unfinished` file. But for the rest two, `data/finished` and `data/chunked`, you dont have to create the file, the codes will create for you! 

#### Where do we collect our vocabulary from? 

The codes first collect all volcabulary from the training ariticle file and training summary file. And pick up the most common `VOCAB_SIZE = 200000` words as our finalised vocabulary. We could modify this size by ourselves. 

#### What about chunking file? 

Say you have 1000 articles in your dataset and you want to saparate them into several subfiles. That is what chunking does. By defining the number of articles contained in a single chunk, `CHUNK_SIZE = 1500`. We should take this size into consideration based on the number of articles contained in our dataset. Because, **WikiHow**, **BigPatent** dataset have more articles than CNN/Daily Mails dataset. 

#### Sample Valid and test size

Basically, **validation set** and **test set** are converted into binary file, aka `.bin` file and saved in `data/finished`. And the chunked files are saved in `chunked/main_valid` and `chunked/main_test`. However, when doing experiment, the validation and test set might be too large to perform. Therefore, in the last part of the codes, 

```python
#Performing rouge evaluation on 1.9 lakh sentences takes lot of time. So, create mini validation set & test set by borrowing 15k samples each from these 1.9 lakh sentences
    make_folder(os.path.join(chunk_path, "valid"))
    make_folder(os.path.join(chunk_path, "test"))
    bin_chunks = os.listdir(os.path.join(chunk_path, "main_valid"))
    bin_chunks.sort()
    samples = random.sample(set(bin_chunks[:-1]), 2)  # Exclude last bin file; contains only 9k sentences
    valid_chunk, test_chunk = samples[0], samples[1]
    shutil.copyfile(os.path.join(chunk_path, "main_valid", valid_chunk),os.path.join(chunk_path, "valid", "valid_00.bin"))
    shutil.copyfile(os.path.join(chunk_path, "main_valid", test_chunk), os.path.join(chunk_path, "test", "test_00.bin"))
```

It samples one validation bin file `valid_00.bin` and one test bin file `test_00.bin` from **`main_valid`**. *So the test file here is sampled from the chunked validation dataset!!*

I think we can modify this part to meet our own experiment needs. 


