---
title: Glaudink CSS failus su CSStidy
category: atviras-kodas
image: i/placeholder.jpg
description: Kas yra CSStidy ir kaip juo naudotis. CSS failų glaudinimas ir formatavimas.
---

CSS failai neatsiejami kiekviename tinklapyje. Jų puslapių peržiūros metu vartotojai atsiunčia labai daug. Dažniausiai naršyklės juos kešuoja, bet ne visos, kai kurios to nedaro. Kiekvienas naujas vartotojas užsukęs į tinklapį iškart gauna “porciją” CSS failų (pakankamai dažnai jų puslapyje būna ne vienas).

Tad daug atsiunčiamų tokių failų yra bereikalingas Jūsų serverio srauto ir resursų naudojimas. Tikrai ne viena kompanija siūlo įvairių būdų šiems resursams sumažinti, bet apie juos dabar nekalbėsiu. Pakalbėsiu apie CSStidy. Atviro kodo programą, kurią galima naudoti bet kurioje operacinėje sistemoje.

Nors jos paskirtis tvarkyti CSS failo turinį pašalinant nereikalingu aprašus, tačiau ji atlieka daug daugiau nei panašaus pobūdžio programos:

-   Spalvų pavadinimus paverčia į šešioliktaines išraiškas (spalva “red” tampa \#FF0000).
-   Pašalina nereikalingus ir save perrašančius dublikatus.
-   Pagal kompresijos lygį šalina tarpus ir tuščias eilutes.
-   Trumpina aprašus, pavyzdžiui “padding: 10px 10px 10px 10px” tampa “padding:10px”.
-   Trumpina spalvų kodus: \#000000 tampa \#000.

Na, pirmiausia tai tikriausiai turėtumėte pradėti nuo šios programos įdiegimo. Ubuntu operacinėje sistemoje (o taip, aš jos mylėtojas) tai galite padaryti taip:

    csstidy css/style.css css/style_optimized.css

Jeigu nenaudojate šios operacinės sistemos, parsisiųskite programos versiją iš [sourceforge.net](http://sourceforge.net/projects/csstidy/) svetainės.

Yra \*.exe failas (kaip matote, Windows vartotojai tikrai neužmiršti).

Kas įdomiausia, kad CSStidy parašytas dviem kalbomis: PHP ir C++. Kadangi Lietuvoje labai daug PHP fanų, tai galbūt atsiras norinčių padėti šiai programinei įrangai vystytis :)

Trumpai parodysiu, kaip programa naudotis terminale. Komandos pavyzdys:

    csstidy css/style.css css/style_optimized.css

Čia css/style\_optimized.css yra failas, į kurį bus išsaugotas naujas CSS failas. Tiesa, keli naudingi parametrai šiai komandai (jie rašomi po failų vardų):

-   `—sort\_properties=true|false` ir `—sort\_selectors=true|false`: gražiai išrikiuos CSS kodą pagal abėcėlę. Jeigu CSS nėra blokais aprašytas (pavyzdžiui: tam tikra sekcija CSS kodo aprašo viršutinę puslapio dalį (angl. header), kitas CSS blokas aprašo kokią nors kitą puslapio dalį) tai šie parametrai turėtų būti įjungti.
-   `—compress\_colors=true|false`: nors tai daroma automatiškai, tačiau verta žinoti, kad su šia komanda suglaudinami spalvų aprašai.
-   `—preserve\_css=true|false`: pavojingas parametras, nes jis šalina komentarus ir dažniausiai naudojamus “hackus” naršyklėms.

Štai pavyzdys terminale kaip vesti parametrus (skirta tiems, kas tikrai nežino):

    csstidy css/style.css css/style_optimized.css --compress_colors=true

Oficiali svetainė CSStidy projekto: csstidy.sourceforge.net
