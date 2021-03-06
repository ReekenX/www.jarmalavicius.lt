---
title: Mano Raspberry Pi - jau metai!
category: raspberry-pi
image: i/raspberry_pi_schema.png
description: Ką galima nuveikti su Raspberry Pi? Mano komentarai apie šį įrenginį pasinaudojus juo metus. Kam jį galima panaudoti, kokie jo trūkumai ir privalumai.
---

Raspberry PI kompiuterį, B versijos, gavau prieš metus laiko (2013 metais, sausį). Tai buvo labai puiki, mano įmonės, kurioje dirbu, dovana. Tiesa, tada nuspręsti kam jį panaudosiu buvo ypatingai sunku. Nors, aišku, internete tai tikrai pilna straipsnių apie panaudojimą. Ir kai kiti kolegos gavo šią dovaną, tai girdėjau pačius populiariausius panaudojimus: daryti NAS serverį failams talpinti, senų žaidimų konsolę arba media centrą. Žodžiu, nieko originalaus.

Bet aš išbandžiau ir tai! Taigi, mąstote pirkti bet pirmiau norite gauti šiek tiek atsiliepimo ir apžvalgos? Skaitom!

![Raspberry Pi - kreditinės kortelės dydžio stebuklas!](/i/raspberry_pi_schema.png)

**1. Populiariausi projektai**

Pasidaryti NAS serverį nėra sunku. Tiesa, mane tai žudo kariavimas su Samba, bet iš esmės, tai per kelias valandas prijungus kokią talpyklą (HDD išorinį) galėsite failais keistis ne tik vidiniame, bet ir išoriniame tinkle. Išoriniam tinklui labai puikiai veikia [OwnCloud](http://owncloud.org/) programa.

Media centras vienas populiariausių projektų internete. Aš buvau nustebintas labai paprastu įdiegimu. Media centro programinei įrangai naudojau [XMBC](http://xbmc.org/). Tiesa užtruko kelias valandas, juk tai Raspberry Pi! Dar labiau buvau nustebintas, kai jis neužlūžo žiūrint beveik 8GB filmą ant didelio ekrano. HD kokybė tikrai puiki, persukti filmą ar atsukti/pakeisti - tikrai nesudaro jokių problemų. Plius, dar įsirašius programą telefone, labai lengvai galima buvo media centrą valdyti tiesiog telefone.

Tiesa, norint turėti Media centrą teks įsigyti keletą daiktų, o tai - papildomos lėšos. Savaime suprantama, kad reikalingas monitorius, HDMI kabelis, kolonėlės ir LAN laidas arba WiFi adapteris. Jeigu tokią įrangą reikia įsigyti, tai jau nemažai išlaidų. Bet, manau, kad tai mano sekantis pirkinys. Turiu omeny, kad planuoju įsigyti dar vieną Raspberry PI būtent šiam tikslui.

**2. GPIO**

PI turi dar tokius antgalius su kuriais gali daryti elektronines magijas. Pavyzdžiui kokius valdiklius. Tiesa, susipirkti visokius lituoklius, laidus, rezistorius, kondensatorius ir visa kita, tai kainavo. Bet šiaip, smagu, kad gali valdyti elektros energiją, žiūrėti rezultatus ir taip domėtis elektronika. Tikrai daug apie tai sužinojau Raspberry PI dėka.

Perspėsiu, kad tie kas užsiima elektronika ir bando GPIO, tai persiskaitykit kurių išeinančių jungčių geriau nesuliesti, kad PI nesudegtų. Google apie tai tikrai daug aprašyta. Gaila žmonių, kurie tą patyrė.

**3. Kam aš dabar naudoju Raspberry PI?**

Taigi, praėjus metams, mano Raspberry labiau tapo barbe-devindarbe.

Pirmiausiai, tai Raspberry Pi filmuoja butą motion programos dėka. Ji vaizdą saugo tada, kai kažkas pradeda judėti. Paprasta USB kamera prijungta prie Raspberry PI. Vaizdą realiu laiku galiu visada pažiūrėti per internetą (pvz. telefone surinkus tam tikrą URL adresą). Nors galima daryti video archyvus, bet aš pasidariau, kad įrašinėtų į diską tik tai, kas juda. Veikia puikiai tikrai. O vaizdų kokybė, savaime aišku, priklauso nuo kameros. Tiesa, senos kameros su 1.3 man neveikė niekaip. Tik naujoviškesnės.

NAS serveris - antras panaudojimo būdas. Pasinaudojus btsync aš turiu nemokamą ir neribotą Dropbox'ą. Labai smagu, kad tokia programinė įranga buvo sukurta. Ji veikia pasakiškai, ne kartą universitete išgelbėjo, kai namie pamiršdavau kokius darbus kuriuos turėjau nunešti pristatyti.

Cron'as - tai tokia programa, kuri reguliariai gali paleisti tam tikras komandas. Pavyzdžiui padaro atsargines kopijas serveriams, parašo laiškus kur kam reikia, aplanko svetaines kur būtina atidaryti kasdien, kad gauti taškų ir pan.

**4. Verdiktas**

Eh, jau išsidaviau, kad planuoju dar vieną pirkti dėl namų kino centro. Bet vistiek pasakysiu, kad Raspberry Pi - tikrai apsimoka. Tiesa, jis lėtas IO funkcijoms, kartais tai net erzina. Tai bus aktualu, kai norėsite įsirašyti programas. Bet tai ne priežastis jo nepirkti.

Gal kas bandėsi kitokias alternatyvas ir parekomenduotų geriau?
