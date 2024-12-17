# TransComp 

This README provides an overview of the Model _TransComp_ within iDesignRES.  

It is handled by TU Wien and part of WP 1, Task number 1.4. 

## Purpose of the model  

The purpose of the model is routed is manyfold and can be summarized by the following: 

* __Transport sector component model:__ First and foremost, it is designed to allow for a regional analysis of the development of energy demand by the transport sector. 

* __Regional implications of decarbonization scenarios to transport sector:__ It functions as an extension of large-scale energy system models and translates global decarbonization scenarios to the regional transport sector. 

* __Stress-testing of transport sector modelling in energy system models:__ The increased granularity in the parametrization of the transport sector representation serves further to test the accuracy in the modelling of transport sector as a demand sector in larger-scale models applied in this project. 

## Model design philosophy  

The starting point of the design of this model was the modelling of charging infrastructure requirements, distinguishing these requirements between long-distance transport and transport activity within regions. In terms of geographic resolution, the goal was to decrease the geographic granularity from classic location-allocation models, while still representing relevant granularity to distinguish between long-distance and regional transport. As the adoption of energy infrastructure concerns all transport modes, the model formulation was extended to include multiple transportation modes which are conceptualized as “layers” that are overlapping, all represented with consistent geographic resolution and temporal resolution. The scope of analysis in terms of the transport demand that needs to be serviced, and available transport services (modes, technologies, types of vehicles, fuel types, ... ) is set by the user. The reason for this is the following: The transport sector encompasses many different subsectors, including different types of modes, related infrastructures and consumer’s that have a limited interference with and relevance to each other.  

## Input to and output from the model  

### Input Parameters

In the following, the model parameters for the basic application are listed (optional parameters concerning, e.g., policies/subsidies are excluded here).

#### Basic Model Parameters

##### Spatial and Temporal Extent
- **Time horizon** of model and a **graph representation** of the region of interest.

##### Modes, Vehicle Types, Drivetrain Technologies, and Fuels
- Selection of modes, vehicle types, drivetrain technologies, and fuels.
- Considered **routes, goods, income classes, region types** (e.g., urban, rural, suburban).
- Carbon price development.

##### Mode Infrastructure
- **CAPEX** of infrastructure.
- **OPEX** of infrastructure.
- Initial transport capacity of mode infrastructure (by location).
- Travel speed (by region type).

###### When Mode is Represented with Vehicle Stock
- Initial vehicle stock structure (by generation of car models).
- **CAPEX** of vehicles.
- **OPEX** costs (excluding fuel costs).
- Lifetimes.
- Technical parameters:  
  - Specific consumption, tank capacity, peak fueling capacity.  
  - Annual range, occupation/load.  
  - Possible goods (including passengers) to be transported.  
  - Tank, specific emissions.

- Fuel costs (by location).
- CAPEX & OPEX of fueling infrastructure.

###### When Mode is Represented Without Explicit Modeling of Vehicle Stock
- Specific emissions.
- Levelized costs.

##### Routes, Goods, Income Classes, Region Types
- Origin-destination data.
- Monetary budgets, values of time by income class/consumer type/type of good.
- Region-type-specific cost components for the operation of vehicles (e.g., parking fees).

---

### Output Parameters

The decision variables of the model are:

1. **Transport activity** by mode, vehicle type, drivetrain technology, and route.
2. **Fueled energy** by fuel, region, route, vehicle type, and technology.
3. **Vehicle stock** by route, consumer type.
4. **Mode infrastructure and fueling infrastructure capacities** by mode/fuel type, by location.
5. **Budget excesses** (penalization term for this can be set by the user).


## Implemented features  

- Two different possibilities to model a mode: _Levelized cost modelling_ vs. _stock-based modelling_
- __Energy-system model related features:__ Softcoupling to energy system models via energy prices, supply infrastructure costs and availibility, fueling infrastructure capacitires and activity
- __Policy-related features:__ Subsidies for modes and vehicles, bans of new registrations, goals concerning emissions
- __Behavioural features:__ Value of time, monetary budget

## Core assumption  

### Cost-Optimality
- **Monetary budget, expected market shares**:  
  As the regional scope of this is too granular to accurately model, constraints and granularity of different consumer groups are introduced to counteract these effects.

### Simplifications in the Model
- **Travel demand**:  
  This is treated as an exogenous input to the model.  
  - No rebound effect from the deployment of infrastructures is considered.  
  - No effects of mode or technology choice and costs on travel demand are included.

### Vehicle Availability
- **Availability of different vehicle types**:  
  Constraints are imposed to limit vehicle availability based on:  
  - Assumptions derived from insights in scientific literature, or  
  - Outputs from other models.

### Additional Considerations
- **Vehicle possession vs. Income class vs. Purpose of trip**:  
  Marginal benefits are expected in these areas.
- **Lengths of connections between regions**:  
  Assumed to be consistent, including the related infrastructures.


## Repository (Remove this part if the model is uploaded in this repository and you don't want to refer to an external repository) 

(https://github.com/antoniamgolab/iDesignRES_transcompmodel.git)[https://github.com/antoniamgolab/iDesignRES_transcompmodel.git]