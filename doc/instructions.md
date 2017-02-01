

## Strcuture

### SMIR classes

`Domain entity -> Independent entity`

-   Generic Object -> Object
-   File
-   Group
-   User

### Internal classes

`Domain entity -> Internal entity`

Is used internal representation of VSD framework structures

- Mapping
- Status
- Modificator

### Objects classes

`Domain entity -> Object property`

Property values that are used to annotate an object with a predefined values. The terms are collected from various sources and its structure recreated. The last level (things to use to annotate) are most likely to be instances. Here a list of object property terms:

-   Gender (instances):
-   Title (honorific Prefix, classes)
-   License (Policy, instances):
-   Segmentation method (instances)
-   MR contrast (instances)
-   Mr sequences acronyms (instances)
-   Modalities (classes)
-   Ethnic group (instances)
-   Format (classes)
-   Dominance (Handedness)
-   Organism (classes)
-   Units (instances)
-   Anatomical region -> FMA





###  How to add "value lists" <span id="value"></span>

- create a category class in `Object property`
- add the list as instance
- if the list is has subcategories, use the subclasses and add `Abbreviation` to the terms that should appear in the list


### add to object types <span id="types"></span>
to define is a new predicate is default or at least known to the type, add a object property:

- has_default_property or has_property + the new predicate

![typeimg](assets/typeimg.png)


## Add new object property

we have sometimes Label and Abbreviation, use it as rdfs:Label (Abbreviation)

example for sequence: `Turbo Spin Echo (TSE)`

## Add new predicate (label, attribute to VSD) with Protege

** make sure the new entity option is using the setting "use iri of active ontology" **

![protege settings](assets/settings.png)

first, decide what typ of property:

1. **annotation property**: if consistent, consists of classes or is a generic label like selfUrl
2. **object property**: if multiple instances are need or mappes other instances (value lists, icenses, modality etc.)
3. **data porperty**: anything with a datatype string, integer, uri etc. most commonly used

second, look for ontology term

- load ontologies from the "external" github folder
- http://aber-owl.net/ontology
- https://www.ebi.ac.uk/ols/
- http://bioportal.bioontology.org/
- http://swoogle.umbc.edu

if you have a list of predefined values: add it to the object property class. last level (things to use to annotate) are gooing most likely to be instances

all properties have a

```
rdfs:label -> label of the property
DisplayLabel -> how to display it to the user (if to be displayed)
add a comment to clarify the meaning
all entries are type literal@en
```

third, create the mapping

- add instance of "Mapping"
- label: "p_object_new_property"
- annotation property: MappingTo and add there the Property previously created
- add property assertion `has_property_modificator` [user|system|file]
- now add the mapping to the objects type `has_property` or `has_default_property`

## addon: default mappings for new object types

change `db7925ac_a8f1_47a8_860f_0cdb9ed18b5f` to the desired indivdual (object type) and add it directly to the owl for a new object type

```xml
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#a4330bca_7b02_432d_8d89_787c0027cd0e"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#ac1e9418_cf1e_471b_9e44_ea7f71069698"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#b3081f13_637b_4319_befb_8a623de26b31"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#cb25f8e6_95b0_4c23_b1d4_0128b7c337a5"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#f63fc9ba_3ee2_4d3c_aaec_6d268bfd0097"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#0e0500a5_2492_4f95_a055_1c969a6552fe"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#10dcdaf9_6bdb_4b1f_bda7_2c46e5f1c29d"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#213634ed_fec9_4f36_9e79_228f46642e87"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#34127d03_aea2_4a24_871c_6f7e9ac72823"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#57930446_dc48_4445_9615_d0e08f3a7dac"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#8a20edb0_c831_4dbf_9e06_fec8c583a39e"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#8bcdf331_a3e2_4764_bc44_40d0f22d856f"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#8da83cb0_8c7f_4de3_8f33_53806f782f79"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#859670b5_8337_4f2d_8473_a2761b49e09f"/>
    </ObjectPropertyAssertion>
    <ObjectPropertyAssertion>
        <ObjectProperty IRI="#d88fc04d_8920_4f54_ad17_b9094e13865a"/>
        <NamedIndividual IRI="#db7925ac_a8f1_47a8_860f_0cdb9ed18b5f"/>
        <NamedIndividual IRI="#908630bc_610b_47cd_9cc1_ad7b2e2a1e75"/>
    </ObjectPropertyAssertion>


find some queries here `misc/miaf-queries.md`