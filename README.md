# pliny_wall_of_fame_DHBeneluxJournal2026
This repository contains the data and the code to replicate the results described in the paper "Pliny’s “Wall of Fame”: A Digital Semantic Approach to Citations and Sources in Books 2-6 of the _Naturalis Historia_", published in DH Benelux Journal 2026 by Valeria Irene Boano (KU Leuven) (https://orcid.org/0009-0003-2791-1365).

## Repository structure:

### Data
The data folder contains the dataset used in the paper, in 5 different formats. 
All the formats contain book 2-6 of the _Naturalis Historia_, extracted from https://github.com/lascivaroma/latin-lemmatized-texts/tree/0.1.2 and further annotated. 
The corpus is annotated with linguistic information and Named Entity Recognition (NER) for persons. Individuals are linked to Wikidata and to the _Realencyclopädie der classischen Altertumswissenschaft_ (RE). 
See the full paper for a detailed descritpion of the annotation.
-----------------------------------------------------------------------------------------------------------------------------------------
#### Data columns
The columns in the data contains the following information:
- **wordref_id**: unique identifier for each token, to be combined with extra column	
- **extra**: extra number or letter, to be attached with the wordref_id to unambiguously identify each token
- **sent_id**: unique sentence id
- **book**: book (from 2 to 6)	
- **section**: section of the book	
- **capitalized**: 0/1 value to distinguish between capitalized and not capitalized tokens
- **token**
- **lemma**
- **lemma_index**: lemma index to distinguish between homographic lemmas (see LASLA documentation)	
- **pos**: Part of Speech tag, according to LASLA annotation schema	
- **morphology**: morphological analysis, according to LASLA tag schema	
- **gold_ner**: gold NER annotation in BIO format	
- **wikidata**: Wikidata link	
- **TM_Real**: RE identifier	
- **Artikel**: RE article	
- **wikidata_qid**	
- **Wikidata_label**	
- **is_author_index**: Boolean value for distinguishing sources in the text. The value has been semi-automatically corrected, as described in the paper	
- **merged_entity_id**: number assigned to each mention. A multi-token mention is assigned the same number. 
- **in_index**: Boolean value that states if an author is mentioned in Pliny's index for that book (see the paper for details)
- **instance_of_id**	
- **instance_of_label**	
- **is_human**: Boolean value to distinguish between humans and deities/mythological entities
- **citizenship_id**	
- **citizenship_label**	
- **language_id**	
- **language_label**	
- **occupation_id**	
- **occupation_label**	
- **sex_or_gender_id**	
- **sex_or_gender_label**	
- **is_author_wikidata**: authorial status on the basis of Wikidata values (includes false negatives)	
- **citizenship_group**: Roma, Graecia, Africa, Asia or Germania (defined with Wikidata values)
- **language_group**: Latin, Greek, Other (defined with Wikidata values)	
- **is_politician**: Boolean value to distinguish between authors with and without a political status, on the basis of Wikidata occupation values
- **occupation_category**: geohistorian (= Geographer or historian), philoscientist (= Philosopher or scientist), poet, polymath, politician (defined with Wikidata values)	
- **period_final**: archaic, classic, hellenistic, augustean (=Augustan), early_empire

----------------------------------------------------------------------------------------------------------------------------
#### Files
The folder contains the following files:

- '**nh_original.csv**': this file contains the corpus with the information described above
- '**nh_original_dates.csv**': this file contains the 'begin_date_final' and 'end_date_final' values, extracted from Evelien de Graaf's dataset
- '**nh_extended_withdates.csv**': this file was generated on date 13/10/2026 with the code stored in the notebook 'wikidata_properties_extraction_pwof_DHBen2026.ipynb'. It contains the ids and labels for the Wikidata properties described in the code (P31, P27, P1412, P106, P21)
- '**nh_categorized.csv**': in this file the entities are grouped in citizenship groups, language groups, occupation groups and chronological groups as described in the paper. The file is generated with the notebook 'wikidata_categorization_pwof_DHBen26.ipynb'.
- '**nh_annotated.csv**': this file contains the data that was used to produce the graphs and calculations described in the paper. The Wikidata values were extracted in date 27/01/2026.
--------------------------------------------------------------------------------------------------------------------
### Code

- '**wikidata_properties_extraction_pwof_DHBen2026.ipynb**': this Jupyter Notebook can be use to extract the Wikidata properties with the wikidata Python library. Properties are attached to the dataset. Input file: 'nh_original_dates.csv'; Output file: 'nh_extended_withdates.csv'
- '**wikidata_categorization_pwof_DHBen26.ipynb**: this code categorizes the individuals contained in the corpus on the basis of the extracted Wikidata values. Input file: 'nh_extended_withdates.csv'; Output file: 'nh_categorized.csv'
- '**results_pwof_DHBen26.ipynb**': this code produces the results presented in the paper. Input file:  'nh_categorized.csv' or 'nh_annotated.csv' (only the latter will output exactly the same results as described in the paper, since it contains the Wikidata values extracted in January)