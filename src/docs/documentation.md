---
title: Documentation
---

# Documentation
---
---

## Project Structure
---

docs/
  Intro.md - documentation pages
src/ - contains profiles and valueset definitions
  Patient.yaml - profile for patient
  Observation/
     bmi.yaml - specific profile for observation
  vs.gender.yaml - valueset definition
  vs.gender.csv  - codes for valueset
ig.yaml - manifest file

## New Resource Profile Template
---

- description: Text definition of the profile
- name: Name for this structure definition (computer friendly)
- status: The status of this structure definition. Enables tracking the life-cycle of the - content. draft | active | retired | unknown
- fhirVersion: FHIR Version this StructureDefinition targets
- kind: primitive-type | complex-type | resource | logical
- abstract: Whether the structure is abstract (false)
- type: Type defined or constrained by this structure (AdverseEvent)
- baseDefinition: Definition that this type is constrained/specialized from "http://hl7.org/fhir/StructureDefinition/AdverseEvent"
- derivation: specialization | constraint - How relates to base definition - constraint
- title: Name for this structure definition (human friendly) 'AZ AdverseEvent Profile'
- experimental: For testing purposes, not real usage - false
- date: Date last changed "2020-09-30"
- publisher: Name of the publisher (organization or individual) - "AstraZeneca"

- elements:
  - extension:
    - AZEmployeeReporter:
      - type: string
     -  description: AZ Employee Reporter
     -  title: AZ Employee Reporter Extension
     -  experimental: false
     -  date: "2020-12-18"
    -   publisher: AstraZeneca--

## ValueSets
---

A ValueSet resource instance specifies a set of codes drawn from one or more code systems, intended for use in a particular context. Value sets use CodeSystem resources by referring to them via their canonical reference.

### How to create a new ValueSet
---

Create a yaml file with the `vs.` prefix in the `src` folder.
The template looks as follows:

```
system: https://healthsamurai.github.io/ig-ae/CodeSystem/condition-outcome
description: AZ condition outcome valueset
concepts:
  - code: resolved
    display: Resolved
  - code: recovering
    display: Recovering
  - code: ongoing
    display: Ongoing
  - code: resolvedWithSequelae
    display: Resolved with Sequelae
  - code: fatal
    display: Fatal
  - code: unknown
    display: Unknown
  - code: recovered
    display: Recovered
```    


## CodeSystems
---

A CodeSystem resource declares the existence of and describes a code system or code system supplement and its key properties, and optionally defines a part or all of its content. Also known as Ontology, Terminology, or Enumeration.

### How to create a new CodeSystem
---

Create a yaml file with the `cs.` prefix in the `src` folder.
The template looks as follows:

```
description: Defines possible condition outcomes
content: complete
title: Condition Outcome
name: ConditionOutcome
version: 0.1.0
status: active
date: 2021-01-19T13:20:31+00:00
publisher: AstraZeneca
concepts:
- code: resolved
  display: Resolved
- code: recovering
  display: Recovering
- code: ongoing
  display: Ongoing
- code: resolvedWithSequelae
  display: Resolved with Sequelae
- code: fatal
  display: Fatal
- code: unknown
  display: Unknown
- code: recovered
  display: Recovered
```