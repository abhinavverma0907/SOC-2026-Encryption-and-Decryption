# NLP
Before moving onto the implementation of the RNNs, we need to have a look over this topic, since the data is not always given in the most easiest to implement form, we need to process the data before passing it to the model which we want to train since model can take in only the numbers.
If you think, passing ASCII values is the way to go then sadly:( it isn't, because the model thinks that A is inferior as compared to Z since its ASCII value is lesser.  
To tackle this we use the embedding of the words technique where we assign each word in a nD vector space and we link the realtionship between two vectors being the inner product of both of them,
and this is precisely what we want the neural network to learn as well.

This is a huge topic in itself, I thought we would go over it when we start transformers but sry, i had to bring this now because of the question, since I thought character-character embedding as done in ceiser cipher might help, but is straight up giving dumb values.
So go over this topic, i would say skim over this as of now understand basic things and we are good to go.     
Resources:   
https://www.geeksforgeeks.org/nlp/text-preprocessing-for-nlp-tasks/      
https://www.youtube.com/watch?v=fLvJ8VdHLA0       
https://www.youtube.com/watch?v=LPZh9BOjkQs&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&index=5
