---
lab:
  title: Vision Studio でテキストを読み取る
---

# VisionのOCR機能を使用してテキストを読み取る

この演習では、Azure AI サービスを使用して、Azure AI Vision の光学式文字認識機能を確認します。 Vision Studio を使用して、コードを記述することなく、画像からテキストを抽出する実験を行います。

画像中に埋め込まれているテキストの検出と解釈は、コンピューター ビジョン共通の課題です。 これは、光学式文字認識 (OCR) と呼ばれます。 この演習では、Azure AI Vision サービスを含む Azure AI サービス リソースを使用します。 次に、Vision Studio を使用して、さまざまな種類の画像で OCR を試します。

## 推定時間 : 10 分

## 演習リソース作成

[**Lab00の手順**](./LAB_00-Startup_Hands-on_Lab.md)  に従って、リソースを作成してください。

- すでに実施済みの場合は、次の手順に進んでください。

##  Azure AI Visionへのアクセス

1. 作成したプロジェクトにアクセスをします。Azure AI Foundry Portalの左側に表示されるメニューから **AIサービス** を選択します。 

1. 移動した **Azure AI サービス** のページで **AI機能を使用してソリューションを活性化する** のセクションから **Visionとドキュメント** を選択します。

1. **Vision + Document** の画面が表示され、Visionの機能をテストすることが可能となっていることが確認できます。

   

## OCR機能を使用して画像からテキストを抽出する

1. **View all other vision capabilities** セクションにて、 **Image** タブに切り替えて  **[Optical character recognition]** のタイルをクリックします。
1. 以下のリンクを使用してファイルをダウンロードします。ダウンロードしたzipファイルは展開してから使用します。
    [**https://aka.ms/mslearn-ocr-images**](https://aka.ms/mslearn-ocr-images) 
1. 展開したフォルダ内にある **[advert.jpg]** という名前のファイルを見つけます。**Drag and drop video file here~** と書かれているボックス（サンプル画像左側）からアップロードします。
1. 返却される内容を確認します。
    - **[Detected attributes]\(検出された属性\)** には、画像中に見つかったテキストが領域、行、単語の階層構造で整理されています。
    - 画像では、次に示すように、テキストの場所は境界ボックスによって示されます。

1. ここで、別の画像を試してみましょう。次は **letter.jpg** をアップロードします。

1. 2 つめの画像の結果を確認します。 テキストと、テキストの境界ボックスが返されるはずです。 時間がある場合は、**note.jpg** と **receipt.jpg** を試してください。

時間がある場合は、サンプル画像や独自の画像をいくつか自由にお試しください。日本語が含まれる画像の読み取りも可能です。

このサービスでできることの詳細については、[光学式文字認識](https://learn.microsoft.com/azure/ai-services/computer-vision/overview-ocr)に関する Azure AI Vision のドキュメントを参照してください。
