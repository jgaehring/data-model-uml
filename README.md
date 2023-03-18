# Data Food Consortium UML data model

This repository contains the DFC UML model representing the DFC ontology. A model is more precise than an ontology. When implemented, it allows an application to use the concepts defined in the corresponding ontology.

This data model could be used to generate source code from. That's what we do with our connector.

To edit these `.uml` files you can use Eclipse with the `Eclipse Modeling Tools` plugin. It provides a graphical interface to edit objects and properties.

## Overview

The model is divided into several files containing concepts:
  - agent.uml: `Agent`, `Enterprise`, `Person` and `CustomerCategory`.
  - common.uml: `Address`, `QuantitativeValue`, measures and facets objects. 
  - connector.uml: the main package that contains all the others.
  - product.uml: `DefinedProduct` and `SuppliedProduct`.
  - sale.uml: `CatalogItem`, `Offer`, `Price`.
  - skos.uml: objets to manage SKOS taxonomies.

## UML profile

One UML profile is defined in the `connector.profile.uml` file.

The following stereotypes are defined:

| Stereotype | Description |
| ----------- | ----------- |
| property | Defines a class property. |
| propertyMultiple | Defines a list of class properties. |
| constructor | Allow to mark a method as contructor. |
| initializer | Used to bind a constructor parameter to its corresponding class property. |
| initializerParent | Used to bind a constructor parameter to a property in the super class. |
| getter | Used to mark a method as a getter. |
| setter | Used to mark a method as a setter. |
| adder | Used to mark a method as an adder (able to add some object). |
| remover | Used to mark a method as a remover (able to remove some object). |
| external | Used to mark external package (deprecated). |
| semantic | Used to map classes and properties to their corresponding URI. |
| blankNode | Used to mark a class as a blank node. |

## Ontology concepts currently supported

Please refer to the [`SUPPORTED.md` document](https://github.com/datafoodconsortium/data-model-uml/blob/main/SUPPORTED.md).

## Rules for adding a new interface

To be writen.

## Rules for adding a new class

To be writen.

## Troubleshooting

### Stereotypes from an applied profile are missing

Open the broken UML file in a text editor. 

Ensure that the whole file content is wrapped with an `<xmi></xmi>` tag like:

```
<xmi:XMI xmi:version="20131001" xmlns:xmi="http://www.omg.org/spec/XMI/20131001" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:datafoodconsortium_connector="http://static.datafoodconsortium.org/uml/connector/connector.profile.uml" xmlns:ecore="http://www.eclipse.org/emf/2002/Ecore" xmlns:uml="http://www.eclipse.org/uml2/5.0.0/UML" xsi:schemaLocation="http://static.datafoodconsortium.org/uml/connector/connector.profile.uml connector.profile.uml#_3OuvQK70Ee2D9pavmCI82g">
	<uml:Package xmi:id="_XGqrsNwDEeyr_asPBQgiSQ" name="org.datafoodconsortium.connector.product" URI="https://datafoodconsortium.org/uml/package/product">
		The content...
	</uml:Package>
</xmi>
```

The UML file must contain a `<ProfileApplication></ProfileAppication>` section just before closing the `</uml:Package>` tag like:

```
<profileApplication xmi:id="_ZaCIsK76Ee27bvIjdr5biQ">
      <eAnnotations xmi:id="_ZaEk8K76Ee27bvIjdr5biQ" source="http://www.eclipse.org/uml2/2.0.0/UML">
        <references xmi:type="ecore:EPackage" href="connector.profile.uml#_CgHckK74Ee2D9pavmCI82g"/>
      </eAnnotations>
      <appliedProfile href="connector.profile.uml#_xSn38NtjEeyHhf8rtkVHoQ"/>
</profileApplication>
```

The applied stereotypes must be found between the closing tag `</uml:Package>` and the closing tag `</xmi>` like:

```
<datafoodconsortium_connector:getter xmi:id="_GW3yUNxrEeyr_asPBQgiSQ" base_Operation="_EKMr8NxWEeyr_asPBQgiSQ"/>
```

You will need the profile id and the profile `ecore:EPackage` id. To find them, open the UML profile file in a text editor:
- The profile id is contained into the `xmi:id` property of the `<uml:Profile>` opening tag like:

```
<uml:Profile xmi:version="20131001" xmlns:xmi="http://www.omg.org/spec/XMI/20131001" xmlns:ecore="http://www.eclipse.org/emf/2002/Ecore" xmlns:uml="http://www.eclipse.org/uml2/5.0.0/UML" xmi:id="_xSn38NtjEeyHhf8rtkVHoQ" name="datafoodconsortium_connector" URI="http://static.datafoodconsortium.org/uml/connector/connector.profile.uml" metaclassReference="_xSn4D9tjEeyHhf8rtkVHoQ _xSn4ENtjEeyHhf8rtkVHoQ _d-HW8NxLEeyr_asPBQgiSQ _hrrqAN2tEeyvAvnuL8ASsQ _ASxCoN5fEeyYcZ-IGE__4Q _YWlAMOA8Eeyy8cy9J23hHA">
```
- The `ecore:EPackage` id is contained into the `xmi:id` property of the first `<contents xmi:type="ecore:EPackage" ...>` like:

```
<contents xmi:type="ecore:EPackage" xmi:id="_3OuvQK70Ee2D9pavmCI82g" name="datafoodconsortium_connector" nsURI="http://static.datafoodconsortium.org/uml/connector/connector.profile.uml" nsPrefix="datafoodconsortium_connector">
```

__You must ensure that in your broken UML file:__
- The `<xmi>` opening tag contains a `xsi:schemaLocation` property pointing to the profile filename followed by the profile `ecore:EPackage` id: `connector.profile.uml#<profile's EPackage xmi:id>`. Example:

```
<xmi ... xsi:schemaLocation="http://static.datafoodconsortium.org/uml/connector/connector.profile.uml connector.profile.uml#_3OuvQK70Ee2D9pavmCI82g">
```
- The `<ProfileApplication>` references the `ecore:EPackage` id like:

```
<eAnnotations xmi:id="_ZaEk8K76Ee27bvIjdr5biQ" source="http://www.eclipse.org/uml2/2.0.0/UML">
    <references xmi:type="ecore:EPackage" href="connector.profile.uml#_CgHckK74Ee2D9pavmCI82g"/>
</eAnnotations>
```
- The `<ProfileApplication>` contains a `<appliedProfile>` pointing to the profile id like:

```
<appliedProfile href="connector.profile.uml#_xSn38NtjEeyHhf8rtkVHoQ"/>
```