# MachinesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**deactivateMachine**](MachinesApi.md#deactivateMachine) | **POST** /v1/machines/{id}/deactivate | Deactivate a machine |
| [**getMachine**](MachinesApi.md#getMachine) | **GET** /v1/machines/{id} | Get a machine |
| [**listMachines**](MachinesApi.md#listMachines) | **GET** /v1/licenses/{licenseId}/machines | List the machines of a license |


<a id="deactivateMachine"></a>
# **deactivateMachine**
> Machine deactivateMachine(id).execute();

Deactivate a machine

The machine no longer counts as using the license, freeing its place when the license has a maximum number of machines. Validating the license key on the machine activates it again, unless the license is on its maximum number of machines by then. Deactivating a deactivated machine does nothing.  The license token &#x60;validateKey&#x60; returned to the machine isn&#39;t revoked: the application can keep running offline until it expires. Machines can&#39;t be deleted: they&#39;re deleted with their license.  **Token access**: customer, license, machine tokens with the &#x60;machine:write&#x60; permission (or the matching write one). A token reaches the machine it&#39;s scoped to, or the machines of its license or customer.  **Required role permission**: &#x60;machine:deactivate&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.MachinesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: token
    HttpBearerAuth token = (HttpBearerAuth) defaultClient.getAuthentication("token");
    token.setBearerToken("BEARER TOKEN");

    MachinesApi apiInstance = new MachinesApi(defaultClient);
    String id = "m9Tq3VhD"; // String | 
    try {
      Machine result = apiInstance.deactivateMachine(id)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MachinesApi#deactivateMachine");
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

[**Machine**](Machine.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Deactivated machine |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Machine not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="getMachine"></a>
# **getMachine**
> Machine getMachine(id).execute();

Get a machine

**Token access**: customer, license, machine tokens with the &#x60;machine:read&#x60; permission (or the matching write one). A token reaches the machine it&#39;s scoped to, or the machines of its license or customer.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.MachinesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: token
    HttpBearerAuth token = (HttpBearerAuth) defaultClient.getAuthentication("token");
    token.setBearerToken("BEARER TOKEN");

    MachinesApi apiInstance = new MachinesApi(defaultClient);
    String id = "m9Tq3VhD"; // String | 
    try {
      Machine result = apiInstance.getMachine(id)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MachinesApi#getMachine");
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

[**Machine**](Machine.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Machine |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Machine not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="listMachines"></a>
# **listMachines**
> MachineList listMachines(licenseId).page(page).pageSize(pageSize).sort(sort).search(search).fingerprint(fingerprint).status(status).execute();

List the machines of a license

**Token access**: customer, license tokens with the &#x60;machine:read&#x60; permission (or the matching write one). A token reaches the license it&#39;s scoped to, or the licenses of its customer.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.MachinesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: token
    HttpBearerAuth token = (HttpBearerAuth) defaultClient.getAuthentication("token");
    token.setBearerToken("BEARER TOKEN");

    MachinesApi apiInstance = new MachinesApi(defaultClient);
    String licenseId = "l3Nv8KwB"; // String | 
    Integer page = 1; // Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
    Integer pageSize = 20; // Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
    String sort = "name"; // String | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
    String search = "macbook"; // String | Case-insensitive text the fingerprint or name contains.
    String fingerprint = "4c:32:75:8f:9a:1e"; // String | Only returns the machine with this exact fingerprint.
    String status = "active"; // String | Only returns the machines with this status.
    try {
      MachineList result = apiInstance.listMachines(licenseId)
            .page(page)
            .pageSize(pageSize)
            .sort(sort)
            .search(search)
            .fingerprint(fingerprint)
            .status(status)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling MachinesApi#listMachines");
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
| **licenseId** | **String**|  | |
| **page** | **Integer**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **pageSize** | **Integer**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **String**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to -createdAt] [enum: name, -name, platform, -platform, createdAt, -createdAt, updatedAt, -updatedAt] |
| **search** | **String**| Case-insensitive text the fingerprint or name contains. | [optional] |
| **fingerprint** | **String**| Only returns the machine with this exact fingerprint. | [optional] |
| **status** | **String**| Only returns the machines with this status. | [optional] [enum: active, deactivated] |

### Return type

[**MachineList**](MachineList.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the machines of the license |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | License not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

