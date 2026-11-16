ADR: frontend-ratkaisu



Tunniste ja päivämäärä: ADR-001, 16.11.2026
Päätös: ehdotus: DOM-ruudukko, enintään 60 × 60 ruutua, päätös varmistetaan suorituskykymittauksella
Ratkaistava ongelma: Kuvion suunnittelu vaatii ruudukon, jossa on satoja ruutuja, joita käyttäjä täyttää, ja jonka pitää toimia näppäimistöllä ja ruudunlukijalla. Pitää päättää, toteutetaanko ruudukko DOM-elementteinä vai canvas-piirtona. Valinta vaikuttaa saavutettavuuteen, suorituskykyyn ja työmäärään 135 tunnin budjetissa.
Vaihtoehdot: DOM ja canvas
Valintakriteerit: saavutettavuus, suorituskyky, toteutuksen työmäärä, testattavuus ja ylläpidettävyys
Päätöksen perustelu: DOM-ruutu on painike, joten näppäimistö ja kohdistus toimivat lähes valmiiksi. Canvasilla ne pitäisi rakentaa erikseen. Canvas on nopeampi suurilla ruudukoilla, mutta 60 x 60 ruudun rajalla DOMin pitäisi riittää, tämä mitataan. DOM on työmäärältään pienempi ratkaisu. Valitsin DOMin, koska saavutettavuus ja työmäärä painavat tässä enemmän kuin suurten ruudukkojen nopeus. 
Saavutettavuus-, tietoturva-, suorituskyky- ja ylläpitovaikutukset: Saavutettavuus: ruudut ovat painikkeita, joten näppäimistö ja kohdistus toimivat lähes valmiiksi. Ruudulle annetaan nimi, ja päätoiminnot testataan käsin ruudunlukijalla. Tietoturva: ei erityistä vaikutusta, ruudukko ei käsittele käyttäjän syöttämää sisältöä, sisältö tulee omasta datasta. Suorituskyky: sadoilla ruuduilla sivu toimii hyvin, mutta tuhansilla voi hidastua. Siksi enimmäiskoko on määritelty ja suorituskyky mitataan eri kokoisilla ruudukoilla. Ylläpito: DOM on helpompi testata ja korjata kuin canvas.
Hyväksytyt kompromissit: Suurten ruudukkojen nopeus, mutta rajatun koon ruudukko riittää tähän käyttöön. Yksinkertaisuus canvasin tehokkuuden sijaan. 
Milloin päätös arvioidaan uudelleen: Jos suorituskykymittauksessa 40 x 40 tai 60 x 60 -ruudukon täyttö tai esikatselu viivästyvät selvästi, harkitaan canvasia tai pienempää maksimikokoa. Jos käyttäjätestissä selviää että käyttäjät tarvitsevat yli 60 x 60 kuvioita, arvioidaan koko uudelleen. Jos ruudunlukija- tai näppäimistötesti paljastaa ongelmia, joita DOM-ratkaisulla ei saada korjattua kohtuullisella työmäärällä. 

