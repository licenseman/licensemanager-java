

# Event


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**type** | **EventType** |  |  |
|**createdAt** | **OffsetDateTime** |  |  |
|**payload** | **Map&lt;String, Object&gt;** | Details of the event, depending on its &#x60;type&#x60;. |  |
|**policyId** | **String** |  |  |
|**licenseId** | **String** |  |  |
|**machineId** | **String** |  |  |
|**machine** | [**EventMachine**](EventMachine.md) |  |  |
|**actor** | [**EventActor**](EventActor.md) |  |  |
|**country** | **String** | ISO 3166-1 alpha-2 code of the country of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |  |
|**latitude** | **BigDecimal** | Approximate latitude of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |  |
|**longitude** | **BigDecimal** | Approximate longitude of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |  |



