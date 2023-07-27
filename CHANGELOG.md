# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Fixed

- `Enterprise`
    - add missing getter and setter on properties `description`, `catalogItems` and `suppliedProduct`
- add multiple missing "adder" stereotype on `Manufacturable`.
- add missing "adder" stereotype on `Offerable`.
- profile XMI href.
- add missing `IUnit` import in `IPrice` and in `Price`.
- add missing things in `Offer`:
    - import `IPrice`
    - add missing setters in properties 
- add missing `IPrice` in `Payable`.
- Add missing method in `Marketable`:
    - `setOfferedItem`
    - `setCustomerCategory`
- Set missing getter and setter for the `description` property of `CustomerCategory`.
- Restore adders.
- `Offer`:
    - change the semantic property `dfc-b:price` to `dfc-b:hasPrice`.

### Added

- Add `localizations` parameter in the constructor of:
    - `Agent`
    - `Enterprise`
    - `Person`
- `Enterprise`
    - add missing constructor parameters.
    - add `catalogs` property.
    - add `technicalProducts` property.
- constructor parameters on `DefinedProduct`.
- `Offerable:setOfferedProduct`
- `Offer`
    - add missing constructor parameters.
- `ICatalogItem`:
    - add `setSku`
    - add `Catalogable` generalization
- `CatalogItem`
    - set `stockLimitation` setter.
    - add missing constructor parameters.
- Stockable:setStockLimitation.
- `SuppliedProduct`:
    - totalTheoreticalStock (property)
    - getTotalTheoreticalStock()
    - setTotalTheoreticalStock()
    - add constructor parameters
- Import `IUnit` in:
    - `AllergenCharacteristic`
    - `NutrientCharacteristic`
    - `PhysicalCharacteristic`
- `Characteristic`:
    - add the `blankNode` stereotype
- `IPrice`:
    - add `setValue`, `setVatRate` and `setUnit`
    - add the `BlankNode` stereotype
- `Price`:
    - add constructor parameters
    - add setter in properties
- `Catalogable`:
    - add `registerInCatalog`
    - add `removeFromCatalog`
- `Browsable`:
    - add `removeItem`
- `IAllergenCharacteristic`
    - add the `BlankNode` stereotype
- `INutrientCharacteristic`
    - add the `BlankNode` stereotype
- `IPhysicalCharacteristic`
    - add the `BlankNode` stereotype
- `ICatalog`
- `ISaleSession`
    - add `getQuantity`
    - add `setQuantity`
    - add `getOffers`
    - add `addOffer`
- `SaleSession`
- `Ellapsable`
    - add setters
    - add stereotypes
- `IOrder`
- `IOrderLine`
- `Order`
    - add properties
- `OrderLine`
    - add properties
- `Payable`
    - add `setPrice`
- connector.profile.uml:
    - the `blankNode` stereotype can be applied on Interface;
- `ISuppliedProduct`
- `ITechnicalProduct`
- `IAgent`

### Changed

- Remove `JsonLdSerializer`.
- `Enterprise`:
    - remove `Nameable`
- Move `getSku` into `ICatalogItem`.
- Change `getQuantityUnit` and `setQuantityUnit` parameter to `IUnit`.
- Rename `quantityUnit` and `quantityValue` to `unit` and `value` of:
    - `QuantitativeValue`
    - `Characteristic`
    - `AllergenCharacteristic`
    - `NutrientCharacteristic`
    - `PhysicalCharacteristic`
- Change constructor `unit` paramater type to `IUnit` of:
    - `QuantitativeValue`
    - `Characteristic`
    - `AllergenCharacteristic`
    - `NutrientCharacteristic`
    - `PhysicalCharacteristic`
- Renamed `Repository` to `Catalog`.
- `Catalogable`
    - rename `getRepository` to `getCatalog`
- `Browsable`:
    - change `getMaintainers` return type to `IEnterprise`
    - renamed `getListedItems` to `getItems`
- Delete classes: `ProductType`, `Unit`, `GeographicalOrigin`, `Certification`, `NatureOrigin`, `PartOrigin`, `CharacteristicDimension`, `AllergenDimension`.
- `SKOSConcept`:
    - not a BlankNode anymore.

## [1.0.0] - 2023-02-06

### Added

- agent.uml
- common.uml
- connector.uml
- connector.profile.uml
- product.uml
- sale.uml
- skos.uml

[unreleased]: https://github.com/datafoodconsortium/data-model-uml/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/datafoodconsortium/data-model-uml/releases/tag/v1.0.0
