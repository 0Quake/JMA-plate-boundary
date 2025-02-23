# 気象庁によるプレート境界 GISデータ
気象庁による「震度データベース」などのコンテンツでは、プレート境界が描かれた地図が表示される。このプレート境界のデータは、有名なPeter Birdらによるデータとは異なり、気象庁が独自に解析したものと思われる。この地図を高精度にトレースし、GISデータに起こしたものを公開する。

[**動的サンプル**](https://github.com/0Quake/JMA-plate-boundary/blob/main/Plate_Boundaries.geojson)

![image](https://github.com/user-attachments/assets/fba03043-e1ed-44ab-8b57-fdc195d7dadc)

## データの作成方法
1. 気象庁HP「震度データベース」で表示される地図のタイルをQGISに読み込む
2. ズームレベル11まで拡大し、灰色線で表示されるプレート境界線に沿ってラインを描く
3. スムージング処理（Plate_Boundaries_smoothed.geojsonのみ該当）
4. 目視でズレがないか確認（全数調査）

## データの仕様
データはGeoJSON形式で、3つのMultiLineString Featureで構成される。
プレート境界の解釈に関しては諸説あるため、各LineStringがどのプレートとどのプレートの境界にあたるかの記述は省く。利用者側で解釈し、追加することを想定している。
1. [Plate_Boundaries.geojson](https://github.com/0Quake/JMA-plate-boundary/blob/main/Plate_Boundaries.geojson)（平滑化なし）
2. [Plate_Boundaries_smoothed.geojson](https://github.com/0Quake/JMA-plate-boundary/blob/main/Plate_Boundaries_smoothed.geojson)（平滑化済み）

※後者は、手描きに起因する荒さを平滑化しているため、人の目に触れる用途に適していると思われます。ただし、機械的処理には前者が適していると思われます。

## 出典
- 気象庁「震度データベース検索」([https://www.data.jma.go.jp/eqdb/data/shindo/](https://www.data.jma.go.jp/eqdb/data/shindo/), 閲覧：2025/02/23, 地図部分を編集して使用)
