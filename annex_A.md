## ANNEX A - Abstract Test Suite (normative)

### A.1 Introduction
These test suites ascertain the compliance of the conformance targets for the HY_Features specification with the specification itself. Each instance of hydrologic feature data is encoded according to a specific interchange schema, so the role of conformance with the abstract specification is that such an implementation schema can be related to the common definitions of HY_Features.

An implementation schema conforming to HY_Features SHALL provide a formal mapping from one or more Feature Types present in the implementation schema to Feature Types defined in this standard specification, including all mandatory properties defined by the realized HY_Features concept. Default values to be assumed must be specified in this mapping.

### A.2 Conformance class: HY_HydroFeature application schema equivalence

| **Conformance Class** | [/spec/hydrology/hydrofeature/1.0/conf/hy_ hydrofeature] (/spec/hydrology/hydrofeature/1.0/conf/hy_ hydrofeature) | 
| --- | --- | 
| Test | [/conf/uml_hydrofeature/namedfeature/*] (/conf/uml_hydrofeature/namedfeature/*) | |
| Test | [/conf/uml_hydrofeature/hydrocomplex/*] (/conf/uml_hydrofeature/hydrocomplex/*) | |
| Test | [/conf/uml_hydrofeature/positioning/*] (//conf/uml_hydrofeature/positioning/*) | |
| Requirement | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test purpose | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test method | Inspect the mapping between the data exchange schema and the HY_Features model to determine that all relevant schema elements are mapped to HY_Features equivalents. |
| Test type | Capability | 

### A.3 Conformance class: HY_SurfaceHydroFeature application schema equivalence

| **Conformance Class** | [/ spec/hydrology/surfacehydrofeature/1.0/conf/hy_ surfacehydrofeature] (/ spec/hydrology/surfacehydrofeature/1.0/conf/hy_ surfacehydrofeature) | 
| --- | --- |
| Test | [/conf/uml_surfacehydrofeature/channelnetwork/*] (/conf/uml_surfacehydrofeature/channelnetwork/*) |
| Test | [/conf/uml_surfacehydrofeature/hydrographicnetwork/*] (/conf/uml_surfacehydrofeature/hydrographicnetwork/*) |
| Test | [/conf/uml_surfacehydrofeature/surfacewaterbodies/*] (/conf/uml_surfacehydrofeature/surfacewaterbodies/*) |
| Test | [/conf/uml_surfacehydrofeature/storage/*] (/conf/uml_surfacehydrofeature/storage/*) | |
| Requirement | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test purpose | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test method | Inspect the mapping between the data exchange schema and the HY_Features model to determine that all relevant schema elements are mapped to HY_Features equivalents. |
| Test type | Capability | 

### A.4 Conformance class: HY_HydrometricFeature application schema equivalence

| **Conformance Class** | [/ spec/hydrology/hydrometricfeature/1.0/conf/hy_ hydrometricfeature] (/ spec/hydrology/hydrometricfeature/1.0/conf/hy_hydrometricfeature) | 
| --- | --- |
| Test | [/conf/uml_ hydrometricfeature/hydrometricfeature/*] (/conf/uml_hydrometricfeature/hydrometricfeature/*) |
| Requirement | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test purpose | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test method | Inspect the mapping between the data exchange schema and the HY_Features model to determine that all relevant schema elements are mapped to HY_Features equivalents. |
| Test type | Capability | 

