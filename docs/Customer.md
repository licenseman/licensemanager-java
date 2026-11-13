

# Customer


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**productId** | **String** |  |  |
|**email** | **String** |  |  |
|**name** | **String** | Display name of the customer. &#x60;null&#x60; when unknown. |  |
|**licenseCount** | **Integer** | Number of licenses of this customer. |  |
|**stripeCustomerId** | **String** | Id of the Stripe customer, when the customer bought licenses through the Stripe integration as a Stripe customer. &#x60;null&#x60; otherwise, e.g. for a guest checkout. |  |
|**paddleCustomerId** | **String** | Id of the Paddle customer, when the customer bought licenses through the Paddle integration. &#x60;null&#x60; otherwise. |  |
|**createdAt** | **OffsetDateTime** |  |  |



