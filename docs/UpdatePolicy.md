

# UpdatePolicy


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** |  |  [optional] |
|**slug** | **String** | Unique within the product. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. |  [optional] |
|**isDefault** | **Boolean** | &#x60;true&#x60; makes this policy the product&#39;s default, in place of the current one. |  [optional] |
|**duration** | [**PolicySettingsDuration**](PolicySettingsDuration.md) |  |  [optional] |
|**maxMachines** | **Integer** | Maximum number of active machines of the licenses created with this policy, copied to each of them. &#x60;null&#x60; for no limit. Defaults to &#x60;null&#x60;. |  [optional] |
|**maxOfflineDurationSeconds** | **Integer** | Longest the applications can run offline with the licenses created with this policy, in seconds, copied to each of them. At least one hour (&#x60;3600&#x60;). Defaults to one week. |  [optional] |
|**maxVersion** | [**PolicySettingsMaxVersion**](PolicySettingsMaxVersion.md) |  |  [optional] |
|**moneyBackGuaranteeDays** | **Integer** | Number of days after their creation during which customers can cancel the licenses created with this policy, from the customer portal or with &#x60;cancelLicense&#x60;, which refunds their Stripe payment. Each license keeps the end of its own period as &#x60;cancellableUntil&#x60;. &#x60;null&#x60; for no money back guarantee. Defaults to &#x60;null&#x60;. |  [optional] |



