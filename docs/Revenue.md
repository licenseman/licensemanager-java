

# Revenue

Revenue in one currency: the licenses sold once, each counting on the day it was created, and the payments of the subscription licenses, each counting on the day it was paid, with the license's policy. Licenses without a price are left out, and so are canceled ones, but in `canceledLicenseCount` and `canceledTotal`.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**currency** | **String** | ISO 4217 code of the currency of the revenue. |  |
|**licenseCount** | **Integer** | Number of licenses sold once in the currency, free ones included, canceled ones and subscription licenses left out. |  |
|**total** | **BigDecimal** | Revenue in the currency, in major units: the prices of the licenses sold once, canceled ones left out, plus the payments of the subscriptions, &#x60;subscriptionTotal&#x60;. |  |
|**subscriptionTotal** | **BigDecimal** | Sum of the payments of the subscription licenses in the currency, before taxes, in major units. |  |
|**paymentCount** | **Integer** | Number of payments of the subscription licenses in the currency. |  |
|**canceledLicenseCount** | **Integer** | Number of canceled licenses sold once in the currency. |  |
|**canceledTotal** | **BigDecimal** | Sum of the prices of the canceled licenses sold once in the currency, in major units: revenue lost to cancellations. |  |
|**thisMonth** | **BigDecimal** | Revenue of the current month, in UTC. |  |
|**lastMonth** | **BigDecimal** | Revenue of the previous month, in UTC. |  |
|**last30Days** | **BigDecimal** | Revenue of the last 30 days, today included, in UTC. |  |
|**byDay** | **List&lt;BigDecimal&gt;** | Revenue each day, aligned on &#x60;days&#x60;. |  |
|**byMonth** | **List&lt;BigDecimal&gt;** | Revenue each month, aligned on &#x60;months&#x60;. |  |
|**byPolicy** | [**List&lt;ProductStatsNewLicensesByPolicyInner&gt;**](ProductStatsNewLicensesByPolicyInner.md) | Revenue of the licenses of each policy, for the policies with licenses sold in the currency over the covered months. |  |



