# PTRO Ontology - Competency Questions as SPARQL Queries
## Based on Actual Ontology Structure from PTRO.owl

After analyzing the PTRO.owl file from https://github.com/DKFZ-E220/PTRO/blob/main/PTRO.owl, here are two competency questions formulated as SPARQL queries based on the actual classes and properties in the ontology.

---

## Competency Question 1: Retrieve Body Weight Measurements Over Time for Subjects

**Natural Language Question:**
"What are the body weight measurements collected for all mouse subjects across different study days, including their sex and strain information?"

**SPARQL Query:**
```sparql
PREFIX ptro: <https://purls.helmholtz-metadaten.de/ptro#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX ncit: <http://ncicb.nci.nih.gov/xml/owl/EVS/Thesaurus.owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT ?subject ?subjectId ?sex ?strain ?bodyWeight ?bodyWeightUnit ?studyDay
WHERE {
  # Subject identification
  ?subject a ncit:C69256 ;                    # Subject Unique Identifier class
           ptro:DKFZ000008 ?subjectId ;       # Subject identifier string
           ptro:DKFZ000040 ?sex ;             # Sex
           ptro:DKFZ000041 ?strain .          # Strain/Substrain
  
  # Species filter for Mouse
  ?subject ptro:DKFZ000009 ?speciesName .
  FILTER(CONTAINS(LCASE(?speciesName), "mouse") || CONTAINS(LCASE(?speciesName), "mus musculus"))
  
  # Body weight measurements
  ?subject ptro:DKFZ000016 ?bodyWeight ;      # Body weight value
           ptro:DKFZ000015 ?bodyWeightUnit ;  # Body weight unit
           ptro:DKFZ000018 ?studyDay .        # Study day of body weight collection
}
ORDER BY ?subject ?studyDay
```

**Use Case:**
This query enables researchers to track longitudinal body weight changes across subjects, which is critical for assessing treatment toxicity and overall animal health during preclinical trials. Body weight is a key endpoint in SEND-standardized studies.

**Expected Results:**
| subject | subjectId | sex | strain | bodyWeight | bodyWeightUnit | studyDay |
|---------|-----------|-----|--------|------------|----------------|----------|
| subj:001 | "M001" | "MALE" | "C57BL/6" | 25.3 | "g" | 1 |
| subj:001 | "M001" | "MALE" | "C57BL/6" | 26.1 | "g" | 7 |
| subj:001 | "M001" | "MALE" | "C57BL/6" | 24.8 | "g" | 14 |

---

## Competency Question 2: Find Subject Disposition and Death Information

**Natural Language Question:**
"Which subjects died during the study, what were their death diagnoses, whether the death was treatment-related, and on which study day did they die?"

**SPARQL Query:**
```sparql
PREFIX ptro: <https://purls.helmholtz-metadaten.de/ptro#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX ncit: <http://ncicb.nci.nih.gov/xml/owl/EVS/Thesaurus.owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT ?subject ?subjectId ?sex ?strain ?deathDiagnosis ?treatmentRelation ?studyDayOfDeath ?evaluator
WHERE {
  # Subject identification
  ?subject a ncit:C69256 ;                      # Subject Unique Identifier class
           ptro:DKFZ000008 ?subjectId ;         # Subject identifier
           ptro:DKFZ000040 ?sex ;               # Sex
           ptro:DKFZ000041 ?strain .            # Strain
  
  # Death information
  ?subject ptro:DKFZ000020 ?deathDiagnosis ;    # Death Diagnosis Name (DDTEST)
           ptro:DKFZ000021 ?treatmentRelation ; # Death Diagnosis Result Category (DDRESCAT)
           ptro:DKFZ000023 ?studyDayOfDeath .   # Study day of animal death (DDDY)
  
  # Optional: Evaluator information
  OPTIONAL {
    ?subject ptro:DKFZ000022 ?evaluator .       # Death Diagnosis Evaluator (DDEVAL)
  }
}
ORDER BY ?studyDayOfDeath
```

**Use Case:**
This query is essential for safety assessments in preclinical trials. It helps identify mortality patterns, determine whether deaths were treatment-related, and assess the overall safety profile of interventions. This information is critical for regulatory submissions following SEND standards.

**Expected Results:**
| subject | subjectId | sex | strain | deathDiagnosis | treatmentRelation | studyDayOfDeath | evaluator |
|---------|-----------|-----|--------|----------------|-------------------|-----------------|-----------|
| subj:042 | "M042" | "MALE" | "BALB/c" | "Tumor Burden" | "TREATMENT RELATED" | 35 | "TOX PATHOLOGIST" |
| subj:067 | "F067" | "FEMALE" | "C57BL/6" | "Natural Causes" | "NONTREATMENT RELATED" | 87 | "VETERINARIAN" |

---

## Additional Competency Questions (Bonus)

### Competency Question 3: Clinical Observations Over Time

**Natural Language Question:**
"What clinical observations were recorded for subjects, including the observation description, evaluator, and study day?"

**SPARQL Query:**
```sparql
PREFIX ptro: <https://purls.helmholtz-metadaten.de/ptro#>
PREFIX ncit: <http://ncicb.nci.nih.gov/xml/owl/EVS/Thesaurus.owl#>

SELECT ?subject ?subjectId ?observationTest ?observationResult ?studyDay ?evaluator ?reasonNotDone
WHERE {
  # Subject identification
  ?subject a ncit:C69256 ;
           ptro:DKFZ000008 ?subjectId .
  
  # Clinical observations
  ?subject ptro:DKFZ000034 ?observationTest ;  # Clinical Observations Test Name
           ptro:DKFZ000035 ?observationResult ; # Clinical Observations Result
           ptro:DKFZ000039 ?studyDay .          # Study Day of Clinical Observation
  
  # Optional fields
  OPTIONAL { ?subject ptro:DKFZ000038 ?evaluator . }      # Clinical Observations Evaluator
  OPTIONAL { ?subject ptro:DKFZ000037 ?reasonNotDone . }  # Reason not done
}
ORDER BY ?subject ?studyDay
```

---
### More Examples of Competency Questions: 
- **SPARQL**: [ontop-SPARQL queries](https://github.com/DKFZ-E220/PTRO/blob/main/mapping_PTRO_Ontop/ontop-SPARQL%20queries.md)

## Ontology Structure Notes

Based on the analysis of PTRO.owl, the ontology includes:

### Key Classes:
- **ncit:C69256** - Subject Unique Identifier (core subject class)
- **ncit:C14238** - Mouse (species)
- **ncit:C62289** - Domain (SEND domain concept)
- **ncit:C49572** - Demographics Domain
- **ncit:C49587** - Exposure Domain
- **ncit:C49592** - Laboratory Data Domain
- **ncit:C95085** - Body Weight Domain
- **sty:T015** - Mammal (Semantic Type)
- **sty:T010** - Vertebrate (Semantic Type)

### Key Data Properties (DKFZ-prefixed):
- **DKFZ000008** - Subject identifier (string)
- **DKFZ000009** - Species name (string)
- **DKFZ000010** - Genus species (string)
- **DKFZ000015** - Body weight unit (string)
- **DKFZ000016** - Body weight value (string)
- **DKFZ000017** - Body weight measurement (decimal)
- **DKFZ000018** - Study day of body weight collection (decimal)
- **DKFZ000019** - Death Diagnosis Short Name/DDTESTCD (string)
- **DKFZ000020** - Death Diagnosis Name/DDTEST (string)
- **DKFZ000021** - Death Diagnosis Result Category/DDRESCAT (string)
- **DKFZ000022** - Death Diagnosis Evaluator/DDEVAL (string)
- **DKFZ000023** - Study day of animal death/DDDY (string)
- **DKFZ000034** - Clinical Observations Test Name (string)
- **DKFZ000035** - Clinical Observations Result (string)
- **DKFZ000037** - Reason Test Not Done (string)
- **DKFZ000038** - Clinical Observations Evaluator (string)
- **DKFZ000039** - Study Day of Clinical Observation (decimal)
- **DKFZ000040** - Sex (integer)
- **DKFZ000041** - Strain/Substrain (string)
- **DKFZ000042** - Domain Abbreviation (string)

### Key Object Properties:
- **DKFZ000047, DKFZ000048** - Linking properties
- **DKFZ000076-DKFZ000088** - Various object properties connecting entities
- **roo:P100040** - Property from ROO (Radiation Oncology Ontology)

### Integration with External Ontologies:
- **NCIt** (NCI Thesaurus) - Biomedical terminology
- **STY** (Semantic Types Ontology) - High-level categorization
- **ROO** (Radiation Oncology Ontology) - Radiation therapy concepts
- **CDISC SEND** - All DKFZ properties map to SEND variables

---

## Usage Instructions

### Prerequisites:
1. Load PTRO.owl into a SPARQL-compliant triplestore (GraphDB, Apache Jena Fuseki, Stardog, etc.)
2. Load instance data following the PTRO structure
3. Ensure proper namespace declarations

### Namespace Declarations:
```sparql
PREFIX ptro: <https://purls.helmholtz-metadaten.de/ptro#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX ncit: <http://ncicb.nci.nih.gov/xml/owl/EVS/Thesaurus.owl#>
PREFIX sty: <http://purl.bioontology.org/ontology/STY/>
PREFIX roo: <http://www.cancerdata.org/roo/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcterms: <http://purl.org/dc/terms/>
```

### Execution:
```bash
# Using Apache Jena ARQ
arq --data=ptro-data.ttl --query=query1.sparql

# Using GraphDB Workbench
# Navigate to SPARQL tab and paste query

# Using curl with Fuseki endpoint
curl -X POST http://localhost:3030/ptro/sparql \
  --data-urlencode 'query@query1.sparql' \
  -H 'Accept: application/sparql-results+json'
```

---

## Validation

These queries have been designed based on:
1. Actual class definitions in PTRO.owl
2. SEND (Standard for Exchange of Nonclinical Data) variable mappings
3. NCIt concept codes and their usage in the ontology
4. DKFZ-specific data properties as defined in the OWL file

---

**Ontology Version:** 0.1 alpha  
**Ontology IRI:** https://purls.helmholtz-metadaten.de/ptro  
**Version IRI:** https://purls.helmholtz-metadaten.de/ptro/2025-11-25  
**Creator:** DKFZ-E220  
**License:** CC BY 4.0
