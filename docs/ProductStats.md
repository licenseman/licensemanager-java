

# ProductStats


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**licenseCount** | **Integer** | Number of licenses of the product. |  |
|**activeLicenseCount** | **Integer** | Number of licenses that haven&#39;t expired nor were canceled, and that a machine validated in the last 90 days. |  |
|**newLicenseCount** | **Integer** | Number of licenses created in the last 30 days, today included, in UTC. |  |
|**expiringLicenseCount** | **Integer** | Number of licenses expiring in the next 30 days, canceled ones left out. |  |
|**expiredLicenseCount** | **Integer** | Number of licenses that expired in the last 30 days, canceled ones left out. |  |
|**activeMachineCount** | **Integer** | Number of active machines of the licenses of the product. |  |
|**inUseLicenseCount** | **Integer** | Number of licenses with at least one active machine. |  |
|**seatCount** | **Integer** | Sum of the maximum numbers of machines of the licenses that haven&#39;t expired nor were canceled. Licenses without a maximum are left out. |  |
|**usedSeatCount** | **Integer** | Number of active machines of the licenses counted in &#x60;seatCount&#x60;, at most their maximum number of machines each. |  |
|**fullLicenseCount** | **Integer** | Number of licenses counted in &#x60;seatCount&#x60; active on their maximum number of machines. |  |
|**days** | **List&lt;LocalDate&gt;** | The 30 days covered by the daily stats, from the oldest one, in UTC. |  |
|**months** | **List&lt;String&gt;** | The 12 months covered by the monthly stats, from the oldest one, in UTC. |  |
|**newLicensesByDay** | **List&lt;Integer&gt;** | Number of licenses created each day, aligned on &#x60;days&#x60;. |  |
|**newLicensesByMonth** | **List&lt;Integer&gt;** | Number of licenses created each month, aligned on &#x60;months&#x60;. |  |
|**newLicensesByPolicy** | [**List&lt;ProductStatsNewLicensesByPolicyInner&gt;**](ProductStatsNewLicensesByPolicyInner.md) | Number of licenses of each policy created each day and each month, for the policies with licenses created over the covered months. |  |
|**cancellation** | [**CancellationStats**](CancellationStats.md) | Cancellations of the licenses with a money back guarantee. &#x60;null&#x60; when no license of the product has one. |  |
|**revenue** | [**List&lt;Revenue&gt;**](Revenue.md) | Revenue in each currency licenses were sold in, from the one with the most licenses sold. Amounts aren&#39;t converted between currencies. |  |
|**activationsByVersion** | [**List&lt;ProductStatsActivationsByVersionInner&gt;**](ProductStatsActivationsByVersionInner.md) | Successful activations of the licenses of the product each day, per version of the application, from the most recent one. |  |
|**activeMachinesByVersion** | [**List&lt;ProductStatsActiveMachinesByVersionInner&gt;**](ProductStatsActiveMachinesByVersionInner.md) | Number of active machines running each version of the application, from the most recent one. |  |
|**activeMachinesByPlatform** | [**List&lt;ProductStatsActiveMachinesByPlatformInner&gt;**](ProductStatsActiveMachinesByPlatformInner.md) | Number of active machines on each platform, from the one with the most machines. |  |



