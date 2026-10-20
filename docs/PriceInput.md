

# PriceInput

Price paid for a license. Send `null` instead when it's unknown, which leaves the license out of the revenue stats. Left out on creation, it's `null`.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**amount** | **BigDecimal** | Amount in major units of the currency: &#x60;49.99&#x60; for $49.99, &#x60;5000&#x60; for ¥5,000. &#x60;0&#x60; for a free license. At most as many decimals as the currency&#39;s minor unit: 2 for USD, 0 for JPY. |  |
|**currency** | **String** | ISO 4217 code of the currency, in upper case. |  |



