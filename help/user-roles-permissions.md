---
title: ユーザーの役割と権限
description: Sales Qualifier ユーザーグループがアプリケーションと管理アクセスをどのように制御するかをご覧ください。
feature: Agentic AI, Sales Insights, Account Journeys
role: Admin
TQID: 'https://experienceleague.adobe.com/9X9DYGMvLGcPG--G6rHcDEk91hdT9-XYc9wbiL2Qoww'
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fc7979f3-56c3-43ca-9784-f1ea3dc69c4b
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: d6a8091bd893ea80a26edfc1526646aec037223f
workflow-type: tm+mt
source-wordcount: 246
ht-degree: 4%

---


# ユーザーの役割と権限

Sales Qualifierでは、2つの必要なユーザーグループを使用して、セールスタスクを組織全体の設定から分離します。

## 必要なユーザーグループ

| グループ | 誰が属する | What it grants |
| --- | --- | --- |
| `Sales Qualifier` | 管理者を含む全ユーザー | アプリケーションへのアクセス：見込み顧客、アカウント、エンゲージメントプラン、タスク、パフォーマンス、プロファイル設定 |
| `Sales Qualifier Admins` | `Sales Qualifier` グループに加えて、管理者のみ | 組織全体のCRM接続、ナレッジセンター、およびコンプライアンス設定を管理する&#x200B;**[!UICONTROL 管理者設定]**&#x200B;へのアクセス。 |

標準ユーザーには`Sales Qualifier` グループのみが必要です。 管理者は両方のグループのメンバーシップが必要です。 これらのグループを作成するには、[開始](getting-started.md)を参照してください。

組織は、オプションの`Sales Qualifier BDR managers` グループを作成することもできます。 メンバーはメールパフォーマンスレポートにアクセスできます。

## 管理者アクセス

**[!UICONTROL 管理者設定]**&#x200B;は、両方の必須グループに属するユーザーに対してのみ&#x200B;**[!UICONTROL 管理]**&#x200B;に表示されます。 これらの設定の変更は、組織全体に適用されます。

## 管理者が制御するもの

| 設定 | 設定する場所 | エフェクト |
| --- | --- | --- |
| CRM接続とフィールドマッピング | [統合](integrations.md#map-crm-fields-inbound-mapping) | 見込み顧客またはアカウントに表示されるCRM フィールドと、フィルターとして使用できるフィールドを決定します。 |
| グローバルメールオプトアウト | [統合](integrations.md#configure-global-email-opt-out) | すべての送信メールに登録解除フッターを追加します。 |
| ナレッジセンターとプレイブック | [&#x200B; ナレッジセンター](knowledge-center.md) | 会社のプレイブックをアウトバウンドプロンプトと[AI チャット &#x200B;](ai-assistant.md)で利用できるようにします。 |
| アクティビティの同期 | [統合](integrations.md#configure-activity-sync-outbound-mapping) | Sales Qualifier アウトリーチアクティビティをCRMに表示するかどうかを指定します。 |

標準ユーザーはこれらの設定を使用できますが、変更することはできません。 必要なフィルター、プレイブック参照、またはCRM フィールドが見つからない場合は、管理者にお問い合わせください。

>[!MORELIKETHIS]
>
>* [基本を学ぶ](getting-started.md)
>* [統合](integrations.md)
>* [&#x200B; ナレッジセンター](knowledge-center.md)
