

# License


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**productId** | **String** |  |  |
|**policyId** | **String** |  |  |
|**customerId** | **String** |  |  |
|**key** | **String** | Unique within the product. Case sensitive: &#x60;validateKey&#x60; compares keys exactly. |  |
|**createdAt** | **OffsetDateTime** |  |  |
|**expiresAt** | **OffsetDateTime** | &#x60;null&#x60; when the license never expires. |  |
|**meta** | **Map&lt;String, Object&gt;** | Free-form JSON object. |  |
|**stripePaymentIntentId** | **String** | Id of the Stripe payment intent that paid the license, when it was bought through the Stripe integration. &#x60;null&#x60; otherwise, or when nothing was paid. |  |
|**maxMachines** | **Integer** | Maximum number of active machines the license can be used on. &#x60;null&#x60; when there&#39;s no limit. Can be lower than &#x60;activeMachineCount&#x60; after it was lowered: machines aren&#39;t deactivated to match it. |  |
|**maxOfflineDurationSeconds** | **Integer** | Longest the applications can run offline with the license: the license tokens returned by &#x60;validateKey&#x60; expire this long after they&#39;re issued, unless the license expires sooner. |  |
|**activeMachineCount** | **Integer** | Number of active machines the license is used on. |  |
|**lastActivatedAt** | **OffsetDateTime** | Last time a machine validated the license key. &#x60;null&#x60; when it was never validated. |  |
|**maxVersion** | [**LicenseMaxVersion**](LicenseMaxVersion.md) |  |  |
|**price** | [**Price**](Price.md) |  |  |
|**status** | **LicenseStatus** |  |  |
|**cancellableUntil** | **OffsetDateTime** | End of the money back guarantee: until then, the customer can cancel the license from the customer portal, or with a token. Set from the policy&#39;s &#x60;moneyBackGuaranteeDays&#x60; when the license is created. &#x60;null&#x60; when the customer can&#39;t cancel it. |  |
|**canceledAt** | **OffsetDateTime** | When the license was canceled: validating its key fails since. &#x60;null&#x60; when it wasn&#39;t. |  |
|**cancellationReason** | [**CancellationReason**](CancellationReason.md) |  |  |
|**cancellationComment** | **String** | Comment given when the license was canceled. &#x60;null&#x60; when there&#39;s none. |  |
|**stripeRefundId** | **String** | Id of the Stripe refund of the license&#39;s payment once it was canceled, through the Stripe integration. &#x60;null&#x60; otherwise. |  |
|**updatedAt** | **OffsetDateTime** | Last time the license&#39;s settings were edited, not when its key was validated. |  |



