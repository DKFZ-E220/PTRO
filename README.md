# PTRO - Preclinical Trials in Radiation Oncology Ontology

**This version:**  
https://purls.helmholtz-metadaten.de/ptro/2025-11-25

**Latest version:**  
https://purls.helmholtz-metadaten.de/ptro

**Revision:**  
0.1 alpha

**Authors:**  
DKFZ-E220

**Download serialization:**  
[![RDF/XML](https://img.shields.io/badge/Format-RDF/XML-blue.svg)](PTRO.owl)

**License:**  
[![License](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)

**Visualization:**  
[![Visualize with WebVowl](https://img.shields.io/badge/Visualize_with-WebVowl-blue.svg)](webvowl/index.html)

**Cite as:**  
DKFZ-E220. Revision: 0.1 alpha. Retrieved from: https://purls.helmholtz-metadaten.de/ptro/2025-11-25

## Abstract

PTRO focuses on preclinical data standardized according to SEND, with emphasis on radiation oncology studies. It is not intended to replace clinical trial ontologies or general-purpose biomedical ontologies but to complement them by addressing the specific needs of preclinical research data representation.

PTRO is designed to:

- Support **FAIR data practices** (Findable, Accessible, Interoperable, Reusable).
- Facilitate **flexible querying** within virtual knowledge graph environments.
- Enable researchers to **integrate, compare, and reuse** preclinical trial data across studies and institutions.
- Provide a semantic layer for linking SEND data with related biomedical ontologies.

## Table of Contents

- [Introduction](#introduction)
- [Ontology Overview](#ontology-overview)
- [Download & Formats](#download--formats)
- [Visualization](#visualization)
- [Key Features](#key-features)
- [Usage Examples](#usage-examples)
- [Citation](#citation)
- [References](#references)
- [Acknowledgments](#acknowledgments)
- [License](#license)

## Introduction

The Preclinical Trials in Radiation Oncology (PTRO) ontology provides a comprehensive semantic framework for representing preclinical trial data in radiation oncology research. Built on SEND (Standard for Exchange of Nonclinical Data) standards, PTRO enables semantic integration of experimental data, facilitating data sharing, reuse, and knowledge discovery across research institutions.

## Ontology Overview

PTRO is structured to support the complete lifecycle of preclinical radiation oncology trials, including:

- **Study Design & Methodology**: Trial protocols, experimental groups, treatment regimens
- **Subject Information**: Animal models, demographics, grouping
- **Interventions**: Radiation dosimetry, drug administration, combined therapies
- **Observations & Findings**: Clinical observations, microscopic findings, tumor measurements
- **Results & Outcomes**: Efficacy endpoints, survival data, toxicity assessments

### Key Concepts

The ontology covers several core domains:

1. **Study Administration**: Trial metadata, protocols, regulatory compliance
2. **Subject Domain**: Animal subjects, demographics, disposition
3. **Interventions Domain**: Exposure data, dosing, radiation parameters
4. **Findings Domain**: Clinical observations, body weights, tumor volumes
5. **Special Purpose Domains**: Trial summary, trial sets, relationships

## Download & Formats

The ontology is available in multiple serialization formats:

- **JSON-LD**: [ontology.jsonld](ontology.jsonld)
- **RDF/XML**: [ontology.owl](ontology.owl)
- **N-Triples**: [ontology.nt](ontology.nt)
- **Turtle**: [ontology.ttl](ontology.ttl)

## Visualization

Explore the ontology structure visually:

- **WebVOWL Visualization**: [View Interactive Diagram](webvowl/index.html)

## Key Features

### FAIR Principles Compliance

PTRO is designed from the ground up to support FAIR data principles:

- **Findable**: Rich metadata with persistent identifiers
- **Accessible**: Multiple serialization formats, standard protocols
- **Interoperable**: Links to established biomedical ontologies (NCIt, ROO, STY)
- **Reusable**: Clear licensing, comprehensive documentation, provenance tracking

### Integration with Standards

- **CDISC SEND**: Full alignment with SEND domain models
- **Radiation Oncology Ontology (ROO)**: Interoperability with clinical radiation data
- **NCI Thesaurus (NCIt)**: Leverages standardized biomedical terminology
- **Semantic Types Ontology (STY)**: Semantic categorization of concepts

### Flexible Query Support

PTRO enables powerful queries across preclinical datasets:

- Cross-study comparisons
- Cohort identification based on complex criteria
- Temporal analysis of experimental outcomes
- Integration with external data sources

## Usage Examples

### Example 1: Querying Study Information

```sparql
PREFIX ptro: <https://purls.helmholtz-metadaten.de/ptro/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT ?study ?studyId ?title
WHERE {
  ?study a ptro:Study ;
         ptro:hasStudyIdentifier ?studyId ;
         ptro:hasTitle ?title .
}
```

### Example 2: Finding Radiation Protocols

```sparql
PREFIX ptro: <https://purls.helmholtz-metadaten.de/ptro/>

SELECT ?protocol ?dose ?fractions
WHERE {
  ?protocol a ptro:RadiationProtocol ;
            ptro:hasDose ?dose ;
            ptro:hasFractionation ?fractions .
}
```

## Citation

If you use PTRO in your research, please cite:

**BibTeX:**
```bibtex
@misc{ptro2025,
  author = {DKFZ-E220},
  title = {Preclinical Trials in Radiation Oncology Ontology (PTRO)},
  year = {2025},
  howpublished = {\url{https://purls.helmholtz-metadaten.de/ptro/2025-11-25}},
  note = {Version 0.1 alpha}
}
```

**Plain Text:**
```
DKFZ-E220. (2025). Preclinical Trials in Radiation Oncology Ontology (PTRO). 
Revision: 0.1 alpha. Retrieved from: https://purls.helmholtz-metadaten.de/ptro/2025-11-25
```

## References

1. Giraldo, O., Sabyrrakhim, A., Roscher, M., Euler-Lange, R., Baumann, M., Kurth, I., & Hadiwikarta, W. W. (2024). *Semantic Representation of Preclinical Data in Radiation Oncology*. In Proceedings of the 15th International Conference on Biological and Biomedical Ontology (ICBO 2024). CEUR Workshop Proceedings, 3939. https://ceur-ws.org/Vol-3939/short2.pdf

2. DKFZ-E220. (2025). *Ontology for Preclinical Trials in Radiation Oncology (PTRO)*. GitHub. https://github.com/DKFZ-E220/PTRO/tree/main

3. CDISC SEND Standard. URL: https://www.cdisc.org/standards/foundational/send

4. Traverso A, van Soest J, Wee L, *et al.* The radiation oncology ontology (ROO): Publishing linked data in radiation oncology using semantic web and ontology techniques. Med Phys. 2018. doi: 10.1002/mp.12879.

5. NCI Thesaurus (NCIt). URL: https://ncithesaurus.nci.nih.gov/ncitbrowser/

6. National Library of Medicine. (n.d.). *Semantic Types Ontology (STY)*. URL: https://bioportal.bioontology.org/ontologies/STY

7. Wilkinson, M., Dumontier, M., Aalbersberg, I. et al. The FAIR Guiding Principles for scientific data management and stewardship. Sci Data 3, 160018 (2016). https://doi.org/10.1038/sdata.2016.18

## Acknowledgments

The authors would like to thank [Silvio Peroni](http://www.essepuntato.it/) for developing [LODE](http://www.essepuntato.it/lode), a Live OWL Documentation Environment, and [Daniel Garijo](https://w3id.org/people/dgarijo) for developing [Widoco](https://github.com/dgarijo/Widoco), the program used to create the documentation template.

## License

This ontology is licensed under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to:
- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material for any purpose, even commercially

Under the following terms:
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made.

---

**Repository:** https://github.com/DKFZ-E220/PTRO/tree/main  
**Documentation:** https://purls.helmholtz-metadaten.de/ptro  
**Contact:** DKFZ-E220
