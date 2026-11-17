

# ImportLicenseResult


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**index** | **Integer** | Position of the license in &#x60;licenses&#x60;, from 0. |  |
|**key** | **String** |  |  |
|**status** | [**StatusEnum**](#StatusEnum) | &#x60;created&#x60;: imported. &#x60;skipped&#x60;: a license of the product already uses the key, like one imported before: it&#39;s left as is. &#x60;failed&#x60;: not imported, see &#x60;error&#x60;. |  |
|**licenseId** | **String** | Id of the license created, or of the one using the key. |  |
|**error** | [**ImportLicenseResultError**](ImportLicenseResultError.md) |  |  |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| CREATED | &quot;created&quot; |
| SKIPPED | &quot;skipped&quot; |
| FAILED | &quot;failed&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



