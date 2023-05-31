# Systems Biology Markup Language

## Objects

### SBML

- xmlns
  - Type: string
  - Description: Namespace of the used SBML data model
  - Default: "http://www.sbml.org/sbml/level3/version2/core"
  - Const: True
  - XML: @xmlns
- level
  - Type: integer
  - Description: Level of the SBML document
  - Default: 3
  - Const: True
  - XML: @level
- model
  - Type: [Model](#Model)
  - Description: Models defined in this SBML document

### SBase

- name
  - Type: string
  - Description: Name of the object
  - XML: @name
- meta_id
  - Type: string
  - Description: Meta ID of the object
  - XML: @metaid
- sbo_term
  - Type: [SBOTerm](#SBOTerm)
  - Description: Ontology precisely defining the type of the object
  - XML: @sboTerm 

### Model [_SBase_]

- unit_definitions
  - Type: [UnitDefinition](#UnitDefinition)
  - Description: Contains all Unit definitions
  - Multiple: True
  - XML: listOfUnitDefinitions
- compartments
  - Type: [Compartment](#Compartment)
  - Description: Contains all Compartment definitions
  - Multiple: True
  - XML: listOfCompartments
- species
  - Type: [Species](#Species)
  - Description: Contains all Species definitions
  - Multiple: True
  - XML: listOfSpecies
- parameters
  - Type: [Parameter](#Parameter)
  - Description: Contains all Parameter definitions
  - Multiple: True
  - XML: listOfParameters
- reactions
  - Type: [Reaction](#Reaction)
  - Description: Contains all Reaction definitions
  - Multiple: True
  - XML: listOfReactions

### UnitDefinition [_SBase_]

- units
  - Type: [Unit](#Unit)
  - Description: Base units that make up the unit itself.
  - Multiple: True
  - XML: ListOfUnits

### Unit [_SBase_]

- kind
  - Type: [Kind](#Kind) 
  - Description: Kind of the base unit
  - XML: @kind
- exponent
  - Type: float
  - Description: Exponent of the unit
  - XML: @exponent
- scale
  - Type: integer
  - Description: Scale of the unit
  - XML: @scale
- multiplier
  - Type: float
  - Description: Multiplier of the unit
  - XML: @multiplier

### Compartment [_SBase_]

- spatial_dimensions
  - Type: float
  - Description: Dimensionality of the compartment
  - XML: @spatialDimensions
- size
  - Type: float 
  - Description: Size of the compartment
  - XML: @size
- units
  - Type: string
  - Description: Unique identifier of the unit used in thsi compartment
  - XML: @units
- constant
  - Type: bool
  - Description: Whether the colume is constant or not
  - XML: @constant

### Species [_SBase_]

- compartment
  - Type: string
  - Description: Unique identifier of the compartement
  - XML: @compartment
- initial_amount
  - Type: float
  - Description: The initial amount used for this species
  - XML: @initialAmount
- initial_concentration
  - Type: float
  - Description: Initial concentration of this species
  - XML: @initialConcentration
- substance_units
  - Type: string
  - Description: Unique identifier of the unit that has been used.
  - XML: @substanceUnits
- has_only_substance_units
  - Type: bool
  - Default: False
  - Description: Whether this species is given as a concentration or absolute amount
  - XML: @hasOnlySubstanceUnits
- boundary_condition
  - Type: bool
  - Default: True
  - Description: Whether or not there are boundary conditions found in this species.
  - XML: @boundaryConditions
- constant
  - Type: bool
  - Description: Whether or not the species is constant or not.
  - XML: @constant
- conversion_factor
  - Type: string
  - Description: Unique ID of the conversion factor
  - XML: @conversionFactor

### Parameter [_SBase_]

- value
  - Type: float
  - Description: Value of the estimated parameter
  - XML: @value
- units
  - Type: string
  - Description: Reference to the unit of the estimated parameters
  - XML: @units
- constant
  - Type: bool
  - Description: Whether or not the parameter is constant
  - XML: @constant

### Reaction [_SBase_]

- reversible
  - Type: bool
  - Description: Whether or not the reaction is reversible
  - XML: @reversible
- reactants
  - Type: [SpeciesReference](#SpeciesReference)
  - Description: Reactant references
  - Multiple: True
  - XML: listOfReactants
- products
  - Type: [SpeciesReference](#SpeciesReference)
  - Description: Product references
  - Multiple: True
  - XML: listOfProducts
- modifiers
  - Type: [ModifierSpeciesReference](#ModifierSpeciesReference)
  - Description: Modifier reference
  - Multiple: True
  - XML: listOfModifiers
- kinetic_law
  - Type: [KineticLaw](#KineticLaw)
  - Description: Kinetic law describing the reaction
  - XML: kineticLaw

### SimpleSpeciesReference [_SBase_]

- species
  - Type: string
  - Description: Species ID reference
  - XML: @species

### SpeciesReference [_SimpleSpeciesReference_]

- stoichiometry
  - Type: float
  - Description: Stoichiometry of the given species reference
  - XML: @stoichiometry
- constant
  - Type: bool
  - Description: Whether or not this species is constant in the reaction
  - XML: @constant

### ModifierSpeciesReference [_SimpleSpeciesReference_]

- placeholder
  - Type: string    
  - Description: This is just a placeholder because empty objects are under dev

### KineticLaw [_SBase_]

- math
  - Type: string
  - Description: Mathematical model of the kinetic klaw (WIP)
- local_parameters
  - Type: [LocalParameter](#LocalParameter)
  - Description: Local parameters of this kinetic law
  - Multiple: True
  - XML: listOfLocalParameters

### LocalParameter [_SBase_]

- value
  - Type: float
  - Description: Numerical value of the parameter
  - XML: @value
- units
  - Type: string
  - Description: Reference to the unit that has been used
  - XML: @units

## Enumerations

### Kind

```python
MOLE = "mole"
G = "g"
```

### SBOTerm

```python
REACTION = "sdsd"
LALAL = "sdsd"
JJHJ = "dhjhfjd"
```
