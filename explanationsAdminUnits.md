# Explanations

## Original Compilation

A CSV file has been created (2022-06-27) that captures all the names used in known data sources
and eliminates some problem areas with regards to FAOSTAT and China.  The file has 9 columns - 
ISO2 code, ISO3 code, Menu Name, Official Name, FAO Name, FAOSTAT, WOAH, EUROSTAT, UNFCCC.  
The menu names have the common names for the countries that should be more user friendly then 
either the official names or the FAO names; FAO Name is the name used by FAOSTAT and you 
should use this to return information from the API/database; when retrieving WOAH information 
you can use the ISO3 code or the Official Name; the fields FAOSTAT, WOAH, EUROSTAT, UNFCCC 
shows if the country appears in these datasets.  You will see FAO in the FAOSTAT field if it 
appears and WOAH in the WOAH field, EURO in the EUROSTAT field and UNFCCC in the FAOSTAT UNFCCC 
field.  If you are using EUROSTAT data, use the Official Name field and for UNFCCC and FAO 
Tier 1 use the FAO Name.

This information will also be put into a database table soon.

A further explanation of some of the codes in this file: some countries/autonomous regions/etc. 
have appeared in some data (e.g. Ceuta, Melilla in WOAH) and it may have one of the ISO codes 
but not the other and for some reason it does not appear on ISO’s own list of countries with 
codes.  In the case were I have a ISO-3 code but no ISO-2 code I have created one with a ? as 
a prefix and then a number that has been arbitrarily assigned to create a unique code.  There 
are also 3 anomalies in EUROSTAT: they have changed the ISO-2 code for Greece to EL (not GR 
which is the true ISO-2 code) so there are 2 entries for Greece and also I have had to construct 
a fake ISO-3 code with prefix ?? and then an arbitrary number; they also have UK instead of GB 
for the United Kingdom so therefore the United Kingdom of Great Britain and Northern Ireland 
has 2 entries and one has a fake ISO-3 code; and finally they have Kosovo as a country (FAO and 
WOAH do not) with an ISO-2 code of XK and I have given it a fake ISO-3.  All the fake codes are 
there because the official ISO list does not contain codes for these administrative units.

## China Issues

It is important that we determine what we count as "China" since many data sources have 
different, sometimes hard to determine, definitions for the country that is China.

### FAOSTAT
FAOSTAT defines China as "China, mainland" + "China, Hong Kong SAR" + "China, Taiwan Province of" + "China, Macao SAR"

### WOAH
WOAH has the following units: China (CHN) and Taiwan, Province of China" (TWN) and Hong Kong 
(HKG). And in the latest data set, WOAH has data for 2005-2012 for CHN, 2005-2019 for HKG, and
2005-2019 for TWN.

## Additions

### American Samoa and Guam  
They are technically not countries but not everything in this list is a country but they are 
there either because they have appeared on FAOSTAT, WOAH, or EUROSTAT or are in some GBADs work 
like TEV.  TEV has them but only for aquaculture and as far as I can see FAOSTAT does not track 
aquaculture.  WOAH does track aquatic species but currently (2022-06-28) we have only terrestrial 
species population information.  American Samoa and Guam have been added but they are not listed 
in any of the data source categories.  

## References

https://www.iso.org/iso-3166-country-codes.html, ISO 3166 Country Codes

https://www.iso.org/obp/ui/#search, ISO 3166 Country Codes  Online Browsing Platform
