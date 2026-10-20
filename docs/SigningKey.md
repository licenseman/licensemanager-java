

# SigningKey


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** | Id of the key, in the &#x60;kid&#x60; header of the tokens it signs. |  |
|**algorithm** | [**AlgorithmEnum**](#AlgorithmEnum) | JWT algorithm of the tokens it signs, with an Ed25519 key. |  |
|**publicKey** | **String** | PEM encoded SPKI public key. |  |
|**createdAt** | **OffsetDateTime** |  |  |



## Enum: AlgorithmEnum

| Name | Value |
|---- | -----|
| ED_DSA | &quot;EdDSA&quot; |
| UNKNOWN_DEFAULT_OPEN_API | &quot;unknown_default_open_api&quot; |



