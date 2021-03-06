# General-object-recognition-in-Keras-style-improved-version-__Tensorflow_and_Keras__
Kerasを用いて、一般物体認識を行いました。今回はデータに一般物体認識のデータセット[CIFAR-10]を利用しました。 
# General-object-recognition-by-Keras-style__Tensorflow_and_Keras__

こちらの改良版になります。  
データ拡張として、カラー画像に移動、回転などの処理を加えてデータの水増しを行いました。  
また、オーバーフィッティングさせないために、畳み込み層にL^2ノルムによる正則化の処理を追加しました。  

ネットワークの構築は、モデルの構築の実行結果を見てください。 

【考察】  
訓練データ、テストデータそれぞれの精度は、20エポック付近まで急激に上昇し、あとは緩やかに上昇しています。30エポックと50エポックあたりで階段状
に上昇している箇所がありますが、おそらく局所界に捕まっていたのを脱したものと思われます。双方のグラフが離れることなく同じように上昇していることから、
オーバーフィッティングが発生していないということが分かります。  

損失に関しても、双方の曲線とも同じように下降しているので、このことからもオーバーフィッティングは発生していないことが分かります。

オーバーフィッティングが発生しなく、精度も良いはずなのに、画像を入力して認識させてみた時に、画像認識がうまくいっていない理由が分かりません。  
ここに関して調べ次第、更新します。

【追記】  
訓練データだけでなく、検証データも前処理で正規化を行っていました。予測ロジックではデータセットの画像を無加工で推論しているためこの部分で乖離がありました。正規化を行うとx_testの素性がデータセットに影響して加工されてしまうので、予測ロジックは合っていてバッチ処理が誤っていると考えられるので、x_testの正規化の部分を削除することで、テストデータでも画像認識を成功させることができました。

***
.ipynbファイルが開かれない時は、こちらのリンクにURLを貼ってご覧になってください。  
[nbviewer](https://nbviewer.jupyter.org/)
