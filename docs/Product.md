

# Product


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**slug** | **String** |  |  |
|**name** | **String** |  |  |
|**isTestFromProductId** | **String** | For test products, id of the live product they&#39;re a sandbox of. &#x60;null&#x60; for live products. |  |
|**logoUrl** | **URI** | Public URL of the product&#39;s logo, shown in the web app and the customer portal. &#x60;null&#x60; without a logo. |  |
|**portal** | [**PortalSettings**](PortalSettings.md) |  |  |
|**autoMachineChange** | **Boolean** | Whether a new machine validating a license already on its max machines takes the place of the license&#39;s machine validated the longest ago, rather than being refused with &#x60;machine_limit_reached&#x60;. When the replaced machine is validated again, it takes its place back and the machine that replaced it is locked. See &#x60;validateKey&#x60;. |  |
|**createdAt** | **OffsetDateTime** |  |  |
|**updatedAt** | **OffsetDateTime** |  |  |



