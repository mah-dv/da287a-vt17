# Introduktion till Lumen

- [Presentation](php-lumen.pdf)

## Dagens exempel

### routes/web.php

```php
<?php

use Illuminate\Http\Request;

$app->get('/', function () use ($app) {
    return "Hello World!";
});

$app->get('/movies', 'MoviesController@index');
$app->get('/movies/{id}', 'MoviesController@show');
$app->post('/movies', 'MoviesController@create');

$app->put('/movies/{id}', function($id){
  return "Will soon update the movie with id: " . $id;
});

$app->delete('/movies/{id}', function($id){
  return "Will soon delete the movie with id: " . $id;
});
```

### app/Http/Controllers/MoviesController.php
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class MoviesController extends Controller
{

  public function index(){
    $movies = json_decode(file_get_contents('../resources/movies.json'));
    return response()->json($movies);
  }

  public function show($id) {
    $movies = json_decode(file_get_contents('../resources/movies.json'));

    foreach ($movies->movies as $movie) {
      if ($id == $movie->id) {
        return response()->json($movie);
      }
    }

    return "No movie found";
  }

  public function create(Request $request){

      $id = $request->input("id");
      $title = $request->input("title");
      $genre = $request->input("genre");
      $grade = $request->input("grade");

      if ($id == NULL or $title == NULL or $genre == NULL or $grade == NULL) {
        return "Missing id, title, genre or grade";
      }

      $movies = json_decode(file_get_contents('../resources/movies.json'), true);

      $movie = [];
      $movie["title"] = $title;
      $movie["genre"] = $genre;
      $movie["grade"] = $grade;
      $movie["id"] = $id;

      $movies["movies"][] = $movie;

      file_put_contents('../resources/movies.json', json_encode($movies));

      return "Movie saved";
  }

}
```

### resources/movies.json

```json
{
    "movies":[
        {
            "id":1,
            "title":"Star Wars",
            "genre":"sci-fi",
            "grade":5
        },
        {
            "id":2,
            "title":"Good will hunting"
            ,"genre":"drama"
            ,"grade":5
        },
        {
            "id":3,
            "title":"Sagan om ringen: Sagan om kungens \u00e5terkomst",
            "genre":"fantasy",
            "grade":5
        }
    ]
}
```
