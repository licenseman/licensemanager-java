# LicensesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createLicense**](LicensesApi.md#createLicense) | **POST** /v1/products/{productId}/licenses | Create a license |
| [**deleteLicense**](LicensesApi.md#deleteLicense) | **DELETE** /v1/licenses/{id} | Delete a license |
| [**getLicense**](LicensesApi.md#getLicense) | **GET** /v1/licenses/{id} | Get a license |
| [**getLicenseStats**](LicensesApi.md#getLicenseStats) | **GET** /v1/licenses/{id}/stats | Get the stats of a license |
| [**getSigningKey**](LicensesApi.md#getSigningKey) | **GET** /v1/signing-key | Get the organization&#39;s signing key |
| [**listCustomerLicenses**](LicensesApi.md#listCustomerLicenses) | **GET** /v1/customers/{customerId}/licenses | List the licenses of a customer |
| [**listLicenses**](LicensesApi.md#listLicenses) | **GET** /v1/products/{productId}/licenses | List the licenses of a product |
| [**sendLicenseKeys**](LicensesApi.md#sendLicenseKeys) | **POST** /v1/licenses/send-keys | Email license keys to their customers |
| [**updateLicense**](LicensesApi.md#updateLicense) | **PATCH** /v1/licenses/{id} | Update a license |
| [**validateKey**](LicensesApi.md#validateKey) | **POST** /v1/products/{productId}/validate-key | Validate a license key |


<a id="createLicense"></a>
# **createLicense**
> License createLicense(productId, createLicense).execute();

Create a license

Without a &#x60;key&#x60;, the license gets a random one, like &#x60;7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF&#x60;: 5 groups of 5 characters separated by dashes, each character an upper case letter or a digit other than &#x60;O&#x60;, &#x60;0&#x60;, &#x60;I&#x60; and &#x60;1&#x60;. That&#39;s 32 possible characters encoding 5 bits each, for 125 random bits.  Without a &#x60;policyId&#x60;, the license follows the product&#39;s default policy.  Without an &#x60;expiresAt&#x60;, the license expires after the duration of its policy, or never when the policy has none. &#x60;expiresAt: null&#x60; makes it never expire.  Without a &#x60;price&#x60;, the price paid for the license is unknown: it&#39;s left out of the revenue stats.  The values of &#x60;maxVersion&#x60; left out are taken from the max version of the policy: its hard-coded version, or the times after the creation of the license its versions lock.  The license belongs to the product&#39;s customer with the given &#x60;email&#x60;, which is created when there&#39;s none.  With &#x60;sendKey: true&#x60;, the key is emailed to the customer once the license is created.  The license copies the settings of its policy when it&#39;s created: later changes to the policy don&#39;t affect it. Its key, policy and customer can&#39;t be changed afterwards.  **Required role permission**: &#x60;license:create&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.LicensesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    LicensesApi apiInstance = new LicensesApi(defaultClient);
    String productId = "x7Kp2QaZ"; // String | 
    CreateLicense createLicense = new CreateLicense(); // CreateLicense | 
    try {
      License result = apiInstance.createLicense(productId, createLicense)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LicensesApi#createLicense");
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
| **createLicense** | [**CreateLicense**](CreateLicense.md)|  | |

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created license |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | &#x60;not_found&#x60;: product not found. &#x60;policy_not_found&#x60;: the product has no policy with this &#x60;policyId&#x60; |  -  |
| **409** | &#x60;key_taken&#x60;: key already used by another license of the product |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="deleteLicense"></a>
# **deleteLicense**
> deleteLicense(id).execute();

Delete a license

Deletes the license along with its deactivated machines. A license used on active machines can&#39;t be deleted: deactivate them first. The tokens scoped to the license or its machines stop working, but the license tokens &#x60;validateKey&#x60; already returned stay valid until they expire. Its events can no longer be listed.  **Required role permission**: &#x60;license:delete&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.LicensesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    LicensesApi apiInstance = new LicensesApi(defaultClient);
    String id = "l3Nv8KwB"; // String | 
    try {
      apiInstance.deleteLicense(id)
            .execute();
    } catch (ApiException e) {
      System.err.println("Exception when calling LicensesApi#deleteLicense");
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
| **404** | License not found |  -  |
| **409** | &#x60;license_in_use&#x60;: the license is used on active machines |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="getLicense"></a>
# **getLicense**
> License getLicense(id).execute();

Get a license

**Token access**: customer, license, machine tokens with the &#x60;license:read&#x60; permission (or the matching write one). A token reaches the license it&#39;s scoped to, the licenses of its customer, or the license of its machine.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.LicensesApi;

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

    LicensesApi apiInstance = new LicensesApi(defaultClient);
    String id = "l3Nv8KwB"; // String | 
    try {
      License result = apiInstance.getLicense(id)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LicensesApi#getLicense");
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

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | License |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | License not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="getLicenseStats"></a>
# **getLicenseStats**
> LicenseStats getLicenseStats(id).execute();

Get the stats of a license

Daily number of successful activations of the license over the last 90 days, today included, per machine and per version of the application. Days are in UTC.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.LicensesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    LicensesApi apiInstance = new LicensesApi(defaultClient);
    String id = "l3Nv8KwB"; // String | 
    try {
      LicenseStats result = apiInstance.getLicenseStats(id)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LicensesApi#getLicenseStats");
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

[**LicenseStats**](LicenseStats.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Stats of the license |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | License not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="getSigningKey"></a>
# **getSigningKey**
> SigningKey getSigningKey().execute();

Get the organization&#39;s signing key

Public key verifying the license tokens returned by &#x60;validateKey&#x60;, to embed in applications. Created the first time it&#39;s needed, and never rotated. The organization has a single key, signing the tokens of its live and test products alike: check the tokens&#39; &#x60;aud&#x60; to tell them apart.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.LicensesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    LicensesApi apiInstance = new LicensesApi(defaultClient);
    try {
      SigningKey result = apiInstance.getSigningKey()
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LicensesApi#getSigningKey");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**SigningKey**](SigningKey.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Signing key |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="listCustomerLicenses"></a>
# **listCustomerLicenses**
> LicenseList listCustomerLicenses(customerId).page(page).pageSize(pageSize).sort(sort).search(search).key(key).policyId(policyId).machineVersion(machineVersion).status(status).createdFrom(createdFrom).createdTo(createdTo).lastActivatedFrom(lastActivatedFrom).lastActivatedTo(lastActivatedTo).neverActivated(neverActivated).expiresFrom(expiresFrom).expiresTo(expiresTo).neverExpires(neverExpires).currency(currency).price(price).priceMin(priceMin).priceMax(priceMax).hasPrice(hasPrice).execute();

List the licenses of a customer

Sorting by &#x60;lastActivatedAt&#x60; puts the licenses never activated last in both orders. Sorting by &#x60;price&#x60; compares the amounts whatever their currency, and puts the licenses without a price last in both orders.  **Token access**: customer tokens with the &#x60;license:read&#x60; permission (or the matching write one). A customer token reaches its own licenses.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.LicensesApi;

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

    LicensesApi apiInstance = new LicensesApi(defaultClient);
    String customerId = "c9Wd3RtE"; // String | 
    Integer page = 1; // Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
    Integer pageSize = 20; // Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
    String sort = "key"; // String | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
    String search = "X9ZPA"; // String | Case-insensitive text the key contains.
    String key = "7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF"; // String | Only returns the license with this exact key, case included. Keys of test products start with `TEST-`.
    String policyId = "p4Rt8LmQ"; // String | Only returns the licenses following this policy.
    String machineVersion = "2.3.1"; // String | Only returns the licenses with at least one active machine running this version of the product.
    LicenseStatus status = LicenseStatus.fromValue("active"); // LicenseStatus | Only returns the licenses with this status.
    OffsetDateTime createdFrom = OffsetDateTime.parse("2026-01-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses created at or after this date.
    OffsetDateTime createdTo = OffsetDateTime.parse("2026-02-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses created at or before this date.
    OffsetDateTime lastActivatedFrom = OffsetDateTime.parse("2026-01-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses last activated at or after this date. Licenses never activated are left out.
    OffsetDateTime lastActivatedTo = OffsetDateTime.parse("2026-02-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses last activated at or before this date. Licenses never activated are left out.
    String neverActivated = "true"; // String | `true` only returns the licenses never activated, `false` only the ones activated at least once.
    OffsetDateTime expiresFrom = OffsetDateTime.parse("2026-01-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses expiring at or after this date. Licenses that never expire are left out.
    OffsetDateTime expiresTo = OffsetDateTime.parse("2026-02-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses expiring at or before this date. Licenses that never expire are left out.
    String neverExpires = "true"; // String | `true` only returns the licenses that never expire, `false` only the ones with an expiration date.
    String currency = "USD"; // String | Only returns the licenses paid in this currency.
    BigDecimal price = new BigDecimal("49.99"); // BigDecimal | Only returns the licenses paid exactly this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
    BigDecimal priceMin = new BigDecimal("49.99"); // BigDecimal | Only returns the licenses paid at least this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
    BigDecimal priceMax = new BigDecimal("49.99"); // BigDecimal | Only returns the licenses paid at most this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
    String hasPrice = "true"; // String | `true` only returns the licenses with a price, `false` only the ones without.
    try {
      LicenseList result = apiInstance.listCustomerLicenses(customerId)
            .page(page)
            .pageSize(pageSize)
            .sort(sort)
            .search(search)
            .key(key)
            .policyId(policyId)
            .machineVersion(machineVersion)
            .status(status)
            .createdFrom(createdFrom)
            .createdTo(createdTo)
            .lastActivatedFrom(lastActivatedFrom)
            .lastActivatedTo(lastActivatedTo)
            .neverActivated(neverActivated)
            .expiresFrom(expiresFrom)
            .expiresTo(expiresTo)
            .neverExpires(neverExpires)
            .currency(currency)
            .price(price)
            .priceMin(priceMin)
            .priceMax(priceMax)
            .hasPrice(hasPrice)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LicensesApi#listCustomerLicenses");
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
| **customerId** | **String**|  | |
| **page** | **Integer**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1] |
| **pageSize** | **Integer**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20] |
| **sort** | **String**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to -createdAt] [enum: key, -key, createdAt, -createdAt, expiresAt, -expiresAt, maxMachines, -maxMachines, maxOfflineDurationSeconds, -maxOfflineDurationSeconds, lastActivatedAt, -lastActivatedAt, lockMajorAt, -lockMajorAt, lockMinorAt, -lockMinorAt, updatedAt, -updatedAt, price, -price] |
| **search** | **String**| Case-insensitive text the key contains. | [optional] |
| **key** | **String**| Only returns the license with this exact key, case included. Keys of test products start with &#x60;TEST-&#x60;. | [optional] |
| **policyId** | **String**| Only returns the licenses following this policy. | [optional] |
| **machineVersion** | **String**| Only returns the licenses with at least one active machine running this version of the product. | [optional] |
| **status** | [**LicenseStatus**](.md)| Only returns the licenses with this status. | [optional] [enum: active, inactive, expired] |
| **createdFrom** | **OffsetDateTime**| Only returns the licenses created at or after this date. | [optional] |
| **createdTo** | **OffsetDateTime**| Only returns the licenses created at or before this date. | [optional] |
| **lastActivatedFrom** | **OffsetDateTime**| Only returns the licenses last activated at or after this date. Licenses never activated are left out. | [optional] |
| **lastActivatedTo** | **OffsetDateTime**| Only returns the licenses last activated at or before this date. Licenses never activated are left out. | [optional] |
| **neverActivated** | **String**| &#x60;true&#x60; only returns the licenses never activated, &#x60;false&#x60; only the ones activated at least once. | [optional] [enum: true, false] |
| **expiresFrom** | **OffsetDateTime**| Only returns the licenses expiring at or after this date. Licenses that never expire are left out. | [optional] |
| **expiresTo** | **OffsetDateTime**| Only returns the licenses expiring at or before this date. Licenses that never expire are left out. | [optional] |
| **neverExpires** | **String**| &#x60;true&#x60; only returns the licenses that never expire, &#x60;false&#x60; only the ones with an expiration date. | [optional] [enum: true, false] |
| **currency** | **String**| Only returns the licenses paid in this currency. | [optional] |
| **price** | **BigDecimal**| Only returns the licenses paid exactly this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **priceMin** | **BigDecimal**| Only returns the licenses paid at least this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **priceMax** | **BigDecimal**| Only returns the licenses paid at most this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **hasPrice** | **String**| &#x60;true&#x60; only returns the licenses with a price, &#x60;false&#x60; only the ones without. | [optional] [enum: true, false] |

### Return type

[**LicenseList**](LicenseList.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the licenses of the customer |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Customer not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="listLicenses"></a>
# **listLicenses**
> LicenseList listLicenses(productId).page(page).pageSize(pageSize).sort(sort).search(search).key(key).policyId(policyId).customerId(customerId).machineVersion(machineVersion).status(status).createdFrom(createdFrom).createdTo(createdTo).lastActivatedFrom(lastActivatedFrom).lastActivatedTo(lastActivatedTo).neverActivated(neverActivated).expiresFrom(expiresFrom).expiresTo(expiresTo).neverExpires(neverExpires).currency(currency).price(price).priceMin(priceMin).priceMax(priceMax).hasPrice(hasPrice).execute();

List the licenses of a product

Sorting by &#x60;lastActivatedAt&#x60; puts the licenses never activated last in both orders. Sorting by &#x60;price&#x60; compares the amounts whatever their currency, and puts the licenses without a price last in both orders.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.LicensesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    LicensesApi apiInstance = new LicensesApi(defaultClient);
    String productId = "x7Kp2QaZ"; // String | 
    Integer page = 1; // Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
    Integer pageSize = 20; // Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
    String sort = "key"; // String | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
    String search = "X9ZPA"; // String | Case-insensitive text the key contains.
    String key = "7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF"; // String | Only returns the license with this exact key, case included. Keys of test products start with `TEST-`.
    String policyId = "p4Rt8LmQ"; // String | Only returns the licenses following this policy.
    String customerId = "c9Wd3RtE"; // String | Only returns the licenses of this customer.
    String machineVersion = "2.3.1"; // String | Only returns the licenses with at least one active machine running this version of the product.
    LicenseStatus status = LicenseStatus.fromValue("active"); // LicenseStatus | Only returns the licenses with this status.
    OffsetDateTime createdFrom = OffsetDateTime.parse("2026-01-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses created at or after this date.
    OffsetDateTime createdTo = OffsetDateTime.parse("2026-02-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses created at or before this date.
    OffsetDateTime lastActivatedFrom = OffsetDateTime.parse("2026-01-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses last activated at or after this date. Licenses never activated are left out.
    OffsetDateTime lastActivatedTo = OffsetDateTime.parse("2026-02-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses last activated at or before this date. Licenses never activated are left out.
    String neverActivated = "true"; // String | `true` only returns the licenses never activated, `false` only the ones activated at least once.
    OffsetDateTime expiresFrom = OffsetDateTime.parse("2026-01-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses expiring at or after this date. Licenses that never expire are left out.
    OffsetDateTime expiresTo = OffsetDateTime.parse("2026-02-01T00:00:00.000Z"); // OffsetDateTime | Only returns the licenses expiring at or before this date. Licenses that never expire are left out.
    String neverExpires = "true"; // String | `true` only returns the licenses that never expire, `false` only the ones with an expiration date.
    String currency = "USD"; // String | Only returns the licenses paid in this currency.
    BigDecimal price = new BigDecimal("49.99"); // BigDecimal | Only returns the licenses paid exactly this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
    BigDecimal priceMin = new BigDecimal("49.99"); // BigDecimal | Only returns the licenses paid at least this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
    BigDecimal priceMax = new BigDecimal("49.99"); // BigDecimal | Only returns the licenses paid at most this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
    String hasPrice = "true"; // String | `true` only returns the licenses with a price, `false` only the ones without.
    try {
      LicenseList result = apiInstance.listLicenses(productId)
            .page(page)
            .pageSize(pageSize)
            .sort(sort)
            .search(search)
            .key(key)
            .policyId(policyId)
            .customerId(customerId)
            .machineVersion(machineVersion)
            .status(status)
            .createdFrom(createdFrom)
            .createdTo(createdTo)
            .lastActivatedFrom(lastActivatedFrom)
            .lastActivatedTo(lastActivatedTo)
            .neverActivated(neverActivated)
            .expiresFrom(expiresFrom)
            .expiresTo(expiresTo)
            .neverExpires(neverExpires)
            .currency(currency)
            .price(price)
            .priceMin(priceMin)
            .priceMax(priceMax)
            .hasPrice(hasPrice)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LicensesApi#listLicenses");
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
| **sort** | **String**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to -createdAt] [enum: key, -key, createdAt, -createdAt, expiresAt, -expiresAt, maxMachines, -maxMachines, maxOfflineDurationSeconds, -maxOfflineDurationSeconds, lastActivatedAt, -lastActivatedAt, lockMajorAt, -lockMajorAt, lockMinorAt, -lockMinorAt, updatedAt, -updatedAt, price, -price] |
| **search** | **String**| Case-insensitive text the key contains. | [optional] |
| **key** | **String**| Only returns the license with this exact key, case included. Keys of test products start with &#x60;TEST-&#x60;. | [optional] |
| **policyId** | **String**| Only returns the licenses following this policy. | [optional] |
| **customerId** | **String**| Only returns the licenses of this customer. | [optional] |
| **machineVersion** | **String**| Only returns the licenses with at least one active machine running this version of the product. | [optional] |
| **status** | [**LicenseStatus**](.md)| Only returns the licenses with this status. | [optional] [enum: active, inactive, expired] |
| **createdFrom** | **OffsetDateTime**| Only returns the licenses created at or after this date. | [optional] |
| **createdTo** | **OffsetDateTime**| Only returns the licenses created at or before this date. | [optional] |
| **lastActivatedFrom** | **OffsetDateTime**| Only returns the licenses last activated at or after this date. Licenses never activated are left out. | [optional] |
| **lastActivatedTo** | **OffsetDateTime**| Only returns the licenses last activated at or before this date. Licenses never activated are left out. | [optional] |
| **neverActivated** | **String**| &#x60;true&#x60; only returns the licenses never activated, &#x60;false&#x60; only the ones activated at least once. | [optional] [enum: true, false] |
| **expiresFrom** | **OffsetDateTime**| Only returns the licenses expiring at or after this date. Licenses that never expire are left out. | [optional] |
| **expiresTo** | **OffsetDateTime**| Only returns the licenses expiring at or before this date. Licenses that never expire are left out. | [optional] |
| **neverExpires** | **String**| &#x60;true&#x60; only returns the licenses that never expire, &#x60;false&#x60; only the ones with an expiration date. | [optional] [enum: true, false] |
| **currency** | **String**| Only returns the licenses paid in this currency. | [optional] |
| **price** | **BigDecimal**| Only returns the licenses paid exactly this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **priceMin** | **BigDecimal**| Only returns the licenses paid at least this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **priceMax** | **BigDecimal**| Only returns the licenses paid at most this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **hasPrice** | **String**| &#x60;true&#x60; only returns the licenses with a price, &#x60;false&#x60; only the ones without. | [optional] [enum: true, false] |

### Return type

[**LicenseList**](LicenseList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | One page of the licenses of the product |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | Product not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="sendLicenseKeys"></a>
# **sendLicenseKeys**
> sendLicenseKeys(sendLicenseKeys).execute();

Email license keys to their customers

Emails each customer the keys of its licenses among &#x60;ids&#x60;, with their expiration date: one email per customer, whatever their number of licenses. The licenses can belong to different products of the organization.  Test products only email the members of the organization, so testing never emails real customers: nothing is sent when a license of a test product belongs to a customer whose email isn&#39;t a member&#39;s.  **Required role permission**: &#x60;license:send&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.LicensesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    LicensesApi apiInstance = new LicensesApi(defaultClient);
    SendLicenseKeys sendLicenseKeys = new SendLicenseKeys(); // SendLicenseKeys | 
    try {
      apiInstance.sendLicenseKeys(sendLicenseKeys)
            .execute();
    } catch (ApiException e) {
      System.err.println("Exception when calling LicensesApi#sendLicenseKeys");
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
| **sendLicenseKeys** | [**SendLicenseKeys**](SendLicenseKeys.md)|  | |

### Return type

null (empty response body)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Keys emailed |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | &#x60;not_found&#x60;: one of the licenses wasn&#39;t found |  -  |
| **409** | &#x60;test_recipient_not_member&#x60;: a license of a test product belongs to a customer whose email isn&#39;t a member&#39;s of the organization |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="updateLicense"></a>
# **updateLicense**
> License updateLicense(id, updateLicense).execute();

Update a license

The key, policy and customer of a license can&#39;t be changed: sending them does nothing.  The changes apply to the next validations of the key, not to the license tokens &#x60;validateKey&#x60; already returned, which stay valid until they expire. Lowering &#x60;maxMachines&#x60; doesn&#39;t deactivate machines: the ones already active keep validating, and new ones are refused until enough are deactivated.  **Required role permission**: &#x60;license:update&#x60; when called with a session, granted by the member&#39;s role. API keys aren&#39;t limited by roles.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.auth.*;
import dev.licensemanager.models.*;
import dev.licensemanager.api.LicensesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");
    
    // Configure API key authorization: apiKey
    ApiKeyAuth apiKey = (ApiKeyAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //apiKey.setApiKeyPrefix("Token");

    LicensesApi apiInstance = new LicensesApi(defaultClient);
    String id = "l3Nv8KwB"; // String | 
    UpdateLicense updateLicense = new UpdateLicense(); // UpdateLicense | 
    try {
      License result = apiInstance.updateLicense(id, updateLicense)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LicensesApi#updateLicense");
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
| **updateLicense** | [**UpdateLicense**](UpdateLicense.md)|  | |

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated license |  -  |
| **401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
| **403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
| **404** | License not found |  -  |
| **422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
| **429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

<a id="validateKey"></a>
# **validateKey**
> LicenseToken validateKey(productId, validateKey).execute();

Validate a license key

Checks the license key of the product on a machine and returns a token the application can verify offline with the organization&#39;s public key. Doesn&#39;t need authentication.  The license must allow the &#x60;version&#x60;: up to its &#x60;maxVersion.version&#x60; when it has one, like &#x60;\&quot;2.3\&quot;&#x60; for every 2.3.z version and older. Its &#x60;maxVersion.lockMajorAt&#x60; and &#x60;maxVersion.lockMinorAt&#x60; are enforced once they hard-code &#x60;maxVersion.version&#x60;, within the hour they&#39;re reached. When it doesn&#39;t, the error&#39;s &#x60;latestAllowedVersion&#x60; is the latest release of the product the license allows, so the application can offer to install it.  The machine with the &#x60;fingerprint&#x60; is created when the license has none, and activated when it&#39;s deactivated, unless the license is already active on its maximum number of machines. A machine that&#39;s already active is never refused for the maximum number of machines, even when it was lowered below the number of active machines. Its &#x60;version&#x60;, and its &#x60;name&#x60; and &#x60;platform&#x60; when given, are updated: they can&#39;t be cleared.  The checks run in this order, and the first one failing answers: the license has expired, then it doesn&#39;t allow the version, then it&#39;s on its maximum number of machines. Each failure is recorded as a &#x60;license.validation_failed&#x60; event, except for keys that don&#39;t exist.  Changes to the license, like deactivating the machine or shortening its expiration, don&#39;t revoke the tokens already returned: the application only sees them when it validates its key again, at the latest when its token expires.

### Example
```java
// Import classes:
import dev.licensemanager.ApiClient;
import dev.licensemanager.ApiException;
import dev.licensemanager.Configuration;
import dev.licensemanager.models.*;
import dev.licensemanager.api.LicensesApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.licensemanager.dev");

    LicensesApi apiInstance = new LicensesApi(defaultClient);
    String productId = "x7Kp2QaZ"; // String | 
    ValidateKey validateKey = new ValidateKey(); // ValidateKey | 
    try {
      LicenseToken result = apiInstance.validateKey(productId, validateKey)
            .execute();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LicensesApi#validateKey");
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
| **validateKey** | [**ValidateKey**](ValidateKey.md)|  | |

### Return type

[**LicenseToken**](LicenseToken.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Signed license token |  -  |
| **402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period |  -  |
| **403** | &#x60;license_expired&#x60;: the license has expired. &#x60;version_not_allowed&#x60;: the license doesn&#39;t allow the version, with the &#x60;latestAllowedVersion&#x60;. &#x60;machine_limit_reached&#x60;: the license is already active on its maximum number of machines |  -  |
| **404** | &#x60;not_found&#x60;: the product doesn&#39;t exist, or has no license with this key |  -  |
| **422** | &#x60;validation_error&#x60;: invalid body |  -  |

