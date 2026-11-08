---
type: note
title: Consumer products can contain valuable shipped algorithms that could shorten a competitor's development
tags: [customer, market, security, idea]
date: 2026-11-08
by: luka+codex
confidence: moderate
sources: [https://www.oralb.co.uk/en-gb/oral-health/why-oral-b/electric-toothbrushes/which-oral-b-io-is-right-for-me, https://www.starkey.com/hearing-aids/edge-artificial-intelligence-hearing-aids, https://support.dji.com/help/content?customId=en-us03400006832&documentType=artical&lang=en&paperDocType=paper&re=GB&spaceId=34, https://www.bosch-sensortec.com/en/software-tools/software, https://www.garmin.com/en-US/blog/fitness/how-garmin-watches-track-your-sleep-calculate-sleep-score/, https://www.dyson.co.uk/hair-care/hair-dryers/supersonic-nural]
---

## Tvrdnja i granice dokaza

Deo vrednosti fizičkog proizvoda može biti u algoritmu koji se isporučuje kupcu, u firmwareu, aplikaciji ili lokalnoj biblioteci. Rekonstrukcija takvog algoritma mogla bi konkurentu skratiti razvoj. **To je poslovna hipoteza, a ne dokaz masovnog kopiranja, postojećeg bola ili spremnosti proizvođača da plati zaštitu.**

Ovo je šira mapa kandidata, ne iscrpan spisak svih proizvoda. Funkcije zavise od konkretnog modela; neke mogu biti u aplikaciji ili cloudu, a ne u uređaju. Za svakog kandidata treba proveriti gde se vredna logika zaista izvršava i da li je dostupna za analizu.

## Mapa proizvoda i potencijalno vredne logike

Redovi su **hipoteze za istraživanje kategorija**. Konkretni izvori ispod potvrđuju samo navedene funkcije pojedinih proizvođača, ne sve redove niti komercijalnu potražnju za našim proizvodom.

| Proizvod | Šta bi konkurentu bilo vredno da rekonstruiše |
|---|---|
| Adaptivne četkice za zube | Prepoznavanje pokreta, položaja i kvaliteta četkanja |
| Slušni aparati | Izdvajanje govora, uklanjanje buke, prilagođavanje zvuka |
| Slušalice | Aktivno poništavanje buke, prostorni zvuk, personalizacija |
| Gitarske pedale i digitalna pojačala | Modelovanje pojačala, distorzije i drugih efekata |
| Zvučnici i soundbar uređaji | Korekcija prostorije, obrada basa, usmeravanje zvuka |
| Fotoaparati i akcione kamere | Autofokus, stabilizacija, uklanjanje šuma, obrada boja |
| Dronovi i gimbali | Praćenje objekata, stabilizacija, izbegavanje prepreka |
| Robotski usisivači | Mapiranje, navigacija, prepoznavanje prepreka |
| Robotske kosilice i čistači bazena | Pokrivanje površine, navigacija i detekcija granica |
| Sportski satovi i pametni prstenovi | Procena sna, oporavka, aktivnosti i potrošnje energije |
| Pametne vage | Obrada bioimpedanse i procena sastava tela |
| Teniski i golf analizatori | Rekonstrukcija zamaha, putanje i brzine lopte |
| Biciklistički trenažeri | Simulacija otpora, procena snage i kalibracija |
| Električni bicikli | Prilagođavanje pomoći motora, procena dometa |
| Baterije i prenosne elektrane | Procena napunjenosti, zdravlja baterije i upravljanje punjenjem |
| Espreso aparati | Upravljanje ekstrakcijom, temperaturom i adaptivnim mlevenjem |
| Pametne rerne i indukcione ploče | Procena pečenja i prilagođavanje grejanja |
| Mašine za veš | Procena tereta, vrste tkanine i optimizacija ciklusa |
| Fenovi i uređaji za kosu | Prilagođavanje temperature i protoka vazduha |
| 3D štampači i skeneri | Kalibracija, kompenzacija vibracija i rekonstrukcija geometrije |
| Termalne kamere i daljinomeri | Kalibracija senzora, filtriranje šuma i merenje |
| Kućni senzori kvaliteta vazduha | Pretvaranje sirovih merenja u procene gasova i kvaliteta vazduha |

## Konkretni primeri iz dokumentacije proizvođača

- **Oral-B:** opisuje prepoznavanje četkanja i praćenje zona kroz povezanu aplikaciju. To ne dokazuje da je ceo algoritam u četkici. [Proizvodi i funkcije](https://www.oralb.co.uk/en-gb/oral-health/why-oral-b/electric-toothbrushes/which-oral-b-io-is-right-for-me).
- **Starkey Edge AI:** opisuje lokalnu obradu zvuka, klasifikaciju zvučnog okruženja, poboljšanje govora i smanjenje buke. [Opis proizvođača](https://www.starkey.com/hearing-aids/edge-artificial-intelligence-hearing-aids).
- **DJI:** dokumentuje ActiveTrack praćenje i ponašanje pri detekciji prepreka; podrška zavisi od modela i režima. [Dokumentacija](https://support.dji.com/help/content?customId=en-us03400006832&documentType=artical&lang=en&paperDocType=paper&re=GB&spaceId=34).
- **Bosch Sensortec:** nudi BSEC za obradu i fuziju podataka senzora i BSX za fuziju senzora. Dobavljač algoritamske biblioteke može biti potencijalni kupac, uz proizvođača krajnjeg uređaja. [Softverski portfolio](https://www.bosch-sensortec.com/en/software-tools/software).
- **Garmin:** navodi Firstbeat Analytics kao osnovu ocene sna. [Opis obrade sna](https://www.garmin.com/en-US/blog/fitness/how-garmin-watches-track-your-sleep-calculate-sleep-score/).
- **Dyson Supersonic Nural:** opisuje merenje udaljenosti i automatsko smanjenje temperature pri približavanju kosi i temenu. Sama funkcija ne dokazuje da je algoritam složen ili teško zamenljiv. [Opis proizvoda](https://www.dyson.co.uk/hair-care/hair-dryers/supersonic-nural).

## Zašto kopiran softver nije automatski kopiran proizvod

Dobijen softver može skratiti razvoj, ali su i dalje potrebni kompatibilan hardver, senzori, kalibracija, proizvodnja i eventualni sertifikati. Rekonstruisan algoritam nije isto što i originalni izvorni kod, trening podaci ili kompletna dokumentacija. Softver može zavisiti od određenog čipa ili individualnih parametara uređaja.

Zato treba proveriti dve različite mogućnosti: da li neko može ponovo koristiti postojeći binarni fajl na kompatibilnom hardveru, ili iz analize mora napraviti sopstvenu implementaciju. Te prepreke i odgovarajuća zaštita nisu iste. Obfuskacija sama po sebi ne sprečava svako kopiranje binarnog fajla.

## Prioritet za sledeće istraživanje

**Procena, ne potvrđena potražnja:** prvo ispitati audio uređaje, robotske uređaje i merne instrumente, jer je često moguće definisati konkretnu obradu i izmeriti njen doprinos kvalitetu proizvoda.

Za svaki segment proveriti: ko poseduje algoritam i odlučuje o zaštiti; gde se kod isporučuje; koliko konkurentu skraćuje razvoj; koja zaštita već postoji; koji posao održavanja boli; i da li obfuskacija uz ograničenu formalnu proveru rešava taj problem bolje od postojećeg procesa.

Povezano: [[reverse-engineering-targets-and-intelligence-map]], [[what-code-obfuscation-can-and-cannot-protect-in-shipped-products]], [[algorithm-protection-demand-intersection-remains-unproven-for-named-buyers]].
