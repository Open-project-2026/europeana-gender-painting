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
**AI Use Declaration**

This project used Claude, made by Anthropic, as a coding assistant throughout the workflow. It helped generate the initial structure of all four notebooks, debug API connection errors, and draft documentation text. All code was reviewed, run, and verified by the author before being included. The AI did not choose the research question, interpret the findings, or make analytical decisions on its own.

**Here are three example prompts I actually used:**

I asked it to write a Python script that collects painting records from the Europeana API, querying country by country so I could get around the 1,000-record limit per query.
When the Wikidata search API kept giving me 403 errors, I asked it to find a different way to look up an artist's gender, which is how I ended up using the SPARQL endpoint instead.
I asked it to explain in plain terms what each library I used — pandas, requests, matplotlib, and seaborn — actually does in my project, so I could describe this properly in my technical report.

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
** Early results show that female artists are credited on only 8.2 percent of identified paintings, with the lowest share in the 17th century at 1.4 percent, despite documented female painters such as Artemisia Gentileschi being active in that period. This points toward historical under-attribution rather than an actual absence of female artists.
 ---**
 
## Repository Structure

Here is how I've organised everything in this repository:
At the top level there is this README file and a requirements.txt file listing the Python libraries needed to run the code.
Inside the data folder there are two subfolders. The raw subfolder holds the original data exactly as it came from the Europeana API — the main raw CSV file and a summary file showing how many records came from each country. The processed subfolder holds the cleaned CSV, the final enriched CSV with gender added, and a log file showing the results of the Wikidata gender lookups.
Inside the notebooks folder are the four numbered notebooks in the order they should be run: data collection, then cleaning, then enrichment, then analysis and visualisation.
Inside the outputs folder are the five chart images produced by the analysis notebook.
Inside the docs folder is the original data appendix file plus a new metadata guide that documents every column in the dataset in detail.

---

**Ethical Considerations**

I want to be upfront about a few things in how this project handles its subject matter.
First, on gender: Wikidata's gender field only ever returns "male" or "female" for almost every record I matched. I am not claiming that historical artists' identities were actually that simple — this is a limitation of the data source I used, not a claim I am making about gender itself.
Second, on privacy: everything I collected is metadata about historical artworks and artists who are no longer alive, published by museums and archives under open licences. I did not collect any personal data about living people.
Third, on the "Anonymous" category: many paintings are unattributed for historical reasons that may include the deliberate erasure of women artists' names from the record. Rather than throwing these records away as missing data, I deliberately kept them as their own category so I could study the pattern of anonymity itself.

---

**Limitations**

A few honest limitations of this project that I think are worth stating clearly:
I was only able to match 2,419 of my 7,389 uniquely named artists to a Wikidata entry with a known gender — that's about 32.7%. This means my headline finding of 8.2% female representation only applies to the artists I could actually match, and the real picture across all 27,454 records may look different.
Thirteen records had no usable year at all in their date field, so they could not be placed into a century for the century-based analysis.
My "anonymous" category lumps together several different original labels — things like "Unknown," "Workshop of," "Circle of," and "Follower of" — which probably carry different historical meanings but I treated them as one group to keep the analysis manageable.
Matching names through SPARQL can occasionally confuse one historical figure with another person who happens to share the same name, so there is a small amount of error in the gender data that I have not been able to measure precisely.

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

---

**Dataset Summary Statistics**

Total records collected: 27,454

Named artists: 26,360 (96.0%)

Anonymous: 1,094 (4.0%)

Records with a year successfully extracted: 27,441 (99.95%)

Records with known gender: 8,690 — of which female is 713 (8.2%) and male is 7,977 (91.8%)

Unique artists matched on Wikidata: 2,419 out of 7,389 (32.7%)

---
