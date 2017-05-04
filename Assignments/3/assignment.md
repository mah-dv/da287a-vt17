# Inlämningsuppgift 3 - Webbapplikation med Laravel

Den tredje inlämningsuppgiften handlar om att bygga en webbapplikation med **Laravel**. Webbapplikationen ska hantera olika *resurser* (vilka resurser väljer ni själva) samt ha inloggningsfunktionalitet. Ni ska även visa prov på god versionshantering under utvecklandet av webbapplikationen genom `GitFlow`.

## Uppgiften

Denna uppgift är mycket mer öppen än tidigare uppgifter, vilket innebär att ni sjävla får bestämma innehållet i er webbapplikation. Det är helt okej att återanvända det ny byggt på laborationerna och bygga en webbapplikation med resurserna `produkt`, `review` och `store` om man vill det, men det är även välkommet med egna idéer. Följande ska finnas finnas i inlämningsuppgiften.

1. Ni ska använda `GitFlow` i er utvecklingsprocess på ett **korrekt** sätt, se [Lab 2](../../Labs/2/git.md)
2. Ni ska använda er av minst tre resurser (vilket ska resultera i minst tre `models`)
    - Minst två av resurserna ska ha en relation till varandra. T.ex. en `product` har flera `review`.
3. Varje resurs ska ha en egen `controller`.
4. Ni ska ha följande vyer för var och en av era resurser:
    - **Lista alla exemplar av en resurs (t.ex alla produkter)**
    - **Lista detaljerad information om en resurs (t.ex. en produkt)**
    - Skapa en ny resurs (t.ex. en ny produkt)
    - Redigera en resurs (t.ex. en produkt)
    - Radera en resurs (t.ex. radera en produkt)
    - _De fetstilta vyerna kräven **inte inloggning**_
5. Ni ska även ha en startsida som visar en översikt av webbplatsens syfte och resurser.

I övrigt är uppgiften väldigt öppen, men fokus ska ligga på ett **enkelt och tydligt användargränssnitt**. Använd gärna [Bootstrap](http://getbootstrap.com/) för detta.

## Krav

Följande krav finns på uppgiften:

- Uppgiften ska följa uppgiftsbeskrivningen ovan
- Ni ska använda er av `GitFlow` för versionshantering av webbapplikationen
- Ni ska använda er av `migrations` för att skapa era tabeller
- Ni ska använda er utav `seeds` för att populera era tabeller
- Ni ska använda er utav `controllers` för att hantera logiken för er applikation
- Ni ska använda er utav `models` för att mappar era resurser mot databaser (ORM)
- Ni ska använda er utav `views` för att bygga ert grafiska gränssnitt
- Ni ska använda er utav `authentication` för att skydda vissa vyer (skapa/redigera/radera resurs)
- Ni ska följa PSR-1 & PSR-2 när det gällen hur ni skriver er kod

## Inlämning & deadline
Inlämningen sker genom att ni publicerar er lösning på Github och skickar in adressen till er lösning på Its learning. Glöm inte att uppgiften ska utföras och redovisas enskilt.

Uppgiften ska vara inlämnad senaste söndagen den *14:e maj*, 23.59. Uppgifter som lämnas in efter deadline kommer att rättas i samband med nästa inlämningsuppgift.
