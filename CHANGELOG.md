# Changelog

## 0.3.1 (2026-11-11)

### Changes

- `GET /v1/customers/{customerId}/licenses`: added the new optional `query` request parameter `machinePlatform`
- `GET /v1/products/{productId}/licenses`: added the new optional `query` request parameter `machinePlatform`

## 0.3.0 (2026-11-06)

### Breaking changes

- `POST /v1/customers/{id}/tokens`: added the new `customer:billing` enum value to the `scope/items/` response property for the response status `201`
- `GET /v1/licenses/{id}/events`: added the new `license.payment_failed` enum value to the `data/items/type` response property for the response status `200`
- `GET /v1/licenses/{id}/events`: added the new `license.payment_succeeded` enum value to the `data/items/type` response property for the response status `200`
- `GET /v1/licenses/{id}/events`: added the new `license.subscription_ended` enum value to the `data/items/type` response property for the response status `200`
- `POST /v1/licenses/{id}/tokens`: added the new `customer:billing` enum value to the `scope/items/` response property for the response status `201`
- `POST /v1/machines/{id}/tokens`: added the new `customer:billing` enum value to the `scope/items/` response property for the response status `201`
- `GET /v1/policies/{id}/events`: added the new `license.payment_failed` enum value to the `data/items/type` response property for the response status `200`
- `GET /v1/policies/{id}/events`: added the new `license.payment_succeeded` enum value to the `data/items/type` response property for the response status `200`
- `GET /v1/policies/{id}/events`: added the new `license.subscription_ended` enum value to the `data/items/type` response property for the response status `200`

### Potentially breaking changes

- `GET /v1/customers/{customerId}/licenses`: removed `#/components/schemas/CancellationReason, subschema #2` from the `data/items/cancellationReason` response property `allOf` list for the response status `200`
- `GET /v1/customers/{customerId}/licenses`: added `#/components/schemas/CancellationReason, subschema #2` to the `data/items/cancellationReason` response property `anyOf` list for the response status `200`
- `GET /v1/licenses/{id}`: removed `#/components/schemas/CancellationReason, subschema #2` from the `cancellationReason` response property `allOf` list for the response status `200`
- `GET /v1/licenses/{id}`: added `#/components/schemas/CancellationReason, subschema #2` to the `cancellationReason` response property `anyOf` list for the response status `200`
- `PATCH /v1/licenses/{id}`: removed `#/components/schemas/CancellationReason, subschema #2` from the `cancellationReason` response property `allOf` list for the response status `200`
- `PATCH /v1/licenses/{id}`: added `#/components/schemas/CancellationReason, subschema #2` to the `cancellationReason` response property `anyOf` list for the response status `200`
- `POST /v1/licenses/{id}/cancel`: removed `#/components/schemas/CancellationReason, subschema #2` from the `cancellationReason` response property `allOf` list for the response status `200`
- `POST /v1/licenses/{id}/cancel`: added `#/components/schemas/CancellationReason, subschema #2` to the `cancellationReason` response property `anyOf` list for the response status `200`
- `GET /v1/products/{productId}/licenses`: removed `#/components/schemas/CancellationReason, subschema #2` from the `data/items/cancellationReason` response property `allOf` list for the response status `200`
- `GET /v1/products/{productId}/licenses`: added `#/components/schemas/CancellationReason, subschema #2` to the `data/items/cancellationReason` response property `anyOf` list for the response status `200`
- `POST /v1/products/{productId}/licenses`: removed `#/components/schemas/CancellationReason, subschema #2` from the `cancellationReason` response property `allOf` list for the response status `201`
- `POST /v1/products/{productId}/licenses`: added `#/components/schemas/CancellationReason, subschema #2` to the `cancellationReason` response property `anyOf` list for the response status `201`

### Changes

- `GET /v1/customers/{customerId}/licenses`: added the required property `data/items/customer` to the response with the `200` status
- `GET /v1/customers/{customerId}/licenses`: added the required property `data/items/subscription` to the response with the `200` status
- `POST /v1/customers/{id}/billing-portal-sessions`: endpoint added
- `POST /v1/customers/{id}/tokens`: added the new `customer:billing` enum value to the request property `scope/items/`
- `PATCH /v1/integration-mappings/{id}`: added the required property `recurring` to the response with the `200` status
- `PATCH /v1/integrations/{id}`: added the new optional request property `subscriptionGraceDays`
- `PATCH /v1/integrations/{id}`: added the required property `canBillingPortal` to the response with the `200` status
- `PATCH /v1/integrations/{id}`: added the required property `canManageSubscriptions` to the response with the `200` status
- `PATCH /v1/integrations/{id}`: added the required property `subscriptionGraceDays` to the response with the `200` status
- `POST /v1/integrations/{id}/check`: added the required property `canBillingPortal` to the response with the `200` status
- `POST /v1/integrations/{id}/check`: added the required property `canManageSubscriptions` to the response with the `200` status
- `POST /v1/integrations/{id}/check`: added the required property `subscriptionGraceDays` to the response with the `200` status
- `GET /v1/integrations/{id}/stripe/prices`: added the required property `data/items/recurring` to the response with the `200` status
- `GET /v1/licenses/{id}`: added the required property `customer` to the response with the `200` status
- `GET /v1/licenses/{id}`: added the required property `subscription` to the response with the `200` status
- `PATCH /v1/licenses/{id}`: added the non-success response with the status `409`
- `PATCH /v1/licenses/{id}`: added the required property `customer` to the response with the `200` status
- `PATCH /v1/licenses/{id}`: added the required property `subscription` to the response with the `200` status
- `POST /v1/licenses/{id}/cancel`: added the required property `customer` to the response with the `200` status
- `POST /v1/licenses/{id}/cancel`: added the required property `subscription` to the response with the `200` status
- `GET /v1/licenses/{id}/events`: added the enum value `license.payment_failed` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `GET /v1/licenses/{id}/events`: added the enum value `license.payment_succeeded` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `GET /v1/licenses/{id}/events`: added the enum value `license.subscription_ended` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `POST /v1/licenses/{id}/tokens`: added the new `customer:billing` enum value to the request property `scope/items/`
- `POST /v1/machines/{id}/tokens`: added the new `customer:billing` enum value to the request property `scope/items/`
- `GET /v1/policies/{id}/events`: added the enum value `license.payment_failed` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `GET /v1/policies/{id}/events`: added the enum value `license.payment_succeeded` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `GET /v1/policies/{id}/events`: added the enum value `license.subscription_ended` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `GET /v1/products/{id}/stats`: added the required property `revenue/items/paymentCount` to the response with the `200` status
- `GET /v1/products/{id}/stats`: added the required property `revenue/items/subscriptionTotal` to the response with the `200` status
- `GET /v1/products/{id}/stats`: added the required property `subscriptions` to the response with the `200` status
- `GET /v1/products/{productId}/integrations/slack`: endpoint added
- `POST /v1/products/{productId}/integrations/slack/authorize`: endpoint added
- `GET /v1/products/{productId}/integrations/stripe`: added the required property `integration/anyOf[#/components/schemas/Integration]/canBillingPortal` to the response with the `200` status
- `GET /v1/products/{productId}/integrations/stripe`: added the required property `integration/anyOf[#/components/schemas/Integration]/canManageSubscriptions` to the response with the `200` status
- `GET /v1/products/{productId}/integrations/stripe`: added the required property `integration/anyOf[#/components/schemas/Integration]/subscriptionGraceDays` to the response with the `200` status
- `GET /v1/products/{productId}/integrations/stripe`: added the required property `mappings/items/recurring` to the response with the `200` status
- `GET /v1/products/{productId}/integrations/stripe`: added the required property `requiredPermissions/items/subscriptions` to the response with the `200` status
- `PUT /v1/products/{productId}/integrations/stripe`: added the required property `integration/anyOf[#/components/schemas/Integration]/canBillingPortal` to the response with the `200` status
- `PUT /v1/products/{productId}/integrations/stripe`: added the required property `integration/anyOf[#/components/schemas/Integration]/canManageSubscriptions` to the response with the `200` status
- `PUT /v1/products/{productId}/integrations/stripe`: added the required property `integration/anyOf[#/components/schemas/Integration]/subscriptionGraceDays` to the response with the `200` status
- `PUT /v1/products/{productId}/integrations/stripe`: added the required property `mappings/items/recurring` to the response with the `200` status
- `PUT /v1/products/{productId}/integrations/stripe`: added the required property `requiredPermissions/items/subscriptions` to the response with the `200` status
- `POST /v1/products/{productId}/integrations/stripe/mappings`: added the required property `recurring` to the response with the `201` status
- `GET /v1/products/{productId}/licenses`: added the required property `data/items/customer` to the response with the `200` status
- `GET /v1/products/{productId}/licenses`: added the required property `data/items/subscription` to the response with the `200` status
- `POST /v1/products/{productId}/licenses`: added the required property `customer` to the response with the `201` status
- `POST /v1/products/{productId}/licenses`: added the required property `subscription` to the response with the `201` status
- `DELETE /v1/slack-connections/{id}`: endpoint added
- `PATCH /v1/slack-connections/{id}`: endpoint added
- `POST /v1/slack-connections/{id}/test`: endpoint added

## 0.2.0 (2026-10-27)

### Breaking changes

- `GET /v1/customers/{customerId}/licenses`: added the new `canceled` enum value to the `data/items/status` response property for the response status `200`
- `POST /v1/customers/{id}/tokens`: added the new `license:cancel` enum value to the `scope/items/` response property for the response status `201`
- `GET /v1/licenses/{id}`: added the new `canceled` enum value to the `status` response property for the response status `200`
- `PATCH /v1/licenses/{id}`: added the new `canceled` enum value to the `status` response property for the response status `200`
- `GET /v1/licenses/{id}/events`: added the new `license.canceled` enum value to the `data/items/type` response property for the response status `200`
- `GET /v1/licenses/{id}/events`: added the new `license.refund_failed` enum value to the `data/items/type` response property for the response status `200`
- `GET /v1/licenses/{id}/events`: added the new `license.refunded` enum value to the `data/items/type` response property for the response status `200`
- `POST /v1/licenses/{id}/tokens`: added the new `license:cancel` enum value to the `scope/items/` response property for the response status `201`
- `GET /v1/licenses/{licenseId}/machines`: added the new `locked` enum value to the `data/items/status` response property for the response status `200`
- `GET /v1/machines/{id}`: added the new `locked` enum value to the `status` response property for the response status `200`
- `POST /v1/machines/{id}/deactivate`: added the new `locked` enum value to the `status` response property for the response status `200`
- `POST /v1/machines/{id}/tokens`: added the new `license:cancel` enum value to the `scope/items/` response property for the response status `201`
- `GET /v1/policies/{id}/events`: added the new `license.canceled` enum value to the `data/items/type` response property for the response status `200`
- `GET /v1/policies/{id}/events`: added the new `license.refund_failed` enum value to the `data/items/type` response property for the response status `200`
- `GET /v1/policies/{id}/events`: added the new `license.refunded` enum value to the `data/items/type` response property for the response status `200`
- `GET /v1/products/{productId}/licenses`: added the new `canceled` enum value to the `data/items/status` response property for the response status `200`
- `POST /v1/products/{productId}/licenses`: added the new `canceled` enum value to the `status` response property for the response status `201`

### Changes

- `GET /v1/customers/{customerId}/licenses`: added the enum value `canceled` to the property `allOf[#/components/schemas/LicenseStatus]/` of the `query` request parameter `status`
- `GET /v1/customers/{customerId}/licenses`: added the required property `data/items/canceledAt` to the response with the `200` status
- `GET /v1/customers/{customerId}/licenses`: added the required property `data/items/cancellableUntil` to the response with the `200` status
- `GET /v1/customers/{customerId}/licenses`: added the required property `data/items/cancellationComment` to the response with the `200` status
- `GET /v1/customers/{customerId}/licenses`: added the required property `data/items/cancellationReason` to the response with the `200` status
- `GET /v1/customers/{customerId}/licenses`: added the required property `data/items/stripeRefundId` to the response with the `200` status
- `POST /v1/customers/{id}/tokens`: added the new `license:cancel` enum value to the request property `scope/items/`
- `PATCH /v1/integrations/{id}`: endpoint added
- `POST /v1/integrations/{id}/check`: added the required property `autoRefund` to the response with the `200` status
- `POST /v1/integrations/{id}/check`: added the required property `canRefund` to the response with the `200` status
- `GET /v1/licenses/{id}`: added the required property `canceledAt` to the response with the `200` status
- `GET /v1/licenses/{id}`: added the required property `cancellableUntil` to the response with the `200` status
- `GET /v1/licenses/{id}`: added the required property `cancellationComment` to the response with the `200` status
- `GET /v1/licenses/{id}`: added the required property `cancellationReason` to the response with the `200` status
- `GET /v1/licenses/{id}`: added the required property `stripeRefundId` to the response with the `200` status
- `PATCH /v1/licenses/{id}`: added the new optional request property `cancellableUntil`
- `PATCH /v1/licenses/{id}`: added the required property `canceledAt` to the response with the `200` status
- `PATCH /v1/licenses/{id}`: added the required property `cancellableUntil` to the response with the `200` status
- `PATCH /v1/licenses/{id}`: added the required property `cancellationComment` to the response with the `200` status
- `PATCH /v1/licenses/{id}`: added the required property `cancellationReason` to the response with the `200` status
- `PATCH /v1/licenses/{id}`: added the required property `stripeRefundId` to the response with the `200` status
- `POST /v1/licenses/{id}/cancel`: endpoint added
- `GET /v1/licenses/{id}/events`: added the enum value `license.canceled` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `GET /v1/licenses/{id}/events`: added the enum value `license.refund_failed` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `GET /v1/licenses/{id}/events`: added the enum value `license.refunded` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `POST /v1/licenses/{id}/tokens`: added the new `license:cancel` enum value to the request property `scope/items/`
- `GET /v1/licenses/{licenseId}/machines`: added the new enum value `locked` to the `query` request parameter `status`
- `GET /v1/licenses/{licenseId}/machines`: added the required property `data/items/overriddenByMachineId` to the response with the `200` status
- `GET /v1/machines/{id}`: added the required property `overriddenByMachineId` to the response with the `200` status
- `POST /v1/machines/{id}/deactivate`: added the required property `overriddenByMachineId` to the response with the `200` status
- `POST /v1/machines/{id}/tokens`: added the new `license:cancel` enum value to the request property `scope/items/`
- `GET /v1/policies/{id}`: added the required property `moneyBackGuaranteeDays` to the response with the `200` status
- `PATCH /v1/policies/{id}`: added the new optional request property `moneyBackGuaranteeDays`
- `PATCH /v1/policies/{id}`: added the required property `moneyBackGuaranteeDays` to the response with the `200` status
- `GET /v1/policies/{id}/events`: added the enum value `license.canceled` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `GET /v1/policies/{id}/events`: added the enum value `license.refund_failed` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `GET /v1/policies/{id}/events`: added the enum value `license.refunded` to the property `anyOf[#/components/schemas/EventType]/` of the `query` request parameter `type` (shared schema: `EventType`, also at `anyOf[#/components/schemas/EventType]`, `anyOf[subschema #2]/items`)
- `GET /v1/products`: added the required property `data/items/autoMachineChange` to the response with the `200` status
- `POST /v1/products`: added the new optional request property `allOf[subschema #2]/defaultPolicy/moneyBackGuaranteeDays`
- `POST /v1/products`: added the required property `autoMachineChange` to the response with the `201` status
- `GET /v1/products/{id}`: added the required property `autoMachineChange` to the response with the `200` status
- `PATCH /v1/products/{id}`: added the new optional request property `autoMachineChange`
- `PATCH /v1/products/{id}`: added the required property `autoMachineChange` to the response with the `200` status
- `DELETE /v1/products/{id}/logo`: added the required property `autoMachineChange` to the response with the `200` status
- `PUT /v1/products/{id}/logo`: added the required property `autoMachineChange` to the response with the `200` status
- `POST /v1/products/{id}/reset`: added the required property `autoMachineChange` to the response with the `200` status
- `GET /v1/products/{id}/stats`: added the required property `cancellation` to the response with the `200` status
- `GET /v1/products/{id}/stats`: added the required property `revenue/items/canceledLicenseCount` to the response with the `200` status
- `GET /v1/products/{id}/stats`: added the required property `revenue/items/canceledTotal` to the response with the `200` status
- `GET /v1/products/{productId}/integrations/stripe`: added the required property `integration/anyOf[#/components/schemas/Integration]/autoRefund` to the response with the `200` status
- `GET /v1/products/{productId}/integrations/stripe`: added the required property `integration/anyOf[#/components/schemas/Integration]/canRefund` to the response with the `200` status
- `GET /v1/products/{productId}/integrations/stripe`: added the required property `requiredPermissions/items/optional` to the response with the `200` status
- `PUT /v1/products/{productId}/integrations/stripe`: added the required property `integration/anyOf[#/components/schemas/Integration]/autoRefund` to the response with the `200` status
- `PUT /v1/products/{productId}/integrations/stripe`: added the required property `integration/anyOf[#/components/schemas/Integration]/canRefund` to the response with the `200` status
- `PUT /v1/products/{productId}/integrations/stripe`: added the required property `requiredPermissions/items/optional` to the response with the `200` status
- `GET /v1/products/{productId}/licenses`: added the enum value `canceled` to the property `allOf[#/components/schemas/LicenseStatus]/` of the `query` request parameter `status`
- `GET /v1/products/{productId}/licenses`: added the required property `data/items/canceledAt` to the response with the `200` status
- `GET /v1/products/{productId}/licenses`: added the required property `data/items/cancellableUntil` to the response with the `200` status
- `GET /v1/products/{productId}/licenses`: added the required property `data/items/cancellationComment` to the response with the `200` status
- `GET /v1/products/{productId}/licenses`: added the required property `data/items/cancellationReason` to the response with the `200` status
- `GET /v1/products/{productId}/licenses`: added the required property `data/items/stripeRefundId` to the response with the `200` status
- `POST /v1/products/{productId}/licenses`: added the new optional request property `cancellableUntil`
- `POST /v1/products/{productId}/licenses`: added the required property `canceledAt` to the response with the `201` status
- `POST /v1/products/{productId}/licenses`: added the required property `cancellableUntil` to the response with the `201` status
- `POST /v1/products/{productId}/licenses`: added the required property `cancellationComment` to the response with the `201` status
- `POST /v1/products/{productId}/licenses`: added the required property `cancellationReason` to the response with the `201` status
- `POST /v1/products/{productId}/licenses`: added the required property `stripeRefundId` to the response with the `201` status
- `GET /v1/products/{productId}/policies`: added the required property `data/items/moneyBackGuaranteeDays` to the response with the `200` status
- `POST /v1/products/{productId}/policies`: added the new optional request property `moneyBackGuaranteeDays`
- `POST /v1/products/{productId}/policies`: added the required property `moneyBackGuaranteeDays` to the response with the `201` status

## 0.1.0 (2026-10-20)

Initial release.
