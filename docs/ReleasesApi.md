# ReleasesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createRelease**](ReleasesApi.md#createRelease) | **POST** /v1/products/{productId}/releases | Create a release |
| [**deleteRelease**](ReleasesApi.md#deleteRelease) | **DELETE** /v1/releases/{id} | Delete a release |
| [**getRelease**](ReleasesApi.md#getRelease) | **GET** /v1/releases/{id} | Get a release |
| [**listReleases**](ReleasesApi.md#listReleases) | **GET** /v1/products/{productId}/releases | List the releases of a product |
| [**updateRelease**](ReleasesApi.md#updateRelease) | **PATCH** /v1/releases/{id} | Update a release |


<a id="createRelease"></a>
# **createRelease**
> Release createRelease(productId, createRelease).execute();

Create a release

Releases don&#39;t restrict which versions &#x60;validateKey&#x60; accepts: a machine can run a version without a release. They give the &#x60;latestAllowedVersion&#x60; of its &#x60;version_not_allowed&#x60; errors, among the stable releases already released, and the number of active machines running each version.  **Required role permission**: &#x60;release:create&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.ReleasesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    ReleasesApi apiInstance = new ReleasesApi(defaultClient);
    String productId = "x7Kp2QaZ"; // String | 
    CreateRelease createRelease = new CreateRelease(); // CreateRelease | 
    try {
      Release result = apiInstance.createRelease(productId, createRelease)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ReleasesApi#createRelease");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **productId** | **String**|  | |
| **createRelease** | [**CreateRelease**](CreateRelease.md)|  | |

### Return type

[**Release**](Release.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created release |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **409** | &#x60;version_taken&#x60;: version already released for the product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="deleteRelease"></a>
# **deleteRelease**
> deleteRelease(id).execute();

Delete a release

**Required role permission**: &#x60;release:delete&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.ReleasesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    ReleasesApi apiInstance = new ReleasesApi(defaultClient);
    String id = "r4Lm8VwX"; // String | 
    try {
      apiInstance.deleteRelease(id)
            .execute();
    } catch (ApiException e) {
      System.err.println("Exception when calling ReleasesApi#deleteRelease");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **id** | **String**|  | |

### Return type

null (empty response body)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Deleted |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Release not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="getRelease"></a>
# **getRelease**
> Release getRelease(id).execute();

Get a release

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.ReleasesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    ReleasesApi apiInstance = new ReleasesApi(defaultClient);
    String id = "r4Lm8VwX"; // String | 
    try {
      Release result = apiInstance.getRelease(id)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ReleasesApi#getRelease");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **id** | **String**|  | |

### Return type

[**Release**](Release.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Release |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Release not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="listReleases"></a>
# **listReleases**
> ReleaseList listReleases(productId).page(page).pageSize(pageSize).sort(sort).search(search).releasedFrom(releasedFrom).releasedTo(releasedTo).activeMachineCount(activeMachineCount).activeMachineCountMin(activeMachineCountMin).activeMachineCountMax(activeMachineCountMax).execute();

List the releases of a product

Sorting by &#x60;version&#x60; compares the major, minor and patch numbers as numbers, then puts a pre-release before its stable release. Pre-releases of the same version compare as text, unlike semantic versioning: &#x60;2.0.0-beta.10&#x60; comes before &#x60;2.0.0-beta.2&#x60;. Build metadata is ignored.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.ReleasesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    ReleasesApi apiInstance = new ReleasesApi(defaultClient);
    String productId = "x7Kp2QaZ"; // String | 
    Integer page = 1; // Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
    Integer pageSize = 20; // Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
    String sort = "version"; // String | Field to sort by, prefixed with `-` for descending order. Defaults to `-version`.
    String search = "2.3"; // String | Case-insensitive text the version contains.
    OffsetDateTime releasedFrom = OffsetDateTime.parse("2026-01-01T00:00:00.000Z"); // OffsetDateTime | Only returns the releases released at or after this date.
    OffsetDateTime releasedTo = OffsetDateTime.parse("2026-02-01T00:00:00.000Z"); // OffsetDateTime | Only returns the releases released at or before this date.
    Integer activeMachineCount = 1; // Integer | Only returns the releases running on exactly this number of active machines.
    Integer activeMachineCountMin = 1; // Integer | Only returns the releases running on at least this number of active machines.
    Integer activeMachineCountMax = 1; // Integer | Only returns the releases running on at most this number of active machines.
    try {
      ReleaseList result = apiInstance.listReleases(productId)
            .page(page)
            .pageSize(pageSize)
            .sort(sort)
            .search(search)
            .releasedFrom(releasedFrom)
            .releasedTo(releasedTo)
            .activeMachineCount(activeMachineCount)
            .activeMachineCountMin(activeMachineCountMin)
            .activeMachineCountMax(activeMachineCountMax)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ReleasesApi#listReleases");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **productId** | **String**|  | |
| **page** | **Integer**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **pageSize** | **Integer**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **String**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-version&#x60;. | [optional] [default to -version] [enum: version, -version, releasedAt, -releasedAt, createdAt, -createdAt, activeMachineCount, -activeMachineCount] |
| **search** | **String**| Case-insensitive text the version contains. | [optional] |
| **releasedFrom** | **OffsetDateTime**| Only returns the releases released at or after this date. | [optional] |
| **releasedTo** | **OffsetDateTime**| Only returns the releases released at or before this date. | [optional] |
| **activeMachineCount** | **Integer**| Only returns the releases running on exactly this number of active machines. | [optional] |
| **activeMachineCountMin** | **Integer**| Only returns the releases running on at least this number of active machines. | [optional] |
| **activeMachineCountMax** | **Integer**| Only returns the releases running on at most this number of active machines. | [optional] |

### Return type

[**ReleaseList**](ReleaseList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the releases of the product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="updateRelease"></a>
# **updateRelease**
> Release updateRelease(id, updateRelease).execute();

Update a release

**Required role permission**: &#x60;release:update&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.ReleasesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    ReleasesApi apiInstance = new ReleasesApi(defaultClient);
    String id = "r4Lm8VwX"; // String | 
    UpdateRelease updateRelease = new UpdateRelease(); // UpdateRelease | 
    try {
      Release result = apiInstance.updateRelease(id, updateRelease)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ReleasesApi#updateRelease");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **id** | **String**|  | |
| **updateRelease** | [**UpdateRelease**](UpdateRelease.md)|  | |

### Return type

[**Release**](Release.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated release |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Release not found |  -  |
| **409** | &#x60;version_taken&#x60;: version already released for the product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

