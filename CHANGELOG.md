# Changelog

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
