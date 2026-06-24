****Metadata Guide****

This file documents every column that appears in the cleaned and enriched datasets, so that anyone reusing this data knows exactly what each field means and what values it can take.

**id** — a unique identifier for each record, assigned by Europeana. This never repeats.

**title** — the title of the painting as recorded by the providing institution.

**creator** — the artist's name exactly as it appeared in the original Europeana record, before any cleaning. This sometimes includes extra information like dates or job titles mixed in with the name.

**creator_clean** — the same artist name after I stripped out dates and job titles, so it could be matched against Wikidata more reliably.

**date** — the raw date text exactly as it came from Europeana. This field is messy and can look like a single year, a century, or a range of years.

**year_extracted** — a single four-digit year that I pulled out of the messy date text using pattern matching. If no year could be found, this is left blank.

**century** — the century the painting belongs to, worked out from year_extracted. Values range from "13th century" up to "20th century."

**country** — the country of the institution that provided the record to Europeana.

**provider** — the name of the specific museum, library, or archive that holds the painting.

**rights** — the licence or rights statement attached to the record, for example CC0, CC BY, or a Rights Statements link.

**creator_type** — a category I created to describe what kind of creator information was available. It can be "named" if a real artist name was given, "anonymous" if the record explicitly said something like Unknown or Anonymous, or "missing" if the field was completely empty.

**gender** — the artist's gender, looked up from Wikidata. This is the most important field to understand clearly, so I'm explaining it on its own below.

**birth_year** — the artist's year of birth, also pulled from Wikidata where available.

**match_status** — whether my attempt to match this artist's name to a Wikidata entry succeeded or not. It is either "matched" or "not_found."

---

What the gender column actually means
---
The gender column can only ever hold one of four values, and it's important to know exactly what each one means:

male means Wikidata returned a confirmed male gender for this artist.

female means Wikidata returned a confirmed female gender for this artist.

Anonymous means the original Europeana record never gave a real name to begin with — it said something like "Unknown" or "Anonymous," so there was never anyone to look up.

Unknown means the artist did have a real name in the record, but I could not find a matching entry for them on Wikidata, so their gender is simply not known to this project.

This matters because the 8.2% female figure I report elsewhere in this project only describes the artists who fall into the "male" or "female" categories — it does not include anyone marked as "anonymous" or "unknown."
