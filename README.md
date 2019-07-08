# OGC WaterML 2: Part 3 - Surface Hydrology Features (HY_Features) - Conceptual Model

HY\_Features has been published as part of the [WaterML2 suite](https://www.opengeospatial.org/standards/waterml) of standards. More information about the WaterML2 standards can be found on the [Hydrology Domain Working Group wiki](https://external.opengeospatial.org/twiki_public/HydrologyDWG/WebHome)  

## [Access the specification.](https://docs.opengeospatial.org/is/14-111r6/14-111r6.html)

## [Access the schema.](http://docs.opengeospatial.org/is/14-111r6/uml/)

### [Primer Slides.](https://opengeospatial.github.io/HY_Features/HY_Features_primer/HY_Features_Primer.html)  

### [OGC Definitions Server](https://www.opengis.net/def/appschema/hy_features/hyf/) 

**SKOS and OWL views of HY\_Features code lists, classes, and properties can be accessed from the OGC Definitions Server.**  
The entry point to explore the definitions server is here: [https://www.opengis.net/def/appschema/hy_features/hyf/](https://www.opengis.net/def/appschema/hy_features/hyf/)  

The HY\_Features specification provides a conceptual model expressed in UML. There are multiple ways this can be made available to systems implementing these concepts. The most general view is to provide a set of definitions to ground elements of physical data models in the underlying semantics of the HY\_Features models. To make these definitions accessible, URI (Web address) identifiers for each concept defined by HY\_Features is needed.  Such a facility is provided by the OGC Definitions Server, which supports the OGC URI publication policies and provides human readable (HTML) and machine readable (JSON, XML, etc.) versions of definitions.

Each class (type of feature) and property (association) is provided with a unique URI derived from the UML model using rules defined by ISO19150 [1].

The Definitions Server then provides multiple options for accessing the description and model behind these elements, using these URIs:
1) SKOS (Simple Knowledge Organization System) - a W3C standard for definitions and taxonomies
2) OWL (W3C Web Ontology Language) providing more detail about relationships between defined entities
3) the original UML document in the XMI interchange format

different forms are available through a combination of profiles (views) and encodings (MIME types) - so for example the SKOS view can be delivered using JSON encoding.

The formalisation of the OWL model is under review and intended to be published as an adjunct specification to the HY_Features conceptual model.

### UML Model

An HTML export of the HY\_Features UML model is available on this web page. It is available in several packages [described in detail in section 7.1 of the specification](https://docs.opengeospatial.org/is/14-111r6/14-111r6.html#_the_hy_features_conceptual_model). These html pages contain UML diagrams used in the HY\_Features specification and hyperlinked descriptive content for classes and relations included in the model.  

[HY\_Features_Model: relation to ISO and OGC Standards](https://opengeospatial.github.io/HY_Features/HTML_HYF/HY_Features_Model/)  
[HY\_HydroFeature: catchment / nexus relationships, naming, and river referencing](https://opengeospatial.github.io/HY_Features/HTML_HYF/HY_HydroFeature/)  
[HY\_SurfaceHydroFeature: waterbodies, bathymetry, and networks](https://opengeospatial.github.io/HY_Features/HTML_HYF/HY_SurfaceHydroFeature/)  
[HY\_HydrometricNetwork: hydrometric features relationship to catchments](https://opengeospatial.github.io/HY_Features/HTML_HYF/HY_HydrometricNetwork/)  

[1] ISO 19150-2:2015 Geographic information -- Ontology -- Part 2: Rules for developing ontologies in the Web Ontology Language (OWL)

