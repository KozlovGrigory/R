Визуализация персонажей Звездных войн
================
Mine Çetinkaya-Rundel translated by Basil Yakimov

### Взглянем на фрейм starwars.

``` r
glimpse(starwars)
```

    ## Rows: 87
    ## Columns: 14
    ## $ name       <chr> "Luke Skywalker", "C-3PO", "R2-D2", "Darth Vader", "Leia Or~
    ## $ height     <int> 172, 167, 96, 202, 150, 178, 165, 97, 183, 182, 188, 180, 2~
    ## $ mass       <dbl> 77.0, 75.0, 32.0, 136.0, 49.0, 120.0, 75.0, 32.0, 84.0, 77.~
    ## $ hair_color <chr> "blond", NA, NA, "none", "brown", "brown, grey", "brown", N~
    ## $ skin_color <chr> "fair", "gold", "white, blue", "white", "light", "light", "~
    ## $ eye_color  <chr> "blue", "yellow", "red", "yellow", "brown", "blue", "blue",~
    ## $ birth_year <dbl> 19.0, 112.0, 33.0, 41.9, 19.0, 52.0, 47.0, NA, 24.0, 57.0, ~
    ## $ sex        <chr> "male", "none", "none", "male", "female", "male", "female",~
    ## $ gender     <chr> "masculine", "masculine", "masculine", "masculine", "femini~
    ## $ homeworld  <chr> "Tatooine", "Tatooine", "Naboo", "Tatooine", "Alderaan", "T~
    ## $ species    <chr> "Human", "Droid", "Droid", "Human", "Human", "Human", "Huma~
    ## $ films      <list> <"The Empire Strikes Back", "Revenge of the Sith", "Return~
    ## $ vehicles   <list> <"Snowspeeder", "Imperial Speeder Bike">, <>, <>, <>, "Imp~
    ## $ starships  <list> <"X-wing", "Imperial shuttle">, <>, <>, "TIE Advanced x1",~

### Модифицируйте следующий график для замены цвета всех точек на розовый (`"pink"`).

``` r
ggplot(starwars, 
       aes(x = height, y = mass, color = gender, size = birth_year)) +
  geom_point(color = "pink")
```

    ## Warning: Removed 51 rows containing missing values (geom_point).

![](starwars_files/figure-gfm/scatterplot-1.png)<!-- -->

### Добавьте заголовок и подписи к осям и легенде. Раскомментируйте строчки, чтобы увидеть результат.

``` r
ggplot(starwars, 
       aes(x = height, y = mass, color = gender, size = birth_year)) +
  geom_point(color = "pink") +
  labs(
    title = 'Зависимость роста от веса у персонажей вселенной "Звездных войн"',
    x = "Рост, см", 
    y = "Вес, кг",
    )
```

    ## Warning: Removed 51 rows containing missing values (geom_point).

![](starwars_files/figure-gfm/scatterplot-labels-1.png)<!-- -->

### Выберите одну категориальную переменную из набора данных и постройте столбчатый график ее распределения.

(Небольшой фрагмент стартового кода представлен ниже и этот фрагмент
кода не будет исполняться (настройка `eval = FALSE`), поскольку
имеющийся код синтаксически некорректен и не может быть исполнен,
что заблокирует весь документ. Когда вы дополните этот код, замените
настройку фрагмента на `eval = TRUE` либо вообще удалите опцию
`eval`).

``` r
ggplot(starwars, aes(y = homeworld)) +
  geom_bar()
```

![](starwars_files/figure-gfm/barplot-1.png)<!-- -->

### Выберите одну числовую переменную из набора данных и постройте гистограмму ее распределения.

(На сей раз стартового фрагмента кода нет, работайте самостоятельно\!)

``` r
ggplot(starwars, aes(x = height)) + geom_histogram() +
  labs(x = "Рост, см",
      y = "Частота",
      title = 'Зависимость роста от веса у персонажей вселенной "Звездных войн"'
  )
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

    ## Warning: Removed 6 rows containing non-finite values (stat_bin).

![](starwars_files/figure-gfm/histogram-1.png)<!-- -->

### Выберите числовую и категориальную переменные и создайте визуализацию (вы сами выбираете тип\!) отношения между этими переменными. Помимо вашего кода и результата, изложите интерпретацию вашей визуализации.

``` r
ggplot(starwars, aes(x = species, y = height)) +
  geom_point(alpha = 0.5, color = 'darkgreen') + theme(axis.text.x = element_text(angle=90, hjust=1)) + labs(
    x = "Вид",
    y = "Рост, см",
    title = 'Зависимость роста от расы у персонажей вселенной "Звездных войн"'
  )
```

    ## Warning: Removed 6 rows containing missing values (geom_point).

![](starwars_files/figure-gfm/num-cat-1.png)<!-- -->

Наименьшим ростом среди персонажей “Звездных войн” обладают
представители вида Йоды (Yoda’s species), наибольшим -
квермиане (Quermian). Рост расы людей в этой вселенной колеблется
приблизительно от 150 до 200 см.

### Выберите две категориальные переменные и создайте визуализацию отношения между этими переменными. Помимо вашего кода и результата, изложите интерпретацию вашей визуализации.

``` r
ggplot(starwars, aes(x = homeworld, 
                  fill = species)) + theme(axis.text.x = element_text(angle=90, hjust=1)) + geom_bar() + labs(
    x = "Планета",
    y = "Расы",
    title = 'Представленность рас на разных планетах во вселенной "Звездных войн"'
  )
```

![](starwars_files/figure-gfm/cat-cat-1.png)<!-- -->

Наибольшим разнообразием характеризуются планеты Набу (Naboo), Татуин
(Tatooine), Корусант (Coruscant) и Камино (Camino). На остальных
планетах представлено по одной расе персонажей.

### Выберите две числовые и две категориальные переменные и создайте визуализацию, которая включает все эти переменные. Изложите интерпретацию вашей визуализации.

``` r
ggplot(data = starwars, mapping = aes(x = height, y = mass,
                     colour = homeworld,
                     shape = sex)) +
  geom_point() +
  labs(x = "Рост, см", y = "Масса, кг")
```

    ## Warning: Removed 29 rows containing missing values (geom_point).

![](starwars_files/figure-gfm/multi-1.png)<!-- -->

Подавляющее большинство персонажей весит до 250 кг и имеет рост до 250
см. Наиболее высокие персонажи обитают на Камино (Camino) и Кашиике
(Kashyyyk), персонаж с наибольшим весом - на Нал Хатте (Nal Hatta).
Большинство персонажей имеют разделение по половому признаку,
гермафродитом является единственный персонаж с Нал Хатты (Nal
Hatta), бесполые персонажи обитают на Муунилисте (Muunilist) и Трандоше
(Trandosha).
