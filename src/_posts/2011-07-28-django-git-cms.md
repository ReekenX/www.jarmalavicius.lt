---
title: Django GIT CMS
category: mano-projektai
image: i/mano-projektai/django-git-cms-kitokia-turinio-valdymo-sistema.png
description: Django GIT CMS - kitokia turinio valdymo sistema. Kaip instaliuoti, paleisti ir naudotis.
---

Tai - tikrai neeilinė turinio valdymo sistema. Tuoj suprasite kodėl.

Pirmiausiai **Django GIT CMS neturi jokios administracijos**. Visas turinio valdymas šioje TVS [^1] atliekamas per failus. Taip, perskaitėte teisingai.

Atrodo gana neprofesionaliai? Klystate. Tokia šios sistemos idėja - būti paprastai, lanksčiai ir valdomai ne naršyklės pagalba.

Su Python parašyta sistema, kuri veikia tik ant [Django framework](http://www.djangoproject.com) (veikia puikiai tiek su 1.1, tiek su 1.3 versijomis).

Taip, ji skirta manyčiau IT žmonėms, bet... Viskam yra išimtys. Kodo paryškinimams tekste naudoja populiariausią [Pygments biblioteką](http://pygments.org/) (Python kalbai).

![ GIT logotipas (šios TVS turinio versijavimo sistema)](/i/git-logo.png)

Jums nereikės instaliuoti įskiepių (plugins) nes... Jų čia paprasčiausiai nėra! Todėl jeigu užsimanysite kontaktų formos - teks pasitelkti į pagalbą Django aplikacijos, kurių yra tūkstančiai (o gal ir net daugiau).

**Kaip vyksta turinio administravimas?**

Šios sistemos valdymas vyksta viename kataloge - *content*. Katalogų struktūra tokia:

Perspėjimas: čia išvardinti ne visi katalogai, kuriuose galima valdyti tam tikrą turinį. Daugiau informacijos rasite pačios sistemos kode. Nuoroda žemiau.

Kiekviename kataloge galima valdyti tam tikrą svetainės turinį:

**blog** - tinklaraščio straipsnių (tokių kaip šis) valdymas.

**files** - katalogas failams laikyti (bet kokio tipo failai).

**simplecms** - įvairūs (ne straipsnių) puslapiai, pavyzdžiui: apie mane, autorinės teisės ar pan.

**simplemenus** - meniu, kuris vėliau gali būti atvaizduojamas kaip tik pageidaujama.

**simpletagging** - žymų medis.

Meniu ir žymų valdymą atliksite sukūrę YAML tipo failą. Taip maždaug atrodo meniu failo pavyzdys:

O straipsnių ir puslapių valdymas restruktūrizuoto teksto pagalba (restructured text):

Taigi, prikūrę tokių failų paleidžiame `python manage.py gitcmsload` ir visi duomenys iš failų bus sudėti į duomenų bazę.

Taip, būtent į duomenų bazę. **Django GIT CMS nėra statinio turinio generatorius** (kaip pvz.: hyde, pelican), veikiau dinaminio.

**Django GIT CMS istorija**

Šią sistemą sukūrė Luis Pedro Coelho. Jo tinklaraštį, taip pat padarytą su šia sistema galite [pamatyti čia](http://luispedro.org/).

Paskutinis šio žmogaus įnašas į šią sistemą buvo 2011 metų sausio 24 dieną. Bent jau tokia data buvo, kai rašiau šį straipsnį. O pats pirmas commit'as buvo 2009 metų Rugsėjo pabaigoje. Tad sistema tikrai nėra nauja.

Sistema su Affero 3 (GPL - interneto svetainėms) licenzija yra pasiekiama jo [asmeninėje GitHub paskyroje](https://github.com/luispedro/django-gitcms).

![ Django framework logotipas](/i/django_logo.png)

**Bonus**

Ne paslaptis, kad šią sistemą panaudojau savo tinklaraštyje. Ir naudoju daugiau nei kelis mėnesius. Per tą laiką, pastebėjau kelis trukdančius naudotis šia sistema, dalykus. Todėl teko patobulinti šią sistemą.

Visus pakeitimus rasite [mano GitHub repozitorijoje](https://github.com/ReekenX/django-gitcms)

Atsirado informacija kaip įdiegti šią sistemą, kokių ir kodėl reikia paketų. Tai palengvins sistemos įdiegimą, nes anksčiau reikėdavo gerokai įsigilinti į klaidų pranešimus kol buvo galima paleisti šią CMS.

Parašyti Unit testai. Jų dėka pastebėtos labai senos klaidos buvo lengvai pataisytos. Taigi, nauji pakeitimai greičiausiai „neatkirs“ visos sistemos ;)

Tie, kas mėgsta ne tik gerą programą, bet ir švarų kodą, ras validų PEP8 [^2] kodą :)

Restruktūrizuoti failai dabar reaguos į statusą. Tai reiškia, kad nustačius straipsniui 'unpublished' Jūsų straipsnis nepasirodys svetainėje.

Taip pat patobulinta komanda turinio perkėlimui iš failų į duomenų bazę ir pats procesas optimizuotas.

**Kodėl rekomenduočiau šią, o ne kitą sistemą**

Pirmiausiai, ji parašyta su Python (o aš Python kalbos mylėtojas). Ji naudoja vieną populiariausių framework'ų - Django. Nedidelis funkcionalumas atveria duris į platų vaizduotės pasaulį. Man, populiariausios sistemos kaip Wordpress ir pan. nepatinka dėl per didelio funkcionalumo ir „griozdiškumo“.

Kam reikalinga administracija, juk galima naudoti kokį nors mylimą redaktorių, kaip VIM ar Emacs. Kam paklūsti bandos instinktui rinktis jau sukurtą įprastą Wordpress ar Drupal? :)

Jeigu sumąstysite rinktis panašios paskirties sistemą, būtinai užmeskite akį. O jeigu kas jau tokia naudojasi, būtinai brūkštelėkite komentare. Įdomu pamatyti daugiau tokių sistemų entuziastų :)

[^1]: TVS - Turinio Valdymo Sistema.

[^2]: PEP8 - Python kodo standartų rekomendacija, apie kurią paskaityti [galite čia](http://www.python.org/dev/peps/pep-0008/).
