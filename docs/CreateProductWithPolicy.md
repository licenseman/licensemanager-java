

# CreateProductWithPolicy


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** |  |  |
|**slug** | **String** | Unique within the organization. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. |  [optional] |
|**defaultPolicy** | [**PolicySettings**](PolicySettings.md) |  |  [optional] |
|**isTestFromProductId** | **String** | Creates a test product: a sandbox of this live product of the organization, starting with copies of its policies, releases, &#x60;websiteUrl&#x60;, &#x60;downloadUrl&#x60;, portal settings and &#x60;autoMachineChange&#x60;. |  [optional] |



