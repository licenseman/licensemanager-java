

# SlackConnection


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**teamId** | **String** |  |  |
|**teamName** | **String** |  |  |
|**channelId** | **String** |  |  |
|**channelName** | **String** | Name of the channel when it was connected, with its &#x60;#&#x60;. |  |
|**configurationUrl** | **String** | Page of the installation in Slack. |  |
|**events** | [**List&lt;EventsEnum&gt;**](#List&lt;EventsEnum&gt;) | Notifications the channel gets: &#x60;purchased&#x60; (a license bought through Stripe), &#x60;renewed&#x60; (a subscription renewal paid), &#x60;payment_failed&#x60; (a subscription payment failed) and &#x60;canceled&#x60; (a license canceled, or its subscription ended). |  |
|**status** | [**StatusEnum**](#StatusEnum) | &#x60;revoked&#x60; once Slack refuses the messages, like when the app was removed from the workspace or the channel deleted: remove it and add it again. |  |
|**statusReason** | **String** |  |  |
|**lastSentAt** | **OffsetDateTime** |  |  |
|**createdAt** | **OffsetDateTime** |  |  |



## Enum: List&lt;EventsEnum&gt;

| Name | Value |
|---- | -----|
| PURCHASED | &quot;purchased&quot; |
| RENEWED | &quot;renewed&quot; |
| PAYMENT_FAILED | &quot;payment_failed&quot; |
| CANCELED | &quot;canceled&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| ACTIVE | &quot;active&quot; |
| REVOKED | &quot;revoked&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



