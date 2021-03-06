---
title: Randame vienodus failus su BASH
category: atviras-kodas
image: i/dubliuoti_failai.jpeg
description: Kaip rasti vienodus failus su BASH. Vienodo turinio failų paieška su BASH.
---

Susidūriau visai neseniai su situacija, kai dideliame muzikos archyve buvo daugybė pasikartojančių dainų (failų). Juk erzina kartais, kai pasileidi savo didžiulę muzikos kolekciją ir dažnai pasikartoja tos pačios dainos kurias tenka persukti.

Todėl nusprendžiau tokius failus išrinkti (pirmiausiai), o vėliau ir pašalinti. Kai pamačiau savo komandos eilutės rezultatą nusprendžiau, kad derėtų juo pasidalinti ir su kitais. Bei, paaiškinti kas ką daro (galbūt tai kam nors bus naudinga besimokant BASH). Be to, tai gali būti naudinga ne tik kai turite didelę muzikos kolekciją, galbūt ir kitų failų kolekciją: išeities kodo, paveiksliukų, nuotraukų ir pan.

Kaip sakiau, nagrinėsime patį rezultatą - eilutę, kuri dar nieko netrina, kuri tik parodo vienodo turinio failus:

    find -type f -exec md5sum '&#123;&#125;' ';' | sort | uniq --all-repeated=separate -w 33 | cut -c 35-

Pati komanda velniškai paprasta. Pirmiausiai randame visus failus (failus, bet ne katalogus) su find -type f. Tuomet su kiekvienu failo pavadinimu įvykdome md5sum \<failo vardas\> komandą, kuri išves eilutes tokiu formatu:

    <md5 reikšmė 32 simbolių>  ./pilnas/kelias/iki/failo.vardo

Štai čia dar galime panaudoti keletą komandos find variacijų. Pavyzdžiui galime praleisti tuščius failus su find -not -empty arba galime ieškoti ne dabartiniame kataloge, o konkrečiame, pavyzdžiui: find Darbas/Klientai/Nelegali-Muzika/.

Turėdami šiuos duomenis galime juos išrikiuoti abėcėlės tvarka (komanda sort be jokių argumentų). Pasikartojančių failų (kurių turiniai vienodi ir nesvarbu kokioje disko ar katalogo vietoje jie yra) MD5 reikšmės bus vienodos, todėl išrikiavus sąrašą MD5 reikšmės atsidurs šalia. Pavyzdžiui jeigu gavome tokį sąrašą:

    abcd12345  ./kelias/iki/rihannos-dainos.mp3
    sadf33515  ./kelias/su/kita/daina.mp3
    abcd12345  ./kelias/iki/kitos/rihannos-super-mega-mix-dainos.mp3

Tai po rikiavimo turėsime tokį:

    abcd12345  ./kelias/iki/kitos/rihannos-super-mega-mix-dainos.mp3
    abcd12345  ./kelias/iki/rihannos-dainos.mp3
    sadf33515  ./kelias/su/kita/daina.mp3

Kai turime visą tokį sąrašą, jau galėsime surasti vienodus failus tiesiog peržiūrėjus tokį sąrašą. Bet juk tai laiko švaistymas, nes Jūsų sąraše gali pasitaikyti daug *ne* vienodų failų. Todėl su sekančia komanda pašalinsime iš sąrašo tokias MD5 reikšmes kurios faile nepasikartoja. Tą padarysime su komanda uniq --all-repeated=separate -w 33. Pirmas argumentas nustato, kad komanda atspausdintų tik pasikartojančias eilutes, antrasis argumentas nurodo, kad tikrinimą ar eilutės vienodos daryti tik su pirmais 32 simboliais (iki 33 simbolių). MD5 reikšmė yra visada 32 simbolių.

Dabar jau turėsime visą sąrašą TIK su pasikartojančiais failais. Jų MD5 reikšmėmis ir failo pavadinimais. Jeigu naudoti aukščiau parašytą sąrašą, tai gausime tik tai:

    abcd12345  ./kelias/iki/kitos/rihannos-super-mega-mix-dainos.mp3
    abcd12345  ./kelias/iki/rihannos-dainos.mp3

Toks sąrašas yra nepatogus, nes turime teksto kuris ne tik mums nieko nesako, bet ir „šiukšlina“ išvestį. Apkirpsime eilutes su komanda cut -c 35-. Tikriausiai smalsu kodėl skaičius 35 yra panaudotas? Prisiminkite mūsų išvesties formatą: 32 simboliai MD5 reikšmei, du tarpai ir toliau failo vardas.

Internete, tiesa, radau ne vieną būdą išspręsti [šiai problemai](http://www.commandlinefu.com/commands/view/3555/find-duplicate-files-based-on-size-first-then-md5-hash).

Na, o va šitame taške jau sužinojau apie jau egzistuojančią programą kuri daro viską ką aprašiau aukščiau: fdupes. Įdiegiam:

    sudo apt-get install fdupes

Naudojam:

    fdupes -r .

Pirmiausiai ieškos pagal dydį, vėliau pagal MD5 išraišką. Komanda tikrai greitai veikia (kadangi kitoks rūšiavimas vyksta, tai greičiau nei mano aprašytas būdas).

Kadangi jau neproduktyviai išleidau laiką savo komandai, tikiuosi kam nors besimokančiam BASH tai pasirodys naudinga.
