

# Machine


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**licenseId** | **String** |  |  |
|**fingerprint** | **String** | Identifies the machine. Unique within the license. |  |
|**platform** | **String** |  |  |
|**name** | **String** |  |  |
|**status** | [**StatusEnum**](#StatusEnum) | Whether the machine counts as using the license. |  |
|**version** | **String** | Version of the application last validated on the machine. |  |
|**lastValidatedAt** | **OffsetDateTime** | When the license was last validated on the machine. |  |
|**createdAt** | **OffsetDateTime** |  |  |
|**updatedAt** | **OffsetDateTime** |  |  |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| ACTIVE | &quot;active&quot; |
| DEACTIVATED | &quot;deactivated&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



