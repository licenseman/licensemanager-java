

# LicenseToken


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**license** | **String** | JWT signed with the Ed25519 key of the product&#39;s organization (&#x60;alg: EdDSA&#x60;, &#x60;kid&#x60;: id of the key). Its claims:  - &#x60;iss&#x60;: name of the organization. It changes when the organization is renamed: check &#x60;aud&#x60; rather than &#x60;iss&#x60;. - &#x60;aud&#x60;: id of the product. Test and live products share the organization&#39;s key, so check &#x60;aud&#x60; to refuse the tokens of a test product. - &#x60;sub&#x60;: license key. - &#x60;fp&#x60;: fingerprint of the machine. - &#x60;mv&#x60;: the license&#39;s &#x60;maxVersion.version&#x60;, like &#x60;\&quot;2.3\&quot;&#x60;, so the application can check the versions it updates to offline. &#x60;null&#x60; when it allows every version. - &#x60;iat&#x60;: when the token was issued. - &#x60;nbf&#x60;: two hours before &#x60;iat&#x60;, so machines whose clock is behind accept the token. - &#x60;exp&#x60;: the license&#39;s &#x60;maxOfflineDurationSeconds&#x60; after &#x60;iat&#x60;, or when the license expires if that&#39;s sooner. |  |



