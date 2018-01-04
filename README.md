# BRK-Ontology
A web ontology for BRK


## Remarks
- `Appartementsrecht` can not logically be of type `Onroerendezaak`, because an `Onroerendezaak` is a tangible thing.
- Associations between `Onroerendzaak` and `Onroerendezaakaffiliatie` differ between Modeldocumentatie BRK Levering and CDMKAD.
- This definition is of geometry of Leidingnetwerk is hard/impossible to understand: “De begrenzing van een leidingnetwerk kan zowel lijnvormig als vlakvormig worden beschreven. Lijnvormig houdt in dat het leidingnetwerk bestaat uit een netwerk van lijnketens, die onderling minimaal een punt in de keten gemeenschappelijk hebben. Vlakvormig houdt in dat de lijnketens onderling zodanig met elkaar zijn verbonden dat een vlakvormige figuur (polylijn) is af te leiden. In het lijnvormige geval kan ook de strookbreedte, waarbinnen de grenslijn ligt, zijn opgenomen. In zo'n geval is, indien nodig, een vlakvormige figuur te berekenen.”
- It would be preferable to model codelists like AardKadasterverzoek or SoortGrootte as SKOS concepts. 
- The compositition relationships between TerInschrijvingAangebodenStuk and Ondertekenaar look funny. Is it true that data about the Ondertekenaar are always part of the document? And could the Ondertekenaar be the author? Besides that, heeftAlsEquivalentieVerklaarder lacks an explanation.
- An Aantekening can have geometry. Therefore it is a spatial object, but that contradicts its definition. This is resolved by introducing brk:Aantekeninggebied (brk:Aantekening can be related to brk:Aantekeninggebied by means of dct:spatial).
- IMKAD and CDMKAD model some things differently, for example:
    * TeboekgesteldeZaak and subclasses exist in IMKAD, not in CDMKAD;
    * property Leidingnetwerk.breedteNetwerkstrook exists in IMKAD, not in CDMKAD;
    * Erfpachtcanon occurs in CDMKAD, not in IMKAD.  
   CDMKAD is taken to be authoritative. That seems strange, because CDMKAD seems to be only a model for a single application. The reason the model should be based on CDMKAD is that CDMKAD is de model for BDS (BRK Data Services), which is the system the Kadaster uses internally for BRK data. And it will be the system that will serve as a data source for the Linked Data version of the BRK.
- Not sure if the model makes sense with respect to Tenaamstelling related to persons and samenwerkingsverband. It is partly unclear because definitions are missing.
- Some relationships, like isVermeldIn, exist between many class pairs. Could there be a benefit to defining a common ObjectProperty that has subproperties for each class pair (domain class and range class)? It has not been done (yet). To these similar properties the name of the domain (subject) is prefixed, i.e. persoonVermeldIn has domain brk:Persoon. Using the range may be more natural, but that could lead to duplicate property names because a class can be the range of multiple relationships like isVermeldIn. Schema:mentions is used to group isVermeldIn properties and schema:isBasedOn is used to group isGebaseerdOp properties.
- Regarding location and address: It does not seem necessary to define properties for addresses because address data should be covered by the LOCN vocabulary. Address instances (linked by the locn:address property) can be of type brk:BinnenlandsAdres or brk:BuitenlandsAdres, and of type brk:Woonadres or brk:Postadres.
- Note the distinction between 'het eigendom' (een bezitting) and 'de eigendom' (een recht).
- How model historical information (change history and audit trail) needs to be aligned with solutions applied in other base registries in the data platform (BAG BRT, IMRO, ...).
- Addresses can be related to BAG resources, NatuurlijkPersoon can be related to the BRP. Those relationships are not in the model, because they do not seem to require special semantics in the BRK domain.
- There is an inconsistency within the CDMKAD model: OnroerendeZaak.aardCultuurBebouwd and OnroerendeZaak.aardCultuurOnbebouwd have a cardinality of 0..1 in the diagram, but in the description it says multiple values are allowed.
- Are aardCultuurBebouwd and aardCultuurOnbebouwd correctly defined as properties of OnroerendeZaak? It seems better to make them properties of Perceel. Whether or not an OnroerendeZaak is built up seems to make no sense for Appartementsrecht or Leidingnetwerk.
- Similar to the point above: Can Appartementsrecht or Leidingnetwerk have an 'erf'? If not, properties omschrijvingOnderzoekErfdienstbaarheden and toestandsdatumOnderzoekErfdienstbaarheden have a wrong domain.
- Properties `omschrijvingOnderzoekErfdienstbaarheden`, `toestandsdatumOnderzoekErfdienstbaarheden` and `erfdienstbaarheid` have to do with Erfdienstbaarheid, but Erfdienstbaarheid is not a separate entity in CDMKAD. Would it make sense to make a class Erfdienstbaarheid? A new class `OnderzoekErfdienstbaarheden` was created as a result of normalization. 
- A definition of `omschrijvingOnderzoekErfdienstbaarheden` could not be found.
