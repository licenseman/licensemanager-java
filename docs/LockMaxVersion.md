

# LockMaxVersion

The licenses can use every version released after their creation, until their major version locks `majorAfter` it, then the updates of their major version until their minor version locks `minorAfter` it, if ever. Bug fixes are never locked.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**type** | [**TypeEnum**](#TypeEnum) |  |  |
|**majorAfter** | [**LockMaxVersionMajorAfter**](LockMaxVersionMajorAfter.md) |  |  |
|**minorAfter** | [**LockMaxVersionMinorAfter**](LockMaxVersionMinorAfter.md) |  |  |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| LOCK | &quot;lock&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



