

# IntegrationMapping


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**integrationId** | **String** |  |  |
|**provider** | [**ProviderEnum**](#ProviderEnum) |  |  |
|**productId** | **String** |  |  |
|**policyId** | **String** |  |  |
|**externalProductId** | **String** | Id of the product in the provider: &#x60;prod_…&#x60; in Stripe, &#x60;pro_…&#x60; in Paddle. |  |
|**externalPriceId** | **String** | Id of the price in the provider: &#x60;price_…&#x60; in Stripe, &#x60;pri_…&#x60; in Paddle. |  |
|**stripeProductId** | **String** | Deprecated: use &#x60;externalProductId&#x60;, which it equals. |  |
|**stripePriceId** | **String** | Deprecated: use &#x60;externalPriceId&#x60;, which it equals. |  |
|**productName** | **String** | Name of the provider&#39;s product when it was mapped. |  |
|**price** | [**Price**](Price.md) |  |  |
|**recurring** | [**IntegrationMappingRecurring**](IntegrationMappingRecurring.md) |  |  |
|**status** | [**StatusEnum**](#StatusEnum) | &#x60;error&#x60; when the price can no longer be paid, explained by &#x60;statusReason&#x60;. |  |
|**statusReason** | **String** |  |  |
|**createdAt** | **OffsetDateTime** |  |  |



## Enum: ProviderEnum

| Name | Value |
|---- | -----|
| STRIPE | &quot;stripe&quot; |
| PADDLE | &quot;paddle&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| ACTIVE | &quot;active&quot; |
| ERROR | &quot;error&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



