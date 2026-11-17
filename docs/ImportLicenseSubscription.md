

# ImportLicenseSubscription

Subscription of the provider keeping the license valid, like one moved to Stripe by Lemon Squeezy's migration: its renewals then extend this license rather than creating one with a new key. Its price must be mapped to a policy of the product, which the license follows instead of `policyId`, and the license's expiration, version and money back guarantee follow the subscription like the ones it creates. Read from the provider of the product's mode, through the integration.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**provider** | [**ProviderEnum**](#ProviderEnum) | Provider of the subscription. |  |
|**externalId** | **String** | Id of the subscription in the provider: &#x60;sub_…&#x60; in Stripe and in Paddle. |  |



## Enum: ProviderEnum

| Name | Value |
|---- | -----|
| STRIPE | &quot;stripe&quot; |
| PADDLE | &quot;paddle&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



