ADR: frontend-ratkaisu

Tunniste ja päivämäärä: ADR-003, 16.11.2026 Tila: ehdotus (vahvistetaan käyttäjätestin ja prototyypin jälkeen).
Päätös: Mobiilissa tuetaan esikatselua, mallin avaamista ja tallennusta sekä perusmuokkausta napauttamalla ruutuja. Täyttä ruudukkoeditoria ei optimoida puhelimelle: suurta ruudukkoa vieritetään tai zoomataan. 
Ratkaistava ongelma: Editori on suunniteltu ensisijaisesti tietokoneelle tai tabletille. 20 sarakkeen ruudukko on yli 360 px leveä, ja pieniin ruutuihin on vaikea osua puhelimella. Pitää päättää kuinka paljon muokkausta puhelimella tuetaan, jotta työmäärä pysyy max. 135 tunnissa.
Vaihtoehdot: 
	1. täysi muokkaus puhelimelle. 
	2. esikatselu ja perusmuokkaus puhelimella, täysi editori isolla näytöllä.
	3. puhelimella vain esikatselu ja avaaminen, ei muokkausta.
Valintakriteerit: käytettävyys pienellä näytöllä, saavutettavuus, täyttö myös napautuksella eikä pelkästään vedolla, toteutuksen työmäärä, testattavuus
Päätöksen perustelu: Käyttäjä suunnittelee kuvion ensisijaisesti kotona isolla näytöllä, joten täyden mobiilieditorin tekeminen ei tuo suurta hyötyä työmäärään nähden. Pelkkä esikatselu on kuitenkin liian rajoittunut, koska pieni korjaus puhelimella voisi olla hyödyllinen olla mukana. Vaihtoehto 2:ssa on tasapaino: ruutu on vähintään 24 px, jolloin 360 px:n näkymään mahtuu noin 13 saraketta, joten isompi ruudukko vieritetään. Täyttö tehdään napautuksella.
Saavutettavuus-, tietoturva-, suorituskyky- ja ylläpitovaikutukset: Saavutettavuus: kosketuskohteet 24 px tai suuremmat ja napautus vaihtoehtona vedolle, vieritys vaatii selkeän indikaattorin. Tietoturva: ei merkittävää vaikutusta. Suorituskyky: pienempi näkyvä alue puhelimella, ei erityistä vaikutusta. Ylläpito: kaksi asettelua (mobiili ja työpöytä) tuo enemmän testattavaa, mutta pieni rajaus pitää sen hallittavana.
Hyväksytyt kompromissit: Puhelimella ei ole täyttä editoria, ja suuren ruudukon vieritys ei ole niin sujuvaa kuin työpöydällä. Vähintään 24 px ruutu tarkoittaa, ettei koko 20 sarakkeen ruudukko näy kerralla 360 px:ssä.
Milloin päätös arvioidaan uudelleen: Jos käyttäjätestissä testaajat yrittävät muokata puhelimella ja pitävät vieritystä tai pieniin ruutuihin osumista hankalana, tai jos puhelinmuokkaus nousee tärkeäksi ominaisuudeksi, laajuus arvioidaan uudelleen. Samoin jos prototyypin mobiilinäkymän toteutus vie selvästi odotettua enemmän aikaa.