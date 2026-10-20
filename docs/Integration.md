

# Integration


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**provider** | [**ProviderEnum**](#ProviderEnum) |  |  |
|**livemode** | **Boolean** | Whether it&#39;s connected in live mode, for the live products, or in test mode, for the test products. |  |
|**accountName** | **String** | Name of the Stripe account, &#x60;null&#x60; when the API key can&#39;t read it. |  |
|**apiKeyHint** | **String** | Start and end of the API key, to recognize it. |  |
|**webhookUrl** | **String** | URL of the webhook endpoint created on the Stripe account. |  |
|**status** | **IntegrationStatus** |  |  |
|**statusReason** | **String** | Why the integration isn&#39;t &#x60;active&#x60;, &#x60;null&#x60; when it is. |  |
|**lastCheckedAt** | **OffsetDateTime** | Last time its health was checked, done every day. |  |
|**lastEventAt** | **OffsetDateTime** | Last time it received an event from the provider. |  |
|**createdAt** | **OffsetDateTime** |  |  |



## Enum: ProviderEnum

| Name | Value |
|---- | -----|
| STRIPE | &quot;stripe&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



