

# LicenseStats


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**from** | **LocalDate** | First day covered, in UTC. |  |
|**to** | **LocalDate** | Last day covered, in UTC: today. |  |
|**days** | **List&lt;LocalDate&gt;** | The 90 days covered, from the oldest one, in UTC. |  |
|**activationsByMachine** | [**List&lt;LicenseStatsActivationsByMachineInner&gt;**](LicenseStatsActivationsByMachineInner.md) | Machines that activated the license in the period, from the one with the most activations. |  |
|**activationsByVersion** | [**List&lt;LicenseStatsActivationsByVersionInner&gt;**](LicenseStatsActivationsByVersionInner.md) | Versions of the application that activated the license in the period, from the most recent one. |  |



