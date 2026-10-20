

# LicenseMaxVersion

Latest version of the product the license can use: its hard-coded `version`, else the versions released before its locks. All `null` when it can use every version.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**version** | **String** | Hard-coded latest version, taking precedence over &#x60;lockMajorAt&#x60; and &#x60;lockMinorAt&#x60;. &#x60;\&quot;2\&quot;&#x60; allows every 2.y.z version: its minor versions and bug fixes. &#x60;\&quot;2.3\&quot;&#x60; allows every 2.3.z version: its bug fixes. &#x60;null&#x60; when it&#39;s not hard-coded. |  |
|**lockMajorAt** | **OffsetDateTime** | When the major version of the license locks: it then only gets the minor versions and bug fixes of the major version released by then. Once reached, within the hour, the major version of the latest stable release by then is hard-coded in &#x60;version&#x60;, unless a version already is, and the lock is cleared. A lock reached before any stable release is cleared without hard-coding anything. &#x60;null&#x60; when it&#39;s never locked. |  |
|**lockMinorAt** | **OffsetDateTime** | When the minor version of the license locks: it then only gets the bug fixes of the minor version released by then, within the hard-coded major version when there&#39;s one. Never before &#x60;lockMajorAt&#x60;; without it, the major version locks along with the minor version. Once reached, within the hour, the major and minor version of the latest stable release by then is hard-coded in &#x60;version&#x60;, unless a minor version already is, and the lock is cleared. A lock reached before any matching stable release is cleared without hard-coding anything. &#x60;null&#x60; when it&#39;s never locked. |  |



