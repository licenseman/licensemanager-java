

# CreateToken


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**scope** | [**List&lt;ScopeEnum&gt;**](#List&lt;ScopeEnum&gt;) | Permissions of the token. A write permission implies the matching read one. A token creating a token can only give the permissions it has. |  |
|**expiresInSeconds** | **Integer** | How long the token works, in seconds, from 60 (1 minute) to 31536000 (365 days). Defaults to 900 (15 minutes). A token creating a token can&#39;t give it a later expiration than its own: it&#39;s shortened to it. |  [optional] |



## Enum: List&lt;ScopeEnum&gt;

| Name | Value |
|---- | -----|
| CUSTOMER_READ | &quot;customer:read&quot; |
| CUSTOMER_WRITE | &quot;customer:write&quot; |
| LICENSE_READ | &quot;license:read&quot; |
| LICENSE_WRITE | &quot;license:write&quot; |
| MACHINE_READ | &quot;machine:read&quot; |
| MACHINE_WRITE | &quot;machine:write&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



