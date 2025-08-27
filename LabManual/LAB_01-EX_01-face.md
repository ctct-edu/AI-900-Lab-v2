---
lab:
  title: Vision Studio で顔を検出する
---

# Faceの機能を使用して顔を検出する

Vision ソリューションは、多くの場合、AI が人間の顔を検出できることを必要とします。 架空の小売企業 Northwind Traders が、最適な支援を提供するために、顧客が店舗内のどこに立っているかを特定するとします。 これを実現する 1 つの方法は、画像内に顔があるかどうかを判別し、ある場合は、その場所を示す境界ボックス座標を返すことです。

## 推定時間 : 10 分

## 演習リソース作成

　 [**Lab00の手順**](./LAB_00-Startup_Hands-on_Lab.md)  に従って、リソースを作成してください。

 - すでに実施済みの場合は、次の手順に進んでください。

## Azure AI Visionへのアクセス

1. 作成したプロジェクトにアクセスをします。Azure AI Foundry Portalの左側に表示されるメニューから **AIサービス** を選択します。 

1. 移動した **Azure AI サービス** のページで **AI機能を使用してソリューションを活性化する** のセクションから **Visionとドキュメント** を選択します。

1. **Vision + Document** の画面が表示され、Visionの機能をテストすることが可能となっていることが確認できます。

   

## Faceの機能で顔を検出する 

1. **View all other vision capabilities** セクションにて、 **Face** タブに切り替えて  **[Detect faces in an image]** のタイルをクリックします。

1. 以下のリンクを使用してファイルをダウンロードします。ダウンロードしたzipファイルは展開してから使用します。

    [**https://aka.ms/mslearn-detect-faces**](https://aka.ms/mslearn-detect-faces)

1. **store-camera-1.jpg** という名前のファイルを見つけます。2名の人物が含まれる画像で片方だけ顔が見えている状態です。

1. **Drag and drop video file here~** と書かれているボックス（サンプル画像左側）から **store-camera-1.jpg** をアップロードし、返される顔検出の詳細を確認します。

1. **store-camera-2.jpg** という名前のファイルを見つけます。先ほどの画像より人物が増え、全員の顔の一部が確認できる状態です。

1. 先ほどと同様に **store-camera-2.jpg** をアップロードし、返される顔検出の詳細を確認します。

1. **store-camera-3.jpg** という名前のファイルを見つけます。1枚目の画像と類似していますが、人物の顔が植物によってマスクされています。

1. **store-camera-3.jpg** をアップロードし、返される顔検出の詳細を確認します。 隠れている顔が Azure AI Face によってどのように検出されなかったかについて注目してください。

この演習では、Azure AI サービスが画像内の顔をどれだけ検出できるかについて説明しました。 時間がある場合は、サンプル画像や独自の画像をいくつか自由にお試しください。

## 詳細情報

このサービスでできることについて詳しくは、[Azure AI Face サービスに関するページ](https://learn.microsoft.com/azure/ai-services/computer-vision/overview-identity)を参照してください。
