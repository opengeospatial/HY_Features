## 7. The HY_Features common hydrologic feature model (normative)

### 7.1 The HY_Features conceptual model

This standard defines the HY_Features conceptual model as a standard for the identification and description of hydrologic features reflecting both hydrologic significance as well as topological connectivity of hydrologic features by defining the fundamental relationships between the major components of the hydrosphere. Core concepts are that of multiple catchment representation, of catchment hierarchy, of aggregation and segmentation of watercourses including a simple model for the positioning of features along a watercourse using a specific linear referencing system. A utilities package provide common concepts required by the hydrology model that are not hydrology-specific. 

Module identification aims to simplify the scope of each part of the conceptual model in order to improve its accessibility and to provide scope for testing. It is intended that implementations need to consider only those parts of the common model implicated by its scope. Table 1 lists the applications schema, the leaf packages included and the concepts reflected therein. 

Table 1: HY_Features modules, packages and concepts reflected

|Application schema | Concepts reflected | Leaf packages included |
| --- | --- | --- |
| HY_HydroFeature  | fundamental properties and relationships between features governed by the physical laws of Hydrology, naming and context of hydrologic features, location of hydrologic feature along a line | HY_Catchment, HY_HydrographicNetwork, HY_NamedFeature, HY_RiverPositioningSystem, HY_Storage |
| HY_AtmosphericFeature (informative) | hydrologic features  above the Earth’s land surface without complexity and detail of a rainfall-runoff model | --- |
| HY_SubsurfaceHydroFeature (informative) | hydrologic features below the Earth’s land surface without complexity and detail of a groundwater or soil moisture model | --- |
| HY_SurfaceHydroFeature | hydrlogic fetaures on the Earth’s land surface without complexity and detail of hydrologic and hydraulic models | HY_SurfaceWater, HY_SurfaceWaterConfines |
| HY_HydrometricNetwork | hydrometric network as an aggregate of logically connected hydrometric features located on or along a hydrologic feature | --- |
| HY_Utilities | common concepts required by the domain model that are not hydrology-specific such as naming and contextual relations | --- |

The conceptual model is expressed in the Geographic Information Conceptual Schema Language (ISO 19103:2005) based on the Unified Modeling Language (UML). The organization into packages and package dependencies are shown in Figure 7_16.

![Figure 16: HY_Features modules and packages](figs/fig16.png)  
Figure 16: HY_Features modules and packages  

### 7.2	The HY_Features conceptual conformance (mapping)

Conceptual conformance to the HY_Features model is a matter of being able to unambiguously identify what elements of an implementation schema map to the HY_Features model, and the ability to populate all mandatory elements of the Feature Types present in such mappings. 

The HY_Features conceptual model provides the basis for determining whether two references to hydrologic features are references to the same feature, i.e. to determine with what object types the identifiers and names may be assigned, and how to distinguish between the reference concept (e.g. a catchment) and its representation (e.g. flowpath, catchment area or boundary). 

Disparate systems describing hydrologic features may be mapped to the equivalent HY_Features definitions to disambiguate the local usage of terminology and specific implementation choices made. Equivalence here aims to the compatibility of concepts, i.e. the logical similarity which is usually an assessment based on text analyses whereby the referenced concept is considered to be the "lowest common ancestor" of the implementation concept in such a way that the essential properties are met but may be specialized in the relevant context.

An implementation schema conforming to HY_Features shall provide a formal mapping from one or more Feature Types present in the implementation schema to Feature Types defined in the HY_Features specification, including all mandatory properties defined by the realized HY_Features concept. Default values to be assumed must be specified in this mapping. Note that use of a formal encoding of HY_Features, in conjunction with conformance to */req/hy_features_conceptual_model/encoding* constitutes such a formal mapping. 

| **Requirements Class** | [/req/hy_features_conceptual_model](/req/hy_features_conceptual_model) |
| --- | --- |
| Target type | Implementation Schema |
| Name | HY_Features Conceptual Conformance |
| Dependency | [/iso/19109/] (https://inspire-twg.jrc.it/svn/iso) |
| Requirement | [/req/ hy_features_conceptual_model/mapping] (/req/ hy_features_conceptual_model/mapping) |

### 7.3	The HY_Features data conformance (encoding) 

Conformance to the HY_Features model with respect to the data refers to the encoding of the HY_Features concepts.  Designed conform to the General Feature Model - GFM (ISO19109:2006), the conceptual model defines hydrologic features representing the general “FeatureType” as of GFM. Consequently, each feature addressed in the requirements shall be understood as an instance of the GF_FeatureType (aka FeatureType) «metaclass». 

An implementation schema using Feature Types defined using the namespace of a formal encoding of HY_Features shall conform to the requirements specified by that encoding, as defined by the relevant part of HY_Features specification (e.g. HY_Features Part 2: GML encoding) 

| **Requirements Class** | [/req/hy_features_conceptual_model](/req/hy_features_conceptual_model) |
| --- | --- |
| Target type | Implementation Schema |
| Name | HY_Features Conceptual Conformance |
| Dependency | [/iso/19109/] (https://inspire-twg.jrc.it/svn/iso) |
| Requirement | [/req/ hy_features_conceptual_model/encoding] (/req/ hy_features_conceptual_model/encoding) |

(\*\*\* Need to revisit, whether applicab le to describe in conceptual conformance target \*\*\*)

Feature **identifiers** present in data encoded using a HY\_Features conformant implementation schema shall be identical wherever the same Feature instance is being encoded or referenced. This specifically applies to data available in multiple related datasets or exposed by multiple service interfaces.

Regarding **completeness**, all mandatory properties defined by a Feature Type defined in HY\_Features shall be present for each Feature instance encoded by a conformant implementation schema.

| **Requirements Class** | [/req/hy_features_content] (/req/hy_features_content) |
| --- | --- |
| Target type	| Dataset |
| Name | HY_Features Data Conformance |
| Dependency | [/req/hy_features_conceptual_model](/req/hy_features_conceptual_model) |
| Dependency | [/iso/19109/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/iso/19150/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/iso/19136/](https://inspire-twg.jrc.it/svn/iso) |
| Requirement	| [/req/ hy_features_conceptual_model/identifiers] (/req/ hy_features_conceptual_model/identifiers) |
| Requirement	| [/req/ hy_features_conceptual_model/completeness] (/req/ hy_features_conceptual_model/completeness) |

(\*\*\* Need to revisit, whether encoding requirement is still in scope !!! \*\*\* 
(\*\*\* Comment from Rob: How to handle default values – in-schema??? \*\*\*)

### 7.4 The Hydro Feature application schema

The Hydro Feature application schema defines the fundamental properties and relationships between features governed by the physical laws of hydrology. The core concept is that of a catchment and its multiple representation in the real world. Geometric representations such as catchment area, catchment boundary, a linear flowpath as well as topologic representation by hydrographic network, channel network, or the hydrometric network of stations are alternative views representing a catchment. 
The Hydro Feature schema provides a model to identify a hydrologic feature, and thus the opportunity to connect disparate representations of a catchment. By making relationships between identified features expressible in a standard form, this allows the hydrosphere to be divided into a hierarchy of hydrologically connected catchments and related phenomena contained therein, irrespective of the various representations available for these phenomena. The Hydro Feature schema contains five leaf packages: HY_NamedFeature, HY_Catchment, HY_HydrographicNetwork, HY_RiverPositioning, HY_Storage.

| **Requirements Class** | [/req/hy_abstract/*] (/req/hy_abstract/*) |
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_HydroFeature (abstract) |
| Dependency | [/req/hy_utilities/](/req/hy_utilities/) |
| Requirement	| [/req/hy_abstract/hy_namedfeature/*](/req/hy_abstract/hy_namedfeature/*) |
| Requirement	| [/req/hy_abstract/hy_catchment/*](/req/hy_abstract/hy_catchment/*) |
| Requirement	| [/req/hy_abstract/hy_network/*](/req/hy_abstract/hy_network/*) |
| Requirement	| [/req/hy_abstract/hy_positioning/*](/req/hy_abstract/hy_positioning/*) |
| Requirement	| [/req/hy_abstract/hy_storage/*](/req/hy_abstract/hy_storage/*) |

#### 7.4.1	The Named Feature model

The Named Feature model defines the hydrologic feature to which names are given through common usage. It provides a flexible approach to record multiple names and identifiers that may be assigned to an identified feature without necessarily have a formal naming model by providing a means to localize names in a cultural, political or historical context.

![Figure 17: Named Feature model (UML)](figs/fig17.png)
Figure 17: Named Feature model (UML) 

##### 7.4.1.1	Hydro feature

The HY_HydroFeature class denotes the abstraction of the complex Hydrology phenomenon through definition of feature types describing separate aspects of the hydrology phenomenon. This includes related phenomena that participate in hydrologic systems but have specific characteristics. Given the complexity of the domain, and the nature of real-world physical phenomena, for any given feature a wide range of possible characteristics, states and representations may be relevant. 

![Figure 18: Feature types describing separate aspects of the hydrology phenomenon (UML)](figs/fig18.png)
Figure 18: Feature types describing separate aspects of the hydrology phenomenon (UML)

The **identifier** attribute provides a means to assign to the hydrologic feature an unique and unambiguous identifier in a given context. An instance of HY_HydroFeature shall contain an identifier that may be used as a persistent reference to this feature.

The **name** association provides an abstract pattern shared by all hydrologic features where names are given to a feature through common usage, handle issues of cultural, political and historical variability that may occur with trans-boundary features without necessarily have a formal model. This association shall be used where a name or label is assigned to an instance of HY_HydroFeature.

The **context** association provides a general pattern to handle various forms of contextualization of hydrologic features that may be required. This allows to define in which context typical properties are attached, without having to specify every possible value or to standardise the name for it.  Using this mechanism it is not necessary to further specialize HY_Features to assign metadata, at the expense of providing complex data types that are self-describing in terms of the content they contain. 

Generally applicable characteristics assigned to an instance of HY_HydroFeature in a spatial, temporal or classification context may be specified using one or more instances of the associated context property. This may be through an inline value of a specialized data type, or by reference.

| **Requirements Class** | [/req/hy_namedFeature/hydrofeature] (/req/hy_namedFeature/hydrofeature) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_HydroFeature |
| Dependency | [/req/hy_namedFeature/hydrofeaturename] (/req/hy_namedFeature/hydrofeaturename) | 
| Dependency | [/req/hy_namedFeature/hydrofeaturecontext] (/req/hy_namedFeature/hydrofeaturecontext) | 
| Requirement |	[/req/hy_namedFeature/hydrofeature.identifier] (/req/hy_namedFeature/hydrofeature.identifier) | 
| Requirement	| [/req/hy_namedFeature/hydrofeature.name] (/req/hy_namedFeature/hydrofeature.name) | 
| Requirement	| [/req/hy_namedFeature/hydrofeature.context] (/req/hy_namedFeature/hydrofeature.context) | 

#### 7.4.2	The Catchment model

The catchment model defines a logical network of catchments each intentionally represented by geometry or topology. The catchment model defines relationships between catchments, and between catchment and its common outlet. 
The catchment model allows for the existence of catchments to be recognized, and identifiers assigned based on inflow or outflow nodes even if stream networks, areas and boundaries are not reliably determined. This is sufficient to define simplified hierarchies. It is intended that hydrological reporting applications may use this model without the full complexity and detail of scientific catchment models. 

The catchment model provides the topological concept to consider an arbitrary point on, or projected onto, the land surface as the outfall of a corresponding catchment. Positioned in the hydrographic network, this point provides the identifiable reference point to which alternative representations may refer. The logical network of catchments is the basis to  establish topological relationships between hydrometric stations without the detail of stream flow, flow conditions or cartographic interpretation. 

![Figure 19: Catchment model (UML)](figs/fig19.png)
Figure 19: Catchment model (UML)

##### 7.4.2.1	Catchment representation

The HY_CatchmentRepresentation class conceptualize the representation of the catchment by geometric data such as flowpath, catchment area, and catchment boundary, as well as toplogically by networks..With respect to geometry, the most common concepts in use in hydrology to display a catchment are defined as:

•	HY_Flowpath class with respect to the linear representation,
•	HY_CatchmentArea class with respect to the areal representation,
•	HY_CatchmentBoundary class with respect to the boundary (polygon) representing a catchment.

The HY_Network class is defined with respect to a high-order network to which hydrologic features participate allowing features that may or may not be connected at the representation level to be logically connected using this system. The hydrographic network of water bodies, the network of channels as well as the network of logically connected hydrometric stations are considered to be representation of a catchment  defined to reflect the different study areas they have. 

In related contexts other types of catchment representation may exist. Concepts that not conforms to a special type of catchment representation as defined in this standard, e.g. a time series representing the catchment at its  outflow node, or representations in multi-dimensional perspectives, may use the general catchment representation class. If present, all sub-types of catchment representation shall support the inherent *representedCatchment* property whereby each representation may be realised with an appropriate geometry type.

The *representedCatchment* association shall be used to identify the single catchment represented by geometry or network structure. Each catchment representation shall be implemented with an appropriate geometric representation.

| **Requirements Class** | [/req/hy_catchment/catchmentrepresentation] (/req/hy_catchment/catchmentrepresentation) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_CatchmentRepresentation | 
| Dependency | [/req/hy_catchment/catchment](/req/hy_catchment/catchment) | 
| Requirement	| [/req/hy_catchment/catchmentrepresentation.representedcatchment](/req/hy_catchment/catchmentrepresentation.representedcatchment) | 

##### 7.4.2.2	Catchment

The HY_Catchment class defines the catchment as the unit wherein all hydrologic processes take place, without an identification of the hydrologic determination. HY_Catchment is a specialization of the general HY_HydroFeature class. It inherits identifier, name and context properties from the generalization. The HY_Catchment class carries the associations: *containing Catchment*, *upstreamCatchment*, *jointCatchment*, *outflowNode*, *inflowNode*, *boundaryLine*.

The **containingCatchment** (Fig 20a) association provides a means to describe the nesting of catchments in a simple “is-in” containment hierarchy as typically used for high order organization of management and reporting units. If required, this association shall be used to identify the catchment therein the relevant catchment is nested.

The **upstreamCatchment** (Fig 20b)  association provides a means to describe the basin immediately upstream of the relevant basin without knowing a particular inflow location. Note that this defines the topological hierarchy between basins; the nesting is inherited from the catchment class. This association shall be used to identify a basin immediately upstream of the relevant basin.

The **jointCatchment** (Fig 20c)  association provides a means to describe the interaction of the catchment with another catchment crossing an arbitrary boundary line. This line may be the divide separating adjacent  catchments, or the diffuse divide between non-delineated sub catchments within an encompassing catchment, or a fictive line between distant catchments. If required, this association shall be used to identify the catchments interacting across a boundary line. The  boundary line may be described by summits which may be located in the catchment network as inflow or outflow nodes.

![Figure 20: Catchment hierarchy properties](figs/fig20.png)
Figure 20: Catchment hierarchy properties

a) Catchment in question (C2) is part of the containing catchment (C), b) C2 has an upstream catchment (C3), c) sub-catchment of C2 has joint sub-catchment 

The **outflowNode** (Fig 21b)  association provides a pattern to identify the location of outflow of the contributing basin. This allows to identify the downstream basin whereby the inflow location coincides with the outflowNode. This association shall be used to identify the location where water flows out of the relevant basin. To sufficiently describe an upstream-downstream-relation, the outflowNode shall coincide with the inflowNode of a downstream basin

The **inflowNode** (Fig 21c) association provides a pattern to identify the location of inflow to the receiving basin. This allows to identify the upstream basin whereby the outflow location coincides with the inflowNode. This association shall be used to identify the location where water flows into the relevant basin. To sufficiently describe a upstream-downstream-relation, the inflowNode shall coincide with the outflowNode of a upstream basin. 

The **boundaryLine** (Fig 21a) association provides a means to identify the conceptual line bounding the catchment. This association shall be used to describe the boundary line by infinite summits which may be located in the catchment network as inflow or outflow nodes.

![Figure 21: Catchment identification properties](figs/fig21.png)
Figure 21: Catchment identification properties

a) Catchment in question (C2) has an outflow node (N2), b) C2 has an inflow Node (N3), c) C2 has a boundary line (red) with an outfall (N2) and a summit (N3)

| **Requirements Class** | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_Catchment |
| Dependency | [/req/hy_namedFeature/hydrofeature] (/req/hy_namedFeature/hydrofeature) | 
| Dependency | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) | 
| Dependency | [/req/hy_catchment/outfall] (/req/hy_catchment/outfall) |
| Dependency | [/req/hy_catchment/watersheddivide] (/req/hy_catchment/watersheddivide) |
| Requirement |	[/req/hy_catchment/catchment.containingcatchment] (/req/hy_catchment/catchment.containingcatchment) | 
| Requirement |	[/req/hy_catchment/catchment.upstreamcatchment] (/req/hy_catchment/catchment.upstreamcatchment) | 
| Requirement |	[/req/hy_catchment/catchment.jointcatchment] (/req/hy_catchment/catchment.jointcatchment) | 
| Requirement |	[/req/hy_catchment/catchment.outflownode] (/req/hy_catchment/catchment.outflownode) | 
| Requirement |	[/req/hy_catchment/catchment.inflownode] (/req/hy_catchment/catchment.inflownode) | 
| Requirement |	[/req/hy_catchment/catchment.boundaryline] (/req/hy_catchment/catchment.boundaryline) | 

##### 7.4.2.3	Catchment aggregate

The HY_CatchmentAggregate class specializes the general HY_Catchment class with respect to a set of hydrologically discrete (dendritic) catchments, all at the same hierarchy level without any overlap, to be nested in an encompassing catchment at the next upper hierarchy level. This allows to describe multiple inflow into a catchment (aggregate) provided by several hydrologically discrete sub-catchments each contributing to the common outflow of the catchment (aggregate). 

Any catchment aggregate may be contained in a containing catchment aggregate at the next higher level, which consists of many neighboring catchment aggregates. This does not necessarily implies a series of containing catchments, but rather a jumping to the “highest” upper-level system as typically used for reporting purposes.

The HY_CatchmentAggregate class inherits the *containingCatchment*, *upstreamCatchment*, *jointCatchment*, *outflowNode*, *inflowNode* and *boundaryLine* properties, and carries one association: *subCatchment*.

| **Requirements Class** | [/req/hy_catchment/catchmentaggregate] (/req/hy_catchment/catchmentaggregate) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_CatchmentAggregate |
| Dependency | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) | 
| Dependency | [/req/hy_catchment/dendriticcatchment] (/req/hy_catchment/dendriticcatchment) | 
| Requirement |	[/req/hy_catchment/catchmentaggregate.subcatchment] (/req/hy_catchment/catchmentaggregate.subcatchment) | 

##### 7.4.2.4	Dendritic catchment

The HY_DendriticCatchment class specializes the general HY_Catchment class with respect to the hydrologically discrete catchment, which is determined by a single common outlet to which all waters flow and may have an identified inflow node, which coincides with the outflow node of an upstream dendritic catchment.  This class denotes the catchment as the link between an inflow node and an outflow node which allows to describe the dendritic network by upstream-downstream relationships, without knowing the complex hydrology between inflow and outflow nodes. This concept requires a stable identifier that is not merely a function of an arbitrary delineation of the surface, and that catchments are delineated within a simple tree hierarchy. More complex structures may be described as representations using HY_Network representation pattern.

The HY_CatchmentAggregate class inherits the *containingCatchment*, *upstreamCatchment*, *jointCatchment*, *outflowNode*, *inflowNode* and *boundaryLine* properties, and carries one association: *encompassingCatchment*. 

The **code** attribute may be used to assign to the dendritic a unique identifier in given context. If required, the code shall be implemented using a controlled classification or coding system. Example: WMO Basin Codes.  

The **encompassingCatchment** association provides a means to describe the catchment aggregate to which the dendritic catchment contributes flow either from its identified inflow node to the common outlet, or in join with other sub-catchments crossing a divide intern of the encompassing aggregate. This association shall be used to identify the catchment aggregate  encompassing the dendritic catchment.

| **Requirements Class** | [/req/hy_catchment/dendriticcatchment] (/req/hy_catchment/dendriticcatchment) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_DendriticCatchment |
| Dependency | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) | 
| Dependency | [/req/hy_catchment/catchmentaggregate] (/req/hy_catchment/catchmentaggregate) | 
| Requirement |	[/req/hy_catchment/dendriticcatchment.encompassingcatchment] (/req/hy_catchment/dendriticcatchment.encompassingcatchment) |

##### 7.4.2.5	Outfall

...
