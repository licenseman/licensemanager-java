

# PolicySettingsMaxVersion

Latest version of the product the licenses created with this policy can use. `null` allows every version. Defaults to `null`.  - `fixed`: up to a hard-coded `version`. `\"2\"` allows every 2.y.z version: its minor versions and bug fixes. `\"2.3\"` allows every 2.3.z version: its bug fixes. - `lock`: every version released during some time after the license is created, then only the updates of the version reached by then. The major version locks `majorAfter` the creation of the license, then the license only gets the minor versions and bug fixes of its major version. The minor version optionally locks `minorAfter` it, never sooner than the major version, then the license only gets the bug fixes of its minor version. `{ \"type\": \"lock\", \"majorAfter\": { \"value\": 1, \"unit\": \"months\" }, \"minorAfter\": { \"value\": 12, \"unit\": \"months\" } }` allows every version released during the month after the license is created, then the minor versions and bug fixes of the major version reached by then until the end of the first year, then only the bug fixes of the minor version reached by then. `majorAfter` at 0 allows minor versions only, and both at 0 allows bug fixes only: no updates.  Bug fixes are never locked: a hard-coded version has no patch number, like `\"2.3.1\"`, and a lock only locks major and minor versions.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**type** | [**TypeEnum**](#TypeEnum) |  |  |
|**version** | **String** | &#x60;\&quot;2\&quot;&#x60; allows every 2.y.z version: the minor versions and bug fixes of version 2. &#x60;\&quot;2.3\&quot;&#x60; allows every 2.3.z version: the bug fixes of version 2.3. Bug fixes can&#39;t be locked, so patch numbers like &#x60;\&quot;2.3.1\&quot;&#x60; are rejected. |  |
|**majorAfter** | [**LockMaxVersionMajorAfter**](LockMaxVersionMajorAfter.md) |  |  |
|**minorAfter** | [**LockMaxVersionMinorAfter**](LockMaxVersionMinorAfter.md) |  |  |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| FIXED | &quot;fixed&quot; |
| LOCK | &quot;lock&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



