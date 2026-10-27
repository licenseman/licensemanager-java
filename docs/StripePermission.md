

# StripePermission


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**resource** | **String** |  |  |
|**access** | [**AccessEnum**](#AccessEnum) |  |  |
|**reason** | **String** |  |  |
|**optional** | **Boolean** | Whether the key can connect without it, losing what it&#39;s for, explained by &#x60;reason&#x60;. |  |



## Enum: AccessEnum

| Name | Value |
|---- | -----|
| READ | &quot;Read&quot; |
| WRITE | &quot;Write&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



