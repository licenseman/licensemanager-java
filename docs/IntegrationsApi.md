# IntegrationsApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**checkIntegration**](IntegrationsApi.md#checkIntegration) | **POST** /v1/integrations/{id}/check | Check an integration |
| [**connectStripe**](IntegrationsApi.md#connectStripe) | **PUT** /v1/products/{productId}/integrations/stripe | Connect Stripe |
| [**createStripeMapping**](IntegrationsApi.md#createStripeMapping) | **POST** /v1/products/{productId}/integrations/stripe/mappings | Map a Stripe price to a policy |
| [**deleteStripeMapping**](IntegrationsApi.md#deleteStripeMapping) | **DELETE** /v1/integration-mappings/{id} | Delete a mapping |
| [**disconnectIntegration**](IntegrationsApi.md#disconnectIntegration) | **DELETE** /v1/integrations/{id} | Disconnect an integration |
| [**getStripeIntegration**](IntegrationsApi.md#getStripeIntegration) | **GET** /v1/products/{productId}/integrations/stripe | Get the Stripe integration of a product |
| [**listStripePrices**](IntegrationsApi.md#listStripePrices) | **GET** /v1/integrations/{id}/stripe/prices | List the Stripe prices of an integration |
| [**updateStripeMapping**](IntegrationsApi.md#updateStripeMapping) | **PATCH** /v1/integration-mappings/{id} | Change the policy of a mapping |


<a id="checkIntegration"></a>
# **checkIntegration**
> Integration checkIntegration(id).execute();

Check an integration

Checks right away, as done every day, that the API key still works and can manage the webhook endpoint, which is pointed at the server&#39;s webhook URL again (or created again when it was deleted). Updates the status. Doesn&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:update&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.IntegrationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    IntegrationsApi apiInstance = new IntegrationsApi(defaultClient);
    String id = "i8Fz4QnRt"; // String | 
    try {
      Integration result = apiInstance.checkIntegration(id)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling IntegrationsApi#checkIntegration");
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

[**Integration**](Integration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Checked integration |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Integration not found |  -  |
| **409** | &#x60;webhook_url_unreachable&#x60;: Stripe can&#39;t reach the server&#39;s webhook URL |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
| **502** | &#x60;provider_unavailable&#x60;: Stripe couldn&#39;t be reached |  -  |

<a id="connectStripe"></a>
# **connectStripe**
> StripeIntegration connectStripe(productId, connectStripe).execute();

Connect Stripe

Connects the Stripe account of the API key for the organization&#39;s products of the product&#39;s mode, or replaces the key of the existing connection. Checks the key works and has the required permissions, then creates a webhook endpoint on the account, telling the app about payments. Doesn&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:create&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.IntegrationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    IntegrationsApi apiInstance = new IntegrationsApi(defaultClient);
    String productId = "x7Kp2QaZ"; // String | 
    ConnectStripe connectStripe = new ConnectStripe(); // ConnectStripe | 
    try {
      StripeIntegration result = apiInstance.connectStripe(productId, connectStripe)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling IntegrationsApi#connectStripe");
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
| **connectStripe** | [**ConnectStripe**](ConnectStripe.md)|  | |

### Return type

[**StripeIntegration**](StripeIntegration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Stripe integration |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **409** | &#x60;webhook_url_unreachable&#x60;: Stripe can&#39;t reach the server&#39;s webhook URL |  -  |
| **422** | &#x60;validation_error&#x60;: invalid body. &#x60;invalid_api_key&#x60;: not a Stripe secret or restricted key, or Stripe rejected it. &#x60;key_mode_mismatch&#x60;: a test mode key for a live product, or the opposite. &#x60;missing_permission&#x60;: the key lacks required permissions, listed in the message |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
| **502** | &#x60;provider_unavailable&#x60;: Stripe couldn&#39;t be reached |  -  |

<a id="createStripeMapping"></a>
# **createStripeMapping**
> IntegrationMapping createStripeMapping(productId, createIntegrationMapping).execute();

Map a Stripe price to a policy

Paying the price then creates licenses of the product with the policy: one per unit bought. Doesn&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:update&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.IntegrationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    IntegrationsApi apiInstance = new IntegrationsApi(defaultClient);
    String productId = "x7Kp2QaZ"; // String | 
    CreateIntegrationMapping createIntegrationMapping = new CreateIntegrationMapping(); // CreateIntegrationMapping | 
    try {
      IntegrationMapping result = apiInstance.createStripeMapping(productId, createIntegrationMapping)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling IntegrationsApi#createStripeMapping");
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
| **createIntegrationMapping** | [**CreateIntegrationMapping**](CreateIntegrationMapping.md)|  | |

### Return type

[**IntegrationMapping**](IntegrationMapping.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created mapping |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | &#x60;not_found&#x60;: product not found. &#x60;policy_not_found&#x60;: the product has no policy with this &#x60;policyId&#x60;. &#x60;price_not_found&#x60;: the Stripe account has no price with this &#x60;stripePriceId&#x60; |  -  |
| **409** | &#x60;not_connected&#x60;: Stripe isn&#39;t connected in the product&#39;s mode. &#x60;price_mapped&#x60;: the price already creates licenses of a product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid body. &#x60;price_unusable&#x60;: the price is archived, or isn&#39;t a one-time price |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
| **502** | &#x60;provider_unavailable&#x60;: Stripe couldn&#39;t be reached |  -  |

<a id="deleteStripeMapping"></a>
# **deleteStripeMapping**
> deleteStripeMapping(id).execute();

Delete a mapping

Paying the price no longer creates licenses. The licenses it created stay. Doesn&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:update&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.IntegrationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    IntegrationsApi apiInstance = new IntegrationsApi(defaultClient);
    String id = "i8Fz4QnRt"; // String | 
    try {
      apiInstance.deleteStripeMapping(id)
            .execute();
    } catch (ApiException e) {
      System.err.println("Exception when calling IntegrationsApi#deleteStripeMapping");
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
| **404** | Mapping not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="disconnectIntegration"></a>
# **disconnectIntegration**
> disconnectIntegration(id).execute();

Disconnect an integration

Deletes the webhook endpoint from the Stripe account first, then the integration with its mappings, for every product. The endpoint is skipped when it&#39;s already gone or the key no longer works; otherwise, when it can&#39;t be deleted, the integration is kept. The licenses it created stay. Revoke the API key in Stripe afterwards. Doesn&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:delete&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.IntegrationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    IntegrationsApi apiInstance = new IntegrationsApi(defaultClient);
    String id = "i8Fz4QnRt"; // String | 
    try {
      apiInstance.disconnectIntegration(id)
            .execute();
    } catch (ApiException e) {
      System.err.println("Exception when calling IntegrationsApi#disconnectIntegration");
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
| **204** | Disconnected |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Integration not found |  -  |
| **422** | &#x60;missing_permission&#x60;: the key can&#39;t delete the webhook endpoint |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
| **502** | &#x60;provider_unavailable&#x60;: Stripe couldn&#39;t be reached |  -  |

<a id="getStripeIntegration"></a>
# **getStripeIntegration**
> StripeIntegration getStripeIntegration(productId).execute();

Get the Stripe integration of a product

The organization connects one Stripe account for its live products, and one in test mode for its test products. Its mappings tell which Stripe prices create licenses of the product. Doesn&#39;t accept tokens: only API keys and sessions.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.IntegrationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    IntegrationsApi apiInstance = new IntegrationsApi(defaultClient);
    String productId = "x7Kp2QaZ"; // String | 
    try {
      StripeIntegration result = apiInstance.getStripeIntegration(productId)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling IntegrationsApi#getStripeIntegration");
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

### Return type

[**StripeIntegration**](StripeIntegration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Stripe integration |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="listStripePrices"></a>
# **listStripePrices**
> ListStripePrices200Response listStripePrices(id).execute();

List the Stripe prices of an integration

Active one-time prices of active products of the Stripe account, the ones that can be mapped, up to 500. Doesn&#39;t accept tokens: only API keys and sessions.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.IntegrationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    IntegrationsApi apiInstance = new IntegrationsApi(defaultClient);
    String id = "i8Fz4QnRt"; // String | 
    try {
      ListStripePrices200Response result = apiInstance.listStripePrices(id)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling IntegrationsApi#listStripePrices");
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

[**ListStripePrices200Response**](ListStripePrices200Response.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Prices |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Integration not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
| **502** | &#x60;provider_unavailable&#x60;: Stripe couldn&#39;t be reached, or refused the request |  -  |

<a id="updateStripeMapping"></a>
# **updateStripeMapping**
> IntegrationMapping updateStripeMapping(id, updateIntegrationMapping).execute();

Change the policy of a mapping

Only affects the licenses created afterwards. Doesn&#39;t accept tokens: only API keys and sessions.  **Required role permission**: &#x60;integration:update&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.IntegrationsApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    IntegrationsApi apiInstance = new IntegrationsApi(defaultClient);
    String id = "i8Fz4QnRt"; // String | 
    UpdateIntegrationMapping updateIntegrationMapping = new UpdateIntegrationMapping(); // UpdateIntegrationMapping | 
    try {
      IntegrationMapping result = apiInstance.updateStripeMapping(id, updateIntegrationMapping)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling IntegrationsApi#updateStripeMapping");
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
| **updateIntegrationMapping** | [**UpdateIntegrationMapping**](UpdateIntegrationMapping.md)|  | |

### Return type

[**IntegrationMapping**](IntegrationMapping.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated mapping |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | &#x60;not_found&#x60;: mapping not found. &#x60;policy_not_found&#x60;: its product has no policy with this &#x60;policyId&#x60; |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

