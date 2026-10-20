

# LockMaxVersionMajorAfter

Time after the creation of a license its major version is locked, in seconds or calendar months: it then only gets the minor versions and bug fixes of the major version released by then. `0` locks it when the license is created.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**value** | **Integer** |  |  |
|**unit** | [**UnitEnum**](#UnitEnum) | Calendar months: a license created on January 31 with a 1 month duration expires on the last day of February. |  |



## Enum: UnitEnum

| Name | Value |
|---- | -----|
| MONTHS | &quot;months&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



