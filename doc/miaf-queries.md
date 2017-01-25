## queries in vsd meta onto

### list the genders with abbreviation and label

```
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX vsd: <http://www.virtualskeleton.ch/vsd#>

SELECT DISTINCT ?uri ?label ?abbr

FROM <http://www.virtualskeleton.ch/data/vsd>

WHERE {
?uri <http://www.w3.org/2000/01/rdf-schema#subClassOf> <http://purl.obolibrary.org/obo/PATO_0000047> .
?uri <http://www.w3.org/2000/01/rdf-schema#label>   ?label .
?uri vsd:abbreviation ?abbr .
}

LIMIT 100
```

### and the modalities

```
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX vsd: <http://www.virtualskeleton.ch/vsd#>

SELECT DISTINCT ?uri ?label ?abbr

FROM <http://www.virtualskeleton.ch/data/vsd>

WHERE {
?uri <http://www.w3.org/2000/01/rdf-schema#subClassOf> vsd:mr-sequence-acronym .
?uri <http://www.w3.org/2000/01/rdf-schema#label>   ?label .
?uri vsd:abbreviation ?abbr .
}
```

### list the properties of a class

```
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX vsd: <http://www.virtualskeleton.ch/vsd#>

SELECT DISTINCT ?p ?label 

FROM <http://www.virtualskeleton.ch/data/vsd>

WHERE {
vsd:mr-sequence-acronym ?p ?label
}
```

### PRefix list

```
PREFIX rdf:     <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX owl:     <http://www.w3.org/2002/07/owl#>
PREFIX rdfs:    <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd:     <http://www.w3.org/2001/XMLSchema#>
PREFIX dct:     <http://purl.org/dc/terms/>
PREFIX foaf:    <http://xmlns.com/foaf/0.1/>
PREFIX miaf:    <http://www.virtualskeleton.ch/MIAF.owl#>
PREFIX ns1:     <http://virtualskeleton.ch/data/fma>
PREFIX fma:     <http://purl.org/sig/ont/fma/>
PREFIX odrl:    <http://www.w3.org/ns/odrl/2/>
PREFIX mrda:    <http://neurolog.unice.fr/ontoneurolog/v3.0/ontoneurolog-mr-dataset-acquisition.owl#>
PREFIX obo:     <http://purl.obolibrary.org/obo/>
PREFIX obi:     <http://purl.obolibrary.org/obo/OBI_>
PREFIX ero:     <http://purl.obolibrary.org/obo/ERO_>
PREFIX obcs:    <http://purl.obolibrary.org/obo/OBCS_>
PREFIX pato:    <http://purl.obolibrary.org/obo/PATO_>
PREFIX uberon:  <http://purl.obolibrary.org/obo/uberon/core#>
PREFIX edam:    <http://edamontology.org/>
PREFIX sio:     <http://semanticscience.org/resource/>
PREFIX bim:     <http://cbakerlab.unbsj.ca:8080/sebi/BIM.owl#>
PREFIX birnlex: <http://bioontology.org/projects/ontologies/birnlex#>
PREFIX csp:     <http://purl.bioontology.org/ontology/CSP/>
PREFIX dcm:     <http://dicom.nema.org/resources/ontology/DCM/>
PREFIX vocab:   <http://open.vocab.org/terms/>
PREFIX lic:     <http://purl.org/NET/rdflicense/>
PREFIX sedi:    <http://semantic-dicom.org/dcm#>
PREFIX unit:    <http://qudt.org/vocab/unit#>
PREFIX ncit:    <http://ncicb.nci.nih.gov/xml/owl/EVS/Thesaurus.owl#>
```


### all entries with type and class and uri

```

SELECT DISTINCT *
WHERE {
?individual rdf:type ?type .
OPTIONAL { ?type rdfs:subClassOf ?class }
}
ORDER BY ?class

```

### instances of a class with abbreviation: get all license indstance

```

SELECT DISTINCT ?uri ?abbr

WHERE {

?uri rdf:type odrl:Policy .
?uri uberon:ABBREVIATION ?abbr

}

ORDER BY ?abbr
```

#### Other properties for
- Handedness: `<http://purl.bioontology.org/ontology/SNOMEDCT/57427004>`
- Gender: `obo:PATO_0000047`
- License: `odrl:Policy`
- MR contrast: `mrda:MR-image-contrast`
- segmentation method: `miaf:00000347`
- ethnic group: `obo:ERO_0001972`

### Subclasses with abbreviations: get all mr-sequence acronyms

```
SELECT DISTINCT ?uri ?abbr
WHERE {

?class rdfs:subClassOf* miaf:00000014 .
?uri rdf:type ?class .
?uri uberon:ABBREVIATION ?abbr .

}

ORDER BY ?abbr

## can be use to check if abbr is missing OPTIONal {?uri uberon:ABBREVIATION ?abbr } .
```


#### other properties
- title: foaf:honorificPrefix
- 


### object properties with display label

```
SELECT DISTINCT ?s ?disp ?uri ?label ?abbr 

WHERE {


?s rdf:type owl:DatatypeProperty .
?s rdfs:label ?label .
?s miaf:00000376 ?disp .

OPTIONAL {
    ?s uberon:ABBREVIATION ?abbr .
    }
}

ORDER BY ?disp

## can be use to check if abbr is missing OPTIONal {?uri uberon:ABBREVIATION ?abbr } .
```


### show mappings list

```
SELECT DISTINCT ?pURI ?pLabel ?mURI ?mLabel 

WHERE {

?pURI  miaf:4df62452_761a_4d13_9c77_98e09ab4e66c  ?mURI .
?pURI rdfs:label ?pLabel .
?mURI rdfs:label ?mLabel .
FILTER (lang(?mLabel) = "en" )
}

ORDER BY ?mLabel
```

### show all object properties for object type raw images

```
raw_image: miaf:c56d337f_b0af_4860_92c6_9b134863a5d8


SELECT DISTINCT ?label ?o ?p

WHERE {

miaf:c56d337f_b0af_4860_92c6_9b134863a5d8 ?p ?o .
?p a owl:ObjectProperty .
?o rdfs:label ?label .

}

ORDER BY ?label
```

### showl object properties of type raw which are has_default_property

```
SELECT DISTINCT ?o ?name

WHERE {
miaf:c56d337f_b0af_4860_92c6_9b134863a5d8 ?p ?o .
?p a owl:ObjectProperty ;
    rdfs:label ?label .
FILTER (regex(?label, "has_default_property") )

?o rdfs:label ?name .


}

ORDER BY ?name
```

### show mappings with related label of the mapping 
this gets all the available (properties / defaultproperties) for object type segmentation

```
    SELECT DISTINCT ?p ?label ?o ?name ?mlabel ?map

WHERE {
miaf:5d1ff8d5_c3b7_40d9_804e_683f2700e8f6 ?p ?o .
?p a owl:ObjectProperty ;
    rdfs:label ?label .

?o rdfs:label ?name .
?o miaf:4df62452_761a_4d13_9c77_98e09ab4e66c ?map .
?map miaf:928cadf1_8d82_4177_87c9_51b5b840616e ?mlabel .

}

ORDER BY ?label

```


## selecting all mapping and show display label and type and range
```
SELECT DISTINCT ?pURI ?pLabel ?mURI ?mLabel ?rdftype ?rtype ?r ?dsip

WHERE {

?pURI  miaf:4df62452_761a_4d13_9c77_98e09ab4e66c  ?mURI .
?pURI rdfs:label ?pLabel .
?pURI rdf:type ?rdftype .
?mURI rdfs:range ?r .
?mURI rdfs:label ?mLabel .
?mURI rdf:type ?rtype .
  ?mURI miaf:928cadf1_8d82_4177_87c9_51b5b840616e ?dsip .
FILTER (lang(?mLabel) = "en" )
}

ORDER BY ?mLabel
```