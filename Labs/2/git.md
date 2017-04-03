# Labb 2
I den andra laborationen tittar vi på versionshanteirng med Git och tittar på HTTP + REST. Vi kommer bland annat att bekanta oss med [Git](https://git-scm.com/), [GitHub](https://github.com) och branch-modellen [GitFlow](http://nvie.com/posts/a-successful-git-branching-model/). Vi tar också en titt på verktyget [RESTClient](https://addons.mozilla.org/sv-se/firefox/addon/restclient/) och leker med ett REST-API. Laborationen är uppdelad i följande delar:

1. Versionshantering med Git
	1. Introduktion till Git
	2. Delning av kod med GitHub
	3. Semantisk versionering med GitFlow
2. Introduktion till HTTP och REST
	1. RESTClient
	2. Utforska enhörnings-API:t
	3. HTTP-anrop med PHP
	4. GUI med Bootstrap

## Förberedelser
Inför denna labb ska ni ha **skapat ett konto på Github**, **installerat GitFlow** och **installerat Postman**.

### Skapa ett konto hos Github

Gå in på [Github](https://github.com/) och fyll i registreringsformuläret på förstasidan om du inte redan har ett konto där.

### Installera GitFlow

På den virtuella maskinen installerar du GitFlow genom att skriva

```bash
$ sudo apt-get install git-flow
```

Det går även att installera GitFlow på macOS eller Windows. Installationsanvisningar finns här](https://github.com/nvie/gitflow/wiki/Installation).

### Installera RESTClient

[RESTClient](https://addons.mozilla.org/sv-se/firefox/addon/restclient/) är ett tillägg till Firefox. Öppna upp länken i Firefox på den virtuella maskinen och klicka på knappen "+ Lägg till i Firefox", godkänn installationen och starta om Firefox. RESTClient nås nu genom den röda ikonen i det övre högra hörnet i Firefox (se bild nedan).

![RESTClient i Firefox](restclient.png)

## 1. Versionshantering med Git

GitHub har en enkel [online-guide för Git](https://try.github.io). Testa den innan du går vidare.

Nät du har gått guiden testar vi att börja versionshantera förra veckans bygge med Git. Öppna upp ett terminalfönster och navigera till den kod du skrev förra veckan. Om den ligger i */home/student/testing*, räcker det med att du skriver

```bash
$ cd testing
```

Initiera ett Git-repository genom att skriva

```bash
$ git init
```

Lägg sedan till alla filer (dvs den enda filen...) genom att skriva

```bash
$ git add .
```

Säkerställ att filen är tillagd genom att skriva

```bash
$ git status
```

Skapa sedan en commit och ge den ett vettigt commit-meddelande:

```bash
$ git commit -m "Ett vettigt commit-meddelande"
```

Nu är den aktuella versionen av koden sparad i ditt repository.

### 1.2. Delning av kod med Github

Det fina med Git är att det är ett distribuerat versionshanteringssystem. Det går att skicka repositories mellan olika utvecklare, men i praktiken görs det oftast genom att använda en central repository-tjänst, som exempelvis GitHub.

#### Dela kod på GitHub

Börja med att gå till [GitHub](https://github.com) och skapa ett repository genom att klicka på knappen **Start a project**. Ange ett passande namn, exempelvis *testing*. Lägg inte till några filer, utan klicka direkt på **Create repository**. Det är helt okej att projektet är offentligt, du kan alltid ta bort det senare.

Du får nu ett antal val att göra. Det tredje alternativet (*...or push an existing repository from the command line*) är det vi är ute efter. Kopiera kommandona som finns beskrivna och kör i terminalen från den plats där din Git-hanterade källkod finns:

```bash
$ git remote add origin https://github.com/koddas/testing.git
$ git push -u origin master
```

Observera att *koddas* är Johans användarnamn på GitHub, så du måste byta ut det mot ditt eget. Observera även att *testing.git* är ett namn som beror på vad du valde att ditt projekt skulle heta.

Ditt projekt finns nu på GitHub. Gå in på GitHub och hitta det. Testa att göra några förändringar i din fil och lägg till en extra fil med valfritt innehåll. Skicka sedan upp förändringarna på GitHub.

##### Ge skrivrättigheter till andra personer

Vem som helst kan ta ditt projekt (om det är offentligt) och vidareutveckla det. De kan även föreslå att du använder deras förbättringar genom att skapa en *pull request*. En del personer litar du troligtvis mer på, och dessa kan du ge skrivrättigheter till ditt projekt. Hitta någon eller några av dina medstudenter och lägg till dem som collaborators i ditt projekt. Du gör detta genom att klicka på fliken **Settings** och sedan välja **Collaborators** i menyn. Ange ditt lösenord och gå vidare. Du kan nu lägga till dina betrodda medmänniskor genom att ange deras användarnamn eller e-postadresser. GitHub skickar nu en inbjudan till berörda parter via e-post.

#### Arbeta med existerande projekt på GitHub

Att bidra och vidareutveckla existerande projekt är en viktig del av Git-tanken. Det finns två sätt att göra detta på: genom att *klona* ett existerande projekt, eller genom att *forka* ett existerande projekt.

##### Klona ett projekt

När du klonar ett projekt på GitHub skapar du en lokal kopia av repositoryt på din dator. Om ägaren till repositoryt har angett dig som collaborator kan du använda `git push` för att uppdatera repositoryt med ny kod. Om du inte är en collaborator, kommer du inte att kunna göra detta. Testa att klona ett projekt, exempelvis *Medoo* som vi tittade kort på under förra labben:

```bash
$ git clone https://github.com/catfan/Medoo
```

Säkerställ att projektet klonats genom att skriva

```bash
$ ls
```

Syns projektet i listan har allt gått väl.

##### Forka ett projekt

Att forka ett projekt på GitHub är lite annorlunda mot att klona det. Genom att forka ett projekt, skapas en kopia av projektet på GitHub med dig som ägare. Denna kopia kan du sedan klona ner lokalt som ovan och sedan uppdatera med `git push`. Testa detta genom att gå in på exempelvis [Johans förolämpningsgenerator](https://github.com/koddas/php-web-application) och klicka på knappen **Fork** i det övre högra hörnet. Nu har du tillgång till en egen kopia av projektet på *https://github.com/ditt_användarnamn/php-web-application*. Testa att klona projektet på samma sätt som i föregående avsnitt, göra en förändring i koden och sedan skicka upp den till ditt forkade repo på GitHub igen.

### 1.3. Semantisk versionering med GitFlow

## 2. Introduktion till HTTP och REST
När man arbetar med webben så inkluderar detta ofta att man hanterar data mellan olika källor. I denna labb innebär det att vi kommer att arbeta med data om enhörningar, närmare bestämt med data från det enhörnings-API som ni hittar på följande adress: [http://unicorns.idioti.se/](http://unicorns.idioti.se/). Surfa till sidan om bekanta er med dess uppbyggnad, som egentligen består av två vyer:
- Visa alla enhörningar
- Visa information om en specifik enhörning
Notera vilka URL:r som används för att visa alla enhörningar/information om en specifik enhörning. Ser ni ett mönster?

### 2.1. Postman / RestClient
När man arbetar med API:r så är det bra att ha dokumentation kring det API som man arbetar med. Så att man kan se vilka tjänster som API:t tillhandahåller. I vårt fall finns dokumentation om enhörnings-API:t på denna adress [http://unicorns.idioti.se/api.html](http://unicorns.idioti.se/api.html). Läs igenom detta - och fråga labbhandledaren om oklarheter finns.

När ni satt er in API:t så är det dags att testa API:t! Eftersom det inte är helt enkelt att testa annat än `GET`-metoder från webbläsaren så använder man ofta verktyg till detta. Exempel på sådana verktyg är [`Postman`](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop), som är en app till Chrome och [`RestClient`](https://addons.mozilla.org/sv-se/firefox/addon/restclient/) som är ett addon till Firefox. Genom dessa verktyg kan man enkelt testa att anrop olika API:r.

- Installera valfritt verktyg ovan.

### 2.2. Utforska enhörnings-API:t
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

### 2.3. HTTP-anrop med PHP
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

### 2.4. GUI med Bootstrap
Vi vill ju bytta ett GUI i HTML/CSS för vår webbapplikation. Har ni inte koll på HTML så gå [denna kurs på CodeAcademy](https://www.codecademy.com/learn/web). När ni börjar få koll på HTML så rekomenderar jag att ni använder er utav ett CSS-ramverk för att styla er sida, rekomenderat här är [Bootstrap](http://getbootstrap.com/). På startsidan på [Bootstraps - Getting started](http://getbootstrap.com/)-sida finns flera mallar att utgå från. Bygga nu ett lämpligt GUI för er tjänst - så är ni redo att hoppa till [inlämningsuppgiften](../../Assignments/1/assignment.md) sedan!
