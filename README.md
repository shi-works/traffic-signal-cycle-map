# traffic-signal-cycle-map
## Public Website
https://shi-works.github.io/traffic-signal-cycle-map/
## サンプル画像
![image](https://user-images.githubusercontent.com/71203808/232997203-c44e3aab-d648-4be7-97bd-b635d3eaedb2.png)

# データの取得
## 交差点制御情報
### jartic_opendata_kousaten_dl.py
- 日本道路交通情報センター（JARTIC）がオープンデータとして公開している、[交差点制御情報（zip形式）](https://www.jartic.or.jp/)を一括でダウンロードするプログラムです。
#### 使用データ  
`kousaten_PrefRoman.csv`
#### データ取得結果  
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/traffic-signal-cycle/data/202304030911.7z`,286.7MB

# データの加工
## 交差点制御情報
### calc_average_cycle.py
- [交差点制御情報（csv形式）](https://www.jartic.or.jp/)をもとに、信号の平均サイクル長を算出するプログラムです。
#### 使用データ
- 交差点制御情報
- zipファイルをcsvファイルに解凍したものを使用
- ファイル名に「制御」の記載のあるcsvファイルを使用  
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/traffic-signal-cycle/data/202304030911.7z`,286.7MB
#### 出力結果  
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/traffic-signal-cycle/out/Pref_Control_202302_Average_Cycle.7z`,415.1KB

### csvfile-merge.py
- 算出した、47都道府県の平均サイクル長（csv形式）をマージするプログラムです。
#### 出力結果  
``

### csvfile-add-latlon.py
- マージ済みの平均サイクル長（csv形式）に信号交差点の位置座標を付与するプログラムです。
#### 使用データ  
`全国_制御_202302_平均サイクル長.csv`  
`intersection_position.csv`※後述の交差点位置情報

## 交差点位置情報

# ライセンス
本データセット（使用データ及び出力結果）は[CC-BY-4.0](https://github.com/shi-works/traffic-accident-pmtiles/blob/main/LICENSE)で提供されます。使用の際には本レポジトリへのリンクを提示してください。

また、本データセットは、第13回大都市交通センサスの定期券発売実績調査データを加工して作成したものです。本データセットの使用・加工にあたっては、[国土交通省のリンク・著作権・免責事項](https://www.mlit.go.jp/link.html)を必ずご確認ください。

# 免責事項
利用者が当該データを用いて行う一切の行為について何ら責任を負うものではありません。
