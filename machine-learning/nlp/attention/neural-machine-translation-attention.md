#### Neural Machine Translation By Jointly Learning to Align and Translate
- Paper Link: https://arxiv.org/pdf/1409.0473.pdf
- Conference: ICLR 2015
- Authors: Yoshua Bengio, Dzmitry Bahdanau, KyungHyun Cho

#### Introduction
- Encoder Decoder compress all the information into single vector which might be difficult for longer sentences.
- Hence Performance deterioates over sequence length which is greater than training corpus.
- Solution: Jointly Align and Translate the relavant information only from the text. (Attention)

#### Background: NMT
- Tranlation: finding target sequence y that maximizes **conditional probability** of y given source sentence x.
  - p(y | x)
- Encoder-Decoder based translation:
  - Kalchbrenner, N. and Blunsom, P. (2013). Recurrent continuous translation models. (EMNLP 2013)
  - Cho, K., van Merrienboer, B., Gulcehre, C., Bougares, F., Schwenk, H., and Bengio, Y. (2014a). Learning phrase representations using RNN encoder-decoder for statistical machine translation. (EMNLP 2014)
  - Sutskever, I., Vinyals, O., and Le, Q. (2014). Sequence to sequence learning with neural networks. ( NIPS 2014 )
    - LSTM Based Encoder Decoder for NMT for English to French translation task.
    - Re-Rank Candidate Translation??
- RNN Encoder Decoder
  - Encoder
    - RNN state: h_t = f(x_t, h_(t-1)) -> f: non-linear
    - Context Vector: c = q({h_1, h_2, ..., h_(T_x)}) -> q: non-linear
  - Decoder:
    - Training on: p(y) = Joint Probabity of target labels given source context vector

- Learning to align and Translate (Attention):
  - p(y_i| y_1, ..., y_(i-1), x) = g(y_(i-1), s_i, c_i)
  - context vector: c_i = Weighted Summation(h_i)
  - weights: exp(e_ij) / sum(exp(e_ij))
  - e_ij: Alignment Model: Scores how well pos j matches output i
  
