# Comparative Genomics Services - High Level Design

Araport Comparative Genomics Services is planned to provide a simple API to perform comparative genomics for the *Arabidopsis Thaliana* species.

The module may utilize services of well-known data providers such as Ensemble/EnsebmlePlant and other reference databases.

##Content

**[Summary](#summary)**

**[Phylogenetic Trees API](#phylogenetic-api)**

**[Orthologs API](#orthologs-api)**

**[Homology API](#homology-api)**

**[Feature Lookup API](#feature-lookup-api)**

**[Resource Information](#resource-information)**

##<a name="summary"></a>Summary

##<a name="phylogenetic-api"></a>Phylogenetic Trees API

* phylogeneticTreeById

Retrieves a feature phylogenetic tree that contains a feature stable identifier from Ensemble Plants Compara database.

### Parameters
#### Required
| Name       | Type                             | Description                                                                  | Default                                                                                   | Example Values |
|------------|----------------------------------|------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|----------------|
| feature_id | String                           | An Arabidopsis stable Feature ID. The stable identifier (gene or transcript) | -                                                                                         | AT3G52430      |
| format     | Enumerated String (hh, phyloxml) | Output format of a tree.                                                     | nh. By default a tree will be returned in a NH (Newick format) unless otherwise specified | nh             |

#### Optional

| Name         | Type                                                                                                                          | Description                                 | Default | Example Values |
|--------------|-------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|---------|----------------|
| nh_format    | Enumerated String (full, display_label_composite, simple, species, species_short_name, ncbi_taxon, ncbi_name, njtree, phylip) | The format of a NH (New Hampshire request). | simple  | simple              |
| feature_type | Enumerated String (gene, mRNA)                                                                                                | Filter by feature type                      | gene    | gene           |

##<a name="orthologs-api"></a>Orthologs API

##<a name="homology-api"></a>Homology API

##<a name="feature-lookup-api"></a>Feature Lookup API

##<a name="resource-information"></a>Resource Information

| Methods          | search   | Description                   |
|------------------|----------|-------------------------------|
| Response Formats | nh       | Newick Serilaization Format   |
|                  | phyloxml | PhyloXML Serialization Format |
|                  | orthoxml | OrthoXML Serialization Format |
|                  | json     | JSON Format                   |