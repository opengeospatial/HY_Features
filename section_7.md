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

(\*\*\* Need to revisit, whether applicable to describe in conceptual conformance target \*\*\*)

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

The Hydro Feature application schema defines the fundamental properties and relationships between features governed by the physical laws of hydrology. The core concept is that of a catchment and its multiple representation in the real world (see section 6.2 of this standard). Catchment area, catchment boundary, and linear flowpath as well as a cartographic visualisation are defined to reflect the most concepts in use to represent of catchment. 

The Hydro Feature schema conceptualize the abstraction of the complex Hydrology phenomenon through definition of feature types each describing separate aspects of the hydrology phenomenon. This includes related phenomena that participate in hydrologic systems but have specific characteristics. Figure 18 shows the special features types describing separate aspects of the hydrology phenomenon. Given the complexity of the domain, and the nature of real-world physical phenomena, for any given feature further specialisation as well as a wide range of possible characteristics, states and representations may be relevant. 

![Figure 18: Feature types describing separate aspects of the hydrology phenomenon (UML class diagram)](figs/fig18.png)
Figure 18: Feature types describing separate aspects of the hydrology phenomenon (UML class diagram)

The Hydro Feature schema provides a model to identify a hydrologic feature, and thus the opportunity to connect disparate representations. By making relationships between identified features expressible in a standard form, this allows the hydrosphere to be divided into a hierarchy of hydrologically connected catchments and related phenomena contained therein, irrespective of the various representations available for these phenomena. The Hydro Feature schema contains five leaf packages: HY_NamedFeature, HY_Catchment, HY_HydrographicNetwork, HY_RiverPositioning, HY_Storage.

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

The Named Feature model defines the hydrologic feature basically as a feature to which names are given through common usage (Figure 17). It provides a flexible approach to record multiple names and identifiers that may be assigned to an identified feature without necessarily have a formal naming model by providing a means to localize names in a cultural, political or historical context. Each  special hydrologic feature type (Figure 18) inherits the general relationships defined for the HY_HydroFeature class. The HY_HydroFeature class carries the properties: *identifier*, *name*, and *context*.

![Figure 17: Named Feature model (UML class diagram)](figs/fig17.png)
Figure 17: Named Feature model (UML class diagram) 

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

The catchment model (Figure 19) defines a logical network of catchments each intentionally represented by a geometric shape or by networks displayed using these. The catchment model supports the multiple representation of a catchment and allows for the existence of catchments to be recognized, and identifiers assigned based on inflow or outflow nodes. This is sufficient to define a simple hierarchy (see section 6.3.1) and a topological network of catchments (see section 6.3.2), allowing to establish topological relationships between hydrometric stations located in the catchment network, without the details of stream network.

The catchment model provides the topological concept to consider any location on, or projected onto, the land surface as the inflow or outflow node of a corresponding catchment. Located in the catchment network, alternative representations may refer to that identifiable reference location. Using a linear river reference system (as defined in section 7.4.4) an arbitrary location can be placed along the flowpath representation relative to such a referent. This allows to create a flowline network from a sequence of catchment representations 'drawn' between inflow and outflow nodes. Special types of one- and two-dimensional geometric representations in common use in hydrology are defined to support this. 

![Figure 19: Catchment model (UML class diagram)](figs/fig19.png)
Figure 19: Catchment model (UML class diagram)

##### 7.4.2.1	Catchment representation
The HY_CatchmentRepresentation class conceptualize the representation of a catchment using geometric shapes of different dimension as well as the cartographic portrayal of typical networks created from these (see section 6.3.1). Special types of catchment representation are: 

•	HY_Flowpath class with respect to line-shaped representations,
•	HY_CatchmentArea class with respect to area-shaped representations,
•	HY_CatchmentBoundary class with respect to polygon shapes representing a catchment.

Another special type HY_NetworkCartography is defined with respect to the cartographic representation of a high-order network to which hydrologic features participate. This will allow features that are logically connected in the hydrographic network of water bodies, a network of channels or a network of hydrometric stations to be portrayed in thematic maps displaying the network that in its entirety, separately or as set of layers, represents the catchment. 
[\*\*\*do we want mention here other possible networks such as a network of related aquifers, but not in scope of this standard with reference to the conceptual model capturing the specifics of related aquifers, provided with the GroundwaterML 2.0 under development', see annex ..., insert reference to GWML2\*\*\*]. 

Data products that not conforms to the special types defined in this standard, for instance representations in more-dimensional perspectives, or a in time, may use the general HY_CatchmentRepresentation class, whereby each representation may be realised with an appropriate geometry type. If present, all sub-types of catchment representation shall support the inherent *representedCatchment* property whereby each representation may be realised with an appropriate geometry type. HY_CatchmentRepresentation carries two properties: *dimensionality* and  *representedCatchment*:

The *dimensionality* attribute provides a number or term indicating the dimensionality of a geometric shape. If required, this attribute shall be used to describe the geometric dimension used to portray the represented catchment. 
[\*\*\*agreement on this attribute in the swg provided\*\*\*] 

The *representedCatchment* associates describes the multiple representation of a catchment in various data sets and data products. If required, this association shall be used to relate a particular data set or data product to the one, and only one, catchment that is represented. 

| **Requirements Class** | [/req/hy_catchment/catchmentrepresentation] (/req/hy_catchment/catchmentrepresentation) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_CatchmentRepresentation | 
| Dependency | [/req/hy_catchment/catchment](/req/hy_catchment/catchment) | 
| Requirement	| [/req/hy_catchment/catchmentrepresentation.dimensionality](/req/hy_catchment/catchmentrepresentation.dimensionality) | 
| Requirement	| [/req/hy_catchment/catchmentrepresentation.representedcatchment](/req/hy_catchment/catchmentrepresentation.representedcatchment) | 


##### 7.4.2.2	Catchment
The HY_Catchment class defines the catchment and its basic relationships such as catchmant hierarchy and topology as described in section 6.3. HY_Catchment specializes the general HY_HydroFeature class; from this generalization it inherits *identifier*, *name* and *context* properties. HY_Catchment carries the associations: *containing Catchment*, *conjointCatchment*, *upstreamCatchment*,  *outflowNode*, *inflowNode*, *boundaryLine*.

The **containingCatchment** association describes the nesting of catchments in a simple “is-in” containment hierarchy as typically used for high-order organization of management and reporting units. If required, this association shall be used to identify the catchment wherein the catchment is nested.

The **conjointCatchment** association describes the interaction of a catchment with another catchment crossing an arbitrary boundary line. This line may be the divide separating adjacent catchments, or the diffuse divide between non-delineated sub-catchments within an encompassing catchment, or a fictive line between distant catchments. If required, this association shall be used to identify the interacting catchments. 

The **upstreamCatchment** association describes the basin immediately upstream of the relevant basin. This allows to describe the interaction between catchments at inflow nodes which are identified outflow node of an upstream catchment. If required, this association shall be used to identify inflow into the catchment when a particular inflow location is not known, e.g. from headwater and tributary catchments.

The **outflowNode** association describes the location where water flows out of a contributing catchment. This allows to identify the catchment whose inflow location coincides with the outflow node, and to describe an upstream-downstream relation. If required, this association shall be used to identify the location to which the catchment contributes flow, and from where a downstream catchment receives flow from upstream. 

The **inflowNode** association describes the location where water flows into a receiving catchment. This allows to identify the catchment whose the outflow location coincides with the inflow node, and to describe an downstream-upstream relation. If required, this association shall be used to identify the location to where the catchment receives flow, and to which an upstream catchment contributes flow. 

The **boundaryLine** association describes the line bounding the catchment associating an infinite number of nodes on line each to be located in the catchment network. If required, this association shall be used to identify a location on the divide to place the outflow of a contributing catchment when a particular outflow location is not known. 

| **Requirements Class** | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_Catchment | 
| Dependency | [/req/hy_namedFeature/hydrofeature] (/req/hy_namedFeature/hydrofeature) |
| Dependency | [/req/hy_catchment/catchment](/req/hy_catchment/catchment) | 
| Dependency | [/req/hy_catchment/catchment](/req/hy_catchment/catchment) | 
| Dependency | [/req/hy_catchment/outfall](/req/hy_catchment/outfall) | 
| Dependency | [/req/hy_catchment/divide](/req/hy_catchment/divide) | 
| Requirement	| [/req/hy_catchment/catchment.containingcatchment](/req/hy_catchment/catchment.containingcatchment) | 
| Requirement	| [/req/hy_catchment/catchment.jointcatchment](/req/hy_catchment/catchment.jointcatchment) | 
| Requirement	| [/req/hy_catchment/catchment.upstreamcatchment](/req/hy_catchment/catchment.upstreamcatchment) |
| Requirement	| [/req/hy_catchment/catchment.outflownode](/req/hy_catchment/catchment.outflownode) |
| Requirement	| [/req/hy_catchment/catchment.inflownode](/req/hy_catchment/catchment.inflownode) |
| Requirement	| [/req/hy_catchment/catchment.boundaryline](/req/hy_catchment/catchment.divide) |

##### 7.4.2.3	CatchmentAggregate
The HY_CatchmentAggregate class specializes the HY_Catchment class with respect to a set of dendritic catchments, arranged in an encompassing catchment at the next upper hierarchy level without any spatial overlap. This allows to describe multiple inflows into a catchment aggregate through several hydrologically discrete sub-catchments having a single inflow, and contributing to the common outflow of the catchment aggregate. 

A catchment aggregate may be part of a containing catchment at the next higher hierarchy level, which consists of many of those neighbouring catchments. This does not necessarily implies a series of containing catchments, but alloww a jumping to the 'highest' upper-level system as typically used for reporting purposes. The HY_CatchmentAggregate class inherits from generalization the *containingCatchment*, *upstreamCatchment*, *jointCatchment*, *outflowNode*, *inflowNode* and *boundaryLine* properties, and carries two properties: *exorheicDrainage* and *endorheicDrainage*.

The **exorheicDrainage** association describes a catchment, part of the aggregate, which is connected to other catchments through its inflow/outflow node.

The **endorheicDrainage** association describes a catchment, part of the aggregate, which is not connected to other catchments through its inflow/outflow node.

| **Requirements Class** | [/req/hy_catchment/catchmentaggregate] (/req/hy_catchment/catchmentaggregate) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_CatchmentAggregate | 
| Dependency | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) |
| Dependency | [/req/hy_catchment/dendriticcatchment](/req/hy_catchment/dendriticcatchment) | 
| Dependency | [/req/hy_catchment/interiorcatchment](/req/hy_catchment/interiorcatchment) | 
| Requirement	| [/req/hy_catchment/catchmentaggregate.exorheicdrainage](/req/hy_catchment/catchmentaggregate.exorheicdrainage) | 
| Requirement	| [/req/hy_catchment/catchmentaggregate.endorheicdrainage](/req/hy_catchment/catchmentaggregate.endorheicdrainage) | 


##### 7.4.2.4	DendriticCatchment
The HY_DendriticCatchment class specializes the general HY_Catchment class with respect to a hydrologically discrete catchment, which is determined by a single common outlet to which all waters flow. This class denotes the catchment as the topological link between an inflow node and an outflow node allowing catchments to be connected in a dendritic network by upstream-downstream relationships, without knowing the complex hydrology between inflow and outflow nodes. This concept requires a stable identifier that is not merely a function of an arbitrary delineation of the surface, and that catchments are delineated within a simple tree hierarchy. The HY_DendriticCatchment class inherits from generalization the *containingCatchment*, *upstreamCatchment*, *jointCatchment*, *outflowNode*, *inflowNode* and *boundaryLine* properties, and carries two properties: *code* and *encompassingCatchment*. 

The **code** attribute may be used to assign to the dendritic a unique identifier in given context. If required, the code shall be implemented using a controlled classification or coding system. Example: WMO Basin Codes.  

The **encompassingCatchment** association describes the catchment aggregate wherein the dendritic catchment is sub-catchment which is  hydrologically connected to other sub-catchments. If required, this association shall be used to identify the catchment to which the dendritic catchment contributes flow to the common outlet, either from a single identified inflow, or in join with other sub-catchments crossing a divide intern of the encompassing aggregate.

| **Requirements Class** | [/req/hy_catchment/dendriticcatchment] (/req/hy_catchment/dendriticcatchment) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_DendriticCatchment |
| Dependency | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) | 
| Dependency | [/req/hy_catchment/catchmentaggregate] (/req/hy_catchment/catchmentaggregate) | 
| Requirement |	[/req/hy_catchment/dendriticcatchment.code] (/req/hy_catchment/dendriticcatchment.code)
| Requirement |	[/req/hy_catchment/dendriticcatchment.encompassingcatchment] (/req/hy_catchment/dendriticcatchment.encompassingcatchment) 

##### 7.4.2.5	InteriorCatchment
The HY_InteriorCatchment class specializes the general HY_Catchment class with respect to a hydrologically discrete catchment, which is generally not connected to other catchments. This class describes the interior catchment as catchment enveloped by other catchments to which it may temporary contribute. The HY_InteriorCatchment class inherits from generalization the *containingCatchment*, *upstreamCatchment*, *jointCatchment*, *outflowNode*, *inflowNode* and *boundaryLine* properties, and carries one association: *envelopingCatchment*. 

The **envelopingCatchment** association describes the catchment aggregate surrounding the interior sub-catchment. If required, this association shall be used to identify the catchment to which the interior catchment temporary contributes flow to the common outlet. 

| **Requirements Class** | [/req/hy_catchment/interiorcatchment] (/req/hy_catchment/interiorcatchment) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_InteriorCatchment | 
| Dependency | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) |
| Dependency | [/req/hy_catchment/catchmentaggregate](/req/hy_catchment/catchmentaggregate) | 
| Requirement	| [/req/hy_catchment/interiorcatchment.envelopingcatchment](/req/hy_catchment/interiorcatchment.envelopingcatchment) |


##### 7.4.2.6	Outfall
The HY_Outfall class ...
...
. Defining an inflow node which coincides with the outflow node of an upstream catchment, this supports...
...

| **Requirements Class** | [/req/hy_catchment/outfall] (/req/hy_catchment/outfall) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_Outfall | 
| Dependency | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) |
| Dependency | [/req/hy_catchment/divide](/req/hy_catchment/divide) | 
| Dependency | [/req/hy_catchment/indirectposition](/req/hy_catchment/indirectposition) | 
| Requirement	| [/req/hy_catchment/outfall.contributingcatchment](/req/hy_catchment/outfall.contributingcatchment) |
| Requirement	| [/req/hy_catchment/outfall.receivingcatchment](/req/hy_catchment/outfall.receivingcatchment) |
| Requirement	| [/req/hy_catchment/outfall.summitline](/req/hy_catchment/outfall.summitline) |
| Requirement	| [/req/hy_catchment/outfall.relativeposition](/req/hy_catchment/outfall.relativeposition) |


##### 7.4.2.7	Divide
The HY_Divide class ...
...
...
...

| **Requirements Class** | [/req/hy_catchment/divide] (/req/hy_catchment/divide) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_Divide | 
| Dependency | [/req/hy_catchment/referencelocation](/req/hy_catchment/referencelocation) | 
| Requirement	| [/req/hy_catchment/divide.nodeondivide](/req/hy_catchment/outfall.nodeondivide) |


##### 7.4.2.8	ReferenceLocation
The HY_ReferenceLocation class ...
...
...
...

| **Requirements Class** | [/req/hy_catchment/referencelocation] (/req/hy_catchment/referencelocation) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_Divide | 
| Dependency | [/iso/19103/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/req/hy_catchment/catchment](/req/hy_catchment/catchment) |
| Requirement	| [/req/hy_catchment/referencelocation.refpoint](/req/hy_catchment/outfall.refpoint) |
| Requirement	| [/req/hy_catchment/referencelocation.refpointtype](/req/hy_catchment/outfall.refpointtype) |


#### 7.4.3	The Hydrographic Network model
