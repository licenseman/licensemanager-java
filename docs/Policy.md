

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
|**licenseCount** | **Integer** | Number of licenses following this policy. |  |
|**createdAt** | **OffsetDateTime** |  |  |
|**updatedAt** | **OffsetDateTime** |  |  |



