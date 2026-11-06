

# LicenseSubscription

The Stripe subscription keeping the license valid, `null` when it isn't a subscription license. The license expires when it stops being paid, includes every update, and can't be canceled during a money back guarantee.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**stripeSubscriptionId** | **String** |  |  |
|**status** | **String** | Status of the subscription in Stripe: &#x60;active&#x60;, &#x60;trialing&#x60;, &#x60;past_due&#x60; while a failed payment is retried, &#x60;canceled&#x60;, &#x60;unpaid&#x60;, &#x60;paused&#x60;, &#x60;incomplete&#x60; or &#x60;incomplete_expired&#x60;. |  |
|**interval** | [**IntervalEnum**](#IntervalEnum) |  |  |
|**intervalCount** | **Integer** | Number of intervals between payments. |  |
|**quantity** | **Integer** | Units subscribed, multiplying the policy&#39;s machines. |  |
|**price** | [**Price**](Price.md) | Price of one unit for one period, before taxes. |  |
|**currentPeriodEnd** | **OffsetDateTime** | End of the paid period, when the subscription renews or ends. |  |
|**cancelAtPeriodEnd** | **Boolean** | Whether the subscription ends at the end of the period. |  |
|**endedAt** | **OffsetDateTime** |  |  |



## Enum: IntervalEnum

| Name | Value |
|---- | -----|
| DAY | &quot;day&quot; |
| WEEK | &quot;week&quot; |
| MONTH | &quot;month&quot; |
| YEAR | &quot;year&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



