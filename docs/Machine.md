

# Machine


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**licenseId** | **String** |  |  |
|**fingerprint** | **String** | Identifies the machine. Unique within the license. |  |
|**platform** | **String** |  |  |
|**name** | **String** |  |  |
|**status** | [**StatusEnum**](#StatusEnum) | Whether the machine counts as using the license. A &#x60;locked&#x60; machine doesn&#39;t, and its validations are refused with &#x60;machine_locked&#x60;: it overrode a machine that came back. See &#x60;validateKey&#x60;. |  |
|**version** | **String** | Version of the application last validated on the machine. |  |
|**overriddenByMachineId** | **String** | For a machine deactivated or locked by automatic machine changes, the machine that took its place. Validating the key on a deactivated machine that has one takes its place back. &#x60;null&#x60; otherwise. |  |
|**lastValidatedAt** | **OffsetDateTime** | When the license was last validated on the machine. |  |
|**createdAt** | **OffsetDateTime** |  |  |
|**updatedAt** | **OffsetDateTime** |  |  |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| ACTIVE | &quot;active&quot; |
| DEACTIVATED | &quot;deactivated&quot; |
| LOCKED | &quot;locked&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



