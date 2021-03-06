---
title: PDF, DOC, ODT, HTML ir kitų dokumentų konvertavimas
category: atviras-kodas
image: i/doc_i_pdf.gif
description: Dokumentų konvertavimas iš doc į pdf, iš odt į pdf, iš html į pdf. Su LibreOffice pagalba tai padaryti nesunku!
---

Visai neseniai teko konvertuoti didžiulę DOC failų bazę į PDF formatą. Laimei komandinės eilutės įrankiai jau seniai tam sukurti, todėl neteko atidarinėti kiekvieno failo ir išsaugoti.

Tie, kas turi įdiegę LibreOffice, gauna ir įrankį kuriuo komandinėje eilutėje gali konvertuoti failų tipus - lowriter. Paprasčiausias būdas konvertuoti daug failų į PDF formatą:

    lowriter --nologo --convert-to pdf *.doc

OpenOffice taip pat turi šią galimybę, tiesa komanda šiek tiek skiriasi:

    oowriter -t pdf *.doc

Taigi pasinaudoję komandomis aukščiau galite lengvai konvertuoti populiariausius formatus kuriuos palaiko LibreOffice: odt, doc, pdf ir net html. Formatų yra kiek daugiau nei aš aprašiau. Paprasčiausias būdas juos visus susirasti - pažiūrėti GUI aplikacijos išsaugojimo lange, nes savo dokumentacijose LibreOffice to neaprašo.

Dar vienas įrankis, kurį galite įsidiegti atskirai, tačiau jis taip pat yra LibreOffice dalis - pavadinimu unoconv. Jo pagalba galite daryti tą patį:

    unoconv -fpdf *.doc

Daugiau šių komandų argumentų neminėsiu, nes jie - nesusiję su pačiu konvertavimo procesu (daugiausiai tai GUI nustatymai). Tačiau apie visus argumentus ir jų reikšmes galite pasiskaityti komandų pagalbos išvestyse:

    lowriter -h
    oowriter -h
    unoconv -h

Reikėtų paminėti, kad nereikėtų 100% pasikliauti uždaro kodo formatų konvertavimu į atviro kodo. Pavyzdžiui konvertuojant iš doc į odt vaizdas gali atrodo kiek kitaip nei originaliame faile. Bet, kiek turėjau praktikos, veikdavo tikrai gerai.

Nereikėtų naudotis įrankiais kurie konvertavimą atlieką netikru spausdinimo būdu. Tai yra kai konvertuojant failą iškviečiamas spausdinimo langas ir spausdinama į netikrą spausdintuvą, kuris atlieka konvertavimo darbus. Tokiu būdu prarasite meta duomenis failų. Tokius kaip autorystę, antraštes ir kita.
