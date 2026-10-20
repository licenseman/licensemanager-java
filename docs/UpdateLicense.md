

# UpdateLicense


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**expiresAt** | **OffsetDateTime** | &#x60;null&#x60; makes the license never expire. |  [optional] |
|**meta** | **Map&lt;String, Object&gt;** | Free-form JSON object. |  [optional] |
|**maxMachines** | **Integer** | Maximum number of active machines the license can be used on. &#x60;null&#x60; for no limit. |  [optional] |
|**maxOfflineDurationSeconds** | **Integer** | Longest the applications can run offline with the license, in seconds. At least one hour (&#x60;3600&#x60;). |  [optional] |
|**maxVersion** | [**LicenseMaxVersionInput**](LicenseMaxVersionInput.md) | Latest version of the product the license can use. The values left out are kept. |  [optional] |
|**price** | [**PriceInput**](PriceInput.md) |  |  [optional] |



