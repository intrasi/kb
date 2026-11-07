---
type: note
title: Everyday device research demonstrates privacy intrusion unauthorized control fraud and service disruption
tags: [security, customer, market, agents]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [everyday-device-harm-primary-excerpts-2026-11-07, https://unsaflok.com/, https://research.checkpoint.com/2020/dont-be-silly-its-only-a-lightbulb/, https://arxiv.org/abs/1504.04339]
---

## Šta zapravo želimo da pokažemo

Svakodnevni predmeti sadrže softver koji donosi odluke o pristupu, kretanju, grejanju, podacima ili prikazu informacija. Razumevanje tog softvera može olakšati pronalaženje i korišćenje slabosti. **Reverse engineering ne stvara te slabosti i sam po sebi ne daje ovlašćenje za kontrolu uređaja.**

Ovo je casebook sa konkretnim izvorima, pregledanim 7.11.2026. Istorijski nalazi se odnose na tadašnje verzije. Ne tvrdimo da su svi ovi proizvodi danas ranjivi, niti da je AI korišćen u starijim primerima. Ne postoje podaci koji opravdavaju procenu ukupnog budućeg broja napada.

## Konkretni predmeti i demonstrirane mogućnosti

| Predmet / datum | Šta je istraženo i šta je postignuto | Potreban pristup i granica tvrdnje |
|---|---|---|
| **Robotski usisivač Ecovacs**, istraživanje 2024 | Analiza uređaja/aplikacija otkrila probleme kriptografije, autorizacije i pristupa kameri | Neke putanje počinju u radio dometu, druge koriste nalog/cloud; ne jedan univerzalni način napada. [Istraživači](https://dontvacuum.me/talks/HITCON2024/HITCON-CMT-2024_Ecovacs.html) |
| **Hotelska brava Saflok**, objavljeno mart 2024 | Rekonstrukcija zaštićenog formata kartica i povezane slabosti omogućile neovlašćeno otvaranje vrata | Potrebna interakcija sa sistemom kartica/vratima; internet na bravi nije uslov. Nalaz ne važi za sve RFID brave. [Unsaflok](https://unsaflok.com/), [prezentacija](https://unsaflok.com/videos/slides.pdf) |
| **Aparat za kafu Smarter**, septembar 2020 | RE firmwarea i izmena ponašanja: poruka za otkupninu, neprekidno aktiviranje grejača/doziranja/mlina i zvuka | Dostupna lokalna mreža ili Wi-Fi domet u odgovarajućem režimu uređaja; laboratorijski PoC, bez dokazanog požara ili iznuđene uplate. Već tada stara, napuštena platforma. [Avast/Gen](https://www.gendigital.com/blog/insights/research/the-fresh-smell-of-ransomed-coffee-0) |
| **Pametna sijalica i Philips Hue Bridge**, 2020 | RE hub binarnog koda i ZigBee obrade podržao preuzimanje huba preko radio-putanje; moguća dalja mrežna aktivnost | Kontrolisana/zlonamerna sijalica i komunikacija sa hubom, uz korisnički korak u lancu; ne tvrdnja da se svaki dom preuzima samo slanjem komande. Zakrpa opisana u izvoru. [Check Point](https://research.checkpoint.com/2020/dont-be-silly-its-only-a-lightbulb/) |
| **Sobni bicikl Peloton Bike+**, jun 2021 | Analiza boot procesa otkrila problem Verified Boot; demonstriran root pristup, kamera/mikrofon i izmena sistema | Početni fizički pristup. Nije demonstracija daljinskog preuzimanja svakog bicikla preko interneta niti povrede promenom otpora. Peloton izdao zakrpu. [McAfee](https://www.mcafee.com/blogs/other-blogs/mcafee-labs/a-new-program-for-your-peloton-whether-you-like-it-or-not/) |
| **Infuziona pumpa B. Braun i komunikacioni moduli**, 2021 | Istraživanje sistema našlo lanac kojim se menja konfiguracija pumpe u standby/off stanju, sa mogućim uticajem na sledeću terapiju | Pristup istoj mreži, pogođena verzija i konkretan uređaj. Proizvođač izričito kaže da promena tekuće terapije nije moguća i da nije primio prijave stvarne eksploatacije. [B. Braun](https://www.bbraun.com/en/products-and-solutions/b--braun-product-security/05-2021-spacecom--battery-pack-sp-with-wifi--data-module-compact.html), [NHS](https://digital.nhs.uk/cyber-alerts/2021/cc-3930) |
| **Raven II hirurški robot**, 2015 | Istraživači demonstrirali manipulaciju funkcijama, nadjačavanje komandi operatera i prekid rada preko komunikacije | Eksperimentalna istraživačka platforma i kontrolisani mrežni uslovi. Nije dokumentovan napad na pacijenta ili dokaz da je komercijalni da Vinci ranjiv; članak nije dokaz potrebe za binarnom obfuskacijom. [Rad](https://arxiv.org/abs/1504.04339) |
| **Kućni EV punjači**, jul 2021 | Istraživanje aplikacija/cloud platformi/hardvera pokazalo neovlašćenu kontrolu punjenja; kod jedne platforme i izmenu firmwarea/potencijalni ulaz u kućnu mrežu | Zavisno od nalaza potreban pristup cloud servisu ili fizički uređaju. Nije svaka slabost zahtevala RE; globalni zbir uređaja ne dokazuje mogućnost istovremenog rušenja jedne elektro-mreže. Proizvođači uveli ispravke. [Pen Test Partners](https://www.pentestpartners.com/security-blog/smart-car-chargers-plug-n-play-for-hackers/) |
| **Kancelarijski štampač/faks HP Officejet Pro 6830**, avgust 2018 | RE firmwarea pomogao otkrivanju grešaka; demonstrirano preuzimanje preko faks linije, pa dalji napad u laboratorijskoj mreži | Ulaz je telefonska linija; za sledeći korak potrebna mrežna povezanost i dodatna ranjivost. HP objavio zakrpe. [Faxploit](https://research.checkpoint.com/2018/sending-fax-back-to-the-dark-ages/) |
| **Digitalna registarska tablica Reviver**, istraživanje predstavljeno 2024 | Fizička analiza, firmware RE i prilagođeni firmware omogućili kontrolu prikaza tablice | Napad na hardver istraženog modela, ne univerzalno udaljeno preuzimanje. Moguća zloupotreba identiteta vozila je posledica demonstrirane promene prikaza, ne prijavljena kampanja krađe. [IOActive](https://info.ioactive.com/acton/fs/blocks/showLandingPage/a/34793/p/p-0088/t/page/fm/0) |
| **Semafori**, WOOT 2014 | U saradnji sa nadležnima demonstrisana kontrola sistema i mogućnost ometanja saobraćaja | Pristup odgovarajućoj mreži/radiju. Studija se uglavnom oslanja na slabe mrežne kontrole; nije primer obavezno složenog RE. Poseban hardverski MMU ograničava konfliktne signale. [Rad](https://www.usenix.org/system/files/conference/woot14/woot14-ghena.pdf) |

**Tri novija AI primera — robotska kosačica, egzoskelet i robot za pranje prozora — obrađena su posebno:** [[ai-assisted-consumer-robot-research-connects-reverse-engineering-to-physical-and-privacy-risks]]. To je direktnije vezano za našu tezu od starih demonstracija bez AI-ja.

## Šta se već dešavalo van laboratorije?

ABC je 11.10.2024. objavio originalno izveštavanje o vlasnicima Ecovacs X2 uređaja kojima su neovlašćene osobe upravljale usisivačima i puštale uvredljive poruke preko zvučnika. Jedan prijavljeni slučaj uključuje jurenje psa. **Tačan ulaz napadača nije utvrđen**: Ecovacs je ukazivao na ukradene naloge/credential stuffing, a istraživači na nedovoljne dodatne provere. To nije dokaz da su kriminalci koristili isti Bluetooth exploit, RE alat ili AI. [Izveštaj i odgovori kompanije](https://www.abc.net.au/news/2024-10-11/robot-vacuum-yells-racial-slurs-at-family-after-being-hacked/104445408).

Ovaj primer pokazuje stvarnu zloupotrebu mogućnosti uređaja. Ostale laboratorijske slučajeve ne treba preimenovati u stvarne napade sa povređenim žrtvama.

## A ekrani i razglas u vozu?

ENISA popisuje putničke informacione, najavne i entertainment sisteme kao posebne delove železničkog okruženja. Na osnovu njihovih funkcija, **naši scenariji** su lažne informacije o peronu/stanici, zlonamerne poruke, prekid obaveštavanja i trošak vraćanja sistema. [ENISA, novembar 2021, aneks o sredstvima](https://www.enisa.europa.eu/sites/default/files/publications/ENISA%20Report%20-%20Railway%20Cybersecurity%20-%20Good%20Practices%20in%20Cyber%20Risk%20Management.pdf).

**Nisam potvrdio konkretan primarni slučaj u kom je RE ekrana u vozu omogućio kontrolu kočnica.** Za prelazak sa putničkog sistema na upravljanje potrebni su dodatna putanja i propust granice između sistema. Ne treba praviti takvu priču samo zato što oba koriste softver. Izvorna [32C3 prezentacija iz 2015](https://media.ccc.de/v/32c3-7490-the_great_train_cyber_robbery) potvrđuje šire praktično istraživanje železničkih sistema, ali njena dostupna opisna stranica ne dokazuje taj konkretan lanac.

## Vrste štete koje case treba da pokrije

Ovo su izvedene kategorije, ne zbir procenjenih gubitaka:

1. **Privatnost:** kamera/mikrofon, kretanje osobe, mapa doma ili dvorišta, korišćenje uređaja.
2. **Fizički pristup:** otvaranje prostorije i zloupotreba poverenja u sistem pristupa.
3. **Dostupnost:** blokiran uređaj, zaustavljeno punjenje, servis i gubitak radnog vremena.
4. **Integritet rada i informacija:** promenjena konfiguracija, lažan prikaz ili komanda.
5. **Fizička bezbednost:** moguća opasnost od neovlašćenog kretanja ili neodgovarajućeg rada; zavisi od nezavisnih sigurnosnih mehanizama. Bez izmišljanja povreda/požara.
6. **Dalji pristup:** kompromitovan predmet kao početna tačka za drugo okruženje, samo uz odgovarajuću povezanost i dodatne slabosti.
7. **Prevara i poslovni trošak:** zloupotreba identiteta uređaja, moguća iznuda, zakrpe, terenski servis i reputacija. Mogući trošak nije izmeren gubitak.
8. **Intelektualna svojina:** izdvajanje vredne implementacije može pomoći konkurentu; ovaj casebook ne dokumentuje krađu komercijalnog algoritma u svim ovim uređajima.

## Kako „mali intel” postaje koristan

| Sitna informacija | Moguća sledeća korist | Primer/granica |
|---|---|---|
| Format lokalne komande | Razumevanje upravljanja | HOBOT/egzoskelet; komandovanje mora biti pravilno autorizovano |
| Zajednički cloud credential | Potencijalno širenje van kupljenog primerka | Hookii autor-reported primer; obim zavisi od ovlašćenja i izolacije |
| Način provere dozvole u aplikaciji | Otkrivanje da li se odluka sprovodi i na drugoj strani | Ecovacs istraživanje; poznavanje aplikacije ne bi smelo da zameni serversku dozvolu |
| Provera integriteta updatea | Procena mogućnosti prihvatanja izmenjenog koda | Aparat za kafu i drugi slučajevi sa firmware kontrolom |
| Verzija komponente ili servisni interfejs | Sužavanje sigurnosnog istraživanja | Ne dokazuje da postoji primenljiva ranjivost |

**Case koji možemo braniti:** jeftinije razumevanje softvera može povećati broj ljudi i proizvoda koji dolaze pod analizu; ako postoje slabosti, posledice prelaze iz digitalnog u svakodnevni fizički svet. Koliko će porasti stvarni napadi i koliko ih naš proizvod sprečava ostaje da se izmeri.

Vidi [[device-harm-evidence-does-not-establish-obfuscation-as-the-main-remedy]] i izvornu kolekciju [[everyday-device-harm-primary-excerpts-2026-11-07]].
