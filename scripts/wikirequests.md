# Wikidata requests

### Places of birth of dead economists

#### Request source 
https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples#Map_of_places_of_birth_of_dead_economists,_colour-coded_by_era

#### Request script

""
#defaultView:Map
SELECT DISTINCT ?person ?name ?birthplace ?dod ?coord ?layer ?dob WHERE {
{?person wdt:P106 wd:Q188094} UNION {?person wdt:P101 wd:Q8134}
?person wdt:P570 ?dod;
   wdt:P19 ?place .
?place wdt:P625 ?coord
OPTIONAL { ?person wdt:P569 ?dob }
BIND(IF( (?birthyear < 1700), "Pre-1700", IF((?birthyear < 1751), "1700-1750", IF((?birthyear < 1801), "1751-1800", IF((?birthyear < 1851), "1801-1850", IF((?birthyear < 1901), "1851-1900", IF((?birthyear < 1951), "1901-1950", "Post-1950") ) ) ) )) AS ?layer )
?person rdfs:label ?name FILTER (lang(?name) = "en")
?place rdfs:label ?birthplace FILTER (lang(?birthplace) = "en")
} ORDER BY ?dob
""
