---
title: Priežiūros režimo efektyvus įjungimas svetainėse
category: atviras-kodas
image: i/placeholder.jpg
description: Kaip įjungti aptarnavimo („maintenance“ - angl.) režimą efektyviai ir greitai.
---

Jeigu programuojate interneto svetaines turbūt ne kartą tekdavo atnaujinimo darbus atlikti klientų darbo metu. Ir atnaujinimai ne visada tokie jau „nepastebimi“ kaip mes bandome padaryti...

Ypatingai gerai, kad galite savo klientams pasakyti, kad kelioms minutėms kažkas neveiks. Jeigu to nedarote, pagalvokite, ar tikrai gerai atrodo, kai bandote „tyliai“ ir nepastebimai atlikti visus atnaujinimo darbus, bet susimaunate?

Todėl mokėti teisingai/greitai/produktyviai įjungti priežiūros režimą („maintenance mode“ - angl.) yra tikrai didelis profesinis privalumas. Tiesa, tą padaryti yra tikrai ne vienas būdas.

**1. Framework'ų siūlomi sprendimai**

Tokie framework'ai kaip Django ar Symfony (ar daugelis kitų) jau pasiruošę priežiūros būsenai: jie turi tam tikrus modulius ar nustatymuose specialias reikšmes šiam režimui įjungti.

Deja, tokie sprendimai turi tokius trūkumus:

-   Reikia keisti nustatymuose reikšmes.
-   Python atveju reikia perkrauti web servisų konfigūracijas.
-   Ir vistiek ne pats greičiausias sprendimas.

Kaip tą padaryti? Galite paieškoti Google prie savo framework'o pavadinimo prirašę „maintenance mode“. Štai keli atsitiktinių framework'ų pavyzdžiai:

-   [django-maintenancemode](https://pypi.python.org/pypi/django-maintenancemode) (pirmiausiai reikia susikonfigūruoti prieš naudojant)
-   Prestashop atveju tą reikia padaryti per *web administraciją*.

**2. Apache ir mod\_rewrite**

Vienas iš dažniausiai pasitaikančių sprendimo būdų yra perrašyti Apache VirtualHost direktyvą, kuri turėtų kitą DocumentRoot kuriame būtų koks nors index.html failas su priežiūros pranešimu. Tačiau tai turi keletą minusų:

-   Reikia atkomentuoti/užkomentuoti jau parašytą Apache konfigūraciją.
-   Būtina patikrinti apache su apache2ctl -t, kad neatsitiktų taip, kad perkrovimo metu niekas nepasileistų dėl klaidos.
-   Reikia greičiausiai root teisių.

**3. Efektyvus ir greitas apache ir mod\_\_rewrite būdas**

Efektyviausias (turbūt) būdas panaudoti tokią VirtualHost konfigūraciją, kuri priežiūros režimą („maintenance mode“ angl.) įjungtų tik esant maintenance-on failui. Jį pašalinus, apache šio režimo nepaisys.

Kodas:

    <IfModule mod_rewrite.c>
        RewriteEngine On
        RewriteCond %&#123;DOCUMENT_ROOT&#125;/maintenance-on -f
        #RewriteCond %&#123;REMOTE_ADDR&#125; !^TAVO.IP.ADRESAS.CIA$
        RewriteRule !^down-for-maintenance/.*$ /down-for-maintenance/ [R,L]
    </IfModule>

Tikrinimai su IfModule reikalingi jeigu kartais darote kažkokius atnaujinimus web servisų programinėje įrangoje ir yra galimybė sugadinti/nepaleisti mod\_rewrite modulio. Taigi šiomis eilutėmis apsidraudžiate, kad apache vistiek startuotų: blogai galėtų veikti tik viena svetainė (ši), bet ne visos kitos tame serveryje.

Kodas išties paprastas. Eilės tvarka daromi tokie tikrinimai:

-   JEIGU egzistuoja maintenance-on failas;
-   IR JEIGU IP adresas nėra toks kaip nurodytas (galite išvardinti kelias eilutes su skirtingais IP);
-   IR JEIGU klientas dar nėra atidaręs naršyklėje tokio adreso;
-   Nukreipk jį į priežiūros režimo puslapį.

Įjungiam priežiūros režimą:

    cd /kelias/iki/docroot
    touch maintenance-on

Išjungiam priežiūros režimą:

    rm maintenance-on

Na, o sukurtame index faile kataloge down-for-maintenance galite parašyti pranešimą ir pranešti kiek truks atnaujinimai, kokie atnaujinimai daromi ir pan. Akivaizdu, jog tą reikėtų padaryti dar prieš įjungiant aptarnavimo režimą. O vėliau, kai viską ištestuosite, galima tiesiog įdėti kokį JavaScript nukreipimą į svetainę ir tiek (fantazijos dalykas).

**4. Bendrai**

Kaip ten bebūtų, priežiūros režimas visada nėra geras sprendimas:

-   Prarandate lankytojų srautą tam tikrą laiką...
-   Klientai gali pildyti formas ir... Bus nukreipti į priežiūros režimą - nebus išsaugotos jų pildytos formos.

Kalbant apie visokias užsakymų sistemas, kur dirbama su pinigais - visokius aptarnavimo režimus sunku toleruoti klientams.

Bet pagalvokite, kas geriau: suklysti darant atnaujinimus ar pranešti klientams iš anksto ko tikėtis? Tiesa, labai dažni pranešimai tikrai galėtų erzinti.

Greičiausiai idealiausias būdas būtų „load balancing“. Nors tema jau už paprastų web-projektų ribų, dažniausiai. Arba bent jau ne svetainėms, kurios turi tik FTP valdymą.
