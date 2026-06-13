# Who Makes the Canon?
## Gender Representation in European Painting Collections via Europeana

**Course:** Open Scholarship in History and the Humanities (02-04-0130-ue)  
**Institution:** TU Darmstadt  
**Semester:** Summer 2026  
**Repository:** https://github.com/Open-project-2026/europeana-gender-painting

---

## Research Question

This project investigates gender disparities in the attribution and 
representation of artists in digitised European museum painting collections, 
as reflected in Europeana metadata (15th–20th century).

Note: Europeana is a digital aggregator — it reflects and digitally 
perpetuates biases embedded in the original institutional collections 
and their digitisation processes. This project analyses how those biases 
appear in aggregated metadata.

**Sub-questions:**
1. What proportion of paintings are attributed to female vs. male artists?
2. Has this proportion changed across historical centuries?
3. Are there differences between countries in representation of female artists?
4. Does "Anonymous" attribution correlate with centuries where female 
   artists were historically active but institutionally marginalised — 
   suggesting systematic erasure?
5. Are female artists systematically less documented in museum metadata?

---

## Data Source

- **Repository:** Europeana Collections (https://www.europeana.eu)
- **Access method:** Europeana REST API v2
- **API documentation:** https://apis.europeana.eu/en
- **Query:** Paintings with creator metadata
- **Licence:** Records carry CC BY, CC0, or Rights Statements licences
- **Date accessed:** June 2026
- **Records collected:** 50,000+ painting records across 20 European countries

---

## Workflow

1. **Data access** — `notebooks/01_data_collection.ipynb`  
   Query Europeana API by country to collect 50,000+ painting records

2. **Selection / sampling** — handled in notebook 01  
   Filter to records with creator field; deduplicate by record ID

3. **Cleaning / preprocessing** — `notebooks/02_data_cleaning.ipynb`  
   Classify creators as named/anonymous/missing; extract years; 
   normalise text fields

4. **Enrichment** — `notebooks/03_data_enrichment.ipynb`  
   Match artist names to Wikidata; extract gender, birth year, nationality

5. **Analysis and visualisation** — `notebooks/04_analysis_visualisation.ipynb`  
   Gender proportions by century and country; anonymous attribution 
   patterns; metadata completeness analysis

6. **Archiving and sharing** — this public GitHub repository

---

## Repository Structure

---

## FAIR Principles

- **Findable:** Public GitHub repository; data sourced from Europeana 
  with persistent URIs
- **Accessible:** All code and processed data openly available
- **Interoperable:** CSV format; Wikidata Q-IDs used for entity linking
- **Reusable:** Documented workflow; raw data preserved separately; 
  open licence

---

## Key Libraries Used

| Library | Purpose |
|---|---|
| `requests` | Sending API calls to Europeana and Wikidata |
| `pandas` | Data cleaning, transformation, and analysis |
| `matplotlib` | Creating charts and visualisations |
| `seaborn` | Statistical visualisations |
| `re` | Extracting years from messy date strings |
| `time` | Polite pausing between API requests |
