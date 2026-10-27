

# Policy


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**productId** | **String** |  |  |
|**slug** | **String** |  |  |
|**name** | **String** |  |  |
|**isDefault** | **Boolean** | Whether this is the product&#39;s default policy. Each product has exactly one. |  |
|**duration** | [**PolicyDuration**](PolicyDuration.md) |  |  |
|**maxMachines** | **Integer** | Maximum number of active machines of the licenses created with this policy. &#x60;null&#x60; when there&#39;s no limit. |  |
|**maxOfflineDurationSeconds** | **Integer** | Longest the applications can run offline with the licenses created with this policy, in seconds. |  |
|**maxVersion** | [**PolicyMaxVersion**](PolicyMaxVersion.md) |  |  |
|**moneyBackGuaranteeDays** | **Integer** | Number of days after their creation during which customers can cancel the licenses created with this policy, from the customer portal or with &#x60;cancelLicense&#x60;. &#x60;null&#x60; when they can&#39;t. |  |
|**licenseCount** | **Integer** | Number of licenses following this policy. |  |
|**createdAt** | **OffsetDateTime** |  |  |
|**updatedAt** | **OffsetDateTime** |  |  |



