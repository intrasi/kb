---
type: note
title: Reverse engineering can expose product logic and small operational clues across shipped software and hardware
tags: [security, market, customer, agents]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [reverse-engineering-artifacts-web-excerpts-2026-11-07, https://learn.microsoft.com/en-us/azure/firmware-analysis/overview-firmware-analysis, https://www.ic3.gov/CSA/2026/260819.pdf, https://docs.nvidia.com/deeplearning/tensorrt-rtx/latest/reference/cybersecurity-disclosures.html, https://www.usenix.org/conference/usenixsecurity20/presentation/ender]
---

## Kratak odgovor

**Internet nije uslov.** Potreban je dostupan primerak programa, firmwarea, hardvera ili mogućnost posmatranja njegovog ponašanja. Analiza primerka proizvoda i pristup konkretnoj fabrici su odvojene stvari. Vidi [[reverse-engineering-needs-an-accessible-artifact-not-an-internet-connected-target]].

**Ovo je mapa mogućnosti, ne spisak dokazanih napada ili kupaca.** Redovi navode šta bi moglo da se sazna ako odgovarajući podaci zaista postoje i postanu čitljivi. Ne tvrde da svaki uređaj otkriva sve navedeno. Izvedeni primeri označeni su kao hipoteze; referentni slučajevi ispod daju stvarne dokaze.

## Mapa potencijalnih meta

| Meta | Šta bi neko morao da ima | Mogući intel | Poslovna posledica / ograničenje |
|---|---|---|---|
| PLC i industrijski kontroler | Firmware ili uređaj; za lokalne procese projekat/backup | Kontrolna logika, protokol, autentikacija; kod instalacije i recepti/podešavanja | Kopiranje znanja ili priprema napada; generički firmware nije recept određene fabrike |
| Robot i njegov kontroler | Kontrolni softver, simulator ili hardver | Kretanje, transformacije, servisne funkcije; projektom putanje rada | Moguće kopiranje algoritma; promena procesa zahteva dodatni pristup |
| CNC, motion control, frekventni regulator | Softver/podešavanja konkretne mašine | Obrada, regulacija, kalibracija i parametri | Hipoteza: ušteda konkurentskog razvoja; ne nalazi se sve u firmwareu |
| HMI/SCADA i engineering workstation | Aplikacija ili projektni fajl | Tagovi, struktura postrojenja, alarmi i veze sa kontrolerima | Razumevanje procesa; podaci su često u projektima, izvan zaštićenog koda |
| Industrijski gateway, ruter, VPN/firewall uređaj | Firmware ili korišćen uređaj | Verzije komponenti, protokoli, eventualni ključevi i mrežne postavke | Priprema napada ili otkrivanje poslovnih veza; prazna fabrička slika nema tuđu konfiguraciju |
| Kamera, NVR i smart uređaj | Update, aplikacija ili uređaj | Formati, integracije, obrada slike, eventualne servisne mogućnosti | Hipoteza: interoperabilnost, kopiranje ili traženje slabosti; dostupnost zavisi od zaštite |
| Medicinska i laboratorijska oprema | Firmware/aplikacija; za pacijente lokalni podaci | Implementacija protokola i obrade, uslovi alarma | Hipoteza: kopiranje funkcije ili sigurnosna analiza; kod sam po sebi ne sadrži sva merenja |
| Vozila, punjači, telematika | ECU/infotainment firmware ili prateća aplikacija | Poruke, autorizacija funkcija, dijagnostika, integracije | Hipoteza: kompatibilni proizvodi ili zloupotreba funkcija; pristup zavisi od modela |
| Energetika, zgrade, pumpe i kompresori | Kontrolni softver ili projekat | Upravljanje, pragovi, raspored uređaja i procesna logika | Sličan obrazac kao kod PLC-a; konfiguracija lokacije zahteva njen artefakt |
| Desktop CAD/CAM, simulacije, optimizacija | Installer ili instalirana aplikacija | Inženjerske formule, heuristike, parsiranje, izbor algoritama | SDProget potvrđuje vrednost formula; rekonstrukcija nije isto što i konkurentan proizvod |
| Komercijalni SDK: PDF/OCR, geometrija, geodezija, kompresija | Distribuirana biblioteka i javni interfejs | Implementacija algoritma i obrada rubnih slučajeva | Hipoteza: ubrzavanje razvoja zamene; nije dokaz da su svi takvi SDK-ovi nezadovoljni zaštitom |
| Digitalna forenzika i recovery alati | Aplikacija/biblioteka | Rekonstrukcija podataka i poznavanje disk formata | DME je dokumentovan istorijski primer zaštite te logike; danas deo Magneta |
| Customer-hosted enterprise proizvod | Container, VM/appliance ili serverski paket kod kupca | Poslovna pravila, parseri, optimizacija i licenciranje | Kupac upravlja okruženjem; ovo se razlikuje od čistog SaaS-a |
| Mobilne aplikacije i lokalni agenti | Distribuirani paket | Lokalne provere, tokovi, endpointi, eventualne ugrađene tajne | Poznavanje endpointa ne znači da autorizacija servera može da se zaobiđe |
| Igre i plug-inovi | Klijent, plug-in ili njegovo izvršavanje | Klijentska pravila, formati i licenciranje | Hipoteza: cheat/piraterija/kopiranje; serverska logika ostaje zasebna granica |
| Lokalni AI i inference appliance | Model/engine i runtime | Struktura i težine ako su oporavljive, preprocessing/postprocessing | NVIDIA izričito upozorava na moguću rekonstrukciju modela iz engine fajla |
| Custom GPU kernels i drajveri | Distribuirani binarni fajlovi | Izvršne instrukcije i izvediva logika obrade | Alati za disasembliranje postoje; originalni izvor i potpuno ponašanje nisu automatski vraćeni |
| FPGA i hardverski IP | Bitstream i odgovarajući interfejs/uređaj | Implementirani dizajn, zavisno od mogućnosti dekodiranja | Starbleed je primer konkretne slabosti određenih porodica; ne univerzalno razbijanje FPGA zaštite |
| Web frontend, browser dodatak, WebAssembly | Kod isporučen browseru | Klijentska logika, imena funkcija; sourcemap može otkriti izvor | Serverska implementacija i baza nisu time preuzete |
| Servisni alati, updaters, instalacioni paketi | Paket dostupan kupcu ili serviseru | Interni protokoli, podržane komande, verzije i tok ažuriranja | Hipoteza: olakšavanje kompatibilnosti ili dalje analize; sama komanda ne daje ovlašćenje |

## Koliko i sitan podatak može biti vredan?

Sledeći lanci su **analitički primeri**, ne tvrdnje o konkretnim incidentima:

| Mali podatak | Šta može da omogući | Šta ne dokazuje |
|---|---|---|
| Naziv i verzija biblioteke | Sužavanje traženja poznatih grešaka | Da je greška prisutna, dostižna ili nepopravljena backportom |
| Interni URL ili naziv servisa | Razumevanje arhitekture i dalja provera pristupa | Da servis postoji danas ili da nema autentikaciju |
| Naziv funkcije, simbola ili debug putanja | Brže pronalaženje relevantne logike | Ispravnu semantiku ili tajni roadmap |
| Format poruke ili fajla | Kompatibilan alat, nezavisni parser ili sigurnosno testiranje | Da je protokol sam po sebi ranjiv |
| Grana koja proverava licencu | Identifikovanje lokalne odluke vredne zaštite | Da ne postoji dodatna serverska provera |
| Numerički prag ili lookup tabela | Hipoteza o odlučivanju proizvoda | Ceo algoritam ili poreklo parametara |
| Sertifikat, korisničko ime ili password hash | Identifikovanje okruženja ili sigurnosna procena | Privatni ključ, važeću lozinku ili mogućnost prijave |
| Validan zajednički privatni ključ ili credential | Potencijalno ozbiljna zloupotreba, prema stvarnim ovlašćenjima | Da ključ nije opozvan ili ograničen na pojedinačan uređaj |
| Lokalni tagovi, alarmi ili redosled operacija | Razumevanje konkretne proizvodnje | Tačan recept ili trenutnu konfiguraciju bez dodatnog konteksta |
| Razlika između dve verzije | Fokus na novoj funkciji ili bezbednosnoj izmeni | Da je izmena ranjivost ili da stara verzija ostaje dostupna |

Microsoft dokumentuje da firmware analiza može identifikovati komponente/verzije, kriptografski materijal i password hashove. Prisustvo potencijalno opasnog poziva je signal za proveru, ne dokaz ranjivosti. [Dokumentacija](https://learn.microsoft.com/en-us/azure/firmware-analysis/overview-firmware-analysis).

## Provereni primeri koji podupiru mapu

- **Industrijski protokoli:** Nozomi je kroz RE Mitsubishi iQ-R kontrolera rekonstruisao nedokumentovane detalje autentikacije/autorizacije i prijavio osam ranjivosti. Laboratorijski nalaz iz 2023, ne incident krađe algoritma. [Izvor](https://www.nozominetworks.com/blog/nozomi-networks-labs-presents-zero-day-vulnerabilities-affecting-mitsubishi-electric-safety-plcs-at-black-hat-mea-23).
- **Polovni ruteri:** ESET je 2023. kupio 18 uređaja; nakon isključivanja mrtvog i duplog primerka, devet od 16 jedinstvenih konfiguracija bilo je potpuno dostupno. Nađeni su mrežni i poslovni podaci. To je pre svega propust brisanja podataka, bez potrebe za naprednim RE; nije reprezentativna stopa za industriju. [Originalni rad](https://web-assets.esetstatic.com/wls/en/papers/white-papers/used_routers_corporate_secrets.pdf).
- **Štampač/faks:** Check Point je 2018. analizom firmwarea pronašao slabosti i laboratorijski pokazao kompromitovanje HP all-in-one štampača preko telefonske faks linije. HP je objavio zakrpu. Internet nije bio ulazni kanal u štampač; kasnije širenje zavisilo je od lokalne mreže. [Istraživanje](https://research.checkpoint.com/2018/sending-fax-back-to-the-dark-ages/).
- **Formule i recovery logika:** SDProget i istorijski DME slučaj pokazuju da prodavci smatraju konkretnu implementaciju vrednom zaštite. To nisu dokazi AI krađe. [SDProget](https://cpl.thalesgroup.com/sites/default/files/content/case_studies/sdproget-leverages-thales-sentinel-to-implement-flexible-licensing-cs.pdf), [DME](https://www.preemptive.com/wp-content/uploads/2023/11/DME-Forensics-Case-Study.pdf).
- **Lokalni AI:** NVIDIA navodi da engine može omogućiti rekonstrukciju izvornog modela i kada je originalna specifikacija bila šifrovana. To nije dokaz da je svaki model lako oporavljiv ili da se dobija trening skup. [Dokumentacija, ažurirana 15.10.2026](https://docs.nvidia.com/deeplearning/tensorrt-rtx/latest/reference/cybersecurity-disclosures.html).
- **Hardverski IP:** Starbleed, USENIX Security 2020, demonstrira gubitak poverljivosti/integriteta bitstreama određenih Xilinx porodica. Dekriptovani bitstream nije originalni HDL izvor. [Rad](https://www.usenix.org/conference/usenixsecurity20/presentation/ender).

Za dokaze AI upotrebe i njihove granice vidi [[ai-plc-targeting-is-documented-but-does-not-show-an-obfuscation-failure]].

## Šta ovo znači za naš startup?

Treba odvojiti **zaštitu proizvođačevog algoritma** od **zaštite operaterove konfiguracije i podataka**. Kupac može biti OEM, softverski dobavljač ili integrator koji poseduje algoritam; sama fabrika često nema izvorni kod za zaštitu vendorovog firmwarea.

Prvi kandidat za proveru ostaje uska C/C++ biblioteka koja se isporučuje kupcu: vredna logika, podržan build i merljiv zadatak za RE. U industriji bi to mogla biti nesigurnosna obrada/optimizacija na edge računaru. Ovo je hipoteza za discovery i pilot, bez potvrđenog budžeta. Potpuna zaštita PLC-a, real-time upravljanja, GPU modela i FPGA dizajna tražila bi različite proizvode.

**Ne možemo obećati da niko neće saznati ništa.** Potencijalni proizvod treba da pokaže koji konkretan zadatak postaje skuplji ili sporiji, uz tačno ograničen dokaz očuvanja funkcionalnosti. Vidi [[what-code-obfuscation-can-and-cannot-protect-in-shipped-products]].
