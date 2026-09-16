---
title: マーケティングハイライトの設定
description: MarketoとAdobe Marketoの修飾子を連携して、担当者がマーケティングハイライトでライブのMarketo アクティビティによって見込み客を表示およびフィルタリングできるようにする方法について説明します。
feature: Agentic AI, Sales Insights, Account Journeys
role: Admin
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
feature_v2:
  - id: fc7979f3-56c3-43ca-9784-f1ea3dc69c4b
    internal-label: Integrations
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
    internal-label: Administration
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
source-git-commit: d967b633fcb63c64169d3e3fbf305fd2ff82236d
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 3%
---

# マーケティングハイライトの設定

マーケティングハイライトには、電子メールの開封数やクリック数、web訪問、フォーム入力など、各見込み客のライブ [!DNL Marketo] アクティビティが表示されます。 この記事では、[!DNL Marketo] インスタンスを接続してアクティビティが流れるようにする方法について説明します。

>[!IMPORTANT]
>
>この設定を完了するには、[!DNL Marketo]の&#x200B;**[!UICONTROL Admin]**&#x200B;とAdobe Developer Consoleにアクセスする必要があります。 Adobeの担当者と[!DNL Marketo]管理者と協力して、以下の4つの部分を完成させます。

設定には4つの部分があります。

* パート A: Adobe Developer ConsoleでAPI資格情報を作成します。
* パート B:Adobe Marketo修飾子エンドポイントと識別子を収集します。
* パート C: [!DNL Marketo Engage]でWebhookを設定します。
* パート D: Webhookをトリガースマートキャンペーンに追加します。

設定が完了すると、ユーザーは&#x200B;**[!UICONTROL 見込み客]** > **[!UICONTROL マーケティングハイライト]**&#x200B;でこのアクティビティを表示およびフィルタリングします。

## パート A:API資格情報の作成 {#part-a-create-api-credentials}

これらの資格情報により、[!DNL Marketo]はMarketo Qualifierに対して安全に認証できます。

資格情報を作成するには：

1. [Adobe Developer Console](https://developer.adobe.com/console/) に移動し 、Adobe ID を使用してログインします。
1. 「**[!UICONTROL 新しいプロジェクトを作成]**」を選択するか、既存のプロジェクトを開きます。
1. **[!UICONTROL プロジェクトを編集]**&#x200B;を選択し、プロジェクトの名前を`Marketo Qualifier Marketing Highlights`などの識別可能な名前に変更して、**[!UICONTROL 保存]**&#x200B;を選択します。
1. **[!UICONTROL Add API]**&#x200B;を選択し、**[!UICONTROL Experience Platform API]**&#x200B;を選択してから、**[!UICONTROL Next]**&#x200B;を選択します。
1. 認証タイプとして&#x200B;**[!UICONTROL OAuth サーバー間]**&#x200B;を選択し、**[!UICONTROL 次]**&#x200B;を選択します。

   **[!UICONTROL OAuth Server-to-Server]**&#x200B;を使用すると、[!DNL Marketo]は、ユーザーにログインを求めずに、そのサーバーからMarketo Qualifier APIを直接呼び出すことができます。

1. `Marketo Qualifier Marketing Highlights Creds`など、45文字以下の資格情報名を入力してください。
1. 関連付ける製品プロファイルを選択し、**[!UICONTROL 設定したAPIを保存]**&#x200B;を選択します。
1. **[!UICONTROL 接続済み資格情報]**&#x200B;で、**[!UICONTROL OAuth サーバー間]**&#x200B;資格情報を開きます。 「**[!UICONTROL クライアントシークレットを取得]**」を選択し、**[!UICONTROL クライアント ID]**&#x200B;と&#x200B;**[!UICONTROL クライアントシークレット]**&#x200B;をコピーします。 これらの値は、[ パート C](#part-c-configure-the-marketo-webhook)で使用します。

>[!WARNING]
>
>クライアントの秘密鍵を保持します。 パスワードのように扱い、電子メールで送信しないでください。 組織で承認されたセキュアチャネルを使用して、Webhookを設定するユーザーと共有します。

## パート B：エンドポイントと識別子の収集 {#part-b-gather-your-endpoint-and-identifiers}

[ パート C](#part-c-configure-the-marketo-webhook)には3つの値が必要です：

* **エンドポイント URL** – お住まいの地域のMarketo修飾子のWebhook アドレス。
* **imsOrg ID**—Adobe Identity Management システム （IMS）の組織のID （フォーム `{ORG_ID}@AdobeOrg`）。
* **サンドボックス名** - UIに表示される表示名ではなく、Marketo修飾子URL （`sname`値）に表示されるAEP サンドボックスの名前。 小文字のURL値（例：`prod`）を使用します（`Prod`ではなく）。

| 地域 | Webhook エンドポイント URL |
| --- | --- |
| 北米 | `https://5r6xakp9k3.execute-api.us-east-1.amazonaws.com/prod/external/marketo/signals` |
| EMEA | `https://pc72i8q1k3.execute-api.eu-west-1.amazonaws.com/prod/external/marketo/signals` |
| APAC / オーストラリア | `https://5cxxxyqlai.execute-api.ap-southeast-2.amazonaws.com/prod/external/marketo/signals` |

{style="table-layout:auto"}

お住まいの地域、imsOrg ID、またはサンドボックス名がわからない場合は、Adobeの担当者がご確認いただけます。

## パート C:Marketo Webhookの設定 {#part-c-configure-the-marketo-webhook}

Webhookを作成するには：

1. [!DNL Marketo]で、**[!UICONTROL Admin]** > **[!UICONTROL Webhook]**&#x200B;を選択します。
1. **[!UICONTROL 新しいWebhook]**&#x200B;を選択します。
1. **[!UICONTROL URL]**&#x200B;を[ パート B](#part-b-gather-your-endpoint-and-identifiers)から地域のエンドポイント URLに設定します。
1. **[!UICONTROL 要求タイプ]**&#x200B;を`POST`に設定します。
1. **[!UICONTROL 要求トークンエンコーディング]**&#x200B;を`JSON`に設定します。 この設定は必須です。
1. 以下のペイロードテンプレートを&#x200B;**[!UICONTROL テンプレート]**&#x200B;に貼り付けます。 [!DNL Marketo]の&#x200B;**[!UICONTROL トークンを挿入]**&#x200B;を使用して、インスタンス内のフィールド名と一致させます。

   >[!NOTE]
   >
   >JSON エンコーディングでは、文字列トークンを引用符で囲まないでください。 [!DNL Marketo]が自動的に追加します。

   ```json
   {
     "leadId": {{lead.Id:default=0}},
     "email": {{lead.Email Address:default=}},
     "fullName": {{lead.Full Name:default=}},
     "company": {{company.Company Name:default=}},
     "title": {{lead.Job Title:default=}},
     "department": {{lead.Department:default=}},
     "country": {{lead.Country:default=}},
     "score": {{lead.Lead Score:default=0}},
     "rating": {{lead.Lead Rating:default=}},
     "leadStatus": {{lead.Lead Status:default=}},
     "leadSource": {{lead.Lead Source:default=}},
     "isCustomer": {{lead.Is Customer:default=false}},
     "industry": {{company.Industry:default=}},
     "annualRevenue": {{company.Annual Revenue:default=0}},
     "numEmployees": {{company.Num Employees:default=0}},
     "campaignId": {{campaign.id:default=0}},
     "campaignName": {{campaign.name:default=}},
     "programName": {{program.name:default=}},
     "occurredAt": {{system.dateTime:default=}},
     "munchkinId": {{system.munchkinId:default=}},
     "triggerName": {{trigger.Trigger Name:default=}},
     "crmId": {{lead.SFDC ID:default=}},
     "crmType": {{lead.SFDC Type:default=}},
     "crmOwnerEmail": {{lead.Lead Owner Email Address:default=}},
     "crmOwnerFirstName": {{lead.Lead Owner First Name:default=}},
     "crmOwnerLastName": {{lead.Lead Owner Last Name:default=}},
     "attributes": {
       "asset": {{trigger.Name:default=}},
       "link": {{trigger.Link:default=}},
       "subject": {{trigger.Subject:default=}},
       "webPage": {{trigger.Web Page:default=}},
       "category": {{trigger.Category:default=}},
       "details": {{trigger.Details:default=}},
       "sentBy": {{trigger.Sent By:default=}},
       "receivedBy": {{trigger.Received By:default=}},
       "referrer": {{trigger.Referrer:default=}},
       "searchEngine": {{trigger.Search Engine:default=}},
       "searchQuery": {{trigger.Search Query:default=}},
       "imDescription": {{lead.Last Interesting Moment Desc:default=}},
       "imType": {{lead.Last Interesting Moment Type:default=}},
       "imDate": {{lead.Last Interesting Moment Date:default=}},
       "imSource": {{lead.Last Interesting Moment Source:default=}},
       "chatAgentName": {{trigger.Agent Name:default=}},
       "chatAgentEmail": {{trigger.Agent Email:default=}},
       "chatConversationStatus": {{trigger.Conversation Status:default=}},
       "chatConversationSummary": {{trigger.Conversation Summary:default=}},
       "chatGoalName": {{trigger.Goal name:default=}},
       "chatMeetingStatus": {{trigger.meeting status:default=}},
       "chatScheduledFor": {{trigger.Scheduled For:default=}},
       "chatDocumentName": {{trigger.Document Name:default=}},
       "chatDocumentUrl": {{trigger.Document URL:default=}},
       "chatPageUrl": {{trigger.Page URL:default=}}
     }
   }
   ```

1. **[!UICONTROL Webhook Actions]** > **[!UICONTROL カスタムヘッダーを設定]**&#x200B;を選択し、[ パート A](#part-a-create-api-credentials)および[ パート B](#part-b-gather-your-endpoint-and-identifiers)の値を使用して、次のヘッダーを追加します。

   | ヘッダー | 値 |
   | --- | --- |
   | `Content-Type` | `application/json` |
   | `x-client-id` | クライアント ID |
   | `x-client-secret` | クライアント秘密鍵 |
   | `x-gw-ims-org-id` | あなたのimsOrg ID |
   | `x-sandbox-name` | サンドボックス名 |

   {style="table-layout:auto"}

1. 「**[!UICONTROL 保存]**」を選択します。

## パート D:Webhookをトリガースマートキャンペーンに追加する {#part-d-add-the-webhook-to-a-trigger-smart-campaign}

**[!UICONTROL Call Webhook]** フローステップを、既存または新規のトリガースマートキャンペーンに追加します。 そのキャンペーンのスマートリストトリガーによって、どのアクティビティがMarketo修飾子に送信されるかが決まります。

Webhookを追加するには：

1. 既存のトリガースマートキャンペーンを開くか、新しいスマートキャンペーンを作成します（**[!UICONTROL マーケティングアクティビティ]** > **[!UICONTROL 新規]** > **[!UICONTROL スマートキャンペーン]**）。
1. 「**[!UICONTROL スマートリスト]**」タブで、送信するアクティビティのトリガーまたはトリガーを追加します。例えば、**[!UICONTROL 電子メールのリンクをクリック]**、**[!UICONTROL フォームに入力]**、**[!UICONTROL Web ページへの訪問]**&#x200B;などです。
1. 「**[!UICONTROL フロー]**」タブで、**[!UICONTROL Webhookを呼び出す]** ステップを追加し、[ パート C](#part-c-configure-the-marketo-webhook)で作成したWebhookを選択します。
1. スマートキャンペーンをアクティブ化します。

スマートキャンペーンのアクティビティがMarketo Qualifierに取り込まれます。 担当者は、**[!UICONTROL 見込み客]** > **[!UICONTROL マーケティングハイライト]**&#x200B;でこのアクティビティを表示およびフィルタリングします。

>[!MORELIKETHIS]
>
>* [統合の管理](integrations.md)
>* [見込み客](prospects.md)
>* [基本を学ぶ](getting-started.md)
