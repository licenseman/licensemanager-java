

# PortalSettings


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**enabled** | **Boolean** | Whether customers can use the customer portal. When disabled, it answers &#x60;404&#x60;. |  |
|**brandColor** | **String** | Background of the portal&#39;s side panel, as &#x60;#rrggbb&#x60;, stored lower cased. &#x60;null&#x60; for the default color. |  |
|**accentColor** | **String** | Color of the portal&#39;s inputs and buttons, as &#x60;#rrggbb&#x60;, stored lower cased. &#x60;null&#x60; for the default color. |  |
|**returnDomains** | **List&lt;String&gt;** | Domains the portal&#39;s &#x60;return_url&#x60; query parameter may point to, their subdomains included. Other return URLs are ignored, in favor of the product&#39;s &#x60;websiteUrl&#x60;. |  |



