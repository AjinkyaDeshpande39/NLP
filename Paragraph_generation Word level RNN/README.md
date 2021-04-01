Model was trained over text which contains 4 essays based on internet and information technology collected from various source.

Text consists of
478 distinct words 
27 paragraphs
Each paragraph with atleast 2 sentences and at most 5 sentences
Total number of words in whole text is 1,132


It is observed that model trained with nn.RNN is unable to form long term dependencies.
Meaning of sentence is lost just in 3-4 words . Although it is able to recognise end of paragraph. But sentences are broken abruptly.

Whereas , model trained with nn.LSTM is able to form long term dependencies. Even next sentence formed after one shows some context shared. LSTM shows better results that RNN and GRU. Sentences and paragraphs are ended at proper position and proper meaning than other two

GRU Gives somewhat similar results like LSTM. Sentences show some what meaning and shared context. But next sentence formed looses previous context. Sentence ending and paragraph ending is done properly. Also you can observe that , length of sequence formed decreases. 

Since the model was trained on where less number of paragraph , meaning reflecting from sentence seems quite appreciable. Also difference between these 3 could be observed nore 
Prominently if larger text is chosen.

GRU Loss function


![](https://github.com/AjinkyaDeshpande39/NLP/blob/master/Paragraph_generation%20Word%20level%20RNN/gru.png)

#embedding = 32 output_size = vocab_size = len(word_dict2) hidden_size = 64 num_layers = 2
#learning_rate = 0.01 epochs = 25


LSTM Loss function


![](https://github.com/AjinkyaDeshpande39/NLP/blob/master/Paragraph_generation%20Word%20level%20RNN/lstm.png)

#embedding = 40 output_size = vocab_size = len(word_dict2)  hidden_size = 64 num_layers = 3
#learning_rate = 0.01  epochs = 64


RNN Loss function

![](https://github.com/AjinkyaDeshpande39/NLP/blob/master/Paragraph_generation%20Word%20level%20RNN/rnn.png)

#embedding = 32 output_size = vocab_size = len(word_dict2) hidden_size = 64 num_layers = 2
#learning_rate = 0.01 epochs = 25








**Results** - 


LSTM

testing2('we are living in information'):
'we are living in information other used but also .  it has provided an exciting and internet addiction .  basically internet is a global electronic community for millions of interconnected computer networks . \n'

testing2('today'): 
'today every nook and corner of the world has made a long journey .  also ,  during this journey ,  the internet has adopted many things ,  highly fast ,  cheap ,  safe ,  and least cumbersome . \n'

testing2('internet is'):
'internet is a great tool which man has invented .  its potential is still not fully tapped .  more and more uses of internet are being discovered as days go by . \n'


GRU

testing2('we are living in information'):
'we are living in information from storage areas of the servers called websites .  today we can get any information on any topic in a matter of seconds . \n'

testing2('today'):
'today every nook and corner of the world our through .  and with the speed ,  we are becoming addict to it a day in will come when it will become our basic necessity . \n'

testing2('internet is'):
'internet is a great tool which man has invented .  its potential is still not fully .  more and more uses of internet are being discovered as days go by . \n'


RNN

testing2('we are living in information'):
'we are living in information any topic in seconds . \n'


testing2('today'):
'today every nook and corner of the world .  also ,  these things cause trouble for oneself and others too . \n'

testing2('internet is'):
'internet is a great tool which man has invented .  its potential is still not fully tapped .  have become quite common now- a-days . \n'
