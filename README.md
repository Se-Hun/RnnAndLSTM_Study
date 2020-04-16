# RnnAndLSTM_Study
RNN과 LSTM에 대해 공부하고 이를 직접 구현하여 학습 시켜봄.

# RNN과 LSTM을 이해할 수 있도록 잘 정리해준 글

* [ratsgo's blog](https://ratsgo.github.io/natural%20language%20processing/2017/03/09/rnnlstm/)
* [크리스토퍼 오라 블로그의 LSTM 문서](http://colah.github.io/posts/2015-08-Understanding-LSTMs)
* [브랜든 로더 : LSTM을 설명하는 훌륭한 동영상을 제공](https://brohrer.github.io/how_rnns_lstm_work.html)


# LSTM 내부 구조 설명

![LSTM과 RNN 비교](https://github.com/Se-Hun/RnnAndLSTM_Study/blob/master/img/RNNandLSTM_basic_image.png)

위의 그림은 LSTM과 RNN을 비교해둔 그림이다.

LSTM은 RNN의 히든 state에 cell-state를 추가한 구조이다.

### LSTM의 Gate들

**Forget gate**는 ‘과거 정보를 잊기’를 위한 게이트이다. ht−1과 xt를 받아 시그모이드를 취해준 값이 바로 forget gate가 내보내는 값이 된다. 시그모이드 함수의 출력 범위는 0에서 1 사이이기 때문에 그 값이 0이라면 이전 상태의 정보는 잊고, 1이라면 이전 상태의 정보를 온전히 기억하게 된다.

**input gate**는 ‘현재 정보를 기억하기’ 위한 게이트이다. ht−1과 xt를 받아 시그모이드를 취하고, 또 같은 입력으로 하이퍼볼릭탄젠트를 취해준 다음 Hadamard product 연산을 한 값이 바로 input gate가 내보내는 값이 된다.

input gate의 출력에 해당하는 it의 범위는 0에서1, Ct의 범위는 -1에서1이기 때문에 각각 강도와 방향을 나타낸다고 이해할 수 있다.

![LSTM의 Gate들](https://github.com/Se-Hun/RnnAndLSTM_Study/blob/master/img/LSTM_gates.png)

