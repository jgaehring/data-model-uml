# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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

[unreleased]: https://github.com/datafoodconsortium/data-model-uml/compare/v2.0.0...HEAD
[2.0.0]: https://github.com/datafoodconsortium/data-model-uml/compare/v1.0.0...v2.0.0
[1.0.0]: https://github.com/datafoodconsortium/data-model-uml/releases/tag/v1.0.0
