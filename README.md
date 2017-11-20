# BRK-Ontology
A web ontology for BRK


## Remarks
1. Appartementsrecht can not logically be of type Onroerendezaak, because an Onroerendezaak is a tangible thing
2. Associations between Onroerendzaak and Onroerendezaakaffiliatie differ between Modeldocumentatie BRK Levering and CDMKAD
3. The definition of ‘sectie’ does not make sense: “De sectie die de sectie binnen de kadastrale gemeente uniek identificeert”
4. This definition is of geometry of Leidingnetwerk is hard/impossible to understand: “De begrenzing van een leidingnetwerk kan zowel lijnvormig als vlakvormig worden beschreven. Lijnvormig houdt in dat het leidingnetwerk bestaat uit een netwerk van lijnketens, die onderling minimaal een punt in de keten gemeenschappelijk hebben. Vlakvormig houdt in dat de lijnketens onderling zodanig met elkaar zijn verbonden dat een vlakvormige figuur (polylijn) is af te leiden. In het lijnvormige geval kan ook de strookbreedte, waarbinnen de grenslijn ligt, zijn opgenomen. In zo'n geval is, indien nodig, een vlakvormige figuur te berekenen.”
5. It would be preferable to model codelists like AardKadasterverzoek or SoortGrootte as SKOS concepts. 
6. The compositition relationships between TerInschrijvingAangebodenStuk and Ondertekenaar look funny. Is it true that data about the Ondertekenaar are always part of the document? And could the Ondertekenaar be the author? Besides that, heeftAlsEquivalentieVerklaarder lacks an explanation.
7. An Aantekening can have geometry. Therefore it is a spatial object, but that contradicts its definition. This is resolved by introducing brk:Aantekeninggebied (brk:Aantekening can be related to brk:Aantekeninggebied by means of dct:spatial).
8. IMKAD and CDMKAD model some things differently. CDMKAD is taken to be authoritative. Is that correct? After all, CDMKAD seems to be only a model for a single application.
9. Not sure if the model makes sense with respect to Tenaamstelling related to persons and samenwerkingsverband. It is partly unclear because definitions are missing.




