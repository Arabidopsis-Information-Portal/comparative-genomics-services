# Comparative Genomics Services - High Level Design

Araport Comparative Genomics Services is planned to provide a simple API to perform comparative genomics for the *Arabidopsis Thaliana* species.

The module may utilize services of well-known data providers such as Ensemble/EnsebmlePlant and other reference databases.

##Content

**[Summary](#summary)**

**[Phylogenetic Trees API](#phylogenetic-api)**

**[Homology API](#homology-api)**

**[Feature Lookup API](#feature-lookup-api)**


##<a name="summary"></a>Summary

##<a name="phylogenetic-api"></a>Phylogenetic Trees API

* phylogeneticTreeById

Retrieves a feature phylogenetic tree that contains a feature stable identifier from Ensemble Plants Compara database.

### Parameters
#### Required

| Name          | Type                             | Description                                                                  | Default                                                                                   | Example Values |
|---------------|----------------------------------|------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|----------------|
| feature_id    | String                           | An Arabidopsis stable Feature ID. The stable identifier (gene or transcript) | -                                                                                         | AT3G52430      |
| output_format | Enumerated String (nh, phyloxml) | Output format of the response                                                | nh. By default a tree will be returned in a NH (Newick format) unless otherwise specified | nh             |

#### Optional

| Name         | Type                                                                                                                          | Description                                 | Default | Example Values |
|--------------|-------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|---------|----------------|
| nh_format    | Enumerated String (full, display_label_composite, simple, species, species_short_name, ncbi_taxon, ncbi_name, njtree, phylip) | The format of a NH (New Hampshire request). | simple  | simple              |
| feature_type | Enumerated String (gene, mRNA)                                                                                                | Filter by feature type                      | gene    | gene           |

___

* phylogeneticTreeBySymbol

Retrieves a feature phylogenetic tree that contains the gene identified by a symbol from Ensemble Plants Compara database.

### Parameters
#### Required

| Name          | Type                             | Description                                      | Default                                                                                   | Example Values |
|---------------|----------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------|----------------|
| symbol        | String                           | An Arabidopsis Symbol or display name of a gene. | -                                                                                         | ABI3           |
| output_format | Enumerated String (nh, phyloxml) | Output format of the response                    | nh. By default a tree will be returned in a NH (Newick format) unless otherwise specified | nh             |

#### Optional

| Name         | Type                                                                                                                          | Description                                 | Default | Example Values |
|--------------|-------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|---------|----------------|
| nh_format    | Enumerated String (full, display_label_composite, simple, species, species_short_name, ncbi_taxon, ncbi_name, njtree, phylip) | The format of a NH (New Hampshire request). | simple  | simple         |
| feature_type | Enumerated String (gene, mRNA)                                                                                                | Filter by feature type                      | gene    | gene           |



### Resource Information

| Methods          | search   | Description                   |
|------------------|----------|-------------------------------|
| Response Formats | nh       | Newick Serilaization Format   |
|                  | phyloxml | PhyloXML Serialization Format |
|                  | orthoxml | OrthoXML Serialization Format |
|                  | json     | JSON Format                   |


##<a name="homology-api"></a>Homology API

* homologyById

Retrieves homology information (orthologs) by an Arabidopsis stable gene identifier from Ensembl Plants Compara database. The species name is set by default as "arabidopsis_thaliana".

### Parameters
#### Required

| Name       | Type   | Description                                                                  | Default | Example Values |
|------------|--------|------------------------------------------------------------------------------|---------|----------------|
| feature_id | String | An Arabidopsis stable Feature ID. The stable identifier (gene or transcript) | -       | AT3G52430      |


#### Optional

| Name           | Type                                                         | Description                                                                                                                                                                                                                 | Default | Example Values     |
|----------------|--------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|--------------------|
| format         | Enumerated String (full, consensed)                          | The layout of the response                                                                                                                                                                                                  | full    | full               |
| feature_type   | Enumerated String (gene, mRNA)                               | Filter by feature type                                                                                                                                                                                                      | gene    | gene               |
| target_species | String                                                       | Filter by species. Supports all species aliases                                                                                                                                                                             | -       | arabidopsis lyrata |
| target_taxon   | Integer                                                      | Filter by taxon                                                                                                                                                                                                             | -       | 81972              |
| sequence       | Enumerated String(none, cdna, protein)                       | The type of sequence to bring back. Setting it to none results in no sequence being returned                                                                                                                                | protein | protein            |
| homology_type  | Enumerated String(orthologues, paralogues, projections, all) | The type of homology to return from this call. Projections are orthology calls defined between alternative assemblies and the genes shared between them. Useful if you need only one type of homology back from the service | all     | all                |

___

* homologyBySymbol

Retrieves homology information (orthologs) by an Arabidopsis symbol from Ensembl Plants Compara database. The species name is set by default as "arabidopsis_thaliana".

### Parameters
#### Required

| Name          | Type                                    | Description                                      | Default  | Example Values |
|---------------|-----------------------------------------|--------------------------------------------------|----------|----------------|
| symbol        | String                                  | An Arabidopsis Symbol or display name of a gene. | -        | ABI3           |
| output_format | Enumerated String( json, xml, orthoxml) | The output format of the response                | orthoxml | orthoxml       |

#### Optional
| Name           | Type                                                         | Description                                                                                                                                                                                                                 | Default | Example Values     |
|----------------|--------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|--------------------|
| format         | Enumerated String (full, consensed)                          | The layout of the response                                                                                                                                                                                                  | full    | full               |
| feature_type   | Enumerated String (gene, mRNA)                               | Filter by feature type                                                                                                                                                                                                      | gene    | gene               |
| target_species | String                                                       | Filter by species. Supports all species aliases                                                                                                                                                                             | -       | arabidopsis lyrata |
| target_taxon   | Integer                                                      | Filter by taxon                                                                                                                                                                                                             | -       | 81972              |
| sequence       | Enumerated String(none, cdna, protein)                       | The type of sequence to bring back. Setting it to none results in no sequence being returned                                                                                                                                | protein | protein            |
| homology_type  | Enumerated String(orthologues, paralogues, projections, all) | The type of homology to return from this call. Projections are orthology calls defined between alternative assemblies and the genes shared between them. Useful if you need only one type of homology back from the service | all     | all                |


### Resource Information

| Methods          | search   | Description                   |
|------------------|----------|-------------------------------|
| Response Formats | json     | JSON Format                   |
|                  | xml      | XML Serialization Format      |
|                  | orthoxml | OrthoXML Serialization Format |


___

* orthologsById

Retrieves orthologs by an Arabidopsis stable gene identifier from Ensembl Plants Compara database. The species name is set by default as "arabidopsis_thaliana". The homology type is set to "orthologues".

### Parameters
#### Required
| Name          | Type                                    | Description                                                                  | Default  | Example Values |
|---------------|-----------------------------------------|------------------------------------------------------------------------------|----------|----------------|
| feature_id    | String                                  | An Arabidopsis stable Feature ID. The stable identifier (gene or transcript) | -        | AT3G52430      |
| output_format | Enumerated String( json, xml, orthoxml) | The output format of the response                                            | orthoxml | orthoxml       |

#### Optional
| Name           | Type                                   | Description                                                                                  | Default | Example Values     |
|----------------|----------------------------------------|----------------------------------------------------------------------------------------------|---------|--------------------|
| format         | Enumerated String (full, consensed)    | The layout of the response                                                                   | full    | full               |
| feature_type   | Enumerated String (gene, mRNA)         | Filter by feature type                                                                       | gene    | gene               |
| target_species | String                                 | Filter by species. Supports all species aliases                                              | -       | arabidopsis lyrata |
| target_taxon   | Integer                                | Filter by taxon                                                                              | -       | 81972              |
| sequence       | Enumerated String(none, cdna, protein) | The type of sequence to bring back. Setting it to none results in no sequence being returned | protein | protein            |



* orthologsBySymbol

Retrieves orthologs by an Arabidopsis symbol from Ensembl Plants Compara database. The species name is set by default as "arabidopsis_thaliana". The homology type is set to "orthologues".

### Parameters
#### Required

| Name          | Type                                    | Description                                                                  | Default  | Example Values |
|---------------|-----------------------------------------|------------------------------------------------------------------------------|----------|----------------|
| feature_id    | String                                  | An Arabidopsis stable Feature ID. The stable identifier (gene or transcript) | -        | AT3G52430      |
| output_format | Enumerated String( json, xml, orthoxml) | The output format of the response                                            | orthoxml | orthoxml       |

#### Optional
| Name           | Type                                   | Description                                                                                  | Default | Example Values     |
|----------------|----------------------------------------|----------------------------------------------------------------------------------------------|---------|--------------------|
| format         | Enumerated String (full, consensed)    | The layout of the response                                                                   | full    | full               |
| feature_type   | Enumerated String (gene, mRNA)         | Filter by feature type                                                                       | gene    | gene               |
| target_species | String                                 | Filter by species. Supports all species aliases                                              | -       | arabidopsis lyrata |
| target_taxon   | Integer                                | Filter by taxon                                                                              | -       | 81972              |
| sequence       | Enumerated String(none, cdna, protein) | The type of sequence to bring back. Setting it to none results in no sequence being returned | protein | protein            |

### Resource Information

| Methods          | search   | Description                   |
|------------------|----------|-------------------------------|
| Response Formats | json     | JSON Format                   |
|                  | xml      | XML Serialization Format      |
|                  | orthoxml | OrthoXML Serialization Format |


___

* paralogsById
Retrieves paralogs by an Arabidopsis stable gene identifier from Ensembl Plants Compara database. The species name is set by default as "arabidopsis_thaliana". The homology type is set to "paralogues".


### Parameters
#### Required
| Name          | Type                                    | Description                                                                  | Default  | Example Values |
|---------------|-----------------------------------------|------------------------------------------------------------------------------|----------|----------------|
| feature_id    | String                                  | An Arabidopsis stable Feature ID. The stable identifier (gene or transcript) | -        | AT3G52430      |
| output_format | Enumerated String( json, xml, orthoxml) | The output format of the response                                            | orthoxml | orthoxml       |


#### Optional
| Name           | Type                                   | Description                                                                                  | Default | Example Values     |
|----------------|----------------------------------------|----------------------------------------------------------------------------------------------|---------|--------------------|
| format         | Enumerated String (full, consensed)    | The layout of the response                                                                   | full    | full               |
| feature_type   | Enumerated String (gene, mRNA)         | Filter by feature type                                                                       | gene    | gene               |
| target_species | String                                 | Filter by species. Supports all species aliases                                              | -       | arabidopsis lyrata |
| target_taxon   | Integer                                | Filter by taxon                                                                              | -       | 81972              |
| sequence       | Enumerated String(none, cdna, protein) | The type of sequence to bring back. Setting it to none results in no sequence being returned | protein | protein            |
___

* paralogsBySymbol

Retrieves paralogs by an Arabidopsis stable gene identifier from Ensembl Plants Compara database. The species name is set by default as "arabidopsis_thaliana". The homology type is set to "paralogues".

### Parameters
#### Required
| Name          | Type                                    | Description                                                                  | Default  | Example Values |
|---------------|-----------------------------------------|------------------------------------------------------------------------------|----------|----------------|
| feature_id    | String                                  | An Arabidopsis stable Feature ID. The stable identifier (gene or transcript) | -        | AT3G52430      |
| output_format | Enumerated String( json, xml, orthoxml) | The output format of the response                                            | orthoxml | orthoxml       |


#### Optional
| Name           | Type                                   | Description                                                                                  | Default | Example Values     |
|----------------|----------------------------------------|----------------------------------------------------------------------------------------------|---------|--------------------|
| format         | Enumerated String (full, consensed)    | The layout of the response                                                                   | full    | full               |
| feature_type   | Enumerated String (gene, mRNA)         | Filter by feature type                                                                       | gene    | gene               |
| target_species | String                                 | Filter by species. Supports all species aliases                                              | -       | arabidopsis lyrata |
| target_taxon   | Integer                                | Filter by taxon                                                                              | -       | 81972              |
| sequence       | Enumerated String(none, cdna, protein) | The type of sequence to bring back. Setting it to none results in no sequence being returned | protein | protein            |

### Resource Information

| Methods          | search   | Description                   |
|------------------|----------|-------------------------------|
| Response Formats | json     | JSON Format                   |
|                  | xml      | XML Serialization Format      |
|                  | orthoxml | OrthoXML Serialization Format |


##<a name="feature-lookup-api"></a>Feature Lookup API

* lookupById

Find the species and database for a single stable identifier e.g. gene, transcript. The species name is set by default as "arabidopsis_thaliana". 


### Parameters
#### Required

| Name          | Type                          | Description                                                                  | Default | Example Values |
|---------------|-------------------------------|------------------------------------------------------------------------------|---------|----------------|
| feature_id    | String                        | An Arabidopsis stable Feature ID. The stable identifier (gene or transcript) | -       | AT3G52430      |
| output_format | Enumerated String( json, xml) | The output format of the response                                            | xml     | xml            |

#### Optional
| Name   | Type                                | Description                | Default | Example Values |
|--------|-------------------------------------|----------------------------|---------|----------------|
| format | Enumerated String (full, consensed) | The layout of the response | full    | full           |
___

* lookupBySymbol

Find the species and database for a gene symbol. The species name is set by default as "arabidopsis_thaliana".

### Parameters
#### Required

| Name          | Type                          | Description                                      | Default | Example Values |
|---------------|-------------------------------|--------------------------------------------------|---------|----------------|
| symbol        | String                        | An Arabidopsis Symbol or display name of a gene. | -       | ABI3           |
| output_format | Enumerated String( json, xml) | The output format of the response                | xml     | xml            |

#### Optional
| Name   | Type                                | Description                | Default | Example Values |
|--------|-------------------------------------|----------------------------|---------|----------------|
| format | Enumerated String (full, consensed) | The layout of the response | full    | full           |

### Resource Information

| Methods          | search | Description              |
|------------------|--------|--------------------------|
| Response Formats | json   | JSON Format              |
|                  | xml    | XML Serialization Format |

