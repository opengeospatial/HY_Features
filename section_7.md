## 7. The HY_Features common hydrologic feature model (normative)

### 7.1 The HY_Features conceptual model

This standard defines the HY_Features conceptual model as a standard for the identification and description of hydrologic features reflecting both hydrologic significance as well as topological connectivity of hydrologic features by defining the fundamental relationships between the major components of the hydrosphere. Core concepts are that of multiple catchment representation, of catchment hierarchy and topology, of aggregation and segmentation of watercourses including a simple model for the positioning of features along a linear flowpath using a specific linear referencing system. A utilities package provide common concepts required by the hydrology model that are not hydrology-specific. Module identification aims to simplify the scope of each part of the conceptual model in order to improve its accessibility and to provide scope for testing. It is intended that implementations need to consider only those parts of the common model implicated by its scope. Table 1 lists the applications schema, the leaf packages included and the concepts reflected therein. 

Table 1: HY_Features modules, packages and concepts reflected

|Application schema | Concepts reflected | Leaf packages included |
| --- | --- | --- |
| HY_HydroFeature  | fundamental properties and relationships between features governed by the physical laws of Hydrology, naming and context of hydrologic features, location of hydrologic feature along a line | HY_Catchment, HY_HydrographicNetwork, HY_NamedFeature, HY_RiverPositioningSystem, HY_Storage |
| HY_AtmosphericFeature (informative) | hydrologic features  above the Earth’s land surface without complexity and detail of a rainfall-runoff model | --- |
| HY_SubsurfaceHydroFeature (informative) | hydrologic features below the Earth’s land surface without complexity and detail of a groundwater or soil moisture model | --- |
| HY_SurfaceHydroFeature | hydrlogic fetaures on the Earth’s land surface without complexity and detail of hydrologic and hydraulic models | HY_SurfaceWater, HY_SurfaceWaterConfines |
| HY_HydrometricNetwork | hydrometric network as an aggregate of logically connected hydrometric features located on or along a hydrologic feature | --- |
| HY_Utilities | common concepts required by the domain model that are not hydrology-specific such as naming and contextual relations | --- |

The conceptual model is expressed in the Geographic Information Conceptual Schema Language (ISO 19103:2005) based on the Unified Modeling Language (UML). The organization into packages and package dependencies are shown in Figure 16. 

![Figure 16: HY_Features modules and packages](figs/fig16.png)  
Figure 16: HY_Features modules and packages  
**[\*\*\*update figure\*\*\*]**

The following sections describe requirements classes for each application schema, except for the two informative packages concerning atmospheric hydrologic features and subsurface hydrologic features. **[\*\*\* These informative packages are outlined in Annex ... .\*\*\*]**. A conceptual model capturing the specifics of features associated with the groundwater domain will be provided with the GroundwaterML 2.0 under development. **[\*\*\* insert reference to GWML2\*\*\*]**

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
**[(\*\*\* @Rob: please review, whether still applicable to describe conceptual conformance target \*\*\*]** - 

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

**[\*\*\* @Rob: please review, whether an encoding requirement is still in scope !!! \*\*\*]**
**[\*\*\* @Rob: please review this comment from an earlier version: How to handle default values – in-schema??? \*\*\* is this till valid ?]**

### 7.4 The Hydro Feature application schema

The Hydro Feature application schema defines the fundamental properties and relationships between features governed by the physical laws of hydrology. The core concept is that of a catchment and its multiple representation in the real world (see section 6.2 of this standard). Catchment area, catchment boundary, and linear flowpath as well as a cartographic visualisation are defined to reflect the most concepts in use to represent of catchment. 

The Hydro Feature schema conceptualize the abstraction of the complex Hydrology phenomenon through definition of feature types each describing separate aspects of the hydrology phenomenon. This includes related phenomena that participate in hydrologic systems but have specific characteristics. Figure 18 shows the special features types describing separate aspects of the hydrology phenomenon. Given the complexity of the domain, and the nature of real-world physical phenomena, for any given feature further specialisation as well as a wide range of possible characteristics, states and representations may be relevant. 

![Figure 18: Feature types describing separate aspects of the hydrology phenomenon (UML class diagram)](figs/fig18.png)
Figure 18: Feature types describing separate aspects of the hydrology phenomenon (UML class diagram)
**[\*\*\*update class diagram\*\*\*]**

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
**[\*\*\*update class diagram\*\*\*]**

The **identifier** attribute provides a means to assign to the hydrologic feature an (external) identifier in a given context. If required, an instance of HY_HydroFeature shall contain an identifier that may be used as a persistent reference to this feature. An implementation may use the EXT_IdentificationCode type as defined in the Utilities package (section 7.4. ... ) **[include reference]**.

The **name** association provides an abstract pattern to handle names given to the hydrologic feature in cultural, political or historical contexts. This allows to assign a localized name for all or part of a hydrologic feature without necessarily have a formal model. If required, this association shall be used where names are assigned to a feature instance through common usage, of cultural, political and historical variability that may occur with trans-boundary features. An implementation may use the EXT_LocalisedNameCode type as defined in the Utilities package (section 7.4. ... ) **[include reference]**. 

The **context** association provides a general pattern to handle various forms of contextualization of hydrologic features. This allows to define in which context typical properties are attached, without having to specify every possible value or to standardise the property name. If required, this associations shall be used to assign generally applicable characteristics to a feature instance in a spatial, temporal or classification context. It may be specified using one or more instances of the associated context property. An implementation may use the EXT_SpatialContext, EXT_TemporalContext or EXT_ClassificationContext types defined in the Utilities package (section 7.4. ... ) **[include reference]**.  

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
**[\*\*\*update class diagram\*\*\*]**

##### 7.4.2.1	Catchment representation
The HY_CatchmentRepresentation class conceptualize the multiple representation of a catchment in typical data products using single geometric shapes, or by visualization of typical networks the catchment may appear depending on the concern of the undertaken study. Catchment representation refers to the common recognition of a catchment as the unit of study shared across sub-domains, even if a particular representation refer only to one or the other. With respect tp 1D-and 2D-geometry, special sub- types of catchment representation are defined: HY_Flowpath (line-shaped),  HY_CatchmentArea (area-shaped), and HY_CatchmentBoundary  (polygon). The HY_NetworkCartography class is defined with respect to networks to which hydrologic features may participate, and that in its entirety represent, separately or as set of layers, the catchment. This will allow hydrologic features that are logically connected in the hydrographic network, a network of channels, a network of hydrometric stations to be portrayed in thematic map layers, which is common use to cartographically represent a catchment through overlaying a series of layers displaying such networks.

**[\*\*\*do we want include here other possible networks such as a network of related aquifers, which are not in scope of this standard with reference to a conceptual model capturing the specifics of connected aquifers, provided with the GroundwaterML 2.0 under development', see annex .??., -- if so, insert reference to GWML2\*\*\*]** 

In other contexts other types of catchment representation may exist.  Data products that not conforms to the special types defined in this standard, for instance representations in more-dimensional perspectives, or in time, may use the general HY_CatchmentRepresentation class. If present, all sub-types of catchment representation shall support the inherent representedCatchment property whereby each representation may be realised with an appropriate geometry type. HY_CatchmentRepresentation carries one association: representedCatchment. 

The *representedCatchment* association defines the relationship to exactly the catchment that is represented in the data set or product.  If required, this association shall be used to identify the unit wherein the hydrologic processes under study take place. 

| **Requirements Class** | [/req/hy_catchment/catchmentrepresentation] (/req/hy_catchment/catchmentrepresentation) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_CatchmentRepresentation | 
| Dependency | [/req/hy_catchment/catchment](/req/hy_catchment/catchment) | 
| Requirement	| [/req/hy_catchment/catchmentrepresentation.representedcatchment](/req/hy_catchment/catchmentrepresentation.representedcatchment) | 

##### 7.4.2.2	Catchment
The HY_Catchment class defines the catchment and its basic relationships such as catchmant hierarchy and network topology as described in section 6.3. HY_Catchment specializes the general HY_HydroFeature class; from this generalization it inherits *identifier*, *name* and *context* properties. HY_Catchment carries the associations: *containing Catchment*, *conjointCatchment*, *upstreamCatchment*,  *outflowNode*, *inflowNode*, *boundaryLine*.

The **containingCatchment** association describes the nesting of catchments in a simple “is-in” containment hierarchy as typically used for high-order organization of management and reporting units. If required, this association shall be used to identify a catchment wherein the catchment is nested.

The **outflowNode** association describes where water flows out of a contributing catchment. This allows to identify an inflow location that coincides with the outflow node, and to describe an upstream-downstream relation. If required, this association shall be used to identify the location to which the catchment contributes flow, and from where a downstream catchment receives flow from upstream. 

The **inflowNode** association describes where water flows into a receiving catchment. This allows to identify an outflow location that coincides with the inflow node, and to describe an downstream-upstream relation. If required, this association shall be used to identify the location from where the catchment receives flow, and to which an upstream catchment contributes flow. 

The **conjointCatchment** association describes the interaction of a catchment with another catchment crossing an internal boundary line. This line may be a divide separating adjacent catchments, or a diffuse divide between non-delineated sub-catchments within an encompassing catchment, or a fictive line between distant catchments. If required, this association shall be used to identify the interacting catchments. 

The **upperCatchment** association connects the catchment to the adjacent catchment above sharing a common (virtual) boundary line. This allows to describe connected catchments independent from identified inflow or outflow nodes. If required, this association may be used to trace the catchment network in upstream direction from mouth to source. In a dendritic network of catchments, where a catchment is determined by its single outflow node, this association may be used to identify inflow into the catchment when a particular inflow location is not known, for eaxmaple in headwater and tributary catchments. 

The **lowerCatchment** association connects the catchment to the adjacent catchment below sharing a common (virtual) boundary line. This allows to describe connected catchments independent from identified inflow or outflow nodes. If required, this association may be used to trace the catchment network in downstream direction from source to mouth. 

The **boundaryLine** association relates a conceptual line bounding the catchment, which carries an infinite number of nodes on line each to be located in the catchment network as an outfall of corresponding catchment. If required, this association may be used to identify a boundary line on whose lowest point an outfall may be placed when a particular outflow location is not known. 

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

The **exorheicDrainage** association references an exorheic drained catchment. The **endorheicDrainage** association references an endorheic drained catchment, temporarily connected to the enveloping aggregate. If required, these asscoations shall be used to identify the aggregated parts permanently or temporarily interacting with other catchments joined in the envompassing aggregate. 

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
The HY_DendriticCatchment class specializes the general HY_Catchment class with respect to a hydrologically discrete catchment, which is determined by a single common outlet to which all waters flow. This class denotes the catchment as the topological link between an inflow node and an outflow node allowing catchments to be connected in a dendritic network by upstream-downstream relationships, without knowing the complex hydrology between inflow and outflow nodes. This concept requires a stable identifier that is not merely a function of an arbitrary delineation of the surface, and that catchments are delineated within a simple tree hierarchy. The HY_DendriticCatchment class inherits from generalization the *containingCatchment*, *upstreamCatchment*, *conjointCatchment*, *outflowNode*, *inflowNode* and *boundaryLine* properties, and carries two properties: *code* and *encompassingCatchment*. 

The **code** attribute may be used to assign to the dendritic a unique identifier in given context. If required, the code shall be implemented using a controlled classification or coding system. Example: WMO Basin Codes.  

The **encompassingCatchment** association relates to the dendritic catchment the aggregate encompassing the catchment. If required, this association shall be used to identify the catchment encompassing one or more exorheic drained catchments contributing flow to the common outlet, either from a single identified inflow, or in join with other sub-catchments crossing a divide intern of the encompassing aggregate.

| **Requirements Class** | [/req/hy_catchment/dendriticcatchment] (/req/hy_catchment/dendriticcatchment) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_DendriticCatchment |
| Dependency | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) | 
| Dependency | [/req/hy_catchment/catchmentaggregate] (/req/hy_catchment/catchmentaggregate) | 
| Requirement |	[/req/hy_catchment/dendriticcatchment.code] (/req/hy_catchment/dendriticcatchment.code)
| Requirement |	[/req/hy_catchment/dendriticcatchment.encompassingcatchment] (/req/hy_catchment/dendriticcatchment.encompassingcatchment) 

##### 7.4.2.5	InteriorCatchment
The HY_InteriorCatchment class specializes the general HY_Catchment class with respect to a hydrologically discrete catchment, which is generally not connected to other catchments. This class describes the interior catchment as catchment enveloped by other catchments to which it may temporary contribute. The HY_InteriorCatchment class inherits from generalization the *containingCatchment*, *upstreamCatchment*, *conjointCatchment*, *outflowNode*, *inflowNode* and *boundaryLine* properties, and carries one association: *envelopingCatchment*. 

The **envelopingCatchment** association relates to the interior catchment the aggregate surrounding the catchment. If required, this association shall be used to identify the catchment enveloping one or more endorheic drained catchments contributing temporarily flow to the common outlet. 

| **Requirements Class** | [/req/hy_catchment/interiorcatchment] (/req/hy_catchment/interiorcatchment) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_InteriorCatchment | 
| Dependency | [/req/hy_catchment/catchment] (/req/hy_catchment/catchment) |
| Dependency | [/req/hy_catchment/catchmentaggregate](/req/hy_catchment/catchmentaggregate) | 
| Requirement	| [/req/hy_catchment/interiorcatchment.envelopingcatchment](/req/hy_catchment/interiorcatchment.envelopingcatchment) |


##### 7.4.2.6	Outfall
The HY_Outfall class conceptualize the common outlet of a catchment as the topologic node where catchments interact (see section 6.3.2). The outfall marks the place where the outflow node of a contributing catchment meets the inflow node of a receiving catchment. In terms of an outflow node, the outfall identifies the location to which upstream catchments contribute flow due to gravitational forces or pumping; in terms of an inflow node that location is identified from where catchments downstream receive flow collected upstream. 

Topologically placed in the network of catchments, geometric shape and position of the outfall are not explicitly defined. The outfall may get assigned a position relative to a reference location of a particular geometric shape using a linear reference system. The reference location may be a geometric point identified by co-ordinates, or any other feature carrying such a reference point. A fixed landmark, a monitoring station, a spring where groundwater enters the surface, may be a reference point but also a point projected onto the surface or created from merging disjoint locations; vertically arranged points may be aggregated and projected onto surface, a delta of a river system merged to virtual mouth, diffuse groundwater discharge placed on rivers or lakes.  The HY_Outfall class carries four associations: *contributingCatchment*, *receivingCatchment*, *summitLine* and *relativePosition*. 

The **contributingCatchment** association relates a catchment to its outflow node. This allows to describe an arbitrary location on the land surface as the topological outfall to which a catchment contributes flow, received from an upstream inflow node. If required, this association shall be used to identify the catchment contributing to the outflow node as the connecting link between inflow node and outflow node, and thus connecting an upstream catchment (at its outflow node) and a downstream catchment (at its inflow node).  

The **receivingCatchment** association relates a catchment to its inflow node. This allows to describe an arbitrary location on the land surface as the topological outfall where a catchment receives flow from upstream and contributes this to an outflow node. If required, this association shall be used to identify the catchment receiving flow as the connecting link between inflow node and outflow node, and thus connecting an upstream catchment (at its outflow node) and a downstream catchment (at its inflow node).

The **summitLine** association relates a summit line on which the outfall marks the lowest point, associating an infinite number of nodes on line each to be located in the catchment network. If required, this association may be used to identify a summit line on which an outfall may be placed when a particular inflow location is not known.

The **relativePosition** association relates to the outfall a position relative to a reference location located in the network and identified or fixed by coordinates. If required, this association shall be used to assign a position, either expressed as the distance to a reference location, or relative or interpolative to this.  

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
The HY_Divide class describes the boundary line separating adjacent catchments understood as a summit line on which several nodes may be located of which the outfall marks the lowest place. The HY_Divide class carries one association: *nodeOnDivide*. 

The **nodeOnDivide** association relates to the divide a node located on this. This allows an arbitrary node on divide, considered as a permanent reference location, to be located in the network of catchments in terms of an outfall. If required, this association shall be used to identify on the divide a permanent (reference) location identified by co-ordinates.

| **Requirements Class** | [/req/hy_catchment/divide] (/req/hy_catchment/divide) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_Divide | 
| Dependency | [/req/hy_catchment/referencelocation](/req/hy_catchment/referencelocation) | 
| Requirement	| [/req/hy_catchment/divide.nodeondivide](/req/hy_catchment/outfall.nodeondivide) |


##### 7.4.2.8	ReferenceLocation
The HY_ReferenceLocation class describes a permanent, stable reference location such as a landmark fixed and referenced by coordinates.
Placed in the catchment network in terms of an outfall, the reference location will be the referent of the (linear) river reference system; a hydrologic feature associated with a reference location can be considered to be carrier of the referent relative to which a distance may be determined. The HY_ReferenceLocation class carries three properties: *refPoint*, *refPointType*, *networkLocation*. 

The **refPoint** and **refPointType** attributes describes the reference location as point of a particular type. Given that a single point may have several reported locations depending on its nature and the precision of measurement, this attributes describe an accepted common point. If required, the reference point shall be identified using the GM_Point type, or the HY_RefPointType codelist described in Annex ... , table ... . **[insert reference]**  

The **networkLocation** association locates the referent in a given network of catchments. If required, this association shall be used to determine a permanent reference location topologically as inflow to a receiving or outflow of a contributing catchment.

| **Requirements Class** | [/req/hy_catchment/referencelocation] (/req/hy_catchment/referencelocation) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_ReferenceLocation | 
| Dependency | [/iso/19107/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/req/hy_catchment/refpointtype](/req/hy_catchment/refpointtype) |
| Dependency | [/req/hy_catchment/outfall](/req/hy_catchment/outfall) |
| Requirement	| [/req/hy_catchment/referencelocation.refpoint](/req/hy_catchment/outfall.refpoint) |
| Requirement	| [/req/hy_catchment/referencelocation.refpointtype](/req/hy_catchment/outfall.refpointtype) |
| Requirement	| [/req/hy_catchment/referencelocation.networklocation](/req/hy_catchment/outfall.networklocation) |

#### 7.4.3	The Hydrographic Network model
The hydrographic network model (figure XX) defines an aggregate of water bodies. Conceptually, the network of water bodies is understood as the hydrographic appearance of the catchment of study in the particular perspective of the study, and its visualization as a cartographic representation of the catchment. Given that the upstream-downstream relationship is topologically defined in the catchment model (see section 6.4.2), water bodies are aggregated in the hydrographic network irrespective of whether the accumulated water is flowing or not; a water body has no other role than being part of that network the contributing or receiving catchment appears. This allows, permanent and temporary water bodies of flowing or stagnant water to be aggregated in the network, and to visualized.

The hydrographic network is defined independent of the network of containing channels (see section 6.5). This conceptual separation references to the specific concerns of hydrology studying the occurrence, accumulation and circulation of water, and refers to water body accumulating water, which is shaped by the containing channel which exists regardless of whether water flows in or not (see section  6.4). This approach allows to separately visualize the hydrographic network of 'blue' lines or polygons, whereby the logically connected water bodies may or may not be connected at the representation level. 

The hydrographic network model defines the major elements of a hydrographic network and the relationships between them. A network water body may be segmented at vertical cross- or longitudinal sections in succeeding parts, each part in horizontal strata. The water body part associates a typical reference location, allowing to place any other feature relative to this using the (linear) river reference system described in section ... **[insert reference]**. 

![Figure XX: Hydrographic Network model (UML class diagram)](figs/figXX.png)
Figure XX: Hydrographic Network model (UML class diagram)
**[\*\*\*include class diagram\*\*\*]**

##### 7.4.3.1	HydrographicNetwork
The HY_HydrographicNetwork class describes the aggregate of permanent and temporary bodies of flowing or stagnant water; it may be visualized to cartographically represent the catchment that appears in a study as hydrographic network. The HY_HydrographicNetwork class carries one association: *visualization*. 

The **visualization** association relates to the hydrographic network its cartographic visualisation, either as a separate map, or one of many thematic layers. If required, this association shall be used to identify a map or geoschematic view displaying the hydrographic network that in its entirety, separately or as set of layers, represents the catchment without describing the displayed network parts in detail.

| **Requirements Class** | [/req/hy_hydrographicnetwork/hydrographicnetwork] (/req/hy_hydrographicnetwork/hydrographicnetwork) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_HydrographicNetwork |
| Dependency | [/req/hy_catchment/networkcartography] (/req/hy_catchment/networkcartography) | 
| Requirement |	[/req/hy_hydrographicnetwork/hydrographicnetwork.visualization]  (/req/hy_hydrographicnetwork/hydrographicnetwork.visualization)

##### 7.4.3.2	WaterBody, WaterBodyPart, WaterBodyStratum and Glacier
The HY_WaterBody class defines a water body as part of the hydrographic network (aggregate). This refers to a mass of (liquid) water distinct from other masses of water accumulating liquid water. The shape of a water body is determined by the occupied landform, the hosting hydrogeologic unit, a manmade container, tec.; the extent of an open water body bound to atmospheric pressure exerted on its surface. In the context of observation the water body may be understood as the sampled feature of interest. HY_Glacier is defined to model the accumulation of snow and ice. Both water bodies and glaciers may have names within common experience, that may differ with in contexts, or for some parts, are defined special subtypes of the named hydrologic feature. 

Special types of water bodies occurring on the land surface are defined in the 'Surface Hydro Feature' schema (section ...) ***[\*\*\* insert reference\*\*\*]***. Annex ... ***[\*\*\* insert reference\*\*\*]*** describes informative an atmospheric water body and a subsurface water body. A separate conceptual model capturing the specifics of features associated with the groundwater domain will be provided within the GroundwaterML 2.0 specification (under development). ***[\*\*\* insert reference\*\*\*]***

The HY_WaterBodyPart class describes the aggregation of parts into a water body (aggregate); the HY_WaterBodyStratum class the aggregation of horizontal layers in a stratified water body part (aggregate) determined by differences in thermal or salinity characteristics or by oxygen or nutrient content, or by virtual storage zones of a reservoir. HY_WaterBodyPart carries five properties: *fixedLandmark*, *upstreamSegment*,  *downstreamSegment*, *streamCrossSection*, and *streamLongitudinalSection*. With respect to the concept of a zone-based reservoir management, the HY_WaterBodyStratum carries the *storage* association:. 

The **hydrographicNetwork** relates to a water body the network aggregate, **waterBody** the water body to the aggregated part, and **stratifiedWaterBody** the stratified water body to a stratum. If required, these associations shall be used to identify the aggregates wherein a water body, water body part or statum aggregated. 

The **upstreamSegment** and **downstreamSegment** associations relates to a water body part segments up or downstream. If required, these associations shall be used to identify adjacent segments within the water body part.

The **streamCrossSection** and **longitudinalCrossSection** associations relates to a water body part vertical sections confining them.   If required, this association shall be used to identify vertical sections either at right angles to the main (average) direction of flow, or along the centre line. If present, an approriate geometric shape may be defined with implementation.

The **storage** association allows to relate to a water body participating in the hydrographic network storage characteristics. If required, this association shall be used to identify a body of water that is used for storage, regulation and control of water resources. 

| **Requirements Class** | [/req/hy_hydrographicnetwork/waterbody] (/req/hy_hydrographicnetwork/waterbody) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_WaterBody |
| Dependency | [/req/hy_namedFeature/hydrofeature] (/req/hy_namedFeature/hydrofeature) |
| Dependency | [/req/hy_hydrographicnetwork/hydrographicnetwork] (/req/hy_hydrographicnetwork/hydrographicnetwork) | 
| Requirement |	[/req/hy_hydrographicnetwork/waterbody.hydrographicnetwork]  (/req/hy_hydrographicnetwork/waterbody.hydrographicnetwork)

| **Requirements Class** | [/req/hy_hydrographicnetwork/waterbodypart] (/req/hy_hydrographicnetwork/waterbodypart) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_WaterBodyPart |
| Dependency | [/req/hy_namedFeature/hydrofeature] (/req/hy_namedFeature/hydrofeature) |
| Dependency | [/req/hy_catchment/referencelocation] (/req/hy_catchment/referencelocation) |
| Dependency | [/req/hy_hydrographicnetwork/waterbody] (/req/hy_hydrographicnetwork/waterbody) | 
| Dependency | [/req/hy_hydrographicnetwork/waterbodypart] (/req/hy_hydrographicnetwork/waterbodypart) | 
| Dependency | [/req/hy_hydrographicnetwork/crosssection] (/req/hy_hydrographicnetwork/crosssection) | 
| Dependency | [/req/hy_hydrographicnetwork/longitudinalsection] (/req/hy_hydrographicnetwork/longitudinalsection) | 
| Requirement |	[/req/hy_hydrographicnetwork/waterbody.waterbody]  (/req/hy_hydrographicnetwork/waterbody.waterbody) |
| Requirement |	[/req/hy_hydrographicnetwork/waterbody.fixedlandmark]  (/req/hy_hydrographicnetwork/waterbody.fixedlandmark) |
| Requirement |	[/req/hy_hydrographicnetwork/waterbody.upstreamsegment]  (/req/hy_hydrographicnetwork/waterbody.upstreamsegment) |
| Requirement |	[/req/hy_hydrographicnetwork/waterbody.downstreamsegment]  (/req/hy_hydrographicnetwork/waterbody.downstreamsegment) |
| Requirement |	[/req/hy_hydrographicnetwork/waterbody.streamcrosssection]  (/req/hy_hydrographicnetwork/waterbody.streamcrosssection) |
| Requirement |	[/req/hy_hydrographicnetwork/waterbody.streamlongitudinalsection]  (/req/hy_hydrographicnetwork/waterbody.streamlongitudinalsection) |

| **Requirements Class** | [/req/hy_hydrographicnetwork/waterbodystratum] (/req/hy_hydrographicnetwork/waterbodystratum) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_WaterBodyStratum |
| Dependency | [/req/hy_hydrographicnetwork/waterbodypart] (/req/hy_hydrographicnetwork/waterbodypart) | 
| Dependency | [/req/hy_storage/reservoir] (/req/hy_storage/reservoir) | 
| Requirement |	[/req/hy_hydrographicnetwork/waterbodystratum.stratifiedwaterbody]  (/req/hy_hydrographicnetwork/waterbodystratum.stratifiedwaterbody)
| Requirement |	[/req/hy_hydrographicnetwork/waterbodystratum.storage]  (/req/hy_hydrographicnetwork/waterbodystratum.storage)


##### 7.4.3.3	Water Liquid Phase, Water Solid Phase and Glacier
The HY_Water_LiquidPhase and HY_Water_SolidPhase define a very simple concept of accumulation of water and ice (material). In its liquid form water is accumulated in water bodies (stratum),  parts of the hydrographic network; in its solid phase in glaciers, on a body of open water as a layer of ice or snow, or after snowmelt in a water body. HY_Water_LiquidPhase carries the *accumulatingWaterBody* association; HY_Water_SolidPhase associates *accumulatingGlacier*, *snowmelt* and *coveredWaterBody*. If required, these associations shall be used to identify the water body or glacier wherein water as material is accumulated.

| **Requirements Class** | [/req/hy_hydrographicnetwork/waterliquidphase] (/req/hy_hydrographicnetwork/waterliquidphase) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_WaterLiquidPhase |
| Dependency | [/req/hy_hydrographicnetwork/waterbodystratum] (/req/hy_hydrographicnetwork/waterbodystratum) | 
| Requirement |	[/req/hy_hydrographicnetwork/waterliquidphase.accumulatingwaterbody]  (/req/hy_hydrographicnetwork/waterliquidphase.accumulatingwaterbody)

| **Requirements Class** | [/req/hy_hydrographicnetwork/watersolidphase] (/req/hy_hydrographicnetwork/watersolidphase) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_WaterSolidPhase |
| Dependency | [/req/hy_hydrographicnetwork/waterliquidphase] (/req/hy_hydrographicnetwork/waterliquidphase) | 
| Dependency | [/req/hy_hydrographicnetwork/waterbodypart] (/req/hy_hydrographicnetwork/waterbodypart) | 
| Dependency | [/req/hy_hydrographicnetwork/glacier] (/req/hy_hydrographicnetwork/glacier) | 
| Requirement |	[/req/hy_hydrographicnetwork/watersolidphase.snowmelt]  (/req/hy_hydrographicnetwork/watersolidphase.snowmelt)
| Requirement |	[/req/hy_hydrographicnetwork/watersolidphase.coveredwaterbody]  (/req/hy_hydrographicnetwork/watersolidphase.coveredwaterbody)
| Requirement |	[/req/hy_hydrographicnetwork/watersolidphase.glacier]  (/req/hy_hydrographicnetwork/watersolidphase.glacier)


##### 7.4.3.4	Cross-Section amd Longitudinal Section
The HY_CrossSection and HY_LongitudinalSection conceptualize the vertical segmentation confining a water body or a containing channel. Taking into account the separation of a watercourse (see section 6.5) into water body and containing channel, the cross section concept both the (blue) stream cross section at right angles to the main (average) direction of flow, as well as to the transversal bed profile (shape) of a stream bed in a vertical plane; and the longitudinal section concept to the (blue) stream line (envelope of the tangents to the instantaneous flow direction at a given time) or stream centre line (connecting the successive centres of cross sections of a stream) as well as to the line following the deepest part of channel (thalweg) and the line of intersection of a water body with the rising land (shore/bank line). 
 
HY_CrossSection and HY_LongitudinalSection associate a typical reference location: *crossSectionPoint* and *longitudalinalSectionPoint*. If required, these associations shall be used to identify at section a permanent location which is identified by co-ordinates. Located in the network of catchment in terms of an outfall, this supports to place any feature relative to this using the (linear) river reference system described in section ... **[insert reference]**. 


#### 7.4.4	The River Positioning System model
[\*\*\*include class diagram\*\*\*]

#### 7.4.3	The Storage model
[\*\*\*include class diagram\*\*\*]


