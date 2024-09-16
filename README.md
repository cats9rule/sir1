# Kratak opis rezultata

Repozitorijum sadrži 3 direktorijuma: data, jupyter notebooks i rezultati.
Data sadrži skup podataka korišćen u eksperimentima.
Jupyter notebooks sadrži Jupyter sveske u kojima se nalaze kod za pripremu i preprocesiranje podataka, kao i za treniranje modela.

### IPYNB datoteke:
  - data_load_from_csv - kod za učitavanje vrednosti piksela iz CSV datoteke i formiranje PNG datoteka na osnovu piskela, kao i svrstavanje svake slike u poseban direktorijum sa nazivom njene kategorije
  - data-augmentation - sadrži kod za augmentaciju slika iz "disgusted" kategorije, pošto je njihov nedostatak negativno uticao na rezultate
  - data-preproseccing - sadrži kod za upscaling slika, pošto su originalne slike u rezoluciji 48x48, i napravljen je nov skup koji sadrži slike u rezoluciji 192x192.
  - masinsko_ucenje - sadrži kod za testiranje 10 modela mašinskog učenja nad varijacijama skupa podataka (originalni, upscale-ovan, i njihove varijacije u vidu skupova sa jednakim brojem uzoraka u svakoj kategoriji).
  - cnn-detector - sadrži kod za testiranje tri varijante konvolucione neuronske mreže. Sa ovim pristupom nije bilo smisla nastavljati dalje budući da su ove mreže davale ubedljivo najgore rezultate na svakoj varijaciji skupa podataka.
  - fer-efnet-b7 - testiranje EfficientNet B7 modela sa finim podešavanjem na izabranom skupu podataka
  - densenet-classificator - testiranje DenseNet169 modela sa finim podešavanjem na izabranom skupu podataka
  - fer-resnet152 - testiranje ResNet152 modela na upscaled slikama sa augmentovacijom slika radi proširenja kategorije "disgusted"
  - fer-resnet152-with-augmentation - testiranje već fino podešenog modela resnet152 nad skupom podataka, sa ponovnim finim podešavanjem sa uključenom augmentacijom radi proširenja "disgusted" kategorije
  
  
### REZULTATI:
  - evaluation sadrži rezultate testiranja modela mašinskog učenja u vidu classification report-a koji sadrže različite metrike za evaluaciju klasifikacije. Svaki report ima prefiks koji označava skup podataka nad kojim je model treniran, nakon kog sledi samo ime modela.
  - graphs sadrži matrice zabune za modele mašinskog učenja, kao i rezultate treniranja ResNet modela (direktorijumi resnet152 i resnet152-augmented-data)
  
  
Od algoritama mašinskog učenja, najbolje se pokazao CatBoost algoritam nad originalnim skupom podataka (tačnost 51%). Od svih testiranih modela, najbolje se pokazao ResNet model (tačnost 62%). Jednostavni CNN modeli mogu se zanemariti pošto sve uzorke svrstavaju u klasu "happy".
