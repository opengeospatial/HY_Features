## 7. The HY_Features common hydrologic feature model (normative)

### 7.1 The HY_Features conceptual model

This standard defines the HY_Features conceptual model as a standard for the identification and description of hydrologic features reflecting both hydrologic significance as well as topological connectivity of hydrologic features. The fundamental relationships between the major components of the hydrosphere are conceptualised to formally describe the hydrosphere as an hierarchical network of hydrologically connected catchments, and the appearing network phenomena to be visualised, irrespective of the various spatial or temporal representations available for these phenomena. 

Core concepts are that of an abstract catchment with many possible 'realizations', of catchment topology and hierarchy, of aggregation of watercourses, and of positioning on a river using a nominal main flow path. Geographic locations are extended with topological attibutes to describe any location on, or projected onto, the land surface as the inflow or outflow of a corresponding catchment. 

The conceptual model is implemented in several discrete modules. It is intended that implementations need to consider only those parts of the common model required by a particular implementation scope. An implementation may include or exlude feature properties, or override the cardinality of a relationship. For example, if it is expected that a logically determined relationship may be 'nillable' within a particular realisation, the cardinality defined in the conceptual model may be overridden. Table 1 lists the application schemas, the leaf packages included and the concepts reflected therein. 

Table 1: HY_Features modules, packages and concepts  **[removed informative packages from table]**

| Application schema | Concepts reflected | Leaf packages included |
| --- | --- | --- |
| HY_HydroFeature  | fundamental properties and relationships between features governed by the physical laws of Hydrology, naming of hydrologic features, location of hydrologic feature along a line | NamedFeature, HydroComplex, RiverPositioningSystem |
| HY_SurfaceHydroFeature | hydrologic fetaures on the Earth’s land surface without complexity and detail of hydrologic and hydraulic models | ChannelNetwork, HydrographicNetwork, WaterBodyTypes, Storage |
| HY_HydrometricNetwork | hydrometric network of logically connected hydrometric features located on or along a hydrologic feature | --- |

The conceptual model is expressed in the Geographic Information Conceptual Schema Language (ISO 19103:2005) based on the Unified Modeling Language (UML). The organization into packages and package dependencies are shown in Figure 16. The following sections describe requirements classes for each application schema, whereby each feature addressed in the requirements shall be understood as an instance of the GF_FeatureType (aka FeatureType) «metaclass». 

![Figure 16: HY_Features modules and packages](figs/fig16.png)  
Figure 16: HY_Features modules and packages  

### 7.2	The HY_Features conceptual conformance (mapping)

The HY_Features model is a 'conceptual model', not intended as a directly implementable model for data exchange or persistence. The conformance target of the HY_Feature model is therefore a logical model of an implementation that encodes aspects of the HY_Features model. 

Conformance to the HY_Features model is a matter of being able to unambiguously identify what elements of an implementation schema map to the HY_Features model, and inclusion of all mandatory properties of the HY_Feature defined Feature Types in such mappings. 

The HY_Features conceptual model provides the basis for determining whether two references to hydrologic features are references to the same feature, i.e. to specify the real world type of features independent of the implementation schema used. Specifically, it provides the means to distinguish between the reference concept (e.g. a catchment) and its realizations as geographic features (e.g. flowpath, catchment area or boundary), and hence to declare that different realizations share common concept of hydrological connectivity. 

Disparate systems describing hydrologic features may be mapped to the equivalent HY_Features definitions to disambiguate the local usage of terminology and specific implementation choices made. 

Note that a direct encoding of HY_Features to an implementation platform such as RDF MAY implement such a mapping through annotation or direct correspondance of names to the HY_Feature elements.


| **Requirements Class** | [/req/hy_features_conceptual_model](/req/hy_features_conceptual_model) |
| --- | --- |
| Target type | Implementation Schema |
| Name | HY_Features Conceptual Conformance |
| Dependency | [/iso/19109/] (https://inspire-twg.jrc.it/svn/iso) |
| Requirement | [/req/ hy_features_conceptual_model/mapping] (/req/ hy_features_conceptual_model/mapping) |

**[ this text needs to go in the requirement... 
An implementation schema conforming to HY_Features SHALL provide a formal mapping from one or more Feature Types present in the implementation schema to Feature Types defined in this standard specification, including all mandatory properties defined by the realized HY_Features concept. Default values to be assumed must be specified in this mapping. ]***


### 7.3	The HY_Features data conformance (encoding) 

As a conceptual model HY_Features does not specify conformance requirements regarding the structure of possible encodings. It does however specify that equivalence of feature instances can be expressed. The requirement that arises is therefore that the content of feature identification elements can be matched between implementations. This does not demand the use of identical identifiers across different implementations, but it does require that implementations provide a mechanism to match identifiers from different schemes.

| **Requirements Class** | [/req/hy_features_content] (/req/hy_features_content) |
| --- | --- |
| Target type	| Dataset |
| Name | HY_Features Data Conformance |
| Dependency | [/req/hy_features_conceptual_model](/req/hy_features_conceptual_model) |
| Dependency | [/iso/19109/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/iso/19150/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/iso/19136/](https://inspire-twg.jrc.it/svn/iso) |
| Requirement	| [/req/ hy_features_conceptual_model/identifiers] (/req/ hy_features_conceptual_model/identifiers) |

Implementations of HY_Features SHALL either use common identifiers for instances of Feature Types mapped to the same underlying HY_Features Feature Type, OR provide a mechanism to match identifiers from different identification schemes.

### 7.4 The Hydro Feature application schema

The Hydro Feature schema provides the core concepts of a named hydrologic feature, of a catchment and its multiple realisation within a hydro(spehre) complex and of a river positioning using a linear reference system. Hydrologic features are identified by hydrologic significance and feature topology. Providing a standard terminology for the typical relationships between hydrologic features allows the hydrosphere to be expressed in a consistent way across multiple data products, irrespective of the various spatial or temporal representations available for these phenomena. 

Hydrologic features are usually named in cross-jurisdictional and multi-lingual contexts. The Hydro Feature schema provides a concept for a named hydrologic feature which allows to record multiple names and identifiers without necessarily have a formal naming model. The named hydrologic feature is further elucidated in domain-specific feature types, which specify the properties each specialization uses to define one or more aspects of the hydrology phenomenon (Figure 17). This includes related phenomena that participate in hydrologic systems but have specific characteristics. Given the complexity of the domain, and the nature of real-world physical phenomena, for any given hydrologic feature a wide range of possible characteristics, realizations and representations may be relevant. 

![Figure 17: Hydrologic features describing separate aspects of the hydrology phenomenon (UML class diagram)](figs/fig17.png)
Figure 17: Hydrologic features describing separate aspects of the hydrology phenomenon (UML class diagram)

The Hydro Feature schema provides the core model of catchment and its multiple realisation. The catchment model denotes the hydrologic determination of a catchment by its common outlet and the interaction of catchments through such a defined outfall. This allows to divide the hydrosphere into a logical network of connected catchments. Depending on the perspective of a particular study, the logical catchment is multiple realised by typical features. This 'abstract' realisation of a catchment is typically implemented with geometry attributes. Flowpath, catchment area, and catchment boundary, networks of connected flowpathes, areas or boundaries, but also different cartographic network views are defined to reflect the most common concepts in use to realize the catchment idea. Typical representations of these are defined as geometry attributes of the feature types embodying this realization. 

The Hydro Feature schema provides a model to place a catchment's outfall relative to a reference location which realises the logical outfall. The river positioning model provides a river reference system which allows to assign a position to an outfall using the linear realisation of the catchment that corresponds to the outfall. Given the hydrologic determination of a catchment by its outfall and any location on the land surface considered to be outfall of a catchment, an arbitrary feature of interest can be placed on the linear flowpath realisation of the corresponding catchment, and a position can be assigned using the geometric representations of either of the catchment or the outfall realisation. 

The definitions applied in the Hydro Feature schema are rooted in the definitions given in the WMO Glossary of Hydrology regardless of their application context in respect to the Earth's surface. For the purpose of testing the applicability of the conceptual model in the context of surface water hydrology, the definitions in this standard refer to surface water hydrology. A conceptual model capturing the specifics of features associated with the groundwater domain is developed with reference to the GroundWaterML standard **[ correct ref ]**.

The Hydro Feature schema contains five leaf packages: NamedFeature, HydroComplex, and RiverPositioning. Figure 18 shows the external and internal dependencies.

![Figure 18: External and internal dependencies (UML class diagram)](figs/fig18.png)
Figure 18: External and internal dependencies (UML class diagram) **[new]**

| **Requirements Class** | [/req/hy_abstract/*] (/req/hy_abstract/*) |
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_HydroFeature (abstract) |
| Dependency | [/iso/19103/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/iso/19107/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/iso/19111/](https://inspire-twg.jrc.it/svn/iso) |
| Requirement	| [/req/hy_abstract/namedfeature/*](/req/hy_abstract/namedfeature/*) |
| Requirement	| [/req/hy_abstract/hydrocomplex/*](/req/hy_abstract/hydrocomplex/*) |
| Requirement	| [/req/hy_abstract/positioning/*](/req/hy_abstract/positioning/*) |


#### 7.4.1	The Named Feature model

The Named Feature model (Figure 19) denotes the abstraction of the hydrology phenomenon as a named hydrologic feature. It provides an approach to identify a named hydrologic feature in cross-jurisdiction and multi-lingual contexts by considering the cultural, political and historical aspects of names assigned to hydrologic features in common usage. 

![Figure 19: Named Feature (UML class diagram)](figs/fig19.png)
Figure 19: Named Feature (UML class diagram) 

The HY_HydroFeature feature type is further specialised by separate feature types. Each specialisation inherits the properties from generalization; HY_HydroFeature type has one association: *name*.

The **name** association associates a name given to the hydrologic feature in cultural, political or historical context. If required, this association shall be used where names are assigned to a feature instance in cross-jurisdictional and multi-lingual contexts, that may occur with trans-boundary features. 

| **Requirements Class** | [/req/namedFeature/hydrofeature] (/req/namedFeature/hydrofeature) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_HydroFeature |
| Dependency | [/req/namedFeature/hydrofeaturename] (/req/namedFeature/hydrofeaturename) | 
| Requirement	| [/req/namedFeature/hydrofeature.name] (/req/namedFeature/hydrofeature.name) | 

The HY_HydroFeatureName feature type provides an abstract pattern to handle cultural, political and historical variability of names. This allows to assign a referencable name for all or part of a hydrologic feature without necessarily have a formal model for naming. HY_HydroFeatureName has five attributes: name, namesPart, preferredBy, usage and variantSpelling. If required, an implementation shall use this type to describe the usage of multiple names. The usage type may be identified using the HY_NameUsage codelist described in Annex ...,  table ... 

| **Requirements Class** | [/req/hy_namedFeature/hydrofeaturename] (/req/hy_namedFeature/hydrofeaturename) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_HydroFeatureName |
| Dependency | [/iso/19103/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/iso/19115/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/req/hy_abstract/namedFeature/nameusage](/req/hy_abstract/namedFeature/nameusage) | 
| Requirement |	[/req/hy_abstract/namedFeature/hydrofeature.name](/req/hy_abstract/namedFeature/hydrofeature.name) | 
| Requirement	| [/req/hy_abstract/namedFeature/hydrofeature.namespart](/req/hy_abstract/namedFeature/hydrofeature.namespart) | 
| Requirement	| [/req/hy_abstract/namedFeature/hydrofeature.preferredBy](/req/hy_abstract/namedFeature/hydrofeature.preferredby) | 
| Requirement	| [/req/hy_abstract/namedFeature/hydrofeature.usage](/req/hy_abstract/namedFeature/hydrofeature.usage) | 
| Requirement	| [/req/hy_abstract/namedFeature/hydrofeature.variantspelling](/req/hy_abstract/namedFeature/hydrofeature.variantspelling) | 

#### 7.4.2	The Hydro Complex model
The Hydro Complex model conceptualizes the hydrologic determination of a catchment by defining an outfall in the role of an outflow of a contributing catchment, or inflow to a receiving catchment (Figure 20). Conceptually, each catchment has an outfall, and any outfall associates a corresponding catchment, even if catchment and outfall may be ‘nillable’ in a particular application. A catchment interacts with upper and lower catchments via its outfall, and ultimately contributes flow to the outfall of a containing catchment. Understanding the catchment as the logical link between outfalls, an hierarchical network of catchments (Figure 21) is implied that ultimately links inflow and outflow of the catchment containing this network catchments. 

The Hydro Complex model implies a collection of hydrologic features closed under the condition of the hydrologic determination of a catchment where the union of catchment and its common outlet (conceptualised as outfall) is realised by typical hydrologic features within the same hydro(sphere) complex. This concept references the topological closure of catchment and outfall in such that a realisation of the logical catchment is always of higher topological dimension than the realisation of the corresponding outfall in terms of a topological boundary. For example, a linear flowpath realising a catchment may be understood as an edge between inflow and outflow nodes; the areal realisation of a catchment as a face bounded by linear inflow and outflow.

The Hydro Complex model allows to consider an arbitrary location on, or projected onto, the land surface as the realisation of the logical outfall. Such a 'real' outfall provides an identifiable reference to which alternative catchment realisations may refer. This supports to establish topological relationships between hydrographic features, or hydrographic and hydrometric features. 

The Hydro Complex model allows for the existence of catchments to be recognized, and identifiers assigned by referencing the outfall even if stream networks, catchment areas and watersheds are not reliably determined. It is intended that hydrological reporting applications may use this model without the full complexity and detail of scientific catchment models.

##### 7.4.2.1	Catchment
The HY_Catchment feature type denotes the hydrologic determination by associating an outfall, and the logical network of catchments through internal relationships. Each catchment may associate many different realisations within an implied hydro(sphere) complex under the condition of the hydrologic determination, incl. a topological realisation as an edge 'bounded' by inflow and outflow nodes. HY_Catchment is an abstract class and may be further specialised with respect to catchment interaction. 

![Figure 20: Catchment (UML class diagram)](figs/fig20.png)
Figure 20: Catchment (UML class diagram) 

The HY_Catchment type (Figure 20) specializes the general HY_HydroFeature class. From generalization HY_Catchment inherits the *name* property, and carries the *code* attribute and the associations: *outflow*, *inflow*, *containing Catchment*, *containedCatchment*, *conjointCatchment*, *upperCatchment*, *lowerCatchment*, *realisation*.

The **code** attribute may be used to assign to the catchment a unique identifier in given context. If required, the code attribute shall be implemented using a controlled classification or coding system. Example: WMO Basin Codes.  

The **outflow** and *inflow* associations describe the outfall in terms of outflow or inflow of the corresponding catchment. Assuming a dendritic network of catchments, the outflow of a contributing catchment coincides with the inflow to a receiving catchment. This allows to describe upstream-downstream relations. If required, this association shall be used to identify the place to which flow is contributed, or from where flow is received.

![Figure 21: Catchment and outfall (UML class diagram)](figs/fig21.png)
Figure 21: Catchment and outfall (UML class diagram) 

The **containingCatchment** and **containedCatchment** associations connect the nesting of catchments in a simple “is-in” containment hierarchy as typically used for high-order organization of management and reporting units. If required, this association shall be used to identify a nesting catchment or the catchments nested therein.

![Figure 22: Containing / contained catchment (UML class diagram)](figs/fig22.png)
Figure 22: Containing / contained catchment (UML class diagram) 

The **conjointCatchment** association describes the interaction of a catchment with another catchment crossing an internal boundary line. This line may be a divide separating adjacent catchments, or a diffuse divide between non-delineated sub-catchments within an encompassing catchment, or a fictive line between distant catchments. If required, this association shall be used to identify a catchment contributing with others to a 'joined' outfall. Assuming a dendritic network of catchments, where each catchment is determined by its single outflow, this association may be used to summarize diffuse inflow into an encompassing catchment, as required to describe inflow to headwater catchments. 

![Figure 23: Conjoint / contained catchment (UML class diagram)](figs/fig23.png)
Figure 23: Conjoint / contained catchment (UML class diagram) 

The **upperCatchment** and **lowerCatchment** associations connect the catchment to the adjacent catchment above or below. This allows to describe connected catchments without knowing their inflow or outflow. If required, this association shall be used to trace the catchment network in upstream direction from mouth to source, or downstream from source to mouth. 

![Figure 24: Upper / lower catchment (UML class diagram)](figs/fig24.png)
Figure 24: Upper / lower catchment (UML class diagram)

The **realisation** association relates the catchment to a feature which realises the logical catchment. This supports to link multiple realisations of the same catchment. If required, this association shall be used identify a particular realisation. In case of a topological realisation, the realisation of the catchment shall be of higher dimension than the realisation of the outfall.


| **Requirements Class** | [/req/hy_abstract/hydrocomplex/catchment] (/req/hy_abstract/hydrocomplex/catchment) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_Catchment | 
| Dependency | [/iso/19103/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/req/hy_namedFeature/hydrofeature](/req/hy_namedFeature/hydrofeature) |
| Dependency | [/req/hy_abstract/hydrocomplex/outfall](/req/hy_abstract/hydrocomplex/outfall) | 
| Dependency | [/req/hy_abstract/hydrocomplex/catchment](/req/hy_abstract/hydrocomplex/catchment) | 
| Dependency | [/req/hy_abstract/hydrocomplex/catchmentrealisation](/req/hy_abstract/hydrocomplex/catchmentrealisation) |
| Requirement	| [/req/hy_abstract/hydrocomplex/catchment.outflow](/req/hy_abstract/hydrocomplex/catchment.outflow) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/catchment.inflow](/req/hy_abstract/hydrocomplex/catchment.inflow) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/catchment.containingcatchment](/req/hy_abstract/hydrocomplex/catchment.containingcatchment) |
| Requirement	| [/req/hy_abstract/hydrocomplex/catchment.containedcatchment](/req/hy_abstract/hydrocomplex/catchment.containedcatchment) |  
| Requirement	| [/req/hy_abstract/hydrocomplex/catchment.conjointcatchment](/req/hy_abstract/hydrocomplex/catchment.conjointcatchment) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/catchment.uppercatchment](/req/hy_abstract/hydrocomplex/catchment.uppercatchment) |
| Requirement	| [/req/hy_abstract/hydrocomplex/catchment.lowercatchment](/req/hy_abstract/hydrocomplex/catchment.lowercatchment) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/catchment.realisation](/req/hy_abstract/hydrocomplex/catchment.realisation) | 

##### 7.4.2.2	CatchmentAggregate 
The HY_CatchmentAggregate feature type (Figure 25) specializes the HY_Catchment specifically as a set of dendritic and interior catchments, arranged in an encompassing catchment at the next upper hierarchy level without any spatial overlap. This allows to describe multiple inflows into a catchment aggregate through several hydrologically discrete sub-catchments each with a single inflow, and contributing to a joined outflow of the catchment aggregate, incl. the 'nillable' outflow of interior catchments. The catchment aggregate may be part of a containing catchment at the next higher hierarchy level, which consists of many of those neighbouring catchments. This does not necessarily implies a series of containing catchments, but allows jumping to the 'highest' upper-level system as typically used for reporting purposes.

![Figure 25: Catchment aggregate (UML class diagram)](figs/fig25.png)
Figure 25: Catchment aggregate (UML class diagram)

HY_CatchmentAggregate inherits from generalization the *outflow*, *inflow*, *containing Catchment*, *containedCatchment*, *conjointCatchment*, *upperCatchment*, *lowerCatchment*, and *realisation* properties, and associates the *exorheicDrainage* and *endorheicDrainage*. 

The **exorheicDrainage** association references an exorheic drained catchment connected to others in a dendritic network. The **endorheicDrainage** association references an endorheic drained catchment, temporarily connected to the enveloping aggregate. If required, these asscoations shall be used to identify aggegrated catchment parts which permanently or temporarily interact with other catchment parts at the same hierarchy level. 

| **Requirements Class** | [/req/hy_abstract/hydrocomplex/catchmentaggregate](/req/hy_abstract/hydrocomplex/catchmentaggregate) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_CatchmentAggregate | 
| Dependency | [/req/hy_abstract/hydrocomplex/catchment](/req/hy_abstract/hydrocomplex/catchment) | 
| Dependency | [/req/hy_abstract/hydrocomplex/dendriticcatchment](/req/hy_abstract/hydrocomplex/dendriticcatchment) |
| Dependency | [/req/hy_abstract/hydrocomplex/interiorcatchment](/req/hy_abstract/hydrocomplex/interiorcatchment) |
| Requirement	| [/req/hy_abstract/hydrocomplex/catchmentaggregate.exorheicdrainage](/req/hy_catchment/catchmentaggregate.exorheicdrainage) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/catchmentaggregate.endorheicdrainage](/req/hy_catchment/catchmentaggregate.endorheicdrainage) | 

##### 7.4.2.3	DendriticCatchment
The HY_DendriticCatchment feature type (Figure 26) specializes the general HY_Catchment class specifically as a hydrologically discrete catchment, which is determined by a single common outlet to which all waters flow. This class denotes the catchment as the topological link between an inflow and an outflow allowing catchments to be connected in a dendritic network by upstream-downstream relationships, without knowing the complex hydrology between inflow and outflow. This concept requires a stable identifier that is not merely a function of an arbitrary delineation of the surface, and that catchments are delineated within a simple tree hierarchy. 

![Figure 26: Dendritic catchment (UML class diagram)](figs/fig26.png)
Figure 26: Dendritic catchment (UML class diagram)

HY_DendriticCatchment inherits from generalization the *code*, *outflow*, *inflow*, *containing Catchment*, *containedCatchment*, *conjointCatchment*, *upperCatchment*, *lowerCatchment*, and *realisation* properties, and associates the *encompassingCatchment*.

The **encompassingCatchment** association relates to the dendritic catchment the aggregate encompassing the catchment. If required, this association shall be used to identify the catchment encompassing one or more exorheic or endorheic drained catchments contributing flow to the common outlet, either from a single identified inflow, or in join with other sub-catchments crossing a divide intern of the encompassing aggregate.

| **Requirements Class** | [/req/hy_abstract/hydrocomplex/dendriticcatchment] (/req/hy_abstract/hydrocomplex/dendriticcatchment) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_DendriticCatchment | 
| Dependency | [/req/hy_abstract/hydrocomplex/catchment](/req/hy_abstract/hydrocomplex/catchment) | 
| Dependency | [/req/hy_abstract/hydrocomplex/catchmentaggregate](/req/hy_abstract/hydrocomplex/catchmentaggregate) |
| Requirement	| [/req/hy_abstract/hydrocomplex/dendriticcatchment.encompassingcatchment](/req/hy_abstract/hydrocomplex/dendriticcatchment.encompassingcatchment) | 

##### 7.4.2.4	InteriorCatchment
The HY_InteriorCatchment feature type (Figure 27) specializes the general HY_Catchment class specifically as a hydrologically discrete catchment, which is generally not connected to other catchments. This class describes the interior catchment as a catchment enveloped by other catchments to which it may temporary contribute. 

![Figure 27: Interior catchment (UML class diagram)](figs/fig27.png)
Figure 27: Interior catchment (UML class diagram)

HY_InteriorCatchment inherits from generalization the *code*, *outflow*, *inflow*, *containing Catchment*, *containedCatchment*, *conjointCatchment*, *upperCatchment*, *lowerCatchment*, and *realisation* properties, and associates the *envelopingCatchment*.

The **envelopingCatchment** association relates to the interior catchment the aggregate surrounding the catchment. If required, this association shall be used to identify the catchment enveloping one or more endorheic drained catchments contributing 'nillable' flow to the common outlet. 

| **Requirements Class** | [/req/hy_abstract/hydrocomplex/interiorcatchment](/req/hy_abstract/hydrocomplex/interiorcatchment) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_InteriorCatchment | 
| Dependency | [/req/hy_abstract/hydrocomplex/catchment](/req/hy_abstract/hydrocomplex/catchment) | 
| Dependency | [/req/hy_abstract/hydrocomplex/catchmentaggregate](/req/hy_abstract/hydrocomplex/catchmentaggregate) |
| Requirement	| [/req/hy_abstract/hydrocomplex/interiorcatchment.envelopingcatchment](/req/hy_abstract/hydrocomplex/interiorcatchment.envelopingcatchment) | 

##### 7.4.2.5	Outfall
The HY_Outfall feature type (Figure 28) denotes the hydrologic determination of the outfall by associating a corresponding catchment (Figure 20). The logical outfall marks the place where a catchment interacts with another catchment, i.e. where the outflow of a contributing catchment becomes inflow into a receiving catchment, whereby a catchment may receive flow from several catchments. Logically placed in reference to a catchment which links inflow and outflow, an outfall has a position relative to another outfall 'fixed' by the  catchment. Each outfall may associate different realisations within an implied hydro(sphere) complex under the condition of the hydrologic determination, incl. the topological realisation as a node in terms of the 'boundary' of a catchment edge. 

![Figure 28: Outfall (UML class diagram)](figs/fig28.png)
Figure 28: Outfall (UML class diagram)

HY_Outfall carries the associations: *contributingCatchment*, *receivingCatchment*, *relativePosition* and *outfallRealisation*. 

The **contributingCatchment** association relates to the outfall a catchment that contributes flow. This allows to relate to an outflow an identified inflow and to determine its position through referencing this. If required, this association shall be used to identify the catchment connecting the outfall and the inflow used for reference.  

The **receivingCatchment** association relates to the outfall a catchment that receives flow from here. This allows to relate to an inflow an identified outflow and to determine its position through referencing this. If required, this association shall be used to identify the catchment connecting the outfall and the outflow used for reference. 

The **relativePosition** association assigns to the outfall a position relative to a reference location fixed in the logical network of catchments. This means that the position of an outfall is determined relative to another realised outfall. If required, this association shall be used to assign a position to an inflow or outflow of a catchment using existing reference location.  

The **outfallRealisation** association relates the outfall to a feature which realises the logical outfall. If required, this association shall be used to describe the 'real' object considered to be outfall of a catchment. In case of a topological realisation, the realisation of the outfall shall be of lower dimension than the realisation of the corresponding catchment.

| **Requirements Class** | [req/hy_abstract/hydrocomplex/outfall] (req/hy_abstract/hydrocomplex/outfall) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_Outfall | 
| Dependency | [/req/hy_abstract/hydrocomplex/catchment](/req/hy_abstract/hydrocomplex/catchment) |
| Dependency | [/req/hy_abstract/hydrocomplex/indirectposition](/req/hy_abstract/hydrocomplex/indirectposition) | 
| Dependency | [/req/hy_abstract/hydrocomplex/outfallrealisation](/req/hy_abstract/hydrocomplex/outfallrealisation) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/outfall.contributingcatchment](/req/hy_abstract/hydrocomplex/outfall.contributingcatchment) |
| Requirement	| [/req/hy_abstract/hydrocomplex/outfall.receivingcatchment](/req/hy_abstract/hydrocomplex/outfall.receivingcatchment) |
| Requirement	| [/req/hy_abstract/hydrocomplex/outfall.relativeposition](/req/hy_abstract/hydrocomplex/outfall.relativeposition) |
| Requirement	| [/req/hy_abstract/hydrocomplex/outfall.outfallrealisation](/req/hy_abstract/hydrocomplex/outfall.outfallrealisation) |

##### 7.4.2.6	Catchment Realisation
The HY_CatchmentRealisation feature type (Figure 29) conceptualizes the multiple realisation of a 'un-realised', logical catchment by typical features in common use to communicate the common recognition of a catchment as the unit of study shared across sub-domains. However, particular realisations may refer only to one or the other. HY_Flowpath, HY_CatchmentBoundary, and HY_Catchment Area are special types defined to topologically realise the hydrologic determination of the logical catchment in terms of face, edge and node, as well as to reflect the connectivity of catchments by hydrologic features connected in typical networks. The HY_HydroNetwork type realises a logical catchment in the enirety of connected network features, whereas the HY_CartographicRealisation realises a catchment as set of map layers. The implied topological relationships 'boundary' and 'spoke' reference the ISO topology model described in the ISO1907: Spatial Schema, whereby the realised outfall is always of lower dimension than the realised catchment. 

The catchment realisation concept implies a hydro(sphere) complex in such that if a catchment realisation exists, these features are in the same hydrologic complex as the catchment they realise. In this way any feature realisation of a logical catchment references the hydrologic determination of the realised catchment. If the realised catchment is connected with other catchments via its outfall, possible feature realisations are also connected. 

![Figure 29: Catchment realisation (UML class diagram)](figs/fig29.png)
Figure 29: Catchment realisation (UML class diagram)

The catchment realisation feature types defined in this standard refer to objects on the land surface for the purpose of testing the applicability of the conceptual model in the context of surface water hydrology. In other contexts other types of catchment realisation may exist. Catchment realisations that not conform to the special types defined in this standard, for instance realisations in 3-dimensional perspectives, or in time, may use the general HY_CatchmentRealisation type. HY_CatchmentRealisation carries the *realisedCatchment* association implying the *hydroComplex* feature collection **[(in the conceptual model described by means of 'tagged value') - mention tagged values in general?]**. 

The **realisedCatchment** association relates a particular realisation with exactly the catchment that this feature realises. Referencing the hydrologic complex encompassing the catchment and its realisations, allows the existence of catchments to be recognized without the complexity and detail of a scientific model, and to link multiple realisations. Referencing the hydrologic determination, topological relationships can be established and common identifiers assigned. If required, this association shall be used to identify the unit of study realised in a domain-specific feature. 

| **Requirements Class** | [/req/hy_abstract/hydrocomplex/catchmentrealisation] (/req/hy_abstract/hydrocomplex/catchmentrealisation)|
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_CatchmentRealisation | 
| Dependency | [/req/hy_abstract/hydrocomplex/catchment](/req/hy_abstract/hydrocomplex/catchment) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/catchmentrealisation.realisedcatchment](/req/hy_abstract/hydrocomplex/catchmentrealisation.realisedcatchment) |

The HY_Flowpath feature type specialises HY_CatchmentRealisation with respect to an implied linear geometric representation, incl. a straight line. The flowpath connecting the inflow and outflow of the logical catchment, is topologically understood as an edge bounded by inflow node and outflow nodes, and corresponding to left-bank and right-bank catchment faces. The 'boundary' and 'spoke' properties are described by means of 'tagged values': the topological 'boundary' is of type HY_OutfallRealisation, the topological 'spoke' of type HY_CatchmentArea. 

HY_Flowpath inherits from generalization the *realisedCatchment* association incl. *hydroComplex*, and carries the properties: *shape*, *flowpathNetwork*, and *contourLine*. 

The **shape** attribute defines the linear geometric representation. If required, an implementation shall use a geometry type  defined in ISO19107: Spatial Schema, e.g. GM_Curve type.

The **contourLine** association relates a contour line accompanying a given flowpath. ContourLine references the inflow and outflow node of the flowpath, and allows for an additional linear realisation of a catchment bound to the inflow and outflow nodes of a flowpath. If required, this association shall be used to assign isolines of some kind to a flowpath.     

The **flowpathNetwork** association defines a network as sequence of connected flowpathes. This concept requires a non-branching 'mainstem' of watercourses, and a single linear representation of each of these. If required, this association may be used to identify a network the realises in its entirety a catchment that contains the catchment which is realised by the network part. 

| **Requirements Class** | [req/hy_abstract/hydrocomplex/flowpath] (req/hy_abstract/hydrocomplex/flowpath) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_Flowpath | 
| Dependency | [/iso/19107/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/req/hy_abstract/hydrocomplex/catchmentrealisation](/req/hy_abstract/hydrocomplex/catchmentrealisation) |
| Dependency | [/req/hy_abstract/hydrocomplex/contourline](/req/hy_abstract/hydrocomplex/contourline) | 
| Dependency | [/req/hy_abstract/hydrocomplex/hydronetwork](/req/hy_abstract/hydrocomplex/hydronetwork) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/flowpath.shape](/req/hy_abstract/hydrocomplex/flowpath.shape) |
| Requirement	| [/req/hy_abstract/hydrocomplex/flowpath.contourline](/req/hy_abstract/hydrocomplex/flowpath.contourline) |
| Requirement	| [/req/hy_abstract/hydrocomplex/flowpath.flowpathnetwork](/req/hy_abstract/hydrocomplex/flowpath.flowpathnetwork) |

HY_ContourLine feature type specialises the HY_Flowpath class. It defines a linear contour accompanied to a given flowpath incl. a single polygon. Topologically, the contour is also a flowpath connecting the same inflow node and outflow node, but appears simultaneously to the flowpath. Connecting equal values of a certain property, the contour line may represent shore lines, stream lines or other isolines. HY_ContourLine inherits all properties from generalisation; it carries a *shape* attribute on its own. 

The HY_CatchmentBoundary feature type specialises HY_CatchmentRealisation with respect to an implied linear geometric representation, incl. single polygon. The catchment boundary connecting the inflow and outflow of the logical catchment, whereby inflow and outflow may overlay. It is topologically understood as an edge bounded by inflow node and outflow nodes, and corresponding to left-bank and right-bank catchment faces inside of the boundary. The 'boundary' and 'spoke' properties are described by means of 'tagged values': the topological 'boundary' is of type HY_OutfallRealisation; the topological 'spoke' is of type HY_CatchmentArea. 

HY_CatchmentBoundary inherits from generalization the *realisedCatchment* association incl. *hydroComplex*, and carries the properties: *shape*, and *boundaryNetwork*. 

The **shape** attribute defines the linear geometric representation. If required, an implementation shall use a geometry type  defined in ISO19107: Spatial Schema, e.g. GM_CompositeCurve type.

The **boundaryNetwork** association defines a network as mesh of connected boundaries. This concept requires a mesh of non-overlapping boundary lines, and a single linear representation of each of these. If required, this association may be used to identify a network the realises in its entirety a catchment that contains the catchment which is realised by the network part. 

| **Requirements Class** | [req/hy_abstract/hydrocomplex/catchmentboundary] (req/hy_abstract/hydrocomplex/catchmentboundary) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_CatchmentBoundary | 
| Dependency | [/iso/19107/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/req/hy_abstract/hydrocomplex/catchmentrealisation](/req/hy_abstract/hydrocomplex/catchmentrealisation) |
| Dependency | [/req/hy_abstract/hydrocomplex/hydronetwork](/req/hy_abstract/hydrocomplex/hydronetwork) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/catchmentboundary.shape](/req/hy_abstract/hydrocomplex/catchmentboundary.shape) |
| Requirement	| [/req/hy_abstract/hydrocomplex/catchmentboundary.boundarynetwork](/req/hy_abstract/hydrocomplex/catchmentboundary.boundarynetwork) |

The HY_CatchmentArea feature type specialises HY_CatchmentRealisation with respect to an implied areal geometric representation, incl. plane surface. The catchment area connecting the inflow and outflow of the logical catchment, is topologically understood as a  face bounded inwards by an inflow edge and outwards by an outflow edge. The 'boundary' is described by means of 'tagged values': the inward directed 'boundary' is of type HY_CatchmentBoundary, the outward directed 'boundary' of type HY_Flowpath. A topological 'spoke' is not defined in this standard. 

HY_CatchmentArea inherits from generalization the *realisedCatchment* association incl. *hydroComplex*, and carries the properties: *shape*, and *areaNetwork*. 

The **shape** attribute defines the linear geometric representation. If required, an implementation shall use a geometry type  defined in ISO19107: Spatial Schema, e.g. GM_Surface type.

The **areaNetwork** association defines an aggregate of catchment areas forming a connected network. This concept requires a non-overlapping aggregate of areas, and a single areal representation of each of these. If required, this association may be used to identify a network the realises in its entirety a catchment that contains the catchment which is realised by the network part. 

| **Requirements Class** | [req/hy_abstract/hydrocomplex/catchmentarea] (req/hy_abstract/hydrocomplex/catchmentarea) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_CatchmentArea | 
| Dependency | [/iso/19107/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/req/hy_abstract/hydrocomplex/catchmentrealisation](/req/hy_abstract/hydrocomplex/catchmentrealisation) |
| Dependency | [/req/hy_abstract/hydrocomplex/hydronetwork](/req/hy_abstract/hydrocomplex/hydronetwork) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/catchmentarea.shape](/req/hy_abstract/hydrocomplex/catchmentarea.shape) |
| Requirement	| [/req/hy_abstract/hydrocomplex/catchmentarea.boundarynetwork](/req/hy_abstract/hydrocomplex/catchmentarea.areanetwork) |

The HY_HydroNetwork feature type specialises HY_CatchmentRealisation with respect to a network of connected hydrologic features. Such a network realises in its entirety the hierarchical network of logically connected catchments, which are contained in an ultimate high-order catchment. It may be a sequence of flowpathes, an aggregate of catchment areas or a mesh of catchment boundaries.  HY_HydroNetwork inherits from generalization the *realisedCatchment* association incl. *hydroComplex*, and carries the associations *flowpath*, *catchmentBoundary* and *catchmentArea*. 

The HY_CartographicRealisation feature type specialises HY_CatchmentRealisation separate cartographic layers or maps, displaying a network of hydrologic features which may be connected at the representation level, or not. HY_HydroNetwork inherits from generalization the *realisedCatchment* association incl. *hydroComplex*.

**[continue here]**

 

##### 7.4.2.7	Outfall Realisation (former reference location)
The HY_OutfallRealisation type (Figure ) conceptualizes the idea of an arbitrary feature of interest that may be considered as outfall. Any location within a hydro(sphere) complex may realise the logical outfall, specifically as a permanent, stable reference location fixed or referenced by coordinates; outfall realisation may be represented by any geometric object, incl. a single point. 

![Figure : Outfall realisation (UML class diagram)](figs/fig.png)
Figure : Outfall realisation (UML class diagram) 

HY_OutfallRealisation carries three properties: *shape*, *outfallType* and *realisedOutfall* defines the relationship to exactly the catchment that is realisedby the special feature type.  If required, this association shall be used to reference the catchment wherein hydrologic processes are studied and reported by the data set or data product. Outfall realisation is defined here with the option to use a geometry type defined in ISO19107: Spatial Schema. To express the type of the realised outfall verbally, a term from the HY_TypeOfOutfall codelist may be used. Note that alternative code lists may be used but should be related to the terms in Annex E using an appropriate formalism.  

this allows, and identifiers to be assigned by referencing the outfall even if stream networks, catchment areas and watersheds are not reliably determined.. through reference to the outfall

| **Requirements Class** | [/req/hy_abstract/hydrocomplex/outfallrealisation] (/req/hy_abstract/hydrocomplex/outfallrealisation) | 
| --- | --- |
| Target type	| Implementation schema |
| Name | HY_CatchmentRealisation | 
| Dependency | [/iso/19107/...](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/req/hy_abstract/hydrocomplex/outfall](/req/hy_abstract/hydrocomplex/outfall) | 
| Dependency | [/req/hy_abstract/hydrocomplex/typeofoutfall](/req/hy_abstract/hydrocomplex/typeofoutfall) | 
| Requirement	| [/req/hy_abstract/hydrocomplex/outfallrealisation.typeofoutfall](/req/hy_abstract/hydrocomplex/outfallrealisation.shape |
| Requirement	| [/req/hy_abstract/hydrocomplex/outfallrealisation.typeofoutfall](/req/hy_abstract/hydrocomplex/outfallrealisation.typeofoutfall) 
| Requirement	| [/req/hy_abstract/hydrocomplex/outfallrealisation.realisedoutfall](/req/hy_abstract/hydrocomplex/outfallrealisation.realisedoutfall) 

**[needs review]**
he reference location may be a geometric point identified by co-ordinates, or any other feature carrying such a reference point. A fixed landmark, a monitoring station, a spring where groundwater enters the surface, may be a reference point but also a point projected onto the surface or created from merging disjoint locations; vertically arranged points may be aggregated and projected onto surface, a delta of a river system merged to virtual mouth, diffuse groundwater discharge placed on rivers or lakes. 


The HY_ReferenceLocation class describes a permanent, stable reference location such as a landmark fixed and referenced by coordinates.
Placed in the catchment network in terms of an outfall, the reference location will be the referent of the (linear) river reference system; a hydrologic feature associated with a reference location can be considered to be carrier of the referent relative to which a distance may be determined. The HY_ReferenceLocation class carries three properties: *refPoint*, *refPointType*, *networkLocation*. 

The **refPoint** and **refPointType** attributes describes the reference location as point of a particular geometry. Given that a single point may have several reported locations depending on its nature and the precision of measurement, these attributes describe an accepted common point. If required, the reference point shall be identified using the GM_Point type, or the HY_RefPointType codelist described in Annex ... , table ... . **[insert reference]** Note that alternative code lists may be used but should be related to the terms in Annex E using an appropriate formalism.  

The **networkLocation** association locates the reference location in a given network of catchments. If required, this association shall be used to determine a referent topologically as inflow to a receiving or outflow of a contributing catchment.

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



#### 7.4.5	The River Positioning system

**[text moved from 7.4.2: catchment model]**
**[START Using a linear river reference system (as defined in section 7.4.4) any feature of interest can be placed on the linear flowpath relative to such a referent. This allows to create a flowline network from a sequence of flowpathes 'drawn' between inflow and outflow nodes. Special types of one- and two-dimensional geometric representations in common use in hydrology are defined to support this. END]**

This supports to build an hierachical network realising the catchment, and to visualise these network views using an appropriate geometric representation. 

The River Positioning model (figure 25) provides a simple model to place a feature of interest 'along a river' via topology and geometry (see section 6.4). River Positioning introduces the concept of Indirect Position where a position is determined on the linear representation of the catchment linking the feature of interest and an identified reference location either as absolute distance, relative or interpolative to the referent. This concept uses a (linear) river reference system whose origin is set at the outfall of the catchment that corresponds to the feature of interest, and whose linear shape is given by the flowpath representing the catchment linking the outfall (origin) with the outfall marked by the reference location. Each catchment has its own reference system which can be combined as necessary using catchment topology. Applying the linear referencing along flowpath to a given network of catchments, a hydrographic or channel network can be thought as a sequence of catchments visualised using an appropriate geometric representation. 

![Figure 25: River Positioning System (UML class diagram)](figs/fig25.png)
Figure 25: River Positioning System (UML class diagram)
**[\*\*\*!!! Dave, fig25 updated\*\*\*]**

The HY_IndirectPosition class provides a pattern to assign a position to a particular location relative to an identified reference location using a river referencing system based on catchment topology and (linear) catchment representation.  Understanding the newly placed location topologically as inflow node to a receiving (lower) catchment, and a (downstream) reference location as the identified outflow node of this catchment, the length of the flowpath representing this catchment between inflow and outflow determines the position; or vice versa the length of the flowpath representing a (upper) catchment which receives flow from an identified inflow node and contributes to the new place. This allows at the representation level to place a feature of interest interpolative on a flowpath between identified reference locations each understood as inflow or outflow nodes of a catchment, even if this is not explicitly delineated. 

This type may use ISO 19148(2012):LinearReferencing understanding the (linearly represented) catchment between the new location and the reference location as the 'event' in terms of ISO19148 that associates the inflow/outflow node to be placed with the outflow/inflow node marked by the reference location; in terms of catchment representation, the flowpath starting at the location to be placed and drawn towards the known reference location may be understood as an event in terms of ISO19148. HY_IndirectPosition associates four properties: *absolute*, *relative*, *referenceLocation*, *riverReferenceSystem*.

**[\*\*\* does ISO19148 needs to be listed as a normative document 'that constitutes provisions' in the hyf standard? - I think NO, since we not use ISO19148, we simply note (in line 440) that 19148 is supported by hyf. \*\*\*]**

The **absolute** and **relative** attributes provide an absolute or relative value for the distance to the identified reference point, including an indication of accuracy and precision of the absolute value. If required, an implementation should use the HY_DistanceToRefPoint type to provide the absolute value, and HY_RelativePosition type for the relative or interpolative value. Both types are defined here using basic types defined in ISO19103: Conceptual Schema. To express the relative position verbally, a term from the  HY_RelativePositionDescription codelist of general terms commonly used in hydrology to describe a spatial relationship between two locations may be used. Note that alternative code lists may be used but should be related to the terms in Annex E using an appropriate formalism.  

The *referenceLocation* association describes the reference location located in the network of catchments (referent in terms of ISO 19148). This supports to place an arbitrary feature of interest relative to inflow and outflow nodes using catchment topology. If required, this association shall be used to identify the permanent location relative to which a position is assigned to the outfall, or a feature of interest understood as such.

The *riverReferenceSystem* association describes the linear river reference system applied. This supports to place a feature of interest using the linear flowpath representing a catchment whose outfall marks the located start of the flowpath directed towards an identified reference location. If required, this association shall be used to identify the river reference system applied to assign a position to an outfall, or a feature of interest understood as such; an implementation may use the HY_RiverReferenceSystem type defined in this standard.

| **Requirements Class** | [/req/hy_riverpositioningsystem/indirectposition] (/req/hy_riverpositioningsystem/indirectposition) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_IndirectPosition |
| Dependency | [/req/hy_catchment/referencelocation] (/req/hy_catchment/referencelocation) | 
| Dependency | [/req/hy_riverpositioningsystem/distancetorefpoint] (/req/hy_riverpositioningsystem/distancetorefpoint) | 
| Dependency | [/req/hy_riverpositioningsystem/relativeposition] (/req/hy_riverpositioningsystem/relativeposition) | 
| Dependency | [/req/hy_riverpositioningsystem/riverreferencesystem] (/req/hy_riverpositioningsystem/riverreferencesystem) | 
| Requirement |	[/req/hy_riverpositioningsystem/indirectposition.absolut]  (/req/hy_riverpositioningsystem/indirectposition.absolut)
| Requirement |	[/req/hy_riverpositioningsystem/indirectposition.relative]  (/req/hy_riverpositioningsystem/indirectposition.relative)
| Requirement |	[/req/hy_riverpositioningsystem/indirectposition.referencelocation]  (/req/hy_riverpositioningsystem/indirectposition.referencelocation) |
| Requirement |	[/req/hy_riverpositioningsystem/indirectposition.riverreferencesystem]  (/req/hy_riverpositioningsystem/indirectposition.riverreferencesystem) |

The HY_RiverReferenceSystem class provides a topology-based reference system to simply assign a position 'along a river' using its geometric representation. The origin of the river reference system is set at the location to be placed, understood as outfall of a catchment. The geometric shape is defined by the linear flowpath representing the catchment between the origin and an identified reference location upstream or downstream of the origin. The position on flowpath is provided as distance from the located start of the flowpath at origin and end at reference location towards the flowpath is directed.  Requiring an origin, a shape and an axis, HY_RiverReferenceSystem carries three associations: *locatedStart*, *linearElement*, *axis*. 

The **locatedStart** association locates the origin of the river reference system at the start of the linear flowpath, i.e. at the inflow or outflow node of the represented catchment. The **linearElement** association defines the flowpath representing the catchment between origin and reference location as the linear shape used in the river reference system. The **axis** association describes the axis orientation from the located start (origin) directed towards the referent (reference point). If required, these associations shall be applied to assign a position to an outfall, or a feature of interest understood as such.

| **Requirements Class** | [/req/hy_riverpositioningsystem/indirectposition.riverreferencesystem] (/req/hy_riverpositioningsystem/indirectposition.riverreferencesystem) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_RiverReferenceSystem |
| Dependency | [/req/hy_catchment/outfall] (/req/hy_catchment/outfall) | 
| Dependency | [/req/hy_catchment/flowpath] (/req/hy_catchment/flowpath) |
| Dependency | [/req/hy_riverpositioningsystem/riverreferencesystemaxis] (/req/hy_riverpositioningsystem/riverreferencesystemaxis) | 
| Requirement |	[/req/hy_riverpositioningsystem/riverreferencesystem.locatedstart]  (/req/hy_riverpositioningsystem/indirectposition.locatedstart) |
| Requirement |	[/req/hy_riverpositioningsystem/riverreferencesystem.linearelement]  (/req/hy_riverpositioningsystem/riverreferencesystem.linearelement) |
| Requirement |	[/req/hy_riverpositioningsystem/riverreferencesystem.referencelocation]  (/req/hy_riverpositioningsystem/riverreferencesystem.referencelocation) |
| Requirement |	[/req/hy_riverpositioningsystem/riverreferencesystem.axis]  (/req/hy_riverpositioningsystem/riverreferencesystem.axis) |

### 7.5 The Surface Hydro Feature application schema

The Surface Hydro Feature application schema provides concepts of hydrologic features occurring on the land surface to enable contextually related information models to build relationships to the catchment model and the hydrographic network model described in this standard (sections 7.4.2 and 7.4.3).  An informative surface water  model defines the most common types of a water body accumulating water on the land surface, each special by origin, size, or the phase of the contained water, by the property to move, or their interaction with other bodies of water. Taking into account the conceptual separation of a watercourses (see section 6.5) into a water body and its containing channel, the concepts of surface water bodies are provided separately from those of the confining structures. The surface water confines model conceptualize common structures confining a water body on the land surface, including their aggregation into a network of channels, to formalise relationships to the hydrographic network model and the catchment model. The Surface Hydro Feature application schema contains the packages: HY_SurfaceWater and HY_SurfaceWaterConfines. 
contains the packages: HY_SurfaceWater and HY_SurfaceWaterConfines. 

![Figure 26: The surface water and surface water confines model (UML class diagram)](figs/fig26.png)
Figure 26: The surface water and surface water confines model (UML class diagram)

#### 7.5.1	The Hydrographic Network model
The hydrographic network model (figure 23) defines a logical network of water bodies. Conceptually, the aggregate of water bodies is understood as the hydrographic appearance of the catchment of study in the perspective of the undertaken study, and the visualisation of the hydrographic network as a cartographic representation of the catchment. Given that a topological upstream-downstream relationship is defined between catchments (see section 6.4.2), a water body has no other role than being part of the network that mirrors the network of contributing and receiving catchments. This means that the connectivity between water bodies appearing in the hydrographic network is virtual, and that water bodies can be aggregated in the hydrographic network irrespective of whether the accumulated water is flowing or not. This allows to aggregate permanent and temporary water bodies of flowing or stagnant water in a network view portraying a catchment, and to visualise the represented the catchment. To supports this concept of a virtual connectivity, parts in the hydrographic network associate typical reference points which can be located topologically as outfall of a corresponding catchment.

Following the conceptual separation of a watercourse into water body and containing channel (see section 6.5), the hydrographic network is defined independent of the network of containing channels. This approach allows to separately visualise the hydrographic network of 'blue' lines or polygons, whereby the logically connected water bodies may or may not be connected at the representation level. 

The hydrographic network model defines the major elements describing the hydrographic network and the relationships between them. A network water body may be segmented at vertical cross- or longitudinal sections in succeeding parts, each part in horizontal strata. A water body part associates a typical reference location, allowing to place another feature relative to this using the (linear) river reference system described in section 7.4.5. 

![Figure 23: Hydrographic Network model (UML class diagram)](figs/fig23.png)
Figure 23: Hydrographic Network model (UML class diagram)
**[\*\*\*!!! Dave, fig23 updated\*\*\*]**

##### 7.5.1.1	HydrographicNetwork
The HY_HydrographicNetwork class describes the aggregate of permanent and temporary bodies of flowing or stagnant water, as what the catchment under study appears, and that may be visualised in map layers to cartographically represent this catchment. The HY_HydrographicNetwork class carries one association: *visualisation*. 

The **visualisation** association relates to the hydrographic network its cartographic visualisation, either as a separate map, or one of many thematic layers. If required, this association shall be used to identify a map or geoschematic view displaying the hydrographic network that in its entirety, separately or as set of layers, represents the catchment without describing the displayed network parts in detail.

| **Requirements Class** | [/req/hy_hydrographicnetwork/hydrographicnetwork] (/req/hy_hydrographicnetwork/hydrographicnetwork) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_HydrographicNetwork |
| Dependency | [/req/hy_catchment/networkcartography] (/req/hy_catchment/networkcartography) | 
| Requirement |	[/req/hy_hydrographicnetwork/hydrographicnetwork.visualisation]  (/req/hy_hydrographicnetwork/hydrographicnetwork.visualization) |

##### 7.5.1.2	WaterBody, WaterBodyPart and WaterBodyStratum
The HY_WaterBody and HY_WaterBodyPart class define a water body, or part of this, participating in the hydrographic network. The HY_WaterBodyStratum class describes a horizontal layer in a stratified water body determined by differences in thermal or salinity characteristics or by oxygen or nutrient content, or by virtual storage zones of a reservoir. 

The water body concept refers to an accumulated mass of liquid water, distinct from other masses of water. Its shape is determined by the occupied landform, the hosting hydrogeologic unit, a man made container, or another confining structure, and in case of on open waterbody bound to atmospheric pressure exerted on its surface. Each water body, or part of this, may be described in terms of a reservoir storing water for future use. In the context of hydrometric observation, a water bod may be understood as the feature of interest sampled by a hydrometric (sampling) feature. A water body is defined as special type of the named hydrologic feature (see section 7.4.1), because of names usually given to a water body in common experience varying whithin context or for some parts. Special types of water bodies occurring on the land surface are described in the 'Surface Hydro Feature' application schema in section ... . **[\*\*\* insert reference\*\*\*]**. A separate conceptual model capturing the specifics of features associated with the groundwater domain will be provided within the GroundwaterML 2.0 specification (under development). **[\*\*\* insert reference\*\*\*]** 

**[\*\*\*  HY_Glacier is removed from the model. -- it's an issue similar to atmospheric and groundwater features, and since no relationship to a (glacier fed) catchment is defined. the accumulation of ice from atmospheric origin is subject of specific glacier models not in scope (see line 365) -- it's sufficient here (I think) to have the WaterSolidPhase feature which is still needed with respect to ice cover, is in soil, snowmelt discharging in water body, ..., to reflect snow and ice as parts in the hydrographic network \*\*\*]**

HY_WaterBody and HY_WaterBodyPart inherit from the generalization the *identifier*, *name* and *context* properties. HY_WaterBody, HY_WaterBodyPart and HY_WaterBodyStratum each associate the aggregate in which they participate. The *hydrographicNetwork* association relates to a water body the network, *waterBody* to a water body its parts, and *stratifiedWaterBody* to the stratified water body part its strata. If required, these associations shall be used to identify the aggregates the water body, water body part or statum are parts of. HY_WaterBodyPart carries five properties: *fixedLandmark*, *upstreamSegment*,  *downstreamSegment*, *streamCrossSection*, and *streamLongitudinalSection*. HY_WaterBodyStratum has two properties: *storage* and *stratumType*.

The **fixedLandmark** associates to the water body part a permanent landmark referenced by co-ordinates. If required, this shall be used to identify on a water body (part) a permanent reference location which can be located in the network of catchment as outfall. This supports to place a water body part relative to this using the (linear) river reference system described in section 7.4.5. 

The **upstreamSegment** and **downstreamSegment** associations relate to a water body (part) parts up or downstream. If required, these associations shall be used to identify upstream or downstream segments connected with the water body (part).

The **streamCrossSection** and **longitudinalCrossSection** associations relate to a water body (part) vertical sections confining them.  If required, this association shall be used to identify sections either at right angles to the main (average) direction of flow, or along the stream (centre) line.

The **storage** association describes a zone in a stratified water body, part of the network, terms of storing water as a resource for future use. If required, this association shall be used to describe the reservoir used for storage, regulation and control of water resources. The **stratumType** attribute may be used to specify the type of the stratum or zone using a term from a controlled vocabulary.

| **Requirements Class** | [/req/hy_hydrographicnetwork/waterbody] (/req/hy_hydrographicnetwork/waterbody) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_WaterBody |
| Dependency | [/req/hy_namedFeature/hydrofeature] (/req/hy_namedFeature/hydrofeature) |
| Dependency | [/req/hy_hydrographicnetwork/hydrographicnetwork] (/req/hy_hydrographicnetwork/hydrographicnetwork) | 
| Requirement |	[/req/hy_hydrographicnetwork/waterbody.hydrographicnetwork]  (/req/hy_hydrographicnetwork/waterbody.hydrographicnetwork) |

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
| Dependency | [/iso/19103/](https://inspire-twg.jrc.it/svn/iso) |
| Dependency | [/req/hy_hydrographicnetwork/waterbodypart] (/req/hy_hydrographicnetwork/waterbodypart) | 
| Dependency | [/req/hy_storage/reservoir] (/req/hy_storage/reservoir) | 
| Requirement |	[/req/hy_hydrographicnetwork/waterbodystratum.stratifiedwaterbody]  (/req/hy_hydrographicnetwork/waterbodystratum.stratifiedwaterbody) |
| Requirement |	[/req/hy_hydrographicnetwork/waterbodystratum.stratumtype]  (/req/hy_hydrographicnetwork/waterbodystratum.stratumtype) |
| Requirement |	[/req/hy_hydrographicnetwork/waterbodystratum.storage]  (/req/hy_hydrographicnetwork/waterbodystratum.storage) |

##### 7.5.1.3	Water Liquid Phase and Water Solid Phase 
The HY_Water_LiquidPhase and HY_Water_SolidPhase define a simple concept of the accumulation of water in water bodies. This definition refers to the matter accumulated to a mass of water. In its liquid form water is considered accumulated in water bodies; in its solid phase water may be accumulated after melting, or as a layer of ice or snow on an open water body. The accumulation of water in the atmosphere or below the land surface, e.g. rain, soil moisture or groundwater, is not in scope of this standard, as well as the accumulation of snow and ice in glaciers which is subject of glaciology science. Informative packages describing a simple model to take into account water from atmospheric origin, particularly from precipitation, or water occurring below the land surface without the complexity and detail of rainfall-runoff or groundwater models, are provided in Annex ... . **[\*\*\* insert reference \*\*\*]**. A conceptual model capturing the specifics of features associated with the groundwater domain will be provided with the GroundwaterML 2.0 under development. **[\*\*\* insert reference to GWML2\*\*\*]**

HY_Water_LiquidPhase carries the association *accumulatingWaterBody*; HY_Water_SolidPhase associates two properties: *snowmelt* and *coveredWaterBody*. If required, these associations shall be used to identify the water body, part of the network, where liquid water as a material is accumulated. 

| **Requirements Class** | [/req/hy_hydrographicnetwork/waterliquidphase] (/req/hy_hydrographicnetwork/waterliquidphase) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_WaterLiquidPhase |
| Dependency | [/req/hy_hydrographicnetwork/waterbodystratum] (/req/hy_hydrographicnetwork/waterbodystratum) | 
| Requirement |	[/req/hy_hydrographicnetwork/waterliquidphase.accumulatingwaterbody]  (/req/hy_hydrographicnetwork/waterliquidphase.accumulatingwaterbody) |

| **Requirements Class** | [/req/hy_hydrographicnetwork/watersolidphase] (/req/hy_hydrographicnetwork/watersolidphase) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_WaterSolidPhase |
| Dependency | [/req/hy_hydrographicnetwork/waterliquidphase] (/req/hy_hydrographicnetwork/waterliquidphase) | 
| Dependency | [/req/hy_hydrographicnetwork/waterbodypart] (/req/hy_hydrographicnetwork/waterbodypart) | 
| Requirement |	[/req/hy_hydrographicnetwork/watersolidphase.snowmelt]  (/req/hy_hydrographicnetwork/watersolidphase.snowmelt)
| Requirement |	[/req/hy_hydrographicnetwork/watersolidphase.coveredwaterbody]  (/req/hy_hydrographicnetwork/watersolidphase.coveredwaterbody) |

##### 7.5.1.4	Cross-Section and Longitudinal Section
The HY_CrossSection and HY_LongitudinalSection conceptualize the segmentation of a water body or a containing channel through vertical sections. Taking into account the conceptual separation of a watercourse (see section 6.5) into a water body and the containing channel, the cross section concept refers to both the cross section of a water body orthogonal to the direction of flow, and to the transversal profile of a channel; the longitudinal section concept refers to centre, stream or contour lines such a thalweg, shore or bank lines. 
 
HY_CrossSection and HY_LongitudinalSection each associate to a vertical section typical reference points: *crossSectionPoint* and *longitudalinalSectionPoint*. Located in the network of catchments, vertical sections allow to place a feature of interest relative to this using the (linear) river reference system described in section 7.4.5. If required, these associations shall be used to identify at a vertical section the permanent reference location located in the network of catchments as outfall. 

| **Requirements Class** | [/req/hy_hydrographicnetwork/crosssection] (/req/hy_hydrographicnetwork/crosssection) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_CrossSection |
| Dependency | [/req/hy_catchment/referencelocation] (/req/hy_catchment/referencelocation) | 
| Requirement |	[/req/hy_hydrographicnetwork/crosssection.crosssectionpoint]  (/req/hy_hydrographicnetwork/crosssection.crosssectionpoint)

| **Requirements Class** | [/req/hy_hydrographicnetwork/longitudinalsection] (/req/hy_hydrographicnetwork/longitudinalsection) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_CrossSection |
| Dependency | [/req/hy_catchment/referencelocation] (/req/hy_catchment/referencelocation) | 
| Requirement |	[/req/hy_hydrographicnetwork/longitudinalsection.longitudinalsectionpoint]  (/req/hy_hydrographicnetwork/longitudinalsection.longitudinalsectionpoint) |

#### 7.5.2 The Channel Network model 

The Surface Water Confines model (figure 26) defines a logical network of channels. Conceptually, the aggregate of channels is understood as the geomorphologic appearance of the catchment of study in the perspective of the undertaken study, and its visualisation as a cartographic representation of the catchment. Such as for the hydrographic network, network parts are virtually connected based on catchment topology, allowing channels to be aggregated irrespective of containing a perennial, intermittent or ephemeral water body. 

Following the conceptual separation of a watercourse into water body and containing channel (see section 6.5), the channel network is defined independent of the network of water bodies. This approach allows to separately visualize the drainage pattern, whereby the logically connected channels may or may not be connected at the representation level. 

The channel network model defines the major elements of channel network, and the relationships between them. A network water body may be segmented at vertical cross- or longitudinal sections in succeeding parts. To support the concept of a virtual connectivity, channel parts associate typical reference points which can be located topologically as outfall of a corresponding catchment. This allows to place a feature of interest relative to this using the (linear) river reference system described in section 7.4.5. 

![Figure 27: Channel network model, incl. relation to the hydrogaphic network model (UML class diagram)](figs/fig27.png)
Figure 27: Channel network model, incl. relation to the hydrogaphic network model (UML class diagram)

##### 7.5.2.1	ChannelNetwork
The HY_ChannelNetwork class describes the aggregate of channels, as what the cachment under study appears, and that may be visualized in map layers to cartographically represent this catchment. The HY_ChannelNetwork class carries twoi properties: *drainagepattern*, *visualization*. 

The **drainagePattern** attribute describes in general the drainage pattern. If required, an implementation may use a term from the HY_DrainagePattern codelist described in Annex ... , table ... . **[insert reference]** Note that alternative code lists may be used but should be related to the terms in Annex E using an appropriate formalism.  

The **visualisation** association relates to the channel network its cartographic visualisation, either as a separate map, or one of many thematic layers. If required, this association shall be used to identify a map or geoschematic view displaying the channel network that in its entirety, separately or as set of layers, represents the catchment without describing the displayed network parts in detail.

| **Requirements Class** | [/req/hy_channelnetwork/channelnetwork] (/req/hy_channelnetwork/channelnetwork) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_ChannelNetwork |
| Dependency | [/req/hy_catchment/networkcartography] (/req/hy_catchment/networkcartography) | 
| Dependency | [[/req/hy_channelnetwork/drainagepattern] (/req/hy_channelnetwork/drainagepattern) |
| Requirement |	[/req/hy_channelnetwork/channelnetwork.visualisation]  (/req/hy_channelnetwork/channelnetwork.visualisation) | 
| Requirement |	[/req/hy_channelnetwork/channelnetwork.drainagepattern]  (/req/hy_channelnetwork/channelnetwork.drainagepattern) |

##### 7.5.2.2	Channel and channel part
The HY_Channel and HY_ChannelPart class define a channel, or part of this between vertical sections, participating in the channel network. The concept refers to natural or man-made, open or closed channels through or along which water may flow, or not.  

HY_Channel and HY_ChannelPart each associate the aggregate in which they participate. The *channelNetwork* association relates to a network channel the channel network, and *channelPart* to a channel its parts. If required, these associations shall be used to identify the aggregates the channel and the channel part are parts of. HY_ChannelPart carries three properties: *containedWaterBody*, *profileTransversal*,  *profileLongitudinal*. 

The **containedWaterBody** association relates to the channel part a water body part. Associating the contained water body allows to describe a watercourse as the channel through or along which water may flow [3]. If required, this association shall be used to identify the water body part (mass of water) contained in the channel part. 

The **profileTransversal** and  **profileLongitudinal** associations relate to the channel the separating transversal or longitudinal profile. If required, this association shall be used to identify the vertical section either at right angles to the main (average) direction of flow, or along a line. 

| **Requirements Class** | [/req/hy_channelnetwork/channel] (/req/hy_channelnetwork/channel) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_Channel |
| Dependency | [/req/hy_channelnetwork/channelnetwork] (/req/hy_channelnetwork/channelnetwork) |
| Requirement |	[/req/hy_channelnetwork/channel.channelnetwork]  (/req/hy_channelnetwork/channel.channelnetwork) |

| **Requirements Class** | [/req/hy_channelnetwork/channelpart] (/req/hy_channelnetwork/channelpart) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_ChannelPart |
| Dependency | [/req/hy_channelnetwork/channel] (/req/hy_channelnetwork/channel) |
| Dependency | [/req/hy_hydrographicnetwork/waterbodypart] (/req/hy_hydrographicnetwork/waterbodypart) | 
| Dependency | [/req/hy_hydrographicnetwork/crosssection] (/req/hy_hydrographicnetwork/crosssection) | 
| Dependency | [/req/hy_hydrographicnetwork/longitudinalsection] (/req/hy_hydrographicnetwork/longitudinalsection) | 
| Requirement |	[/req/hy_channelnetwork/channelpart.channel]  (/req/hy_channelnetwork/channelpart.channel) |
| Requirement |	[/req/hy_channelnetwork/channelpart.containedwaterbody]  (/req/hy_channelnetwork/channelpart.containedwaterbody) |
| Requirement |	[/req/hy_channelnetwork/channelpart.profiletransversal]  (/req/hy_channelnetwork/channelpart.profiletransversal) |
| Requirement |	[/req/hy_channelnetwork/channelpart.profilelongitudinal]  (/req/hy_channelnetwork/channelpart.profilelongitudinal) |

#### 7.5.3 The Surface Water Body types 

The Surface Water model defines typical specialisations of the water body defined in section 7.4.3 of this standard. Being a specialization of the HY_WaterBody class, each subtype inherits from the general HY_HydroFeature class the name and context properties which allows to handle names given in cross-jurisdiction and multi-lingual contexts to a river, canal, lake, lagoon, estuary, or impoundment, as well as to describe them in related contexts, e.g. water resources assessment. 

The HY_River subtype defines the existence of body of surface water, participating in a hydrographic network, special due to its property to permanently or temporarily flow. 

The HY_Canal subtype defines the existence of body of surface water, participating in a hydrographic network, special due to its artificial origin (man-made).

The HY_Lake subtype defines the existence of body of surface water, participating in a hydrographic network, special due to its considerable size.  

The HY_Impoundment subtype defines the existence of body of surface water, participating in a hydrographic network, special due to be formed by collecting water, as by a dam. 

The HY_Lagoon subtype defines the existence of body of surface water, participating in a hydrographic network, special due to its shallow depth and interaction with the open sea.

The HY_Estuary subtype defines the existence of body of surface water, participating in a hydrographic network, special due to branching and its interaction with the open sea.

Each water body specialisation is understood to be part of the hydrographic network, and may generally consist of several parts, may be stratified or used as reservoir. In other contexts other specialisations, or a typical segmentation may exist, that not conform to the types defined in this standard may use the general water body or water body part types.


#### 7.5.4	The Storage model

The Storage model (figure 24) provides a concept to describe any water body, or a part/stratum of this, in terms of a reservoir storing water for future use. The separate storage model allows to describe the hydrographic network without the details of storage capacities that a water body may have, and vice versa storage reservoirs to be referenced independent of their role within a network. To virtually connect a reservoir (defined as special water body) with other water bodies in the hydrographic network, a typical reference point on reservoir is defined allowing to place a feature of interest relative to this using the (linear) river reference system described in section 7.4.5. Details of connectivity may be designed with a particular application. 

Special concepts of surface or underground reservoirs may be defined with application. The storage concept can be applied to surface and subsurface reservoirs, whereby underground reservoirs should not be confused with the groundwater reservoir which usually refers to the containing aquifer. A conceptual model capturing the specifics of features associated with the groundwater domain will be provided with the GroundwaterML 2.0 under development. **[\*\*\* insert reference to GWML2\*\*\*]** 

![Figure 24: Storage model (UML class diagram)](figs/fig24.png)
Figure 24: Storage model (UML class diagram)
**[\*\*\*!!! Dave, fig24 updated\*\*\*]**

The HY_Reservoir class specializes the water body, either natural or man-made, used for storage, regulation and control of water resources. The reservoir concept refers to a mass of water managed in zones between operating levels. Being a specialization of the HY_WaterBody class, the reservoir inherits from the general HY_HydroFeature class the name and context properties which allows to describe the reservoirs in a related context, e.g. flood control or water supply. 

HY_Reservoir associates to a reservoir a typical reference point: *barrierePoint*. Located in the network of catchments, a barrier point allows to place a feature of interest relative to this using the (linear) river reference system described in section 7.4.5. If required, these associations shall be used to identify on reservoir a permanent reference location located in the network of catchments as outfall. 

| **Requirements Class** | [/req/hy_storage/reservoir] (/req/hy_storage/reservoir) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_Reservoir |
| Dependency | [/req/hy_hydrographicnetwork/waterbody] (/req/hy_hydrographicnetwork/waterbody) | 
| Dependency | [/req/hy_catchment/referencelocation] (/req/hy_catchment/referencelocation) | 
| Requirement |	[/req/hy_storage/reservoir.barrierpoint]  (/req/hy_storage/reservoir.barrierpoint) | 


### 7.6 The Hydrometric Network application schema

The Hydrometric Network schema (figure 29) defines a logical model to take into account a network of hydrometric stations as a specific appearance of the catchment of study in the perspective of an hydrologic observation, without the detail of the observation strategy. The core concept is that of a network of logically connected hydrometric stations situated in the catchment that is represented with the cartographic visualisation of the network. This enables contextually related information models to relate monitoring stations and observing posts to the hydrologic features, finally to the represented catchment, as usually required in the context of environmental reporting or when interpreting, comprising and processing results of preceding observations into a new set of data. 

![Figure 28: Hydrometric network model (UML class diagram)](figs/fig28.png)
Figure 28: Hydrometric network model (UML class diagram)
**[\*\*\*insert class diagram\*\*\*]**

The hydrometric network model introduces the concept of 'position on river' which allows an arbitrary hydrologic station, even free from position, to be located in the network of catchments to establish upstream-downstream relationships, and to assign a position releative to a reference location, or to place another feature of interest relative to a network station using the (linear) river reference system described in section 7.4.5. 

The HY_HydrometricNetwork class defines the network aggregate consisting of hydrometric features which may be separated into several hydrometric feature parts. To support the concept of a virtual connectivity, a hydrometric feature associate typical reference points which can be located topologically as outfall of a corresponding catchment. HY_HydrometricFeature and HY_HydrometricFeaturePart classes associate the aggregate in which they participate. HY_HydrometricFeature associates a *positionOnRiver*. 

| **Requirements Class** | [/req/hy_hydrometricnetwork/hydrometricnetwork] (/req/hy_hydrometricnetwork/hydrometricnetwork) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_HydrometricNetwork |
| Dependency | [/req/hy_catchment/networkcartography] (/req/hy_catchment/networkcartography) | 
| Requirement |	[/req/hy_hydrometricnetwork/hydrometricnetwork.visualisation]  (/req/hy_hydrometricnetwork/hydrometricnetwork.visualisation)| 

| **Requirements Class** | [/req/hy_hydrometricnetwork/hydrometricfeature] (/req/hy_hydrometricnetwork/hydrometricfeature) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_HydrometricFeature |
| Dependency | [/req/hy_hydrometricnetwork/hydrometricnetwork] (/req/hy_hydrometricnetwork/hydrometricnetwork) |
| Dependency | [/req/hy_catchment/referencelocation] (/req/hy_catchment/referencelocation) | 
| Requirement |	[/req/hy_hydrometricnetwork/hydrometricfeature.hydrometricnetwork]  (/req/hy_hydrometricnetwork/hydrometricfeature.hydrometricnetwork)| 
| Requirement |	[/req/hy_hydrometricnetwork/hydrometricfeature.positiononriver]  (/req/hy_hydrometricnetwork/hydrometricfeature.positiononriver)| 

| **Requirements Class** | [/req/hy_hydrometricnetwork/hydrometricfeaturepart] (/req/hy_hydrometricnetwork/hydrometricfeaturepart) |
| --- | --- |
| Target type	| Implementation Schema |
| Name | HY_HydrometricFeaturePart |
| Dependency | [/req/hy_hydrometricnetwork/hydrometricfeature] (/req/hy_hydrometricnetwork/hydrometricfeature) |
| Requirement |	[/req/hy_hydrometricnetwork/hydrometricfeaturepart.hydrometricfeature]  (/req/hy_hydrometricnetwork/hydrometricfeaturepart.hydrometricfeature)| 



** END OF SECTION 7 --- END OF SECTION 7 --- END OF SECTION 7 --- END OF SECTION 7 --- END OF SECTION 7 --- END OF SECTION 7 **


