

# EventActor

Who caused the event: a user of the app, an API key, a token, `automation` for the changes the app makes on its own, like applying the version locks, or `integration` for the changes of an integration, like the licenses a Stripe payment creates. `null` for requests that don't authenticate, like validating a license key.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**type** | [**TypeEnum**](#TypeEnum) |  |  |
|**id** | **String** | &#x60;null&#x60; when the integration has been disconnected. |  |
|**name** | **String** |  |  |
|**email** | **String** |  |  |
|**image** | **String** | URL of the user&#39;s profile picture. |  |
|**start** | **String** | First characters of the key, to recognize it. |  |
|**tokenType** | [**TokenTypeEnum**](#TokenTypeEnum) | Type of resource the token is scoped to. |  |
|**subjectId** | **String** | Id of the resource the token is scoped to. |  |
|**provider** | [**ProviderEnum**](#ProviderEnum) | Service the integration connects to. |  |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| USER | &quot;user&quot; |
| API_KEY | &quot;apiKey&quot; |
| TOKEN | &quot;token&quot; |
| AUTOMATION | &quot;automation&quot; |
| INTEGRATION | &quot;integration&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



## Enum: TokenTypeEnum

| Name | Value |
|---- | -----|
| CUSTOMER | &quot;customer&quot; |
| LICENSE | &quot;license&quot; |
| MACHINE | &quot;machine&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



## Enum: ProviderEnum

| Name | Value |
|---- | -----|
| STRIPE | &quot;stripe&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



