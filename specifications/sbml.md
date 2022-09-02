# Systems Biology Markup Language

### SBML

- __xmlns*__
  - Type: string
  - Description: Namespace of the used SBML data model
  - Default: http://www.sbml.org/sbml/level3/version2/core
  - Const: True
  - XML: @xmlns
- __level__
  - Type: integer
  - Description: Level of the SBML document
  - Default: 3
  - Const: True
  - XML: @level
- __model__
  - Type: [Model](#Model)
  - Description: Models defined in this SBML document

### SBase

- __name__
  - Type: string
  - Description: Name of the object
  - XML: @name
- __meta_id__
  - Type: string
  - Description: Meta ID of the object
  - XML: @metaid
- __sbo_term__
  - Type: [SBOTerm](#SBOTerm)
  - Description: Ontology precisely defining the type of the object
  - XML: @sboTerm 

### Model [_SBase_]

- __unit_definitions__
  - Type: [UnitDefinition](#UnitDefinition)
  - Description: Contains all Unit definitions
  - Multiple: True
  - XML: listOfUnitDefinitions
- __compartments__
  - Type: [Compartment](#Compartment)
  - Description: Contains all Compartment definitions
  - Multiple: True
  - XML: listOfCompartments
- __species__
  - Type: [Species](#Species)
  - Description: Contains all Species definitions
  - Multiple: True
  - XML: listOfSpecies
- __parameters__
  - Type: [Parameter](#Parameter)
  - Description: Contains all Parameter definitions
  - Multiple: True
  - XML: listOfParameters
- __reactions__
  - Type: [Reaction](#Reaction)
  - Description: Contains all Reaction definitions
  - Multiple: True
  - XML: listOfReactions

### UnitDefinition [_SBase_]

- __units*__
  - Type: [Unit](#Unit)
  - Description: Base units that make up the unit itself.
  - Multiple: True
  - XML: ListOfUnits

### Unit [_SBase_]

- __kind*__
  - Type: [Kind](#Kind) 
  - Description: Kind of the base unit
  - XML: @kind
- __exponent*__
  - Type: float
  - Description: Exponent of the unit
  - XML: @exponent
- __scale*__
  - Type: integer
  - Description: Scale of the unit
  - XML: @scale
- __multiplier*__
  - Type: float
  - Description: Multiplier of the unit
  - XML: @multiplier

### Compartment [_SBase_]

- __spatial_dimensions__
  - Type: float
  - Description: Dimensionality of the compartment
  - XML: @spatialDimensions
- __size__
  - Type: float 
  - Description: Size of the compartment
  - XML: @size
- __units__
  - Type: string
  - Description: Unique identifier of the unit used in thsi compartment
  - XML: @units
- __constant*__
  - Type: bool
  - Description: Whether the colume is constant or not
  - XML: @constant

### Species [_SBase_]

- __compartment*__
  - Type: string
  - Description: Unique identifier of the compartement
  - XML: @compartment
- __initial_amount__
  - Type: float
  - Description: The initial amount used for this species
  - XML: @initialAmount
- __initial_concentration__
  - Type: float
  - Description: Initial concentration of this species
  - XML: @initialConcentration
- __substance_units__
  - Type: string
  - Description: Unique identifier of the unit that has been used.
  - XML: @substanceUnits
- __has_only_substance_units*__
  - Type: bool
  - Description: Whether this species is given as a concentration or absolute amount
  - XML: @hasOnlySubstanceUnits
- __boundary_condition*__
  - Type: bool
  - Description: Whether or not there are boundary conditions found in this species.
  - XML: @boundaryConditions
- __constant*__
  - Type: bool
  - Description: Whether or not the species is constant or not.
  - XML: @constant
- __conversion_factor__
  - Type: string
  - Description: Unique ID of the conversion factor
  - XML: @conversionFactor

### Parameter [_SBase_]

- __value__
  - Type: float
  - Description: Value of the estimated parameter
  - XML: @value
- __units__
  - Type: string
  - Description: Reference to the unit of the estimated parameters
  - XML: @units
- __constant*__
  - Type: bool
  - Description: Whether or not the parameter is constant
  - XML: @constant

### Reaction [_SBase_]

- __reversible*__
  - Type: bool
  - Description: Whether or not the reaction is reversible
  - XML: @reversible
- __reactants__
  - Type: [SpeciesReference](#SpeciesReference)
  - Description: Reactant references
  - Multiple: True
  - XML: listOfReactants
- __products__
  - Type: [SpeciesReference](#SpeciesReference)
  - Description: Product references
  - Multiple: True
  - XML: listOfProducts
- __modifiers__
  - Type: [ModifierSpeciesReference](#ModifierSpeciesReference)
  - Description: Modifier reference
  - Multiple: True
  - XML: listOfModifiers
- __kinetic_law__
  - Type: [KineticLaw](#KineticLaw)
  - Description: Kinetic law describing the reaction
  - XML: kineticLaw

### SimpleSpeciesReference [_SBase_]

- __species*__
  - Type: string
  - Description: Species ID reference
  - XML: @species

### SpeciesReference [_SimpleSpeciesReference_]

- __stoichiometry__
  - Type: float
  - Description: Stoichiometry of the given species reference
  - XML: @stoichiometry
- __constant*__
  - Type: bool
  - Description: Whether or not this species is constant in the reaction

### ModifierSpeciesReference [_SimpleSpeciesReference_]

- __placeholder__
  - Type: string    
  - Description: This is just a placeholder because empty objects are under dev

### KineticLaw [_SBase_]

- __math__
  - Type: string
  - Description: Mathematical model of the kinetic klaw (WIP)
- __local_parameters__
  - Type: [LocalParameter](#LocalParameter)
  - Description: Local parameters of this kinetic law
  - Multiple: True
  - XML: listOfLocalParameters

### LocalParameter [_SBase_]

- __value__
  - Type: float
  - Description: Numerical value of the parameter
  - XML: @value
- __units__
  - Type: string
  - Description: Reference to the unit that has been used
  - XML: @units

## Ontologies

#### Kind

```python
MOLE = "mole"
G = "g"
```

#### SBOTerm

```python
REACTION = "sdsd"
LALAL = "sdsd"
JJHJ = "dhjhfjd"
```