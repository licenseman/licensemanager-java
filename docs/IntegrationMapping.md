

# IntegrationMapping


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**integrationId** | **String** |  |  |
|**productId** | **String** |  |  |
|**policyId** | **String** |  |  |
|**stripeProductId** | **String** |  |  |
|**stripePriceId** | **String** |  |  |
|**productName** | **String** | Name of the Stripe product when it was mapped. |  |
|**price** | [**Price**](Price.md) |  |  |
|**status** | [**StatusEnum**](#StatusEnum) | &#x60;error&#x60; when the price can no longer be paid, explained by &#x60;statusReason&#x60;. |  |
|**statusReason** | **String** |  |  |
|**createdAt** | **OffsetDateTime** |  |  |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| ACTIVE | &quot;active&quot; |
| ERROR | &quot;error&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



