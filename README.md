# ReadMe
- 何をやっているのか
  - 東日本大震災で発生した津波が、例え遠隔地であっても地価に間接的な下落(因果効果)をもたらすのでは？という仮説をDifference-in-differencesというモデルで検証した。
- どのように行ったのか
  - 「遠隔地」を和歌山県に設定(∵ 東日本大震災の被災地から距離がある、沿岸部の地域と内陸部の地域が大体半々くらい、原子力発電所がないのでその分交絡因子をカットできる)
  - 土地総合情報システム(by 国土交通省)というサイト( https://www.land.mlit.go.jp/webland/ ) から和歌山県の地価データをスクレイピング(beautiful soup)
  - pd.DataFrame型にデータを直して、分析に必要なデータを加える(地価と年月、住所はサイトからそのまま持ってこれるので、市町村ごとに標準誤差をクラスタリングするためのダミーを作る)
  - 内陸部と沿岸部の平均地価のグラフから(i)平行トレンドを満たしていること、(ii)2012年以降で沿岸部は地価の落ち込みがあることを確認。(厳密に確認しようとすると検定をしなければいけないが、今回は簡易版ということでグラフで確認するだけにとどめる)
  - DIDモデルを立ててRで結果を確認。(立式についてはnotebook参照)
- 結果
  - DID estimator の推定量は -5815, p値 0.0002529.
-　まとめ
  - 東日本大震災によって和歌山県沿岸部の地価は5815円下落した。
  - 大震災によって、例え直接的な被害は被っていなくとも、人々のリスク認知が変容した結果として沿岸部の地価の下落がもたらされたのかもしれない。
