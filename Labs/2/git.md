# Labb 2
I den andra laborationen tittar vi på versionshanteirng med Git. Vi kommer bland annat att bekanta oss med [Git](https://git-scm.com/), [GitHub](https://github.com) och branch-modellen [GitFlow](http://nvie.com/posts/a-successful-git-branching-model/). NÅGONTING WEBBIGT Laborationen är uppdelad i följande delar:

1. Versionshantering med Git
	1. Introduktion till Git
	2. Delning av kod med GitHub
	3. Semantisk versionering med GitFlow
2. Introduktion till HTTP och REST
	1. Postman
	2. Utforska enhörnings-API:t
	3. HTTP-anrop med PHP
	4. GUI med Bootstrap

## Förberedelser
Inför denna labb ska ni ha **skapat ett konto på Github** och **installerat GitFlow**.

### Skapa ett konto hos Github

Gå in på [Github](https://github.com/) och fyll i registreringsformuläret på förstasidan om du inte redan har ett konto där.

### Installera GitFlow

På den virtuella maskinen installerar du GitFlow genom att skriva

```bash
$ sudo apt-get install git-flow
```

Det går även att installera GitFlow på macOS eller Windows. Installationsanvisningar finns här](https://github.com/nvie/gitflow/wiki/Installation).

## Versionshantering med Git

### Introduktion till Git

### Delning av kod med Github

### Semantisk versionering med GitFlow

## Introduktion till HTTP och REST
När man arbetar med webben så inkluderar detta ofta att man hanterar data mellan olika källor. I denna labb innebär det att vi kommer att arbeta med data om enhörningar, närmare bestämt med data från det enhörnings-API som ni hittar på följande adress: [http://unicorns.idioti.se/](http://unicorns.idioti.se/). Surfa till sidan om bekanta er med dess uppbyggnad, som egentligen består av två vyer:
- Visa alla enhörningar
- Visa information om en specifik enhörning
Notera vilka URL:r som används för att visa alla enhörningar/information om en specifik enhörning. Ser ni ett mönster?

### Postman / RestClient
När man arbetar med API:r så är det bra att ha dokumentation kring det API som man arbetar med. Så att man kan se vilka tjänster som API:t tillhandahåller. I vårt fall finns dokumentation om enhörnings-API:t på denna adress [http://unicorns.idioti.se/api.html](http://unicorns.idioti.se/api.html). Läs igenom detta - och fråga labbhandledaren om oklarheter finns.

När ni satt er in API:t så är det dags att testa API:t! Eftersom det inte är helt enkelt att testa annat än `GET`-metoder från webbläsaren så använder man ofta verktyg till detta. Exempel på sådana verktyg är [`Postman`](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop), som är en app till Chrome och [`RestClient`](https://addons.mozilla.org/sv-se/firefox/addon/restclient/) som är ett addon till Firefox. Genom dessa verktyg kan man enkelt testa att anrop olika API:r.

- Installera valfritt verktyg ovan.

### Utforska enhörnings-API:t
Vi kommer här att fokusera på att *hämta* data från vårt enhörnings-API, alltså att använda oss utav GET-metoden. Återigen - ha API-dokumentationen nära till hands för att se hur det fungerar: [http://unicorns.idioti.se/api.html](http://unicorns.idioti.se/api.html). I Postman/RestClient gör följande:

1. Hämta ut alla enhörningar:
	- I HTML-format
	- I JSON-format
	- I XML-format
2. Hämta ut detaljerat information om en specifik enhörning (valfri):
	- I HTML-format
	- I JSON-format
	- I XML-format

API:t stödjer även fler HTTP-metoder, så som `POST` - för att lägga till en enhörning, `PUT` - för att uppdatera en enhörning och `DELETE` för att ta bort en enhörning. Skulle ni ha sätt någon cool enhörning som ni vill lägga till i databasen går detta utmärkt - men radera eller uppdatera ej de enhörningarna som just nu finns i databasen.

### HTTP-anrop med PHP
Nu är det dags att att göra våra HTTP-anrop genom PHP (och grunden till vår kommande webbapplikation). Detta kan man göra genom PHP:s egna inbyggda funktioner, men det är mycket enklare att använda paket för detta t.ex. [guzzle](https://github.com/guzzle/guzzle) eller [Unirest](http://unirest.io/php.html). I exemplet nedan används *guzzle*:

```php
<?php
require("vendor/autoload.php");

use GuzzleHttp\Client;

// Skapa en HTTP-client
$client = new Client();

// Anropa URL: http://unicorns.idioti.se/
$res = $client->request('GET', 'http://unicorns.idioti.se/');

// Omvandla JSON-svar till datatyper
$data = json_decode($res->getBody());

// @TODO Gör något fantastiskt med vår data!
```

*OBS.* Tänk på att att skapa er composer-fil, och ange de paket som ni använder där!

Mer dokumentation kring paketen hittar ni på deras webbplatser: [guzzle](https://github.com/guzzle/guzzle) eller [Unirest](http://unirest.io/php.html). Nu till lite uppgifter för er:

1. Genom PHP hämta alla enhörningar (i JSON) och skriv ut de på er sida, genom egenskapad HTML-kod.
2. Genom PHP hämta detaljerad information om en enskild enhörning (i JSON) och skriv ut de på er sida, genom egenskapad HTML-kod.

### GUI med Bootstrap
Vi vill ju bytta ett GUI i HTML/CSS för vår webbapplikation. Har ni inte koll på HTML så gå [denna kurs på CodeAcademy](https://www.codecademy.com/learn/web). När ni börjar få koll på HTML så rekomenderar jag att ni använder er utav ett CSS-ramverk för att styla er sida, rekomenderat här är [Bootstrap](http://getbootstrap.com/). På startsidan på [Bootstraps - Getting started](http://getbootstrap.com/)-sida finns flera mallar att utgå från. Bygga nu ett lämpligt GUI för er tjänst - så är ni redo att hoppa till [inlämningsuppgiften](../../Assignments/1/assignment.md) sedan!
