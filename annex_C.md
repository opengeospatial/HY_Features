## ANNEX C - The Subsurface Hydro Feature application schema (informative)

### C.1 – The Subsurface Hydro Feature model 

The informative Subsurface Hydro Feature schema introduces a simple model to take into account water occurring below the land surface in formations of rock or soil as a catchment contribution to a common outlet, without the complexity and detail of a groundwater model.  This concept refers to the holistic approach of the catchment as the unit wherein surface and subsurface water continuously interact in the hydrologic cycle, and all water ultimately is flowing to an identified outlet. It is intended that contextually related information models may use the concepts defined here, to build relationships to hydrologic features, finally to a catchment represented in data describing the properties of subsurface water and typcial data products derived from these to display the occurence and distribution of groundwater and water in soil.

The Subsurface Hydro Feature model introduces a concept of subsurface water accumulated in water bodies which participate in the hydrographic network. This allows groundwater and water in soil to be related to a permanent reference location which can be located in the catchment network, and finally to add places where water enters the surface or disappears underground to the hierachical network of catchments in terms of an inflow or outflow node of a corresponding catchment. This supports special hydrogeological appearances of the catchment network, which may be displayed using particular geometric shapes and symbology. 

The Subsurface Hydro Feature model is introduced with respect to that branch of hydrology which deals with groundwater, applied to all types of subsurface water. Information models focused on a special type of subsurface water may use the defined feature types to relate groundwater or water in soil as inflow or outflow to a catchment, without modeling in detail the interaction of groundwater and surface water.  A conceptual model capturing the specifics of features associated with the groundwater domain will be provided with the GroundwaterML 2.0 under development. 

Following the conceptual separation of watercourses, the subsurface hydro feature schema contains the packages: HY_SubsurfaceWater and HY_SubsurfaceWaterConfines. 

![Figure 15: Subsurface Hydro Feature model (UML class diagram)](figs/fig15.png) 
Figure 15: Subsurface Hydro Feature model (UML class diagram) 
**[\*\*\*update figure\*\*\*]**

### C.2 The Subsurface Water model 

The Subsurface Water model defines the most popular types of water occuring in the satured and non-satured zone of the lithosphere with respect to pressure head or the property to move due to gravity and capillary action. Specialising the liquid water type defined in the hydrogaphic network schema, groundwater and vadose water accumulated in a water body is considered to be part of a hydrographic network.  

The HY_Groundwater class specializes HY_Water_LiquidPhase with respect to the existence of water occupying the saturated zone. It inherits the *accumulatingWaterBody* association from generalisation, which allows to relate groundwater to the hydrographic network aggregate of water bodies. 

The HY_VadoseWater class specializes HY_Water_LiquidPhase with respect to the existence of water occupying the unsaturated zone. It inherits the *accumulatingWaterBody* association from generalisation, which allows to relate subsurface water to the hydrographic network aggregate of water bodies. This type is further specialised to HY_SoilWater, HY_SoilMoisture and HY_GravitationalWater.

#### C.3 The Subsurface Water Confines model
The Subsurface Water confines model defines basic types of hydrogeologic units containing groundwater or vadose water. Conceptually, the hydrogeologic unit is understood as the hydrogeologic appearance of the catchment of study in the perspective of particular study, and its visualisation as a cartographic representation of the catchment. Similar to hydrographic or channel network, network parts may be connected based on catchment topology. However, the aggregation and segmentation of hydrogeologic units is not in scope the hydrologic feature feature model. A conceptual model capturing the specifics of features associated with the groundwater domain will be provided with the GroundwaterML 2.0 under development. 

The general HY_HydrogeologcUnit class is intended to represent a catchment network by displaying hydrologically significant characteristics of water-containing formations of rock or soil, allowing further contextual specializations. The HY_Aquifer class defines the general existence of the containing unit wherein groundwater may be accumulated, understood as groundwater reservoir. HY_Aquifer carries an association to a well used to extract, inject or infiltrate water from or to the aquifer. The HY_Well class is defined with respect to the potential carrier of a reference location. This would allow to associate an aquifer to a permanent reference location which can be located in the catchment network, and finally to place the location of the well in the hierachical network of catchments in terms of an inflow or outflow node of a corresponding catchment. This supports special hydrogeological appearances of the catchment network, which may be displayed using particular geometric shapes and symbology. HY_Well carries the association to the reference location: wellLocation.

