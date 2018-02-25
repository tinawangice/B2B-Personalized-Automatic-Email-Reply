# Email_generation_seq2seq_backend

## The email generation system contains 2 main parts: 

#### 1.	Seq2Seq Model for email generating – which will automatically output the reply based on the input. 
#### 2.	API connects gmail to the Seq2Seq Model 

The data is from:  https://www.cs.cornell.edu/~cristian/Cornell_Movie-Dialogs_Corpus.html


### Step1: Data Preparation
There are 10,000 dialogues cleaned for the training. To simplify the training process, all sentences are padded into length of 50. Each word is embedded into 100 dimension vectors(https://nlp.stanford.edu/projects/glove/).

### Step2: Build LSTM layers with Keras
After data preparation, 2 LSTM layers are built with Keras. 
The embedded questions are input for first LSTM, which output a 300-dimension vector for each question. 
The 300-dimension vector can be thought as the summary of the question, and becomes input for the second LSTM layer.

Using GPU, it took 1 week to train 16,000 dialogues for 160 epochs. The loss decreased from 8 at beginning to 0.03.

### Step3: API connects to Gmail
Finally, fetch_emails.py will fetch information from emails. The email body will generate from the trained Seq2seq model.







