

# Mrr


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**currency** | **String** |  |  |
|**mrr** | **BigDecimal** | Monthly recurring revenue: the price of every ongoing subscription in the currency, times its quantity, brought to one month (a year counts for a twelfth), before taxes and discounts. |  |
|**byInterval** | [**List&lt;MrrByIntervalInner&gt;**](MrrByIntervalInner.md) | Ongoing subscriptions and MRR of each billing period, like monthly and yearly, from the highest MRR. |  |
|**byPolicy** | [**List&lt;MrrByPolicyInner&gt;**](MrrByPolicyInner.md) | MRR of each policy, from the highest. |  |
|**byMonth** | **List&lt;BigDecimal&gt;** | MRR at the end of each month, aligned on &#x60;months&#x60;, today for this month, at the current prices of the subscriptions. |  |



