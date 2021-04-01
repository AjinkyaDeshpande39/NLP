# Seq2seq
 > based on paper sequence to sequence learning with neural networks
 >https://arxiv.org/abs/1409.3215
 >This paper proposes a the pioneering paradigm for nerual machine translation using a simple yet applaudable encoder-decoder RNN pair. Although, being the poorest of performers in this list, it earns a spot due to its novely.
Note: A few changes have been made in order to improve performance
>
>CODE - Translation(1) (1).ipynb
>
>SAVED MODEL - translate2_4.pth

In this project , we built an NMT model based on seq2seq paper. Model consists of Encoder rnn and Decoder rnn. 

Dataset used was Multi30k from torchtext.dataset. 
Source is German and Target is English. i.e. task is to build model that would able to translate from German to English.

![](https://github.com/AjinkyaDeshpande39/NLP/blob/master/seq2seq/block_diag.png)

Encoder performs task of forming a vector encoding of complete sentence that will be passed into decoder. 
Decoder based on source encodings and target sentence develops relation between source and target languages . This trained model then could be used for translation porpose.

Here , encoder is built with simple pytorch's inbuilt LSTM units. Embeddings are made trainable. We used LSTM because it is helpfull in building long term dependencies

Decoder takes last hidden state of encoder and word encodings and generates output sentence. It builds relation between soruce that is german here and target that is english here.

With the model built , below are listed some hyperparameters and results . Although loss is not good metric for NLP tasks, Loss is also plotted to check convergence of model
>
>#embedding = 60
>#output_size = english_vocab_size
>#hidden_size =128
>#num_layers = 2
>#batch_size = 128
>#learning_rate = 0.01
>#epochs = 5
>
![](https://github.com/AjinkyaDeshpande39/NLP/blob/master/seq2seq/train_loss.png)
*train loss*


# Some results 
sentence = 'ein mann lehnt sich in der nähe einer belebten straße an ein gebäude .'  # 'a man leans against a building near a busy street .'
predicted - 'a man is standing in the middle of a large crowd'

>#Note 
> Although the results obtained were not very good, this project gave us an exposure to the neural machine translation.
