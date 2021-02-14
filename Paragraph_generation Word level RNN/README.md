Model was trained over text which contains 4 essays based on internet and information technology collected from various source.

Text consists of
478 distinct words 
27 paragraphs
Each paragraph with atleast 2 sentences and at most 5 sentences
Total number of words in whole text is 1,132


It is observed that model trained with nn.RNN is unable to form long term dependencies.
Meaning of sentence is lost just in 3-4 words . Although it is able to recognise end of paragraph. But sentences are broken abruptly.

Whereas , model trained with nn.LSTM is able to form long term dependencies. Even next sentence formed after one shows some context shared. LSTM shows better results that RNN and GRU. Sentences and paragraphs are ended at proper position and proper meaning than other two

GRU also gives disappointing results same as RNN. Sentences show some what meaning and shared context. But next sentence formed has totally different context. Sentence ending and paragraph ending is done properly.

Since the model was trained on where less number of paragraph , meaning reflecting from sentence seems quite appreciable. Also difference between these 3 could be observed nore 
Prominently if larger text is chosen.
