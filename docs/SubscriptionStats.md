

# SubscriptionStats

Subscriptions to recurring Stripe prices, each with its subscription license.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**activeCount** | **Integer** | Number of ongoing subscriptions: &#x60;active&#x60;, &#x60;trialing&#x60; or &#x60;past_due&#x60;. |  |
|**trialingCount** | **Integer** |  |  |
|**pastDueCount** | **Integer** | Number of them whose renewal failed, as Stripe retries it: their licenses stay valid for the integration&#39;s grace days. |  |
|**cancelingCount** | **Integer** | Number of them set to end at the end of their period. |  |
|**newCount** | **Integer** | Number of subscriptions started in the last 30 days. |  |
|**endedCount** | **Integer** | Number of subscriptions that ended in the last 30 days. |  |
|**churnRate** | **BigDecimal** | Share of the subscriptions ongoing 30 days ago that ended since, from 0 to 1. |  |
|**newByMonth** | **List&lt;Integer&gt;** | Number of subscriptions started each month, aligned on &#x60;months&#x60;. |  |
|**endedByMonth** | **List&lt;Integer&gt;** | Number of subscriptions that ended each month, aligned on &#x60;months&#x60;. |  |
|**activeByMonth** | **List&lt;Integer&gt;** | Number of ongoing subscriptions at the end of each month, aligned on &#x60;months&#x60;, today for this month. |  |
|**mrr** | [**List&lt;Mrr&gt;**](Mrr.md) | MRR in each currency, from the highest number of subscriptions. Amounts aren&#39;t converted between currencies. |  |



