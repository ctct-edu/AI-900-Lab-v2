---
lab:
  title: Language Studio で質問応答を使用する
---

# LanguageのQ&A機能を使用して質問応答を使用する

この演習では、質問と回答のナレッジ ベースを作成し、トレーニングします。 ナレッジ ベースのコンテンツは、架空の旅行代理店である Margie's Travel の Web サイトにある既存の FAQ ページから取得されます。 その後、それを顧客が使用したときに役に立つかどうかを、Language Studio を使用して確認します。

Azure AI Language には "質問応答" 機能が含まれています。それを使用してナレッジ ベースを作成します。ナレッジ ベースは、質問と回答のペアを手動で入力することによって、あるいは既存のドキュメントまたは Web ページから作成できます。 Margie's Travel では既存の FAQ ドキュメントを使用したいと考えています。

言語サービスの質問応答機能を使用すると、質問と回答のペアを入力することによって、あるいは既存のドキュメントまたは Web ページからナレッジ ベースをすばやく作成できます。 その後、組み込みの自然言語処理機能を使用して、質問を解釈し、適切な回答を見つけ出します。

## 推定時間 : 30 分

## Languageリソースを作成する

質問応答を使用するには、**Language**リソースが必要です。

1. 別のブラウザー タブで Azure portal ([https://portal.azure.com](https://portal.azure.com?azure-portal=true)) を開き、研修用の Microsoft アカウントを使用してサインインします。

    > MFAが求められた場合は画面の指示に従ってMicrosoft Authenticatorをセットアップして認証を行ってください

1. **[&#65291;リソースの作成]** ボタンをクリックし、**言語サービス**を検索します。 **言語サービス** のタイルで**作成** ボタンから **言語サービス** を選択します。 **[Select additional features]** ページが表示されたら次の設定を使用します。

    - **Default features(既定の機能)**: 既定の機能はそのままにしておきます
    - **Custom features(カスタム機能)**: Custom question answering(カスタム質問応答)を選択(select)します
    
    **[Continue to create your resource]** を選択します
    
1. **[Create Language]** ページで、次の設定を指定します。

    - **Project Details(プロジェクトの詳細)**
        - **[サブスクリプション]**: 従量課金
        - **[リソース グループ]**: 既存のリソース グループから選択(AI900StudentXX)
    - **Instance Details(インスタンスの詳細)**
        - **[リージョン]**: East US 2    
        - **名前**: グローバルに一意な名称
        - **価格レベル**: S もしくは F0
    - **Custom question answering(カスタムの質問応答)**
        - **Azure Search のリージョン**: East US 2
        - **Azure Search の価格レベル**: Basic B(15 indexes) もしくは Free F (3 Indexes) 
    - **Responsible AI Notice(責任ある AI に関する通知)**
        - **チェックボックス**: オン（チェックを入れる）

1. **[確認と作成]** を選択し、次に **[作成]** を選択します。 カスタム質問応答ナレッジ ベースをサポートする言語サービスがデプロイされるのを待ちます。

    > **注** 無料レベルの **Azure Cognitive Search** リソースを既にプロビジョニングしてある場合は、クォータにより、別のリソースを作成できない場合があります。 その場合は、**Free F** 以外のレベルを選択します。

## 新しいプロジェクトの作成

1. 新しいブラウザー タブで Language Studio ポータル ([https://language.azure.com](https://language.azure.com?azure-portal=true)) を開き、画面右上のSign Inボタンから研修用の Microsoft アカウントを使用してサインインします。

1. 言語リソースの選択を求めるメッセージが表示されたら、次の設定を選択します。
    - **Azure Directory**:*サブスクリプションを含む Azure ディレクトリ*(CTCテクノロジー株式会社)。
    - **Azure Subscription**: *使用する Azure サブスクリプション*(従量課金)
    - **Resource name**:*前のタスクで作成したリソース。*

    言語リソースの選択を求めるメッセージが表示***されない***場合、原因として、お使いのサブスクリプションに複数の言語リソースが存在していることが考えられます。その場合は、次の操作を行います。
    1. ページの上部にあるバーで、**[設定] (&#9881;)** ボタンを選択します。      
    1. **[設定]** ページで、**[リソース]** タブを表示します。
    1. 先ほど作成した言語リソースを選択し、[**リソースの切り替え**] を選択します。
    1. ページの上部で、[**Language Studio**] を選択して、Language Studio のホーム ページに戻ります。

1. Language Studio ポータルの上部にある **[Understand questions and conversational language]** のタブに切り替え、**[Custom question answering]** を選択します。 **[Create new project]** で新しいカスタム質問応答プロジェクトを作成します。

1. **[Choose language setting for resource]** ページで、 **[I want to select the language when I create a projects in this resource(このリソースでプロジェクトを作成するときに言語を選択する)]** を選択し、 **[Next]** をクリックします。**
   
1. **[Enter basic information]** ページで、次の詳細を入力し、**[Next]** をクリックします。
   
    - **language resource**: 選択済みの言語リソース  
    - **Azure Search resource**: 選択済みのAzure Search リソースAzure Search リソース
    - **name**: `MargiesTravel`
    - **description**: `A simple knowledge base`
    - **source language**: 日本語(Japanese)
    - **Default answer when no answer is returned**: `答えが見つかりません`
    
1. **[Review and finish]** ページで、**[create project]** を選択します。

1. **[Manage sources(ソースの管理)]** ページが表示されます。 **[+Add source]** を選択し、**[URLs]** を選択します。

1. **[Add URLs]** ボックスで、**[+ Add url]** を選択します。 次のように入力し、 **[Add all]** を選択します。
   
    - **URL の名前**: `MargiesKB`
    - **URL**: `https://raw.githubusercontent.com/ctct-edu/AI-900-Lab-v2/main/LabManual/doc/margies_faq.docx`
    - **classify file structure**: "Auto-detect "

## ナレッジ ベースを編集する

ナレッジ ベースは、FAQ ドキュメントの詳細と事前定義の応答に基づいて作成されます。 カスタムの質問と回答のペアを追加して、これらを補完することができます。

1. 左側のパネルを展開し、**[Edit knowledge base]** を選択します。 次に、**[+]** を選択して新しい質問ペアを追加します。
1. **[Add a new question answer pair]** ダイアログ ボックスで、**[Question]** に「`こんにちは`」と入力し、**[Answer]** に「`こんにちは！ご質問はなんでしょうか？`」と入力して、**[Done]** を選択します。
1. 追加したQAペアを選択して、**[Alternate questions]\(代替の質問\)** を展開します。**[+ Add alternate question]\(+ 代替の質問を追加する\)** を選択します。 次に、"こんにちは" の代替フレーズとして「`ご質問をどうぞ！`」を入力します。
1. **[Question answer pairs]** ペインの上部にある **[保存(フロッピー状のアイコン)]** を選択してナレッジ ベースを保存します。

## ナレッジ ベースのトレーニングとテスト

ナレッジ ベースが作成されたので、それをテストできます。

1. **[Question answer pairs]** ペインの上部にある **[テスト(フラスコ型のアイコン)]** を選択してナレッジ ベースをテストします。
1. テスト ペインの下部に「`こんにちは`」というメッセージを入力します。 *こんにちは！ご質問はなんでしょうか？* という応答が返されます。
1. テスト ペインの下部に「`航空券の予約をしたいです`」というメッセージを入力します。 FAQ から適切な応答が返されるはずです。

    > **注** 応答には、"短い回答" とより詳細な "回答文節" が含まれています。回答文節には、最も一致する質問の FAQ ドキュメントの全文が表示され、短い回答は文節からインテリジェントに抽出されます。** ** テスト ペインの上部にある **[短い回答を表示する]** チェック ボックスを使用して、応答から短い回答を得るかどうかを制御できます。

1. `予約のキャンセルをしたい場合はどうすればよいですか？` のような別の質問を試してみてください
1. ナレッジ ベースのテストが完了したら、**[テスト]** を選択してテスト ペインを閉じます。

## 詳細情報

- 質問応答サービスの詳細については、[こちらのドキュメント](https://docs.microsoft.com/azure/cognitive-services/language-service/question-answering/overview)を参照してください。
