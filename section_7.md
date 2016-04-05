## 7. The HY_Features common hydrologic feature model (normative)

### 7.1 The HY_Features conceptual model

This standard defines the HY_Features conceptual model as a standard for the identification and description of hydrologic features reflecting both hydrologic significance as well as topological connectivity of hydrologic features by defining the fundamental relationships between the major components of the hydrosphere. Core concepts are that of multiple catchment representation, of catchment hierarchy and topology, of aggregation and segmentation of watercourses including a simple model for the positioning of features along a linear flowpath using a specific linear referencing system. A utilities package provide common concepts required by the hydrology model that are not hydrology-specific. 

Module identification aims to simplify the scope of each part of the conceptual model in order to improve its accessibility and to provide scope for testing. It is intended that implementations need to consider only those parts of the common model implicated by its scope. Table 1 lists the applications schema, the leaf packages included and the concepts reflected therein. This section describes for each application schema the defined requirements classes, except for the both informative packages on atmospheric hydrologic features and subsurface hydrologic features. **[\*\*\* These informative packages are outlined in Annex ... .\*\*\*]**. A conceptual model capturing the specifics of features associated with the groundwater domain will be provided with the GroundwaterML 2.0 under development. **[\*\*\* insert reference to GWML2\*\*\*]**

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
[\*\*\*update figure\*\*\*]

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
[\*\*\*update figure\*\*\*]

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
[\*\*\*update figure\*\*\*]

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
[\*\*\*update figure\*\*\*]

##### 7.4.2.1	Catchment representation
The HY_CatchmentRepresentation class conceptualize the multiple representation of a catchment in typical data products using single geometric shapes, or by visualization of typical networks the catchment may appear (see section 6.3.1). Catchment representation refers to the common recognition of a catchment as the unit of study shared across sub-domains, even if a particular representation refer only to one or the other. With respect tp 1D-and 2D-geometry, special sub- types of catchment representation are defined: HY_Flowpath (line-shaped),  HY_CatchmentArea (area-shaped), and HY_CatchmentBoundary  (polygon). The HY_NetworkCartography class is defined with respect to a network to which hydrologic features may participate, and that in its entirety represents, separately or as set of layers, the catchment.  This will allow hydrologic features that are logically connected in the hydrographic network of water bodies, in a network of channels (expressed as drainage pattern), or in a network of hydrometric stations to be portrayed in thematic maps displaying such a network.

[\*\*\*do we want mention here other possible networks such as a network of related aquifers, which are not in scope of this standard with reference to a conceptual model capturing the specifics of connected aquifers, provided with the GroundwaterML 2.0 under development', see annex .??., -- if so, insert reference to GWML2\*\*\*]. 

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
The HY_Divide class describes a boundary line separating adjacent catchments understood as the summit line on which several nodes may be located of which the outfall marks the lowest place. The HY_Divide class carries one association: *nodeOnDivide*. 

The **nodeOnDivide** association relates to the divide a node located on this. This allows an arbitrary node on divide, considered as a permanent reference location, to be located in the network of catchments in terms of an outfall. If required, this association shall be used to identify on the divide a permanent (reference) location identified by co-ordinates.

| **Requirements Class** | [/req/hy_catchment/divide] (/req/hy_catchment/divide) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_Divide | 
| Dependency | [/req/hy_catchment/referencelocation](/req/hy_catchment/referencelocation) | 
| Requirement	| [/req/hy_catchment/divide.nodeondivide](/req/hy_catchment/outfall.nodeondivide) |


##### 7.4.2.8	ReferenceLocation
The HY_ReferenceLocation class describes permanent, stable reference location such as a landmark fixed and referenced by coordinates.
Given that a single point may have several reported locations depending on its nature and the precision of measurement, the reference location describes the accepted location of a reference point, which may be the referent to which linear measures within a network may be determined. Using such a reference point an hydrologic feature can be topologically placed in the catchment network in terms of an inflow or outflow node, which may be considered to be referent of a (linear) river reference system. The HY_ReferenceLocation class carries three properties: *refPoint*, *refPointType*, *networkLocation*. 

The **refPoint** and **refPointType** attributes describes the accepted reference location by co-ordinates or type. If required, the reference point shall be identified by co-ordinates using the GM_Point type, or by type using the HY_RefPointType codelist in **[Annex ..., table ...]**  

The **networkLocation** association locates the referent in a network of catchments. This allows to place the reference location topologically as outfall of a corresponding catchment. If required, this association shall be used to determine a permanent reference location topologically as inflow to a receiving or outflow of a contributing catchment.

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
[\*\*\*include figure\*\*\*]

#### 7.4.4	The River Positioning System model
[\*\*\*include figure\*\*\*]

#### 7.4.3	The Storage model
[\*\*\*include figure\*\*\*]


