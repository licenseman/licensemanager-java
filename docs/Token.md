

# Token


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**token** | **String** | Token to send as &#x60;Authorization: Bearer &lt;token&gt;&#x60;. |  |
|**type** | [**TypeEnum**](#TypeEnum) | Type of resource the token is scoped to. |  |
|**scope** | [**List&lt;ScopeEnum&gt;**](#List&lt;ScopeEnum&gt;) |  |  |
|**expiresAt** | **OffsetDateTime** | When the token stops working. |  |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| CUSTOMER | &quot;customer&quot; |
| LICENSE | &quot;license&quot; |
| MACHINE | &quot;machine&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



## Enum: List&lt;ScopeEnum&gt;

| Name | Value |
|---- | -----|
| CUSTOMER_READ | &quot;customer:read&quot; |
| CUSTOMER_WRITE | &quot;customer:write&quot; |
| LICENSE_READ | &quot;license:read&quot; |
| LICENSE_WRITE | &quot;license:write&quot; |
| LICENSE_CANCEL | &quot;license:cancel&quot; |
| MACHINE_READ | &quot;machine:read&quot; |
| MACHINE_WRITE | &quot;machine:write&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



