# Implementation clarifications
This week we dwelled into the RNN architecture and I gave some practice questions on it, Since this topic of NLP, tomake the model and running is pretty straightforwarded but, doing the pre-processing is something new to learn.
I would suggest you to go through the NLP.md once and then try implementing the model since you need to process the data before using it.

Sentiment analysis model:
1. download the dataset using .head() observe the test and the train dataset
2. now use smaller text- in train dataset you will find a selected text, which is samller and would do the work
3. so divide the train data into train and test, since given test data doesnt have te segmented text.
4. now use tokenizer from transformer lib- autotokenizer and tokenize your text
5. make a datast class which return pair of tokenized text and its labels both in npdarray form
6. place them in dataloader and declare all your parameters
7. Make your model and use embedding in it from nn.embedding, ensure you put padding_idx=pad_idx to prevent giving embeddings to 0s which were meant to pad, you can embedd to whatever dimention you like
8. use the nn.rnn to get the output of the rnn as a vector, then use torch.max to find the maximum( this is called pooling, in general you dont do it all the cases but in this case it worked best when pooling was done)
9. then train the model after declaring it

I have implemented this model, use this as a reference when stuck:   
https://drive.google.com/file/d/1pWNCwSANQF-gsVnM5KYFRH4SOY6aQ0Gp/view?usp=sharing

Since, NLP wasn't shared to you before, If you want you can skip this question as of now but do this when we talk about transformers, after LSTM
PS: I actually didnt want to use NLP as of now but without NLP it is not giving satisfactory results but you can do the other one - substituition cipher without NLP.

