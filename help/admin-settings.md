---
title: 管理者設定
description: CRM フィールド、アクティビティの同期、メールオプトアウト、その他のSales Qualifierの管理設定を管理する方法について説明します。
feature: Agentic AI, Sales Insights, Account Journeys
role: Admin
TQID: 'https://experienceleague.adobe.com/vbtO6I67ZEaZz3oio9InNErvq5D0wjbRxyDZpTq8Lzo'
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fc7979f3-56c3-43ca-9784-f1ea3dc69c4b
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
internal-label: Administration
source-git-commit: 527d6a99f1ca51371ab0bc44ee61482bac56fc4f
workflow-type: tm+mt
source-wordcount: 1089
ht-degree: 0%

---


# 管理者設定

**[!UICONTROL 管理者設定]**&#x200B;を使用して、CRM統合の設定、ナレッジセンターの管理、メールのオプトアウトの設定を行います。

Sales Qualifierは、SalesforceまたはMicrosoft Dynamics 365に接続します。 この連携により、Account Qualification Agent（AQA）では、リード、アカウント、取引先責任者、アクティビティ、所有者を一貫して把握できます。 また、Sales Qualifierでは、アウトリーチアクティビティとオプトアウトステータスをCRMに書き込み、アウトリーチアクティビティをMarketoに同期することもできます。

CRM接続、フィールドマッピング、およびアクティビティの同期を設定するには、**[!UICONTROL 管理]** > **[!UICONTROL 管理者設定]** > **[!UICONTROL CRM接続]**&#x200B;に移動します。 標準ユーザーは、設定されたCRM データとフィルターを使用できますが、これらの設定を変更することはできません。 CRMを初めて接続する場合は、[開始](getting-started.md#connect-your-crm)を参照してください。

>[!IMPORTANT]
>
>**[!UICONTROL 管理者設定]**&#x200B;にアクセスするには、`Sales Qualifier`と`Sales Qualifier Admins` ユーザーグループの両方のメンバーシップが必要です。

## CRM MCPと組み込みプラグイン

Sales QualifierとCRMの連携には、次のような利点があります。

* **CRM MCP クエリ** - Account Qualification Agentはライブ CRM データをクエリし、回答とインサイトがレコードの現在の状態を反映するようにします。
* **埋め込みプラグイン** - CRM プラグインは、CRM内の[!DNL Marketo Sales Insights] （MSI）インサイトとエージェント型データを表示します。 Sales Qualifierに見込み客を追加するには、このプラグインを使用します。
* **アクティビティの同期** – 管理者が&#x200B;**[!UICONTROL アクティビティの同期]**&#x200B;を有効にすると、アウトリーチアクティビティがCRMとMarketoに同期されます。

## CRM アクセス範囲

Sales Qualifierは、CRMからユーザー、取引先責任者、オーナーのマッピング、リード、アカウント、商談、アクティビティを読み取ります。 ログに記録されたアウトリーチアクティビティとオプトアウトステータスのみがCRMに書き込まれ、アウトリーチアクティビティがMarketoに同期されます。 CRM管理者は、SalesforceまたはDynamicsでAPI アクセスを準備します。 次に、Sales Qualifierの管理者が、CRMを接続し、インバウンドフィールドをマッピングして、アクティビティを同期するかどうかを選択します。

>[!NOTE]
>
>[基本を学ぶ](getting-started.md#connect-your-crm)の資格情報の手順では、CRM オブジェクトへの読み取りアクセスについて説明しています。 アクティビティの同期またはオプトアウトの書き戻しを有効にする場合は、CRM管理者と協力して、CRM設定で必要な対応する書き込みアクセス権を付与します。

## CRM フィールドのマッピング（インバウンドマッピング）

CRMが接続されたら、接続の&#x200B;**[!UICONTROL 管理]**&#x200B;を選択し、**[!UICONTROL インバウンドマッピング]**&#x200B;を開きます。 インバウンドマッピングでは、Sales Qualifierがアプリケーションに取り込むCRM フィールドを制御します。

1. 「**[!UICONTROL セクションを追加]**」を選択します。
1. セクション名と説明を入力します。
1. エンティティタイプを選択します。 **[!UICONTROL 見込み客]**&#x200B;がデフォルトで選択されています。 **[!UICONTROL 連絡先]**、**[!UICONTROL アカウント]**、**[!UICONTROL 商談]**&#x200B;も利用できます。
1. 読み込むCRM フィールドを選択します。

   各フィールド行には、**[!UICONTROL 表示名]**、**[!UICONTROL フィールド名]**、**[!UICONTROL データタイプ]**&#x200B;が表示されます。

1. **[!UICONTROL 見込み客]** リストでフィルターとして使用する見込み客、取引先責任者、または商談の各フィールドについて、**[!UICONTROL フィルター可能]**&#x200B;を有効にします。
1. セクションをプレビューし、**[!UICONTROL 追加]**&#x200B;を選択します。

マッピングされたフィールドは、Sales Qualifierの対応する領域に表示されます。

* 見込み客フィールドが&#x200B;**[!UICONTROL 人物]** タブに表示されます。
* アカウントフィールドは、**[!UICONTROL アカウント]** タブに表示されます。
* 商談フィールドは、**[!UICONTROL アカウント商談]** セクションに表示されます。 フィルター可能な商談フィールドは、**[!UICONTROL My Opportunity Contacts]**&#x200B;に独自の列として表示され、**[!UICONTROL Stage （Opportunity）]**&#x200B;などのラベルが表示されて、連絡先フィールドと区別されます。

## アクティビティ同期の設定（アウトバウンドマッピング）

1. **[!UICONTROL CRM接続]**&#x200B;から、接続されたCRMの&#x200B;**[!UICONTROL 管理]**&#x200B;を選択します。
1. **[!UICONTROL アウトバウンドマッピング]**&#x200B;を開きます。
1. **[!UICONTROL アクティビティ同期]**&#x200B;をオンにして、Sales Qualifier アウトリーチアクティビティをCRMとMarketoに同期します。

アクティビティの同期がオフの場合、Sales Qualifierは引き続きインバウンド CRM データを使用しますが、アウトリーチアクティビティをCRMまたはMarketoに同期しません。

## CRM同期ルールの設定

Sales Qualifierでは、見込み客がアウトバウンドワークフローを通過する際に、リードステータスがSalesforceおよびMicrosoft Dynamicsに自動的に更新されるため、担当者はCRMを手作業で更新する必要がなくなります。

### CRM同期ルールの機能

更新は、リードだけでなく、**[!UICONTROL リード]**、**[!UICONTROL コンタクト]**、**[!UICONTROL アカウント]**、または&#x200B;**[!UICONTROL 商談]** レコードをターゲットにできます。

次のアウトバウンドワークフローのモーメントに対して更新が実行されます。

* ワークフローに追加された、返信された、またはミーティングが予約された
* 担当者またはワークフローによって削除されました。返信なし
* オプトアウトまたは電子メールのバウンス

フィールド値は動的なトークンでパーソナライズできるため、CRMの更新では、静的な値ではなく見込み客の実際のジャーニーを反映できます。 トークンは、代表者の名前、アウトバウンドワークフロー名、ミーティングの日時などの詳細を確認できます。

CRMと互換性のある値のみが書き込まれ、1つの失敗したフィールドが他のフィールドをブロックせず、一時的な問題が自動的に再試行されます。 すべての更新を追跡して、同期した項目と注意が必要な項目を確認できます。

### CRM同期ルールの設定

CRM同期ルールを設定するには、次の手順に従います。

1. 左側のナビゲーションで、**[!UICONTROL 管理]**&#x200B;を展開し、**[!UICONTROL 管理者設定]** > **[!UICONTROL CRM接続]**&#x200B;を選択します。
1. 接続されたCRMの&#x200B;**[!UICONTROL 管理]**&#x200B;を選択し、**[!UICONTROL 同期ルール]**&#x200B;を選択します。
1. ターゲット CRM エンティティとフィールドを選択し、上記のワークフローモーメントにマッピングして、切り替えをオンにします。

CRM同期ルールを設定すれば、セールス部門は、リード、取引先責任者、アカウント、商談のあらゆる段階において、正確かつパーソナライズされた最新のステータスを確認できるようになります。これにより、データ収集の遅延が低減され、手作業による作業が削減されます。

## ナレッジセンタープレイブックの作成 {#knowledge-center}

**[!UICONTROL ナレッジセンター]**&#x200B;では、Account Qualification Agent （AQA）が販売資料にアクセスできます。 Sales Qualifierは、これらの学習リソースを利用して、調査、選定インサイト、自社の販売方法を反映したアウトリーチを生成します。 プレイブックを作成および管理できるのは管理者のみです。

![&#x200B; ナレッジセンター](assets/knowledge-center.png){width="800" zoomable="yes"}

1. 左側のナビゲーションで、**[!UICONTROL 管理]**&#x200B;を展開し、**[!UICONTROL 管理者設定]**&#x200B;を選択し、**[!UICONTROL ナレッジセンター]**&#x200B;を選択します
1. u
1. Sales Qualifierが会社を調査し、メールを作成するために使用する&#x200B;**[!UICONTROL 会社名]**&#x200B;および&#x200B;**[!UICONTROL 会社URL]**&#x200B;を設定します。
1. セールスプレイ、ICP （理想的な顧客像）、ポジショニングガイドなど、さまざまな営業資料を、PDF、PPTX、DOCX形式でアップロードできます。
1. 「**[!UICONTROL プレイブックを作成]**」を選択します。

アップロードされた各ドキュメントには、**[!UICONTROL Ready]**&#x200B;などの処理ステータスと、最終更新日が表示されます。

>[!NOTE]
>
>プレイブックの処理には最大で24時間かかる場合があります。

プレイブックの準備ができたら、担当者は次の2つの場所で使用できます。

* **送信メールプロンプト** - タッチポイントプロンプトで、ドキュメントに名前を付け、使用するコンテキストを記述します。 例えば、`Use the ABC positioning guide from the Knowledge Center and focus on the security value proposition`と入力します。 [&#x200B; タッチポイントの生成とレビュー](outbound-workflows.md#step-3-generate-and-review-touchpoints)を参照してください。
* **AI チャット**：質問のナレッジセンターを参照してください。 例えば、`From the Knowledge Center, help me position our security solution for ABC Corp before tomorrow's call`と入力します。 [AI チャット &#x200B;](ai-assistant.md)を参照してください。

どちらの場合も、生成されたコンテンツは、一般的な調査ではなく、プレイブックのメッセージを反映します。

## グローバルメールオプトアウトの設定

1. 左側のナビゲーションで、**[!UICONTROL 管理]**&#x200B;を展開し、**[!UICONTROL 管理者設定]**&#x200B;を選択します。
1. 「**[!UICONTROL コンプライアンス]**」の下の「**[!UICONTROL メール設定]**」を選択します。
1. **[!UICONTROL すべての電子メールにオプトアウトリンクを含める]**&#x200B;をオンにして、配信停止フッターをアウトバウンドメールに追加します。
1. **[!UICONTROL オプトアウトメッセージテンプレート]**&#x200B;に、フッターテキストを入力します。 登録解除リンクが表示される`{opt_out_link}` トークンを含めます。

設定は自動的に保存されます。

見込客がリンクを選択すると、Sales Qualifierはその見込客への電子メールの送信を停止し、オプトアウトステータスを接続されたCRMに同期させます。

## リファレンス：サンプル API パラメーター

CRM チームはこれらの例を使用して、読み取りアクセスが期待されるリードフィールドを返すことを確認できます。

### Dynamics ODataの例

```text
$select=fullname,_ownerid_value,leadid,emailaddress1,jobtitle,statuscode,createdon,modifiedon,statecode
$filter=_ownerid_value eq '<crmUserId>' [AND additional filters]
$expand=Lead_ActivityPointers(...),parentaccountid(...)
$orderby=modifiedon desc
```

### Salesforce SOQLの例

```sql
SELECT Id, Salutation, FirstName, LastName, Name, Title, Company, Email,
  LeadSource, Status, OwnerId, LastModifiedDate, LastActivityDate, CreatedDate,
  (SELECT Id, Subject, ActivityDate, Status FROM Tasks ORDER BY ActivityDate DESC LIMIT 1),
  (SELECT Id, Subject, ActivityDateTime FROM Events ORDER BY ActivityDateTime DESC LIMIT 1)
FROM Lead
WHERE OwnerId = '<crmUserId>' AND IsDeleted = false
ORDER BY LastModifiedDate DESC
```

>[!MORELIKETHIS]
>
>* [基本を学ぶ](getting-started.md)
>* [見込み客](prospects.md)
