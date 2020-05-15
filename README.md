# ORCID for Wikidata

This repository contains scripts to import authors with information about affiliation and education from ORCID database into Wikidata. Afterwards the author items can be connected to their scienctific articles in Wikidata.

## Background

This work is part of the project (Nachnutzung_von_strukturierten_Daten_aus_Wikidata_für_bibliometrische_Analysen)[https://de.wikiversity.org/wiki/Wikiversity:Wikiversity:Fellow-Programm_Freies_Wissen/Einreichungen/Nachnutzung_von_strukturierten_Daten_aus_Wikidata_f%C3%BCr_bibliometrische_Analysen].

## Requirements

The repository contains a Python script to prepare JSON files for editing Wikidata via [wikidata-cli](https://www.npmjs.com/package/wikidata-cli).

## Usage
1. **Download ORCID archives** at figshare,  eg. for 2019: https://orcid.figshare.com/articles/ORCID_Public_Data_File_2019/9988322/2 
2. **Harvest summaries** by using  	2020-04-01_ORCID_summaries.py  for **ORCID, given name, family name** and **current affiliation** with  arg-statements for path of extracted ORCID-summaries.xml and output-csv  

   e.g. python3  2020-04-01_ORCID_summaries.py /home/folder/orcid_summaries.xml orcid-researchers.csv

3. **Harvest affiliations** by using 2020-03-30_ORCID_affiliations.py for **ORCID, affiliation name, affiliation adress, affiliation id for disambiguation** with args-statements for path of extracted ORCID-activities.xml and output-csv

   e.g. python3  2020-03-30_ORCID_affiliations.py /home/folder/orcid_activities_1.xml orcid-affiliations_1.csv

4. **Harvest publications** by using 2020-05-05_ORCID-works-harvesting.py for **ORCID of author, title and subtitle of publication, ids of publication** with args-statements for path of extracted ORCID-activities.xml and output-csv

   e.g. python3  2020-05-05_ORCID_works-harvesting.py /home/folder/orcid_activities_1.xml orcid-publications_1.csv

5. **Perform duplication check** for items of researchers and **create basic items in Wikidata** using: 2020-04-17_wikidata-CLI.py 
the script uses Wikibase CLI internally. Download and informatin on Wikibase CLI can you find here: https://github.com/maxlath/wikibase-cli

   Besides "wd" as standard input for Wikibase CLI is needed, the scripts expects args-input for input-file (should be that one you created in step 2) and logging-file for note those items for researchers that had been created
   e.g. python3 2020-04-17_wikidata-CLI.py  orcid-researchers.csv logging.txt
   
 
  * to be continued: 
   * upload script for **matching publications recoreded in Wikidata and ORCID of authors in order to establish connection between publications and authors.**
   * upload script for **enrich basic items of researchers in Wikidata with further information about affiliation, education, and other** 
   * add script for **harvesting education-files** and other from ORCID

## License

All source code licensed under GPL
