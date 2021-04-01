# Attention is all you need

> https://arxiv.org/abs/1706.03762 This paper can be said to have revolutionized almost all of Natural Language Processing, all owing to its tremendous simplicity and efficiency which makes it the backbone of almost all present State Of The Art architectures. 
> The proposed Transformer architecture introduces a novel metric called Self-Attention which induces a sense of (soft)alignment amongst the source sentence tokens too.
>
>CODE - seperated_of_trainable_PE_Transformers_(1)_(1).ipynb
>
>SAVED MODEL - Transformer_seq1.pth
>
>Directory also contains some results in detail in txt format
..........................

Dataset used - torch.dataset Multi30k for German to english translation . i.e source sentences are german and target sentences are english.

Embeddings were kept trainable . Fixed embeddings didnt give best results.

The model introduces idea of masked self attention. just like attention used in previous project but not with encoder , decoder , but attention with same kind .
Also, encoder decoder attention is also mentioned in paper and implemented as well.

![](https://github.com/AjinkyaDeshpande39/NLP/blob/master/Attention%20is%20all%20you%20need/transformers_model.png)

**Encoder** -
> - Multihead self attention
> - Feedforward layer

Encoder class is the block which takes source sentences , mapps their attention and applies a add and norm layer at the end.
Here, we have implemented a different approch. Distict Linear layers are used for creating distinct attention heads. These will be used to calculate attention outputs and these outputs will be concatenated . 
Here , number of heads were kept 4 to obtained the best results. Later, they are concatenated and passed through feed forward layer. After each layer within Encoder , residual connection 
followed by layer normalization is applied.

**Decoder**-
> - Multihead self attention
> - Multihead encoder decoder attention
> - Feedforward layer

Decoder block takes target sentence embeddings ,finds self attention , finds attention with encoder's last layer, and then feed forward layer. 
After every operation, residual connection is obtained and layer normalization is applied. Here also distict heads were giving good results. 
Number of heads is kept 4 to obtain best results. 

Transformer model will be as follows - :
> 1) Encoder 
> 2) Decoder (along with encoder's last layer output).
> 3) Linear layer (to map from hidden dimension to output vocab dim)
> 4) Softmax layer is used in paper but we didnt use because we are already using crossentropy loss. Also combination of both doesnt give good results.

**Some hyperparameters** :
>d_model = 512   # embedding dimension
>d_k = 64    # head dimention
>n_dk = 4
>batch_size = 128
>learning_rate = 0.0004
>epochs = 13

detailed description given in txt format.

**some results** :
**BLEU score of *33.02* was obtained** which is greater than previous 2 projects.

These are pairs of actual and predicted sentences.
['a', 'man', 'in', 'an', 'orange', 'hat', ',', 'orange', 'and', 'white', '<unk>', '.']
[['a', 'man', 'in', 'an', 'orange', 'hat', 'starring', 'at', 'something', '.']]

['a', 'boston', '<unk>', 'terrier', 'runs', 'over', 'grass', 'in', 'front', 'of', 'a', 'white', 'fence', '.']
[['a', 'boston', 'terrier', 'is', 'running', 'on', 'lush', 'green', 'grass', 'in', 'front', 'of', 'a', 'white', 'fence', '.']]

['a', 'girl', 'in', 'a', 'karate', 'uniform', 'is', 'doing', 'a', 'trick', '.']
[['a', 'girl', 'in', 'karate', 'uniform', 'breaking', 'a', 'stick', 'with', 'a', 'front', 'kick', '.']]

['five', 'people', 'in', 'winter', 'jackets', 'with', 'helmets', 'standing', 'in', 'the', 'snow', 'with', 'helmets', 'in', 'the', 'background', '.']
[['five', 'people', 'wearing', 'winter', 'jackets', 'and', 'helmets', 'stand', 'in', 'the', 'snow', ',', 'with', 'snowmobiles', 'in', 'the', 'background', '.']]

['people', 'fixing', 'the', 'roof', 'of', 'a', 'house', '.']
[['people', 'are', 'fixing', 'the', 'roof', 'of', 'a', 'house', '.']]

['a', 'man', 'in', 'a', 'bright', 'yellow', 'and', 'a', 'group', 'of', 'men', 'in', 'a', 'dark', 'dress', 'are', 'standing', 'around', 'a', '<unk>', '.']
[['a', 'man', 'in', 'light', 'colored', 'clothing', 'photographs', 'a', 'group', 'of', 'men', 'wearing', 'dark', 'suits', 'and', 'hats', 'standing', 'around', 'a', 'woman', 'dressed', 'in', 'a', 'strapless', 'gown', '.']]

['a', 'group', 'of', 'people', 'standing', 'in', 'front', 'of', 'art', 'supplies', '.']
[['a', 'group', 'of', 'people', 'standing', 'in', 'front', 'of', 'an', 'igloo', '.']]

