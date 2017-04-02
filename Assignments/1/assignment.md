# Inlämningsuppgift 1

## Syfte

Syftet med uppgiften är i stora drag att ni ska:
- Bygga er första webbapplikation (`php`)
- Använda paket genom pakethanterare (`composer`)

Dessutom ska ni förhålla er till de stil-riktlinjer som finns när man skriver PHP-kod. Ni ska följa:
- [PSR-1: Basic Coding Standard](http://www.php-fig.org/psr/psr-1/)
- [PSR-2: Coding Style Guide](http://www.php-fig.org/psr/psr-2/)

## Uppgiften

### Introduktion

Vissa påstår att enhörningar är ett mytologiskt väsen, andra hävdar starkt att de faktiskt är verkliga - och att de finns runt omkring oss. Oavsett vem som har rätt så är det ett väldigt fascinerande djur, vars horn sägs ha magiska krafter, som t.ex. att väcka liv i de döda.

För att sprida information om enhöringar så har vi hittat en data-källa (i form ett API) som tillhandahåller just denna information i `JSON`-format. API:t hittar ni [här](#).

### Webbapplikation

En webbapplikation ska byggas, denna ska ha följande funktionalitet:
- Ett GUI i HTML/CSS där följande vyer ska finnas:
    - Visa alla enhörningar från API:t
    - Visa detaljerad information om en specifik enhörning från API:t
        - I detta fall ska användaren kunna välja vilken enhörning som visas
- Webbapplikationen ska även logga när en användaren besöker någon av vyerna ovan
