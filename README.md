# LicenseManager Java SDK

[![Maven Central](https://img.shields.io/maven-central/v/dev.licensemanager/licensemanager-java)](https://central.sonatype.com/artifact/dev.licensemanager/licensemanager-java)
[![Javadoc](https://javadoc.io/badge2/dev.licensemanager/licensemanager-java/javadoc.svg)](https://javadoc.io/doc/dev.licensemanager/licensemanager-java)
[![Publish](https://github.com/licenseman/licensemanager-java/actions/workflows/publish.yml/badge.svg)](https://github.com/licenseman/licensemanager-java/actions/workflows/publish.yml)
[![License](https://img.shields.io/github/license/licenseman/licensemanager-java)](https://github.com/licenseman/licensemanager-java/blob/main/LICENSE)
[![Documentation](https://img.shields.io/badge/docs-licensemanager.dev-blue)](https://licensemanager.dev/docs/sdks/java)

The official Java SDK for the [LicenseManager](https://licensemanager.dev) API: issue, manage and validate software licenses. Built on OkHttp and Gson, with a fluent request builder for each endpoint's optional parameters.

**[Documentation](https://licensemanager.dev/docs/sdks/java)** · **[API reference](https://api.licensemanager.dev/docs)** · **[Changelog](CHANGELOG.md)**

## Requirements

Java 8 or later.

## Installation

```xml
<!-- Maven -->
<dependency>
  <groupId>dev.licensemanager</groupId>
  <artifactId>licensemanager-java</artifactId>
  <version>LATEST_VERSION</version>
</dependency>

<!-- Gradle: implementation("dev.licensemanager:licensemanager-java:LATEST_VERSION") -->
```

## Usage

Create an API key in the LicenseManager app, then create a license after a sale:

```java
import dev.licensemanager.ApiClient;
import dev.licensemanager.api.LicensesApi;
import dev.licensemanager.model.CreateLicense;
import dev.licensemanager.model.License;

public class Example {
    public static void main(String[] args) throws Exception {
        ApiClient client = new ApiClient();
        client.setApiKey(System.getenv("LICENSEMANAGER_API_KEY"));
        LicensesApi licenses = new LicensesApi(client);

        CreateLicense createLicense = new CreateLicense()
            .email("jane@example.com");
        License license = licenses.createLicense("x7Kp2QaZ", createLicense).execute();
    }
}
```

And validate it from your application, which needs no API key:

```java
import dev.licensemanager.api.LicensesApi;
import dev.licensemanager.model.LicenseToken;
import dev.licensemanager.model.ValidateKey;

public class Example {
    public static void main(String[] args) throws Exception {
        LicensesApi licenses = new LicensesApi();

        ValidateKey validateKey = new ValidateKey()
            .key("7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF")
            .fingerprint("4c:32:75:8f:9a:1e")
            .version("1.4.2");
        LicenseToken licenseToken = licenses.validateKey("x7Kp2QaZ", validateKey).execute();
    }
}
```

## Authentication

Most endpoints take an organization API key: keep it on your servers. The endpoints your application calls directly, like validating a key, take no credentials or a token scoped to a customer, license or machine. See [authentication](https://licensemanager.dev/docs/api/authentication) and [scoped tokens](https://licensemanager.dev/docs/api/scoped-tokens).

```java
import dev.licensemanager.ApiClient;

ApiClient client = new ApiClient();
// With an API key, from your backend:
client.setApiKey(System.getenv("LICENSEMANAGER_API_KEY"));
// Or with a token scoped to a customer, license or machine:
client.setBearerToken(token);
```

## Errors

Failed requests answer an error with a stable `code` to branch on, listed for each endpoint in the [API reference](https://api.licensemanager.dev/docs). See [errors](https://licensemanager.dev/docs/api/errors).

```java
import dev.licensemanager.ApiException;

try {
    licenses.getLicense("l3Nv8KwB").execute();
} catch (ApiException error) {
    // The body is { "error": { "code", "message" } }.
    System.err.println(error.getCode() + " " + error.getResponseBody());
}
```

## Reference

Every method is documented, with its parameters and responses, in the [`docs`](docs) folder:

| Class | Methods |
| --- | --- |
| [`LicensesApi`](docs/LicensesApi.md) | `validateKey`, `listLicenses`, `createLicense`, `listCustomerLicenses`, `getLicense`, `deleteLicense`, `updateLicense`, `getLicenseStats`, `cancelLicense`, `sendLicenseKeys`, `getSigningKey` |
| [`PortalApi`](docs/PortalApi.md) | `getPortal`, `requestPortalLink`, `createPortalLink`, `sendPortalLink` |
| [`ProductsApi`](docs/ProductsApi.md) | `listProducts`, `createProduct`, `getProduct`, `deleteProduct`, `updateProduct`, `resetProduct`, `uploadProductLogo`, `deleteProductLogo`, `getProductStats` |
| [`PoliciesApi`](docs/PoliciesApi.md) | `listPolicies`, `createPolicy`, `getPolicy`, `deletePolicy`, `updatePolicy` |
| [`CustomersApi`](docs/CustomersApi.md) | `listCustomers`, `createCustomer`, `getCustomer`, `deleteCustomer`, `updateCustomer` |
| [`MachinesApi`](docs/MachinesApi.md) | `listMachines`, `getMachine`, `deactivateMachine` |
| [`ReleasesApi`](docs/ReleasesApi.md) | `listReleases`, `createRelease`, `getRelease`, `deleteRelease`, `updateRelease` |
| [`TokensApi`](docs/TokensApi.md) | `createCustomerToken`, `createLicenseToken`, `createMachineToken` |
| [`EventsApi`](docs/EventsApi.md) | `listPolicyEvents`, `listLicenseEvents` |
| [`IntegrationsApi`](docs/IntegrationsApi.md) | `getStripeIntegration`, `connectStripe`, `disconnectIntegration`, `updateIntegration`, `checkIntegration`, `listStripePrices`, `createStripeMapping`, `deleteStripeMapping`, `updateStripeMapping` |

## Versioning

This SDK follows [semantic versioning](https://semver.org) and is generated from the [OpenAPI document](openapi.json) of the API: each release is listed in the [changelog](CHANGELOG.md). Please don't open pull requests, they would be overwritten by the next release: [open an issue](https://github.com/licenseman/licensemanager-java/issues) instead.

## License

See [LICENSE](LICENSE).
