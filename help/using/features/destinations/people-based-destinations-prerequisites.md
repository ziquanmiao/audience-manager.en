---
description: Read below for an overview of customer requirements that you need to meet before signing up for People-Based Destinations.  
seo-description: Read below for an overview of customer requirements that you need to meet before signing up for People-Based Destinations.  
seo-title: People-Based Destinations Prerequisites and Considerations
solution: Audience Manager
title: Prerequisites and Considerations
feature: People-based Destinations
exl-id: 7656aa3e-3410-4052-8e29-b702bd0bf149
---
# Prerequisites and Considerations {#prerequisites-considerations}

>[!IMPORTANT]
>This article contains product documentation meant to guide you through the setup and usage of this feature. Nothing contained herein is legal advice. Please consult your own legal counsel for legal guidance.

Read below for an overview of customer requirements that you need to meet before signing up for [!UICONTROL People-Based Destinations].

>[!IMPORTANT]
> Read through this article carefully before moving on to the implementation phase.

## Signing up for [!UICONTROL People-Based Destinations] {#signing-up}

[!UICONTROL People-Based Destinations] is a premium capability that enhances your Audience Manager experience by allowing you to activate your first-party audience segments in people-based environments, by targeting your audience with customized offers on social networks or through email marketing.

Please contact your Adobe representative to take advantage of this premium feature.

## Partner-Specific Prerequisites {#partner-prerequisites}

### [!DNL Facebook] {#facebook}

Before you can use [!UICONTROL People-Based Destinations] to send your first-party audience [!UICONTROL segments] to [!DNL Facebook], make sure you meet the following requirements:

1. Your [!DNL Facebook] user account must have the **Manage campaigns** permission enabled for the Ad account that you plan to use.
2. Add the **Adobe Experience Cloud** business account as an advertising partner in your [!DNL Facebook Ad Account]. Use `business ID=206617933627973`. See [Add Partners to Your Business Manager](https://www.facebook.com/business/help/1717412048538897) for details.
    >[!IMPORTANT]
    > When configuring the permissions for Adobe Experience Cloud, you must enable the **Manage campaigns** permission. This is required for the [!UICONTROL People-Based Destinations] integration.
3. Read and sign the [!DNL Facebook Custom Audiences] Terms of Service. To do this, go to `https://business.facebook.com/ads/manage/customaudiences/tos/?act=[accountID]`, where `accountID` is your [!DNL Facebook Ad Account ID].

### [!DNL LinkedIn] {#linkedin}

Before you can use [!UICONTROL People-Based Destinations] to send your first-party audience segments to [!DNL LinkedIn], make sure your [!DNL LinkedIn Campaign Manager] account has the [!DNL Creative Manager] or higher permission level.

To learn how to edit your [!DNL LinkedIn Campaign Manager] user permissions, see [Add, Edit, and Remove User Permissions on Advertising Accounts](https://www.linkedin.com/help/lms/answer/5753) in the LinkedIn documentation.

See [Understanding and Configuring the LinkedIn People-Based Destination](https://experienceleague.adobe.com/docs/audience-manager-learn/tutorials/data-activation/people-based-destinations/understanding-and-configuring-the-linkedin-pbd.html) for video instructions.

### [!DNL Google Customer Match] {#gcm}

Before you can use [!UICONTROL People-Based Destinations] to send your first-party audience segments to a [!DNL Google Customer Match] destination, make sure you read and adhere to Google's policy for using [!DNL Customer Match], outlined in the [Google support documentation](https://support.google.com/google-ads/answer/6299717).

Next, make sure your [!DNL Google] account is configured for a [!DNL Standard] or higher permission level. See the [Google Ads documentation](https://support.google.com/google-ads/answer/9978556?visit_id=637611563637058259-4176462731&rd=1) for details.

Customers with compliant accounts are automatically allow listed by Google.

## Data Onboarding {#data-onboarding}

Data ingestion for [!UICONTROL People-Based Destinations] currently supports up to 10 hashed email addresses linked to one customer ID ([!DNL CRM ID]), per batch transfer. Uploading more than 10 hashed email addresses linked to one customer ID causes Audience Manager to ingest 10 of them, in no specific order.

Uploading more than 10 hashed email addresses linked to one customer ID in multiple batch transfers causes Audience Manager to retain the most recent 10 email addresses added.

## Data Privacy {#data-privacy}

Although [!UICONTROL People-Based Destinations] allow you to target audiences based on hashed email addresses uploaded by you, you remain prohibited from uploading any directly identifiable visitor information into Audience Manager. In the data onboarding phase, you must ensure that the email addresses you plan to use are hashed with the [!DNL SHA256] algorithm. Otherwise, you won't be able to use them in [!UICONTROL People-Based Destinations].

## Data Hashing Versus Encryption {#data-hashing-encryption}

Encryption is a two-way function. Any encrypted information can also be decrypted, using the correct decryption key. Encrypting data in the context of Audience Manager poses serious risks, since any encrypted form of personally identifiable information can also be decrypted. As opposed to encryption, [!UICONTROL People-Based Destinations] are designed to work with hashed data instead.

Hashing is a one-way function that scrambles the input to produce a unique result. By using proper hashing algorithms, like [!DNL SHA256], there is no way to reverse the hashing function and reveal the unscrambled information. The email addresses that you will onboard to Audience Manager must be hashed with the [!DNL SHA256] algorithm. This way, you can ensure that no unhashed email addresses reach Audience Manager.

## Hashing Requirements {#hashing-requirements}

When hashing the email addresses, make sure to comply with the following requirements:

* Trim all leading and trailing spaces from the email string; example: `johndoe@example.com`, not `<space>johndoe@example.com<space>`;
* When hashing the email strings, make sure to hash the lowercase string;
  * Example: `example@email.com`, not `EXAMPLE@EMAIL.COM`;
* Make sure the hashed string is all lowercase
  * Example: `55e79200c1635b37ad31a378c39feb12f120f116625093a19bc32fff15041149`, not `55E79200C1635B37AD31A378C39FEB12F120F116625093A19bC32FFF15041149`;
* Do not salt the string.

Watch the video below to understand the hashing requirements of [!UICONTROL People-Based Destinations].

>[!VIDEO](https://video.tv.adobe.com/v/29003/)

Adobe Experience Cloud gives you the option to hash customer IDs through the [!DNL Adobe Experience Platform Identity Service (ECID)]. See [SHA256 Hashing Support for setCustomerIDs](https://experienceleague.adobe.com/docs/id-service/using/reference/hashing-support.html) for detailed information on how to use ECID to hash customer IDs.

## Obtaining User Permission {#obtaining-user-permission}

Since [!UICONTROL People-Based Destinations] helps you activate first-party audience data in people-based channels, it is your responsibility to inform and obtain any necessary consents from your customers of how you will use their data for advertising or other purposes.

Before you sign up for [!UICONTROL People-Based Destinations], make sure to obtain your customers' consent before using their information for advertising purposes.

In case your customers wish to opt-out of advertising campaigns, see [Opt-out Management](../../overview/data-security-and-privacy/data-privacy-requests.md) for details on how to stop Audience Manager from collecting data any further.

## Enforcing First-Party Data Activation {#enforcing-first-party-activation}

When using [!UICONTROL People-Based Destinations], you can only use first-party data to activate audience segments in people-based channels. You cannot use any second- or third-party data for audience activation in people-based channels.

When using [!UICONTROL People-Based Destinations], use [Data Export Controls](../data-export-controls.md) to label your [!UICONTROL data sources] and [!UICONTROL destinations] according to the guidelines and requirements from destination platforms and data providers.

## Onboard Authenticated Hashed IDs through Declared ID Targeting {#onboard-authenticated-declared-id}

There are two ways you can bring your offline data to Audience Manager for [!UICONTROL People-Based Destinations].

* [Send batch data](../../integration/sending-audience-data/batch-data-transfer-explained/batch-data-transfer-overview.md) to Audience Manager to ingest hashed email addresses. With this method, you can choose to use the hashed email addresses from your [!DNL CRM] database in [!UICONTROL People-Based Destinations]. Additionally, when using this method, you can also qualify the hashed email addresses for [onboarded traits](../traits/trait-and-segment-qualification-reference.md).
* Use [Declared IDs](../declared-ids.md) to declare hashed email addresses when passing in authenticated customer IDs. When using this method, Audience Manager, on your behalf, only sends to [!UICONTROL People-Based Destinations] the hashed email addresses from users who have authenticated online. The email addresses activated through people-based channels are only the ones in the declared ID event calls. Other email addresses associated with the customer ID are not sent in real-time.
