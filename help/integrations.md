---
title: 統合の管理
description: Outlookの接続、CRM接続の管理、インバウンドフィールドのマッピング、アクティビティの同期、Sales Qualifierでのグローバルメールオプトアウトの設定方法について説明します。
feature: Agentic AI, Sales Insights, Account Journeys
role: User, Admin
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fc7979f3-56c3-43ca-9784-f1ea3dc69c4b
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 351b27d35049b0bb576e9b84f7fd6fada791bb52
workflow-type: tm+mt
source-wordcount: 1379
ht-degree: 1%

---


# 統合

Outlookを接続して、電子メールを送信したり、見込み客の返信を認識したり、ミーティングをスケジュールしたりできます。 リード、取引先責任者、アカウント、商談、アクティビティ、およびオーナーをAccount Qualification Agent（AQA）およびアウトバウンドワークフローで利用できるようにするには、Sales QualifierをSalesforceまたはMicrosoft Dynamics 365に接続することもできます。 Sales Qualifierは、CRM データを読み取り、アウトリーチアクティビティとオプトアウトステータスをCRMに書き込み、アウトリーチアクティビティをMarketoに同期できます。 CRM レコードは変更されません。

この記事では、Outlookの接続、CRM接続の管理、フィールドのマッピング、アクティビティの同期、メール オプトアウトの設定方法について説明します。 CRMを初めて接続する場合は、[開始](getting-started.md#connect-your-crm)を参照してください。

>[!IMPORTANT]
>
>Outlookの接続は担当者ごとに行われます。 この記事で後述するCRMとコンプライアンスの設定は、組織全体に適用されます。 これらの組織全体の設定にアクセスするには、`Sales Qualifier`および`Sales Qualifier Admins` ユーザーグループに属している必要があります。 標準ユーザーは、設定されたCRM データとフィルターを使用できますが、設定を変更することはできません。 [&#x200B; ユーザーの役割と権限](user-roles-permissions.md)を参照してください。

## Outlookの接続

各担当者は、自分のOutlook アカウントを接続します。

1. 「**[!UICONTROL Connect Outlook]**」を選択します。
1. Microsoft アカウントでログインします。
1. 要求されたアクセスを確認して承認します。

この連携により、Sales Qualifierはメールボックスから送信したり、見込み客がいつ返信するかを認識したり、カレンダーでミーティングをスケジュールしたりできます。

接続すると、Sales Qualifierで次の操作が可能になるアクセス権を承認します。

* 見込み客からの返信を識別：
* 電子メールの作成と送信。
* カレンダーでミーティングを予約できます。
* スケジュール設定のために、メールボックスのタイムゾーンと作業時間を確認します。
* これらの機能が引き続き機能するように、自動的にログインしたままにしておけば、再度ログインする必要はありません。

### Outlookの承認（必要な場合）

デフォルトでは、管理者の操作は必要ありません。 各担当者は、Outlookに接続する際に、自分でアクセスを承認します。

Microsoft 365またはMicrosoft Entraのサードパーティアプリに対するユーザーの同意をオフにしている場合、Microsoft 365またはEntra管理者は、組織全体に対してSales Qualifierを1回承認する必要があります。 管理者は、担当者がOutlook アカウントを接続する前に、この承認を完了します。 組織全体での承認が完了すると、各担当者はアカウントを連携させることができます。

### Sales Qualifierでのメールボックスデータの取り扱い

Sales Qualifierは、送信した電子メールに対する返信のみを読み取り、残りの受信トレイには返信しません。 アクティブなエンゲージメント以外の添付ファイルや電子メールは保存しません。 保存されたログイン資格情報は暗号化されています。

## CRM設定を開く

左側のナビゲーションで、**[!UICONTROL 管理]**&#x200B;を展開し、**[!UICONTROL 管理者設定]**&#x200B;を選択します。 設定は、次の2つのグループに編成されます。

| グループ | 項目 |
| --- | --- |
| **[!UICONTROL 統合]** | **[!UICONTROL CRM接続]**、**[!UICONTROL ナレッジセンター]** |
| **[!UICONTROL コンプライアンス]** | **[!UICONTROL メール設定]** |

ナレッジセンターについては、[&#x200B; ナレッジセンター](knowledge-center.md)を参照してください。

## CRM接続の管理

**[!UICONTROL CRM接続]**&#x200B;を選択します。 このページには、**[!UICONTROL Salesforce]**&#x200B;および&#x200B;**[!UICONTROL Microsoft]** （Microsoft Dynamics 365）のカードが含まれています。 各カードには、次のいずれかのステータスが表示されます。

| ステータス | 意味 |
| --- | --- |
| **[!UICONTROL 接続済み]** | 接続はアクティブで認証済みです。 |
| **[!UICONTROL アクティブではありません]** | このCRMには接続が設定されていません。 |
| **[!UICONTROL 必要な権限]** | 接続は認証されましたが、必要なスコープがありません。 カードには、欠落しているスコープが一覧表示されます。 |

>[!NOTE]
>
>一度にアクティブにできるCRMは1つだけです。 一方のCRMが接続されている場合、もう一方のカードは無効になります。 別のCRMを接続する前に、アクティブなCRMの接続を解除します。

未設定のカードには、**[!UICONTROL Connect]**&#x200B;が表示されます。 設定されたカードには、**[!UICONTROL Manage]**&#x200B;と&#x200B;**[!UICONTROL More]** メニューが表示され、**[!UICONTROL 設定の編集]**&#x200B;と&#x200B;**[!UICONTROL 接続の解除]**&#x200B;が表示されます。

### 接続の接続または編集

1. CRM カードで、**[!UICONTROL Connect]**&#x200B;を選択するか、**[!UICONTROL More]** > **[!UICONTROL 設定を編集]**&#x200B;を選択して、既存の接続を更新します。
1. CRM管理者の資格情報を入力します。

   >[!BEGINTABS]

   >[!TAB Salesforce]

   **[!UICONTROL クライアント ID （コンシューマーキー）]**、**[!UICONTROL インスタンス URL]**、**[!UICONTROL クライアントシークレット]**&#x200B;を入力します。 規範的なインスタンス URL フォーム `https://{{mydomain}}.my.salesforce.com`を使用します。

   ![Salesforce接続](assets/crm-conn-salesforce.png){width="800" zoomable="yes"}

   >[!TAB Microsoft Dynamics]

   **[!UICONTROL クライアント ID （コンシューマーキー）]**、**[!UICONTROL テナント ID]**、**[!UICONTROL Microsoft Dynamics インスタンス URL]**、および&#x200B;**[!UICONTROL クライアントシークレット]**&#x200B;を入力します。 規範的なインスタンス URL フォーム `https://{{mydomain}}.crm.dynamics.com`を使用します。

   >[!ENDTABS]

1. **[!UICONTROL Connect]** （または編集時に&#x200B;**[!UICONTROL Save]**）を選択します。

Sales Qualifierが資格情報を拒否した場合は、無効または期限切れの資格情報、権限の欠落、認識できないDynamics テナントなど、原因を特定します。 値を修正して、もう一度試してください。

>[!IMPORTANT]
>
>電子メールでクライアントの秘密鍵を送信しないでください。 組織で承認済みのセキュアチャネルを使用して、Sales Qualifierに入力したユーザーと資格情報を共有します。

### 接続の切断

1. 接続されたCRM カードで、**[!UICONTROL 詳細]** > **[!UICONTROL 切断]**&#x200B;を選択します。
1. 警告を確認し、**[!UICONTROL 切断]**&#x200B;を選択して確認します。

>[!WARNING]
>
>CRMとの接続を解除すると、組織内のすべての見込客に対してアウトバウンドワークフローが一時停止し、再接続するまでCRMから新しい見込客が同期されません。

## CRM フィールドのマッピング（インバウンドマッピング） {#map-crm-fields-inbound-mapping}

インバウンドマッピングでは、Sales Qualifierが読み込むCRM フィールドと、それらのフィールドが表示される場所を制御します。 フィールドはセクションにグループ化され、各セクションはエンティティタイプに属します。

1. 接続されたCRM カードで、**[!UICONTROL 管理]**&#x200B;を選択します。
1. 「**[!UICONTROL インバウンドマッピング]**」タブで、「**[!UICONTROL セクションを追加]**」を選択します。
1. **セクションを選択** ステップで、エンティティタイプを選択し、**[!UICONTROL 次]**&#x200B;を選択します。

   | エンティティ | フィールドが表示される場所 |
   | --- | --- |
   | **[!UICONTROL 見込み客]** | 見込み客の&#x200B;**[!UICONTROL 人物]** タブ。 |
   | **[!UICONTROL 取引先責任者]** | 連絡先レコードです。 |
   | **[!UICONTROL アカウント]** | 「**[!UICONTROL アカウント]**」タブ。 [&#x200B; アカウント &#x200B;](accounts.md)を参照してください。 |
   | **[!UICONTROL 商談]** | アカウントの商談の詳細。 |

1. **[!UICONTROL セクション名]**&#x200B;と、オプションの&#x200B;**[!UICONTROL 説明]**&#x200B;を入力します。 次に、**[!UICONTROL 次へ]**&#x200B;を選択します。
1. **[!UICONTROL フィールドを追加]** ステップで、読み込むCRM フィールドを検索して選択します。 次に、**[!UICONTROL 次へ]**&#x200B;を選択します。 各フィールドには、**[!UICONTROL 表示名]**、**[!UICONTROL フィールド名]**、**[!UICONTROL データタイプ]**&#x200B;が表示されます。
1. **[!UICONTROL 見込み客]**、**[!UICONTROL 連絡先]**、および&#x200B;**[!UICONTROL 商談]** セクションの場合、[見込み客](prospects.md) リストで担当者が必要とする各フィールドの&#x200B;**[!UICONTROL フィルター可能]**&#x200B;をオンにします。

   フィールドのデータタイプがフィルタリングをサポートしていない場合、または別のセクションで既に使用されている場合、フィールドをフィルタリングすることはできません。

   **[!UICONTROL 自分の商談コンタクト]**&#x200B;では、フィルター可能な商談フィールドが、**[!UICONTROL ステージ（商談）]**&#x200B;などのラベルを持つ別々の列として表示されます。 接尾辞は、関連する連絡先のフィールドから商談属性を区別します。

1. **[!UICONTROL プレビュー]**&#x200B;の手順で、選択を確認し、**[!UICONTROL 追加]**&#x200B;を選択します。

後でセクションを変更するには、セクションカードの&#x200B;**[!UICONTROL 編集]**&#x200B;を選択します。 セクションを削除するには、セクション カードで&#x200B;**[!UICONTROL 削除]**&#x200B;を選択します。 個々のフィールドを削除するには、フィールド行で削除アクションを選択します。 各削除を確認します。

## アクティビティ同期の設定（アウトバウンドマッピング） {#configure-activity-sync-outbound-mapping}

Activity syncは、CRMとMarketoにSales Qualifier アウトリーチアクティビティを書き込みます。 電子メールの送信、開封、クリック、返信アクティビティには、アウトバウンドワークフロー名が含まれます。 たとえば、代表者はCRMのアクティビティを利用し、マーケティング部門はリードスコアリングやエンゲージメントのタイムラインにAdobe Marketoのアクティビティを利用できます。

1. 接続されたCRM カードで、**[!UICONTROL 管理]**&#x200B;を選択します。
1. 「**[!UICONTROL アウトバウンドマッピング]**」タブを開きます。
1. **[!UICONTROL アクティビティの同期]**&#x200B;を有効にします。 設定はすぐに保存されます。

アクティビティの同期がオフの場合、Sales Qualifierは引き続きインバウンド CRM データを使用しますが、アウトリーチアクティビティをCRMまたはMarketoに同期しません。

>[!NOTE]
>
>アクティビティの同期には、CRMでの書き込みアクセス権が必要です。 必要な権限がない場合、スイッチは無効になり、Sales Qualifierから管理者に連絡するように求められます。 アクティビティへの書き込みアクセス権を付与するには、CRM管理者と協力します。

## マーケティングハイライトの設定 {#turn-on-marketo-engagement-filtering}

マーケティングハイライトでは、担当者が電子メールの開封数やクリック数など、[!DNL Marketo]のライブのエンゲージメントによって見込み客を見つけ、優先順位を付けることができます。 [&#x200B; マーケティングハイライトによるフィルター](prospects.md#filter-by-marketing-highlights)を参照してください。

管理者は、関連する組織とサンドボックスの[!DNL Marketo]をSales Qualifierに接続する1回限りの設定を完了します。 この設定では、Adobe Developer ConsoleでAPI資格情報を作成し、[!DNL Marketo]でWebhookを設定し、そのWebhookをトリガーのスマートキャンペーンに追加します。 詳細な手順については、[&#x200B; マーケティングハイライトの設定](marketing-highlights-setup.md)を参照してください。

マーケティングハイライトは、北米、EMEA、オーストラリアのすべての生産地域で利用できます。

## グローバルメールオプトアウトの設定 {#configure-global-email-opt-out}

オプトアウト設定では、すべての送信メールに登録解除フッターが追加されます。 標準ユーザーは、個々のメールに対してオフにすることはできません。

1. 左側のナビゲーションで、**[!UICONTROL 管理]**&#x200B;を展開し、**[!UICONTROL 管理者設定]**&#x200B;を選択します。
1. 「**[!UICONTROL コンプライアンス]**」の下の「**[!UICONTROL メール設定]**」を選択します。
1. **[!UICONTROL すべての電子メールにオプトアウトリンクを含める]**&#x200B;をオンにします。
1. **[!UICONTROL オプトアウトメッセージテンプレート]**&#x200B;に、フッターテキストを入力します。 クリック可能な登録解除リンクが表示される`{opt_out_link}` トークンを含めます。

   例：`If you'd prefer not to receive these emails, you can {opt_out_link}.`

設定とテンプレートは自動的に保存されます。

見込客がリンクを選択すると、Sales Qualifierはその見込客への電子メールの送信を停止し、オプトアウトステータスを接続されたCRMに同期します。

## CRM アクセス範囲

Sales Qualifierは、必要なCRM エンティティを読み取り、定義されたデータセットのみを書き戻します。

* **読み取り** - ユーザー、取引先責任者、所有者のマッピング、リード、アカウント、商談、およびアクティビティ。
* **書き込み** - アウトリーチアクティビティのログ記録（[&#x200B; アクティビティ同期](#configure-activity-sync-outbound-mapping)がオンの場合）とオプトアウト状態。

CRM管理者は、SalesforceまたはDynamicsでAPI アクセスを準備します。 次に、Sales Qualifierの管理者が、CRMを接続し、インバウンドフィールドをマッピングして、アクティビティを同期するかどうかを選択します。 初期接続には読み取り専用アクセスが必要です。 アクティビティの同期とオプトアウトの書き戻しには、対応する書き込みアクセスが必要です。

>[!MORELIKETHIS]
>
>* [基本を学ぶ](getting-started.md)
>* [&#x200B; ユーザーの役割と権限](user-roles-permissions.md)
>* [アカウント](accounts.md)
