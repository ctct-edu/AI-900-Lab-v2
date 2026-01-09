---
lab:
  title: 'ラボ 03: Extract data from document'
  module: Module04 Knowledge Mining
---

# ラボ 03 - Document Intelligenceを使用してドキュメントを分析する

## ラボ概要

Azure AI Document Intelligence は、フォームやドキュメントから情報を分析して抽出し、フィールド名とデータを識別できます。

このラボではレシートに記載された内容をDocument Intelligenceのモデルを使用して分析します。

## 推定時間 : 10 分

## 演習リソース作成

　 [**Lab00の手順**](./LAB_00-Startup_Hands-on_Lab.md)  に従って、リソースを作成してください。
 - すでに実施済みの場合は、次の手順に進んでください。

## タスク1 : Document Intelligence へのアクセス

作成したプロジェクトにアクセスをします。Azure AI Foundry Portalの左側に表示されるメニューから **AIサービス** を選択します。 

   ![](./media/lab1/02.png)

移動した **Azure AI サービス** のページで **AI機能を使用してソリューションを活性化する** のセクションから **Visionとドキュメント** を選択します。

![](./media/lab1/03.png)

**Vision + Document** の画面が表示され、Document Intelligenceの機能をテストすることが可能となっていることが確認できます。

![](./media/lab1/04.png)

## タスク 2 : ドキュメントの分析

このタスクでは、Document Intelligence を使用して事前構成済みのモデルでレシートの内容を分析します。

1. **View all other vision capabilities** セクションにて、 **Document** タブの **[Receipts]** のタイルをクリックします。

    ![](./media/lab3/01.png)

1. 分析対象となるレシートを用意します。今回は以下のURLより画像をダウンロードします。
    [**https://aka.ms/mslearn-receipt**](https://aka.ms/mslearn-receipt)

    ※右クリックで「名前を付けてリンク先を保存」を選択すること等でダウンロード可能です

1. ダウンロードしたレシート画像を読み込みます。画面左側の **[Browse for files]** をクリックし、ダウンロードしたファイルを選択します。

    ![](./media/lab3/02.png)

1. ファイルが読み込まれたことを確認して、 **[Run analysis]** をクリックして分析を開始します。

1. 分析が完了すると画面右側に結果が表示されます。 **[Field]** タブで各項目の読み取り内容、確度を確認することができます。一部のアイテム（今回は商品明細にあたる **Item** 欄）は省略されているため、展開することが詳細を確認できます。

    ![](./media/lab3/03.png)



以上でDocument Intelligence Studioを使用したラボは完了です！
