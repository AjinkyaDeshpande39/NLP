# NEURAL MACHINE TRANSLATION BY JOINTLY LEARNING TO ALIGN AND TRANSLATE
> https://arxiv.org/abs/1409.0473based  This paper proposes a the pioneering paradigm for nerual machine translation using a simple yet applaudable encoder-decoder RNN pair.
>  Although, being the poorest of performers in this list, it earns a spot due to its novely.
>   Note: A few changes have been made in order to improve performance
>   
>CODE - Attention_contextInputToHidden_bidirectional.ipynb
>
>SAVED MODEL - Attention_contextToHidden_bidirectional.pth
>
>Directory also contains some results in detail in txt format

.........................................

This paper describe a modified version of seq2seq model. Attention is a method that allowes decoder to get develepoed based on looking at individual encoder timestep. This model 
is very much similar to model built in previous project.

Encoder is built with 2 LSTM bidirectional layers and linear layer stacked over it. The paper decribes about reversing thetarget sentence but we didnt do that. 
Linear layer is added so that model learns direct long term dependencies among words . It increases performance.  
Tanh gives better results over ReLU. Encoder basically encodes source sentence that is german here. This encoding will be used by decoder to translate

Decoder takes encodings of source sentence. Decoder builds relation between source and target sentences.
Decoder is consisting of just 2 layers of LSTM. If context vector ( from prrevious timestep) is provided , the it will be concatenated with current word vector and passed through linear layer to decrease the hidden dimension.

![](https://github.com/AjinkyaDeshpande39/NLP/blob/master/seq2seq_attention/model.png)

The part of attention is written in Transaltion class. Firstly source encodings and target encodings are obtained from Encoder and Decoder . 
Then , context vector is calculated over here. For first timestep , a zero vector as context vector will be passed to decoder that will be ignored in deoced block and wont be concatenated. After that for nth timestep , context vector of n-1th timestep is passed.
This enhances performance of model. Model lerns current word mapping based on previous hidden as well as previous context vector.

Embeddings were not pretrained . They were trained during training this seq2seq with attention model.

Below i am providing results of code . Here , BLEU score is used as metric over performance of model.
>#embedding = 64 
>#hidden_size = 512
>#num_layers = 2
>#batch_size = 128
>#learning_rate = 0.006
>#epochs = 8

![](https://github.com/AjinkyaDeshpande39/NLP/blob/master/seq2seq_attention/Attention%20loss2.png)
*Train loss*

![](https://github.com/AjinkyaDeshpande39/NLP/blob/master/seq2seq_attention/Attention_contextInputToHidden_bidirectional_val.ipynb.png)
*Validation loss*


# Some results.
Model obtains BLEU score of *30.2* that is quite appreciable
These are pairs of actual and predicted sentences.
['two', 'white', 'men', 'are', 'outside', 'near', 'some', 'sort', 'of', 'canopy', '.']
['two', 'young', ',', 'white', 'males', 'are', 'outside', 'near', 'many', 'bushes', '.']

['several', 'men', 'in', 'hard', 'hats', 'are', 'operating', 'a', '<unk>', 'sign', '.']
['several', 'men', 'in', 'hard', 'hats', 'are', 'operating', 'a', 'giant', 'pulley', 'system', '.']

['a', 'little', 'girl', 'is', 'climbing', 'a', 'snow', 'covered', 'fence', '.']
['a', 'little', 'girl', 'climbing', 'into', 'a', 'wooden', 'playhouse', '.']

['a', 'man', 'in', 'a', 'blue', 'shirt', 'is', 'standing', 'on', 'a', 'ladder', 'cleaning', 'a', 'window', '.']
['a', 'man', 'in', 'a', 'blue', 'shirt', 'is', 'standing', 'on', 'a', 'ladder', 'cleaning', 'a', 'window', '.']

['speaks', 'at', 'the', 'stove', 'preparing', 'food', '.']
['two', 'men', 'are', 'at', 'the', 'stove', 'preparing', 'food', '.']

['a', 'green', ',', 'green', ',', 'green', ',', 'and', 'the', 'other', 'man', 'looking', 'back', 'as', 'the', 'other', 'man', 'observes', 'his', 'shirt', '.']
['a', 'man', 'in', 'green', 'holds', 'a', 'guitar', 'while', 'the', 'other', 'man', 'observes', 'his', 'shirt', '.']

['a', 'couple', 'is', 'enjoying', 'a', 'tattoo', '.']
['a', 'man', 'is', 'smiling', 'at', 'a', 'stuffed', 'lion']
