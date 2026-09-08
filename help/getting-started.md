---
title: Sales Qualifierの導入方法
description: アプリケーションの使用を開始する前に、ユーザーグループとCRM接続を含むSales Qualifierの1回限りの管理者設定を完了する方法について説明します。
feature: Agentic AI, Sales Insights, Account Journeys
role: Admin
TQID: 'https://experienceleague.adobe.com/-nfmFwZyZFUZhm-uQUjSyTvrORuqJgKSKnENWYtvubs'
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fc7979f3-56c3-43ca-9784-f1ea3dc69c4b
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 527d6a99f1ca51371ab0bc44ee61482bac56fc4f
workflow-type: tm+mt
source-wordcount: 1017
ht-degree: 0%

---


# Sales Qualifierの導入方法

AdobeがSales Qualifierを組織にプロビジョニングした後、必要なユーザーグループを作成し、SalesforceまたはMicrosoft Dynamics 365に接続する必要があります。[!DNL Marketo]

![Sales Qualifier ホームページ &#x200B;](assets/homepage.png){width="800" zoomable="yes"}

## ユーザーグループの設定

Adobe Admin Consoleのユーザーグループは、Sales Qualifierへのアクセスを制御するために使用されます。 ユーザーがログインするには、両方のグループを作成する必要があります。

グループの設定について詳しくは、[Adobe Admin Console ドキュメント &#x200B;](https://helpx.adobe.com/business/enterprise/users/users-and-groups/user-groups.html)を参照してください。

>[!PREREQUISITES]
>
>グループを作成する管理者は、次の両方の要件を満たす必要があります。
>
>* Adobe アプリ スイッチャーから&#x200B;**[!UICONTROL Admin Console]**&#x200B;へのアクセス権を持つ組織管理者であること。
>* Adobe Experience Platform製品を割り当てられるか、システム管理者になってください。 そうでない場合、Adobe Experience Platformは商品リストに表示されません。

### Sales Qualifier ユーザー

アプリケーションにアクセスするには、ユーザーが`Sales Qualifier` ユーザーグループに属している必要があります。

これらの手順はAdobe Admin Consoleで行われます。

1. アプリスイッチャーから、**[!UICONTROL Admin Console]**&#x200B;を選択します。
1. **[!UICONTROL ユーザー]** > **[!UICONTROL ユーザーグループ]** > **[!UICONTROL 新しいユーザーグループ]**&#x200B;を選択します。
1. グループ名に「`Sales Qualifier`」と入力し、**[!UICONTROL 保存]**&#x200B;を選択します。
1. **[!UICONTROL 割り当てられた製品プロファイル]**&#x200B;を開き、**[!UICONTROL プロファイルの割り当て]**&#x200B;を選択します。
1. **[!UICONTROL Adobe Experience Platform]**&#x200B;を選択します。
1. **[!UICONTROL Default Production All Access]**&#x200B;製品プロファイルを選択し、**[!UICONTROL 適用]**&#x200B;を選択してから、**[!UICONTROL 保存]**&#x200B;を選択します。
1. **[!UICONTROL Users]**&#x200B;を開き、**[!UICONTROL Add users]**&#x200B;を選択して、Sales Qualifierへのアクセスを必要とするすべてのユーザーを追加します。

### Sales Qualifier管理者

CRM接続、[&#x200B; ナレッジセンター](admin-settings.md#knowledge-center)、およびグローバルメールオプトアウト設定を設定する管理者も、`Sales Qualifier Admins` ユーザーグループに属している必要があります。

1. Adobe Admin Consoleで、**[!UICONTROL Users]** > **[!UICONTROL User groups]** > **[!UICONTROL New user group]**&#x200B;を選択します。
1. グループ名に「`Sales Qualifier Admins`」と入力し、**[!UICONTROL 保存]**&#x200B;を選択します。
1. **[!UICONTROL ユーザー]**&#x200B;を開き、**[!UICONTROL ユーザーを追加]**&#x200B;を選択し、管理者を追加します。
1. 各管理者が`Sales Qualifier` グループのメンバーであることを確認してください。

両方のグループのメンバーシップにより、左側のナビゲーションの&#x200B;**[!UICONTROL 管理]**&#x200B;の下に&#x200B;**[!UICONTROL 管理設定]**&#x200B;が表示されます。 標準ユーザーは、管理者が設定したフィールド、フィルター、プレイブックを使用して作業します。 設定されたオプトアウトフッターは、アウトバウンドメールに自動的に適用されます。 標準ユーザーはこれらの設定を変更できません。

ユーザーグループ名は、前述の手順に示すように正確に一致する必要があります。

オプションの`Sales Qualifier BDR managers` グループを作成することもできます。 このグループのメンバーは、メールパフォーマンスレポートにアクセスできます。

## CRMとの接続

Sales QualifierをSalesforceまたはMicrosoft Dynamics 365に接続すると、BDRは、利用者、リード、取引先責任者、アカウント、商談、オーナーの割り当て、関連するアクティビティを包括的に把握できます。 最初の接続では、このCRM データへの読み取り専用アクセスが必要です。 Sales Qualifierを接続する前に資格情報を準備するには、CRM管理者と協力してください。 統合の詳細については、[統合](integrations.md)を参照してください。

>[!PREREQUISITES]
>
>CRM管理インターフェイスにアクセスするには、`Sales Qualifier Admins` Adobe Admin Console グループと`Sales Qualifier` グループに属している必要があります。

>[!BEGINTABS]

>[!TAB Salesforce]

Salesforce システム管理者は、外部クライアントアプリ（接続アプリとも呼ばれます）を作成し、その実行ユーザーを設定します。

>[!PREREQUISITES]
>
>Salesforce管理者に次の権限があることを確認します。
>
>* アプリケーションをカスタマイズ
>* 設定と設定の表示
>* すべてのデータを変更
>* 接続済みアプリの管理
>
>管理者は、クライアント IDとクライアント シークレットを表示するために&#x200B;_接続されたアプリを管理_&#x200B;する必要があります。

1. Salesforceで、**[!UICONTROL Setup]** > **[!UICONTROL App Manager]**&#x200B;に移動し、**[!UICONTROL 新しい接続アプリ]**&#x200B;または&#x200B;**[!UICONTROL 新しい外部クライアントアプリ]**&#x200B;を選択します。
1. アプリケーション名と管理者の連絡先メールを入力します。
1. OAuthを有効にして、コールバック URLを入力します。

   接続でリダイレクトが使用されない場合は、有効なURLを入力します。

1. 次のOAuth スコープを追加します。

   * ID URL サービスにアクセスします（`id`、`profile`、`email`、`address`、`phone`）
   * API （`api`）によるユーザーデータの管理
   * 一意のユーザーID （`openid`）へのアクセス

1. クライアント資格情報フローを有効にし、**[!UICONTROL 別名で実行]** ユーザーを選択します。
1. 実行ユーザーが&#x200B;**読み取り** アクセス権を`Leads`、`Accounts`、`Contacts`、`Tasks`、`Events`、`Opportunity`、`OpportunityContactRoles`および`OpportunityLineItems`に持っていることを確認します。 また、**アクセス アクティビティ**&#x200B;が有効になっていることも確認してください。
1. アプリケーションを保存します。
1. **[!UICONTROL App Manager]**&#x200B;からアプリケーションを開き、**[!UICONTROL 表示]** > **[!UICONTROL 消費者の詳細]**&#x200B;を選択します。
1. Sales Qualifier接続の次の値をコピーします。

   * コンシューマーキー（クライアント ID）
   * Consumer Secret （クライアントシークレット）
   * コールバック URL
   * Salesforce インスタンス URL

手順は、ここで説明するのとは少し異なります。 詳しくは、[Salesforce ドキュメント &#x200B;](https://help.salesforce.com/s/?language=en_US)を参照してください。

### Salesforce インスタンス URLの検索

1. ログインして、ブラウザーのアドレスバー（`{{mydomain}}`値）から組織&#x200B;_マイドメイン_ サブドメインをメモします。
1. Sales Qualifierの正規フォームを使用：`https://{{mydomain}}.my.salesforce.com`。

インスタンス URLとして`lightning.force.com` URLを使用しないでください。

>[!TIP]
>
>CRM接続インターフェイスでスコープが見つからない場合は、**[!UICONTROL 標準オブジェクト権限]**&#x200B;の下にある実行ユーザーのプロファイルで、リード、取引先責任者、アカウント、商談への&#x200B;**読み取り** アクセスを確認してください。 また、割り当てられたすべての権限セットで&#x200B;**[!UICONTROL オブジェクト設定]**&#x200B;を確認します。

>[!TAB Microsoft Dynamics 365]

Microsoft Dynamics 365またはAzure管理者は、アプリケーションを登録し、Dynamics環境に追加します。

1. Microsoft Entra IDで、**[!UICONTROL App registrations]**&#x200B;を選択し、アプリケーションを登録します。
1. クライアント IDとテナント IDをコピーし、クライアントシークレットを作成します。
1. **[!UICONTROL Power Platform管理センター]**&#x200B;で、**[!UICONTROL 環境]**&#x200B;を選択し、Dynamics環境を開きます。
1. **[!UICONTROL 設定]** > **[!UICONTROL ユーザー+権限]** > **[!UICONTROL アプリケーションユーザー]**&#x200B;に移動し、**[!UICONTROL 新しいアプリユーザー]**&#x200B;を選択します。
1. 登録したMicrosoft Entra アプリケーションを選択します。
1. リード、取引先責任者、アカウント、商談、アクティビティへの読み取りアクセス権を付与するセキュリティ役割を割り当てます。

   セキュリティロールが必要です。 アプリケーションがDynamics データにアクセスするには、セキュリティの役割が必要です。

1. クライアント ID、クライアントシークレット、テナント ID、およびDynamics インスタンス URLを収集します。 規範的なURL フォーム `https://{{mydomain}}.crm.dynamics.com`を使用します。

>[!ENDTABS]

### 接続を入力

1. 両方の必須Sales Qualifier グループのメンバーとしてSales Qualifierにログインし、適切なサンドボックスまたは環境が選択されていることを確認します。
1. 左側のナビゲーションで、**[!UICONTROL 管理]**&#x200B;を展開し、**[!UICONTROL 管理者設定]**&#x200B;を選択します。
1. **[!UICONTROL 統合]**&#x200B;の下の&#x200B;**[!UICONTROL CRM接続]**&#x200B;を選択します。

   SalesforceとMicrosoft Dynamicsのカードが表示されます。 非アクティブな接続には&#x200B;**[!UICONTROL Connect]**&#x200B;が表示されます。 設定された接続に&#x200B;**[!UICONTROL Connected]**&#x200B;と&#x200B;**[!UICONTROL Manage]**&#x200B;が表示されます。

   ![Salesforce資格情報](assets/crm-salesforce-config.png){width="800" zoomable="yes"}

1. 使用するCRMの&#x200B;**[!UICONTROL Connect]**&#x200B;を選択します。
1. CRM管理者の資格情報とインスタンス URLを入力します。
1. 接続が成功したら、カードに&#x200B;**[!UICONTROL Connected]**&#x200B;が表示されていることを確認します。

### CRM フィールドのインポート

CRMを接続したら、インバウンドマッピングを設定して、Sales Qualifier内に表示されるCRM フィールドを決定します。 接続されたCRM カードで、**[!UICONTROL 管理]**&#x200B;を選択して&#x200B;**[!UICONTROL インバウンドマッピング]**&#x200B;を開き、読み込むフィールドを持つ各エンティティタイプのセクションを追加します。

インポートしたフィールドをフィルターとして使用できるようにする方法など、完全な手順については、[CRM フィールドのマッピング（インバウンドマッピング） &#x200B;](integrations.md#map-crm-fields-inbound-mapping)を参照してください。

## 次の手順

>[!MORELIKETHIS]
>
>* [見込み客](prospects.md)
>* [&#x200B; アウトバウンドワークフロー](outbound-workflows.md)
