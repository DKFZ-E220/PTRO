# PTRO - Preclinical Trials in Radiation Oncology Ontology

**This version:**  
https://purls.helmholtz-metadaten.de/ptro

**Revision:**  
0.1 alpha (2025-11-25)

**Documentation:** https://dkfz-e220.github.io/PTRO/

**Authors:**  
DKFZ-E220

## Abstract

PTRO focuses on preclinical data standardized according to SEND, with emphasis on radiation oncology studies. It is not intended to replace clinical trial ontologies or general-purpose biomedical ontologies but to complement them by addressing the specific needs of preclinical research data representation.


## Table of Contents

- [Ontology Overview](#ontology-overview)
- [Download & Formats](#download--formats)
- [Key Features](#key-features)
- [Usage Examples](#usage-examples)
- [Citation](#citation)
- [Relevant sources](#relevant-sources)
- [License](#license)


## Ontology Overview

PTRO is structured to support the complete lifecycle of preclinical radiation oncology trials, including:

- **Study Design & Methodology**: Trial protocols, experimental groups, treatment regimens
- **Subject Information**: Animal models, demographics, grouping
- **Interventions**: Radiation dosimetry, drug administration, combined therapies
- **Observations & Findings**: Clinical observations, microscopic findings, tumor measurements
- **Results & Outcomes**: Efficacy endpoints, survival data, toxicity assessments


## Download & Formats

- **RDF/XML**: [PTRO.owl](PTRO.owl)


## Key Features

### FAIR Principles Compliance

PTRO is designed from the ground up to support FAIR data principles:

- **Findable**: Rich metadata with persistent identifiers
- **Accessible**: Multiple serialization formats, standard protocols
- **Interoperable**: Links to established biomedical ontologies (NCIt, ROO, STY)
- **Reusable**: Clear licensing, comprehensive documentation, provenance tracking

### Integration with Standards and Vocabularies

- [**CDISC SEND**](https://www.cdisc.org/standards/foundational/send): Full alignment with SEND domain models
- [**Radiation Oncology Ontology (ROO)**](https://doi.org/10.1002/mp.12879): Interoperability with clinical radiation data
- [**NCI Thesaurus (NCIt)**](https://ncithesaurus.nci.nih.gov/ncitbrowser/): Leverages standardized biomedical terminology
- [**Semantic Types Ontology (STY)**](https://bioportal.bioontology.org/ontologies/STY): Semantic categorization of concepts

## Usage Examples

PTRO enables powerful queries across preclinical datasets:

- **SPARQL**: [ontop-SPARQL queries](https://github.com/DKFZ-E220/PTRO/blob/main/mapping_PTRO_Ontop/ontop-SPARQL%20queries.md)

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

## Relevant sources
* For background information, please refer to our [ICBO-2024 conference paper]( https://ceur-ws.org/Vol-3939/short2.pdf)
* [PTRO documentation](https://dkfz-e220.github.io/PTRO/)
* [RadPlanBio platform](https://helmholtz.software/software/radplanbio)

## License

This ontology is licensed under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to:
- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material for any purpose, even commercially

Under the following terms:
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made.

---

