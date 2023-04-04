---
slug: "ebi-ac-uk"
title: "CROssBAR Data API"
provider: "ebi.ac.uk"
description: "# About CROssBAR & data\n**CROssBAR**: Comprehensive Resource of Biomedical\
  \ Relations with Deep Learning Applications and Knowledge Graph Representations\n\
  CROssBAR is a comprehensive system that integrates large-scale biomedical data from\
  \ various resources e.g UniProt, ChEMBL, Drugbank, EFO, HPO, InterPro & PubChem\
  \ and stores them in a new NoSQL database, enrich these data with deep learning\
  \ based prediction of relations between numerous biomedical entities, rigorously\
  \ analyse the enriched data to obtain biologically meaningful modules and display\
  \ them to the user via easy to interpret, interactive and heterogeneous knowledge\
  \ graphs.\nCROssBAR platform exposes a set of 12 endpoints to query data stored\
  \ in the CROssBAR database. These endpoints help the user to find data of interest\
  \ using different parameters provided by the API endpoint.\nFor example,\nhttps://www.ebi.ac.uk/tools/crossbar/proteins?accession=A0A023GRW5\
  \ -> will provide protein information about accession 'A0A023GRW5' including its\
  \ interactions, functions, cross-references, variations and more.\nhttps://www.ebi.ac.uk/tools/crossbar/activities?moleculeChemblId=CHEMBL465983\
  \ -> will provide ChEMBL bio-interactions related information including targets\
  \ and bio-activity measurements associated with molecule chembl id 'CHEMBL465983'\n\
  \n**Knowledge graphs**\nAnother use case of CROssBAR's API endpoints is in building\
  \ knowledge graphs. These endpoints can be *weaved* together (output from one API\
  \ endpoint fed as input to another API endpoint) programmatically to link nodes\
  \ like protein, disease, drugs etc. as nodes of the graph. The endpoints are designed\
  \ to be independent from each other which allows users the flexibility to drive\
  \ biological networks from any facet e.g drug-centric, disease-centric, gene-centric\
  \ etc. Our service for knowledge graph construction is available at https://crossbar.kansil.org.\n\
  An example for the part of the background queries on the CROssBAR API during the\
  \ construction of a knowledge graph, \n(with the aim of keeping the example simple,\
  \ we have only included the processes related to pathways, genes/proteins and drugs/compounds)\n\
  In this example, we would like to find bio-active compounds (with a pChEMBL value\
  \ threshold of at least 6.0) & drugs targeting all proteins belonging to \"WNT ligand\
  \ biogenesis and trafficking\" pathway (based on Reactome pathway annotations).\n\
  This can be achieved by using endpoints listed on this swagger documentation as\
  \ illustrated in following steps-\nFind bio-active compounds (with a pChEMBL value\
  \ threshold of at least 6.0) & drugs targeting all proteins belonging to \"WNT ligand\
  \ biogenesis and trafficking\" pathway (based on Reactome annotations)\nThis can\
  \ be achieved by using endpoints listed on [this swagger documentation](https://www.ebi.ac.uk/tools/crossbar/swagger-ui.html)\
  \ as illustrated in following steps-\n1. Get all proteins from “/proteins” API endpoint\
  \ which have a reactome pathway name equal to \"WNT ligand biogenesis and trafficking\"\
  .\n2. From the collection of uniprot protein accessions collected from step 1 above,\
  \ we query “/targets” API endpoint to obtain the ‘target_chembl_id’s of these proteins.\n\
  3. From the collection of target_chembl_ids collected from step 2 above, we query\
  \ “/activities” API endpoint with pChEMBL value >=6, to obtain the ’molecule_chembl_id’\
  s of the molecules that we need. \n4. From the collection of uniprot protein accessions\
  \ collected from step 1 above, we find out Drug names and ids from the “/drugs”\
  \ API endpoint that targets our proteins.\n5. From the collection of ’molecule_chembl_id’\
  s obtained in step3, we query “/molecules” endpoint to get the compounds that are\
  \ interacting with the genes/proteins belonging to the “WNT ligand biogenesis and\
  \ trafficking” pathway."
logo: "ebi.ac.uk-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "open_data"
stubs: "ebi.ac.uk-stubs.json"
swagger: "ebi.ac.uk-swagger.json"
---
