# The general procedure of this notobook is:

1.  Pre-train the model with negative log-likelihood loss and save multiples model checkpoints to 'save_model_path' defined in 'Config' tab.

2.  Evaluate the 'ROUGE-l' value of each saved model using 'eval' and select the one with highest 'rouge' score.

3. Train the selected best model with 'RL+MLE' or purely 'RL' loss obejective. Also the code would update parts of your previous saved models.

4.  Use 'eval' again to measure the performance of new updated models and similarly, select the one with highest 'rouge-l' score.

5.  Do testing on the best model using 'test' and output a series of 'rouge' statistics.

6.  Probably can print out some examples (article+AS)


# Some comments regarding to the model

The model we use in this notebook is mainly from the paper [A DEEP REINFORCED MODEL FOR ABSTRACTIVE SUMMARIZATION](https://arxiv.org/pdf/1705.04304.pdf), with some complementary code from [Get To The Point: Summarization with Pointer-Generator Networks](https://arxiv.org/pdf/1704.04368.pdf).

## Encoder:  
* a```bi-direction LSTM``` layer with dimension ```emb_dim = 256, hidden_dim = 512```, the output (h,c) would actually contain ```hidden_dim * 2``` dimension hidden states and also for cell state.


* a ```reduced_h``` and ```reduced_c``` linear MLP layer with input dimension ```hidden_dim * 2``` and output dimension ```hidden_dim```. The purpose of this layer is to reduce the diemnsion of bi-directional hidden and cell state.

* So the output of ```forward``` function in Encoder is ```enc_out, (h_reduced, c_reduced)```

## Encoder attension

* ```W_h, v``` are both linear layer without bias term, ```W_s``` is a normal linear layer. This follows the equation (1) in [pointer](https://arxiv.org/pdf/1704.04368.pdf), outputing the attention score e.

* ```intra_encoder``` follows equation (3,4,5) in [deep](https://arxiv.org/pdf/1705.04304.pdf), which corresponds to the softmax fucntion (equation (2) in [pointer](https://arxiv.org/pdf/1704.04368.pdf))

* Next we need to zero out the probability assigned to padded elements

* At last compute the context vector h

## Decoder attention

* Follows equation (6,7,8) in [deep](https://arxiv.org/pdf/1705.04304.pdf)

## Decoder

* contains both ```encoder_attention, decoder_attention``` layers, a ```x_context``` linear layer, a ```uni-directional LSTM``` layer and pointer network

* ```x_context``` taks input to the decoder and encoder context vector

* Then send the result to ```uni-lstm``` , ```s_t``` is the decoder state

* Next is the encoder and decoder attention layer

* Then is the token-generation layer following equation (9)[deep](https://arxiv.org/pdf/1705.04304.pdf) and also sigmoid activation function (equation (11)). Also pointer mechanism is included in the code (equation 9 in [pointer](https://arxiv.org/pdf/1704.04368.pdf) )

















