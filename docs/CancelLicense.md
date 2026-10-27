

# CancelLicense


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**reason** | **CancellationReason** |  |  |
|**comment** | **String** | What the customer said about the cancellation. |  [optional] |
|**refund** | **Boolean** | Whether to refund the license&#39;s Stripe payment, when it was bought through the Stripe integration. Defaults to the integration&#39;s &#x60;autoRefund&#x60;. Ignored for tokens, which always follow &#x60;autoRefund&#x60;, and when the integration&#39;s &#x60;canRefund&#x60; is false: its API key can&#39;t create refunds. |  [optional] |



