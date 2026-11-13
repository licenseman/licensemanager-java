

# LicenseSubscription

The Stripe or Paddle subscription keeping the license valid, `null` when it isn't a subscription license. The license expires when it stops being paid, includes every update, and can't be canceled during a money back guarantee.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**provider** | [**ProviderEnum**](#ProviderEnum) | Provider of the subscription. |  |
|**externalId** | **String** | Id of the subscription in the provider: &#x60;sub_…&#x60; in Stripe and in Paddle. |  |
|**stripeSubscriptionId** | **String** | Deprecated: use &#x60;externalId&#x60;, which it equals. |  |
|**status** | **String** | Status of the subscription in the provider. Stripe: &#x60;active&#x60;, &#x60;trialing&#x60;, &#x60;past_due&#x60; while a failed payment is retried, &#x60;canceled&#x60;, &#x60;unpaid&#x60;, &#x60;paused&#x60;, &#x60;incomplete&#x60; or &#x60;incomplete_expired&#x60;. Paddle: &#x60;active&#x60;, &#x60;trialing&#x60;, &#x60;past_due&#x60;, &#x60;paused&#x60; or &#x60;canceled&#x60;. |  |
|**interval** | [**IntervalEnum**](#IntervalEnum) |  |  |
|**intervalCount** | **Integer** | Number of intervals between payments. |  |
|**quantity** | **Integer** | Units subscribed, multiplying the policy&#39;s machines. |  |
|**price** | [**Price**](Price.md) | Price of one unit for one period, before taxes. |  |
|**currentPeriodEnd** | **OffsetDateTime** | End of the paid period, when the subscription renews or ends. |  |
|**cancelAtPeriodEnd** | **Boolean** | Whether the subscription ends at the end of the period. |  |
|**endedAt** | **OffsetDateTime** |  |  |



## Enum: ProviderEnum

| Name | Value |
|---- | -----|
| STRIPE | &quot;stripe&quot; |
| PADDLE | &quot;paddle&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



## Enum: IntervalEnum

| Name | Value |
|---- | -----|
| DAY | &quot;day&quot; |
| WEEK | &quot;week&quot; |
| MONTH | &quot;month&quot; |
| YEAR | &quot;year&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



