# pliny_wall_of_fame_DHBeneluxJournal2026
This repository contains the data and the code to replicate the results described in the paper "Pliny’s “Wall of Fame”: A Digital Semantic Approach to Citations and Sources in Books 2-6 of the _Naturalis Historia_", published in DH Benelux Journal 2026.

## Repository structure:

### Data
The data folder contains the dataset used in the paper, in 5 different formats. 
All the formats contain book 2-6 of the _Naturalis Historia_, extracted from https://github.com/lascivaroma/latin-lemmatized-texts/tree/0.1.2 and further annotated. 
The corpus is annotated with linguistic information and Named Entity Recognition (NER) for persons. Individuals are linked to Wikidata and to the _Realencyclopädie der classischen Altertumswissenschaft_ (RE). 
See the full paper for a detailed descritpion of the annotation.

The following columns are part of each format:
- wordref_id: unique identifier for each token, to be combined with extra column	
- extra: extra number or letter, to be attached with the wordref_id to unambiguously identify each token
- sent_id: unique sentence id
- book: book (from 2 to 6)	
- section: section of the book	
- capitalized: 0/1 value to distinguish between capitalized and not capitalized tokens
- token
- lemma
- lemma_index: lemma index to distinguish between homographic lemmas (see LASLA documentation)	
- pos: Part of Speech tag, according to LASLA annotation schema	
- morphology: morphological analysis, according to LASLA tag schema	
- gold_ner: gold NER annotation in BIO format	
- wikidata: Wikidata link	
- TM_Real: RE identifier	
- Artikel: RE article	
- wikidata_qid	
- Wikidata_label	
- is_author_index: Boolean value for distinguishing sources in the text. The value has been semi-automatically corrected, as described in the paper	
- merged_entity_id: number assigned to each mention. A multi-token mention is assigned the same number. 
- in_index: Boolean value that states if an author is mentioned in Pliny's index for that book (see the paper for details)

The files are structured as it follows:

- 'nh_original.csv': this file contains the corpus with the information described above
- 'nh_original_dates': this file contains the 'begin_date_final' and 'end_date_final' values, extracted from Evelien de Graaf's dataset