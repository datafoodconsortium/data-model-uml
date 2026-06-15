# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

TODO:
- Create top classes `Subject` and `Relation` to be generalized by all DFC subjects and relations.
- Rename IQuantity to IQuantitativeValue (**Breaking change**).

## [4.0.0] - 2026-06-10

This major version implements the ontology version 2 changes. It introduces several breaking changes in the generated code.

### Added

- `SuppliedProduct:constructor` variants parameter
- `TechnicalProduct:constructor` variants parameter

### Changed

- Domain : isVariantOf, DefinedProduct -> Variant (**BREAKING CHANGE**)
- Constraint 1:1 for Stock:availabilityDate (**BREAKING CHANGE**)
- Constraint 1:1 for PaymentMethod:paymentMethodProvider (**BREAKING CHANGE**)
- Constraint 1:1 for PaymentMethod:paymentMethodType (**BREAKING CHANGE**)
- Domain : beginDate, (AsPlannedLocalTransformation | AsRealizedTransformation | SaleSession | Shipment | Shipping option) -> (AsPlannedTransformation | AsRealizedTransformation | Catalog | SaleSession | Shipment | Shipping option)
- Domain : endDate, (AsPlannedLocalTransformation | AsRealizedTransformation | SaleSession | Shipment | Shipping option) -> (AsPlannedTransformation | AsRealizedTransformation | Catalog | SaleSession | Shipment | Shipping option)

### Removed

- The `Enterprise` class has been replaced by `Organization` (**BREAKING CHANGE**).

## [3.5.0] - 2026-06-15

### Added

- Add the `Employer` interface.
- Add `Enterprise:affiliates` property.
- `Enterprise` implements the `Employer` interface.

### Fixed

- Fix `LocalizedProduct:theoreticalStock` wrong type (Real -> ITheoreticalStock).

## [3.4.0] - 2026-05-21

This version was created from the [PR#34](https://github.com/datafoodconsortium/data-model-uml/pull/34).

### Added

- Add the `name` property to `CustomerCategory`.

### Changed

- The `QuantitativeValue` class now implements `IQuantity` to be semanticable. We did't do it with the `Quantifiable` interface to let a generic layer.

### Fixed

- Fix `CustomerCategory:description` wrong constructor binding.

### Removed

- Remove the `Quantity` class as there is no Quantity class in the ontology. We should use `QuantitativeValue`.

## [3.3.0] - 2026-05-20

This version was created from the [PR#33](https://github.com/datafoodconsortium/data-model-uml/pull/33).

### Added

- Add `SuppliedProduct` referenceOf.
- Add `OpeningHoursSpecification` class.
- Add `Catalog` missing `maintainers` setter and remover bindings.
- Add `Catalog` missing `items` setter binding.
- Add `Order` missing `lines` setter and remover bindings.
- Add `SaleSession` missing `offers` setter and remover bindings.
- Add `CatalogItem` missing `catalogs` setter and wrong remover bindings.
- Add `CatalogItem` missing `offers` setter and remover bindings.
- Add `DefinedProduct` missing `partOrigin` setter binding.
- Add `DefinedProduct` missing `natureOrigin` setter binding.
- Add `DefinedProduct` missing `certifications` setter binding.
- Add `DefinedProduct` missing `catalogItems` setter and remover bindings.
- Add `DefinedProduct` missing `physicalCharacteristics` setter binding.
- Add `DefinedProduct` missing `nutrientCharacteristics` setter binding.
- Add `DefinedProduct` missing `allergenCharacteristics` setter binding.
- Add `DefinedProduct` missing `claims` setter binding.
- Add `Agent` missing `socialMedias` setter binding.
- Add `Agent` missing `websites` setter binding.
- Add `Agent` missing `emails` setter binding.
- Add `CustomerCategory` name.
- Add `Person` missing `affiliatedOrgs` setter binding.
- Add `Enterprise` missing `technicalProducts` setter and remover bindings.
- Add `Enterprise` missing `catalogItems` setter and remover bindings.
- Add `Enterprise` missing `customerCategories` setter and remover bindings.
- Add `Enterprise` missing `suppliedProducts` setter and remover bindings.

### Fixed

- Fix `Agent` setters for `localizations` and phone numbers.
- Fix `ILocalizedProduct` consumptionFlow -> localConsumptionFlow.
- `Exhibitable` now has adder and remover, image -> images.
- `LocalizedProduct` is now an `Exhibitable`.
- `DefinedProduct` and subclasses are now `Exhibitable`.
- Fix `Order` paymentMethod.
- Fix `PlannedLocalTransformation` bad outcome and associated constructor param types.
- Fix `RealStock` quantity.
- Fix `DeliveryOption` wrong interface realization.
- Fix `LocalizedProduct` quantity getter and setter.
- Fix `PaymentMethod` price getter and setter.
- Fix `PhysicalPlace`, add semantic stereotype to `IGeoJsonFeature`.
- Fix `PhysicalProduct` `quantity` and `images` properties.
- Fix `PlannedLocalConsumptionFlow` wrong method bindings.
- Fix `PlannedLocalProductionFlow` wrong method bindings.
- Fix `ProductBatch` wrong method bindings.
- Fix `RealizedConsumptionFlow` wrong method bindings.
- Fix `RealizedProductionFlow` wrong method bindings.
- Fix `IOpeningHoursSpecification`: Add semantic stereotype.
- Fix `IPlace`: add `Nameable` and `Describable` generalization.
- Fix `Address:country type` -> now a `SkosConcept`.
- Fix `Enterprise:customerCategories` setter and remover wrong parameter type.
- Fix `LocalizedProduct:plannedLocalProductionFlow` wrong setter.
- Fix `CatalogItemManager` setter wrong parameter.

### Removed

- Remove `Quantity` class to keep `QuantitativeValue` instead (there is no Quantity class in the ontology).

## [3.2.1] - 2026-05-05

### Fixed

- Wrong method bindings of `AsPlannedLocalTransformation` and `AsRealizedTransformation`.

## [3.2.0] - 2026-05-05

### Changed

Implement missing changes of [ontology v1.11.0](https://github.com/datafoodconsortium/ontology/blob/master/CHANGELOG.md#1110---2024-01-11):
- Rename `hasIncome` -> `hasInput` and `hasOutcome` -> `hasOutput` in `AsPlannedTransformation`, `AsPlannedLocalTransformation` and `AsRealizedTransformation`.
- Rename `incomeOf` > `inputOf` in `AsPlannedConsumptionFlow`, `AsPlannedLocalConsumptionFlow` and `AsRealizedConsumptionFlow`.
- Rename `outcomeOf` -> `outpufOf` in `AsPlannedProductionFlow`, `AsPlannedLocalProductionFlow` and `AsRealizedProductionFlow`.

## [3.1.0] - 2025-06-26

Add logistic concepts:
- `AsPlannedLocalTransformation`, `AsPlannedLocalConsumptionFlow`, `AsPlannedLocalProductionFlow`.
- `AsRealizedTransformation`, `AsRealizedConsumptionFlow`, `AsRealizedProductionFlow`.
- `DeliveryOption`.
- `LocalizedProduct`.
- `PaymentMethod`.
- `PhysicalPlace`.
- `PhysicalProduct`.
- `PickupOption`.
- `ProductBatch`.
- `RealStock`.
- `TheoreticalStock`.
- `VirtualPlace`.

### Fixed
- Add `AddressOwner:setLocalizations`.
- Add `PhoneNumberOwner:setPhoneNumbers`.
- Import `SKOSConcept` in `IPlannedTransformation`.
- Import `SKOSConcept` in `PlannedTransformation`.
- Add setter to property `PlannedTransformation:consumptionFlow`.
- Add setter to property `PlannedTransformation:productionFlow`.

### Added

Interfaces:
- `IDeliveryOption`.
- `ILocalizedProduct`.
- `IPaymentMethod`.
- `IPhysicalPlace`.
- `IPhysicalProduct`.
- `IPickupOption`.
- `IPlace`.
- `IPlannedLocalFlow`.
- `IPlannedLocalProductionFlow`.
- `IPlannedLocalTransformation`.
- `IProductBatch`.
- `IRealizedConsumptionFlow`.
- `IRealizedFlow`.
- `IRealizedProductionFlow`.
- `IRealizedTransformation`.
- `IRealStock`.
- `IShippingOption`.
- `IStock`.
- `ITheoreticalStock`.
- `IVirtualPlace`.
- `Openable`.

Classes:
- `DeliveryOption`.
- `LocalizedProduct`.
- `PaymentMethod`.
- `PhysicalPlace`.
- `PhysicalProduct`.
- `PickupOption`.
- `PlannedLocalConsumptionFlow`.
- `PlannedLocalTransformation`.
- `ProductBatch`.
- `RealizedConsumptionFlow`.
- `RealizedTransformation`.
- `RealStock`.
- `ShippingOption`.
- `TheoreticalStock`.
- `VirtualPlace`.

## [3.0.0] - 2025-03-26

### Fixed

- Fix SocialMedia duplicated getUrl method (#12).
- Fix missing "Semantic" stereotype on ISocialMedia and IPhoneNumber interfaces (#13).

### Changed

- Changed all references to http://static.datafoodconsortium.org/uml/connector to point to latest github release (via jsdelivr) using https://cdn.jsdelivr.net/gh/datafoodconsortium/data-model-uml/.

### Added

- Add the planned transformation loop (`AsPlannedTransformation`).
- Add image to `DefinedProduct`, see below.

- Interfaces:
  - `IPlannedTransformation`.
  - `IFlow`.
  - `IPlannedFlow`.
  - `IPlannedConsumptionFlow`.
  - `IPlannedProductionFlow`.

- Classes:
  - `PlannedTransformation`.
  - `Flow`.
  - `PlannedConsumptionFlow`.
  - `PlannedProductionFlow`.

- Add the `soldBy` property in `Order`:
  - Add method `getSoldBy` in `IOrder` .
  - Add method `setSoldBy` in `IOrder` .
  - Add property `soldBy` in `Order` .
  - Add paramater `soldBy` in constructor of `Order`.
- Add the `logo` property in `Agent`:
  - Add method `getLogo` in `IAgent`.
  - Add method `setLogo` in `IAgent`.
  - Add property `logo` in `Agent`.
  - Add parameter `logo` in constructor of `Agent`.
  - Add parameter `logo` in constructor of `Enterprise`.
  - Add parameter `logo` in constructor of `Person`.
- Add the `latitude` property in `Address`:
  - Add the `latitude` parameter in constructor.
  - Add the `getLatitude` getter in `Localizable`.
  - Add the `setLatitude` setter in `Localizable`.
- Add the `longitude` property in `Address`:
  - Add the `longitude` parameter in constructor.
  - Add the `getLongitude` getter in `Localizable`.
  - Add the `setLongitude` setter in `Localizable`.
- Add the `region` property in `Address`:
  - Add the `region` parameter in constructor.
  - Add the `getRegion` getter in `Localizable`.
  - Add the `setRegion` setter in `Localizable`.
- Add the `hasFulfilmentStatus` property in `Order`:
  - Add the `fulfilmentStatus` parameter in constructor.
  - Add the `getFulfilmentStatus` getter in `IOrder`.
  - Add the `setFulfilmentStatus` setter in `IOrder`.
- Add the `hasOrderStatus` property in `Order`:
  - Add the `orderStatus` parameter in constructor.
  - Add the `getOrderStatus` getter in `IOrder`.
  - Add the `setOrderStatus` setter in `IOrder`.
- Add the `hasPaymentStatus` property in `Order`:
  - Add the `paymentStatus` parameter in constructor.
  - Add the `getPaymentStatus` getter in `IOrder`.
  - Add the `setPaymentStatus` setter in `IOrder`.
- In `DefinedProduct`:
  - Add the `image` property.
  - Add the `images` parameter in constructor.
  - Add the `hasVariant` property.
  - Add the `isVariantOf` property.
  - Add the `variants` parameter in constructor.
  - Add the `variantOf` parameter in constructor.
- In `SuppliedProduct`:
  - Add the `images` parameter in constructor.
- In the `IDefinedProduct` interface:
  - Add the `addImage` method.
  - Add the `removeImage` method.
  - Add the `getImages` method.
  - Add the `addVariant` method.
  - Add the `getVariants` method.
  - Add the `removeVariant` method.
  - Add the `setVariants` method.
  - Add the `addIsVariantOf` method.
  - Add the `getIsVariantOf` method.
  - Add the `removeIsVariantOf` method.
  - Add the `setIsVariantOf` method.

## [2.1.0] - 2023-11-06

### Added

- Interfaces:
    - New `IPhoneNumber` interface.
    - New `ISocialMedia` interface.
    - New `ContactableByAddress` interface.
    - New `ContactableByEmail` interface.
    - New `ContactableByPhone` interface.
    - New `ContactableByWebsite` interface.
    - New `ContactableBySocialMedia` interface.
    - New `PhoneNumberOwner` interface.
    - New `AddressOwner` interface.
    - New `EmailOwner` interface.
    - New `WebsiteOwner` interface.
    - New `SocialMediaOwner` interface.
    - New `ManagedByMainContact` interface.
    - New `MainContactOwner` interface.

- Classes:
    - New `PhoneNumber` class.
    - New `SocialMedia` class.
    - Support the name of `Enterprise`.

- In the `SUPPORTED.md` file:
    - Add the `PhoneNumber` class;
    - Add `PhysicalPlace:hasPhoneNumber`.

### Changed

- Change the type of `Dialable:number` from Integer to String.
- Change the type of `Contactable:getPhoneNumbers` from `Dialable` to `IPhoneNumber`.
- Change the type of `Contactable:addPhoneNumber` from `Dialable` to `IPhoneNumber`.

### Removed

- The `Contactable` interface.
- The `Emailable` interface.
- The `Identifiable` interface.

## [2.0.0] - 2023-10-03

### Fixed

- `Enterprise`:
    - Add missing getter and setter on properties `description`, `catalogItems` and `suppliedProduct`.
- Add multiple missing "adder" stereotype on `Manufacturable`.
- Add missing "adder" stereotype on `Offerable`.
- Profile XMI href.
- Add missing `IUnit` import in `IPrice` and in `Price`.
- Add missing things in `Offer`:
    - Import `IPrice`;
    - Add missing setters in properties.
- Add missing `IPrice` in `Payable`.
- Add missing method in `Marketable`:
    - `setOfferedItem`;
    - `setCustomerCategory`.
- Set missing getter and setter for the `description` property of `CustomerCategory`.
- Restore adders.
- `Offer`:
    - change the semantic property `dfc-b:price` to `dfc-b:hasPrice`.

### Added

- New stereotype `skosBroader` to add constraint on SKOS concepts.
- Add `localizations` parameter in the constructor of:
    - `Agent`;
    - `Enterprise`;
    - `Person`.
- `Enterprise`:
    - Add missing constructor parameters;
    - Add `catalogs` property;
    - Add `technicalProducts` property.
- Constructor parameters on `DefinedProduct`.
- `Offerable:setOfferedProduct`.
- `Offer`:
    - Add missing constructor parameters.
- `ICatalogItem`:
    - Add `setSku`;
    - Add `Catalogable` generalization.
- `CatalogItem`:
    - Set `stockLimitation` setter;
    - Add missing constructor parameters.
- `Stockable:setStockLimitation`.
- `SuppliedProduct`:
    - Add `totalTheoreticalStock` (property);
    - Add `getTotalTheoreticalStock`;
    - Add `setTotalTheoreticalStock`;
    - Add constructor parameters.
- Import `IUnit` in:
    - `AllergenCharacteristic`;
    - `NutrientCharacteristic`;
    - `PhysicalCharacteristic`.
- `Characteristic`:
    - Add the `blankNode` stereotype.
- `IPrice`:
    - Add `setValue`, `setVatRate` and `setUnit`;
    - Add the `BlankNode` stereotype.
- `Price`:
    - Add constructor parameters;
    - Add setter in properties.
- `Catalogable`:
    - Add `registerInCatalog`;
    - Add `removeFromCatalog`.
- `Browsable`:
    - Add `removeItem`.
- `IAllergenCharacteristic`:
    - Add the `BlankNode` stereotype.
- `AllergenDimension` class.
- `INutrientCharacteristic`:
    - Add the `BlankNode` stereotype.
- `NutrientDimension` class.
- `IPhysicalCharacteristic`:
    - Add the `BlankNode` stereotype.
- `PhysicalDimension` class.
- `ICatalog`.
- `ISaleSession`:
    - Add `getQuantity`;
    - Add `setQuantity`;
    - Add `getOffers`;
    - Add `addOffer`.
- `SaleSession`.
- `Ellapsable`:
    - Add setters;
    - Add stereotypes.
- `IOrder`.
- `IOrderLine`.
- `Order`:
    - Add properties.
- `OrderLine`:
    - Add properties.
- `Payable`:
    - Add `setPrice`.
- connector.profile.uml:
    - The `blankNode` stereotype can be applied on Interface.
- `ISuppliedProduct`.
- `ITechnicalProduct`.
- `TechnicalProduct`.
- `IAgent`.

### Changed

- Replace the URL in the map property attribute by a prefix + a name.
- Remove `JsonLdSerializer`.
- `Enterprise`:
    - Removed `Nameable` interface.
- Move `getSku` into `ICatalogItem`.
- Change `getQuantityUnit` and `setQuantityUnit` parameter to `IUnit`.
- Rename `quantityUnit` and `quantityValue` to `unit` and `value` of:
    - `QuantitativeValue`;
    - `Characteristic`;
    - `AllergenCharacteristic`;
    - `NutrientCharacteristic`;
    - `PhysicalCharacteristic`.
- Change constructor `unit` paramater type to `IUnit` of:
    - `QuantitativeValue`;
    - `Characteristic`;
    - `AllergenCharacteristic`;
    - `NutrientCharacteristic`;
    - `PhysicalCharacteristic`.
- Renamed `Repository` to `Catalog`.
- `Catalogable`:
    - Renamed `getRepository` to `getCatalog`.
- `Browsable`:
    - Changed `getMaintainers` return type to `IEnterprise`.
    - Renamed `getListedItems` to `getItems`
- Deleted classes:
    - `ProductType`;
    - `Unit`;
    - `GeographicalOrigin`;
    - `Certification`;
    - `NatureOrigin`;
    - `PartOrigin`;
    - `CharacteristicDimension`;
    - `AllergenDimension`.
- `SKOSConcept` is not a BlankNode anymore.

## [1.0.0] - 2023-02-06

### Added

- agent.uml
- common.uml
- connector.uml
- connector.profile.uml
- product.uml
- sale.uml
- skos.uml

[unreleased]: https://github.com/datafoodconsortium/data-model-uml/compare/v4.0.0...HEAD
[4.0.0]: https://github.com/datafoodconsortium/data-model-uml/compare/v3.5.0...v4.0.0
[3.5.0]: https://github.com/datafoodconsortium/data-model-uml/compare/v3.4.0...v3.5.0
[3.4.0]: https://github.com/datafoodconsortium/data-model-uml/compare/v3.3.0...v3.4.0
[3.3.0]: https://github.com/datafoodconsortium/data-model-uml/compare/v3.2.1...v3.3.0
[3.2.1]: https://github.com/datafoodconsortium/data-model-uml/compare/v3.2.0...v3.2.1
[3.2.0]: https://github.com/datafoodconsortium/data-model-uml/compare/v3.1.0...v3.2.0
[3.1.0]: https://github.com/datafoodconsortium/data-model-uml/compare/v3.0.0...v3.1.0
[3.0.0]: https://github.com/datafoodconsortium/data-model-uml/compare/v2.1.0...v3.0.0
[2.1.0]: https://github.com/datafoodconsortium/data-model-uml/compare/v2.0.0...v2.1.0
[2.0.0]: https://github.com/datafoodconsortium/data-model-uml/compare/v1.0.0...v2.0.0
[1.0.0]: https://github.com/datafoodconsortium/data-model-uml/releases/tag/v1.0.0
