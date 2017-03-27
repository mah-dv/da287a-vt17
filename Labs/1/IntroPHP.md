# Labb 1
I den första laborationen ska vi introduceras till php, dels genom CLI (command line interface) och genom webbserver. Tacksamt nog kommer PHP med en webbserver som är menad att använda under utveckling. Laborationen är uppdelad i följande delar:
1. Om PHP
    1. CLI - Första exempel
    2. WEB - Första exempel
    3. Hantera formulärsdata
2. Om composer
    1. Analysera en composer-fil
    2. Skriv en egen composer-fil (manuellt & genom CLI)
    3. Skriv ett mindre program m.h.a. composer

## Förberedelser
Inför denna labb ska ni ha **installerat PHP, apache och mysql**. Detta kan ni antingen göra genom:
1. [Johans image](#) för [VM VirtualBox](https://www.virtualbox.org/) (rekommenderat)
2. Genom Xampp för Windows/Mac OS X.

Johans image är rekommenderad då han kommer att supporta detta, då det innebär att alla har samma miljö. Dessutom kommer det krävas senare i kursen, gällande testning & deployment.

## 1. Om PHP
I denna del ska vi introduceras till språket PHP. Vi kommer titta på hur man kommer igång, samt skriver ett litet program i PHP.

### 1.1. CLI - Första exempel
Här ska vi bygga ett litet program som välkomnar användaren, och komplementerar användarens namn. För att köra en PHP-fil i CLI så skriver man följande:
```php filename```
Alltså, för att köra filen `index.php` så skriver man:
```php index.php```

##### Övning: Hello World i CLI
Nu är det dags för er att köra ert första PHP-skript!
- Skapa en PHP-fil vid namn "helloWorld.php"
- Skriv PHP-kod för att skriva ut strängen _"hello world"_
- Kör filen i CLI genom `php helloWorld.php`

#### 1.2. Argument i CLI
Vill man sedan skicka med argument när man kör PHP-skriptet så gör man detta genom mellanslag efter filnamnet, t.ex. om jag vill skicka med _"hejsan"_ & _"hoppsan"_ som argument till filen `index.php` så skriver man:
```php index.php hejsan hoppsan```
För att fånga upp dessa parametrarna i PHP så använder man sig utan variabeln [`$argv`](http://php.net/manual/en/reserved.variables.argv.php) som är en array innehållandes de argument som skickas med genom CLI. Exempel:
- Genom CLI: ```php index.php hejsan hoppsan```
- I PHP:
  ```php
  <?php
  var_dump($argv);
  ````
  Ger följande utskrift:
  ```php
  array(3) {
  [0]=>
  string(9) "index.php"
  [1]=>
  string(6) "hejsan"
  [2]=>
  string(7) "hoppsan"
  }
  ```

 ##### Övning: Argument i CLI
 Skriv ett skript som välkomnar användare, genom att ta dess namn som en parameter. Följande anrop:
 `php index.php Anton`
 ska ge följande utskrift i CLI:
 ```
 Hello Anton! What a wonderful name!
 ```

 #### 1.3. Hantera formulärsdata
 I denna tredje del ska ni hantera data som skickas från formulär. Ni kommer att få en mall, [som ni laddar ner här](form.html), där det finns ett formulär. Studera detta formulär och identifiera följande:
 - Med vilken metod skickas formuläret?
 - Hur identifierar ni vilka namn som de olika fälten har?
 - Var skickas formulärsdata när formuläret skickas iväg?

När ni svarat på dessa frågor har ni kött på benen att bygga en svarssida, som ska presentera det som skickas iväg med formuläret. Skapa en sida som ser ut som denna:

![Svarssida](response.png)

 Vad händer om ni byter metod till *post* i formuläret? Vad blir skillnaden? Hur hanterar ni detta på er svarssida?
