

# Revenue

Revenue of the licenses sold in one currency, each license counting on the day it was created. Licenses without a price are left out, and so are canceled ones, but in `canceledLicenseCount` and `canceledTotal`.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**currency** | **String** | ISO 4217 code of the currency of the revenue. |  |
|**licenseCount** | **Integer** | Number of licenses sold in the currency, free ones included, canceled ones left out. |  |
|**total** | **BigDecimal** | Sum of the prices of the licenses sold in the currency, in major units, canceled ones left out. |  |
|**canceledLicenseCount** | **Integer** | Number of canceled licenses sold in the currency. |  |
|**canceledTotal** | **BigDecimal** | Sum of the prices of the canceled licenses sold in the currency, in major units: revenue lost to cancellations. |  |
|**thisMonth** | **BigDecimal** | Revenue of the current month, in UTC. |  |
|**lastMonth** | **BigDecimal** | Revenue of the previous month, in UTC. |  |
|**last30Days** | **BigDecimal** | Revenue of the last 30 days, today included, in UTC. |  |
|**byDay** | **List&lt;BigDecimal&gt;** | Revenue each day, aligned on &#x60;days&#x60;. |  |
|**byMonth** | **List&lt;BigDecimal&gt;** | Revenue each month, aligned on &#x60;months&#x60;. |  |
|**byPolicy** | [**List&lt;ProductStatsNewLicensesByPolicyInner&gt;**](ProductStatsNewLicensesByPolicyInner.md) | Revenue of the licenses of each policy, for the policies with licenses sold in the currency over the covered months. |  |



