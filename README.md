# 1. Логические исправления

| Локация                  | Было                                                  | Стало                                                            |
| ------------------------ | ----------------------------------------------------- | ---------------------------------------------------------------- |
| `skk_gym_cardio_zona:11` | `if i ! 1 or i ! 3 or i ! 5:`                         | `if i ! 1 and i ! 3 and i ! 5:`                                  |
| `loadg:244`              | `_old_wardrobe[i] < 2 or _old_wardrobe[i] ! 4 or ...` | цепочка условий исправлена на `and`                              |
| `casino:252`             | `_cs_chi < 0 and _cs_chi > 36`                        | `_cs_chi < 0 or _cs_chi > 36`                                    |
| `casino2:260`            | `_cs_chi < 0 and _cs_chi > 36`                        | `_cs_chi < 0 or _cs_chi > 36`                                    |
| `zz_phone:234`           | `hour <= 8 and hour >= 22`                            | `hour >= 22 or hour <= 8`                                        |
| `zz_family:236`          | некорректный диапазон                                 | `hour >= 18 and hour < 24`                                       |
| `zz_family:240`          | некорректный диапазон                                 | `hour >= 20 and hour < 24`                                       |
| `mixa_event:7`           | некорректная проверка периода                         | `hour >= 16 and hour < 24`                                       |
| `mixa_event:12`          | некорректный диапазон                                 | `hour >= 18 and hour < 24`                                       |
| `mixa_event:18`          | некорректный диапазон                                 | `hour >= 20 and hour < 24`                                       |
| `uni_dorm:138`           | некорректная проверка времени                         | `hour <= 15 or hour >= 23`                                       |
| `grandpa:7`              | некорректная проверка месяцев                         | `month = 5 or month = 9`                                         |
| `zz_school_lesson:256`   | условие было приведено к нужной форме                 | `(args[1] = 2 and args[2] = 6) or (args[1] = 4 and args[2] = 6)` |
| `gevent`                 | `dick-vagina > 10 and <= 7`                           | `dick-vagina >= 7`                                               |
| `gevent`                 | `dick-vagina > 6 and <= 3`                            | `dick-vagina >= 3 and dick-vagina < 6`                           |
| `swamp_yard:411`         | проверка диапазона                                    | `hantersIgorQw >= 20 and hantersIgorQw < 25`                     |
| `grandmahelp:38`         | `hour < 9 and hour > 20:`                             | `(hour < 9 or hour > 20):`                                       |
| `grandmahelp:126`        | `hour < 9 and hour > 20:`                             | `(hour < 9 or hour > 20):`                                       |
| `grandmahelp:204`        | `hour < 9 and hour > 20:`                             | `(hour < 9 or hour > 20):`                                       |

# 2. Исправления GT / GS

| Локация                  | Было                                                  | Стало                                                            |
| ------------------------ | ----------------------------------------------------- | ---------------------------------------------------------------- |
| banda_studioQW:996       | gt 'dressing_room'                                    | gt 'zz_pornstudio','dressing_room'                               |
| market_work:545          | gt 'rinwork','start'                                  | gt 'market_work','start'                                         |
| npc_veronika:107         | gt 'veronika_ev5'                                     | gt 'npc_veronika','veronika_ev5'                                 |
| npc_veronika:363         | gt 'veronika_ev7'                                     | gt 'npc_veronika','veronika_ev7'                                 |
| Natasha_events:37        | gs 'Reaction Natasha Gossip'                          | gs 'Natasha_events','Reaction Natasha Gossip'                    |
| Natasha_events:38        | gs 'Actions talk in Progress'                         | gs 'Natasha_events','Actions talk in Progress'                   |

# 3. Исправления переменных

## fn:59

Было:
```QSP
if _tmp_dickkrand >= 99:
```
Стало:
```QSP
if _tmp_dickrand >= 99:
```
## fn:67

Было:
```QSP
elseif dickrand >= 25:
```
Стало:
```QSP
elseif _tmp_dickrand >= 25:
```
## zz_funcs:491

Было использование:
```QSP
_tmp1_dick - 2 > vagina
```
Исправлено на использование функции:
```QSP
_set_gape_dick
```

## zz_pornstudio_films:185

Было:
```QSP
_studio['rating']
```
Стало:
```QSP
studio['rating']
```
## shop:215

Было:
```QSP
$_item_count
```
Стало:
```QSP
item_count
```
Исправление применено в двух местах.

## casino:908, 978, 979

Было:
```QSP
_cs_dealerCards
```
Стало:
```QSP
_cs_dealerHand
```
Исправлено три места.

# 4. Исправления маршрутизации

| Ссылка на локацию        | Было                                                  | Стало                                                            |
| ------------------------ | ----------------------------------------------------- | ---------------------------------------------------------------- |
| zz_pornstudio            | gt 'ofis'                                             | gt 'zz_pornstudio','main'                                        |
| apteka                   | gt 'gaptek','start'                                   | gt 'apteka'                                                      |
| misha                    | gt 'GarGazel'                                         | gt 'gargazel'                                                    |
| Nudelake                 | gt 'Nudelake'                                         | gt 'nudelake'                                                    |
| Gadhouse                 | gt 'gadhouse'                                         | gt 'Gadhouse'                                                    |
| Bella                    | gt 'bella'                                            | gt 'Bella'                                                       |
| Bordel                   | gt'bordel'                                            | gt 'Bordel'                                                      |
| Meadow                   | gt 'meadow'                                           | gt 'Meadow'                                                      |
| MiroslavaHome            | gt 'miroslavahome'                                    | gt 'MiroslavaHome'                                               |
| Prostitute               | gt'prostitute'                                        | gt 'Prostitute'                                                  |
| vokzalG                  | gt 'vokzalg'                                          | gt 'vokzalG'                                                     |
| DanceWhore               | gs 'dancewhore'                                       | gs 'DanceWhore'                                                  |
| igorhome                 | gt 'igorHome' || gt'igorHome'                         | gt 'igorhome'                                                    |
| Poligon                  | gt 'poligon'                                          | gt 'Poligon'                                                     |
| lake                     | gt 'Lake'                                             | gt 'lake'                                                        |
| lakecafe                 | gt 'Lakecafe'                                         | gt 'lakecafe'                                                    |
| Peterroom                | gt'peterroom'                                         | gt 'Peterroom'                                                   |
| husbSex                  | gt'husbsex                                            | gt 'husbSex'                                                     |

# 5. Удаление неиспользуемых локаций

Локации:
```
zz_boys
_quantize1
OLD_menu_notes
```
были удалены.

Перед удалением статический анализ показал отсутствие входящих вызовов из других локаций; обнаруженный self-edge не считался внешним входом.


# 6. Удаление "мертвой" ветви блока if-elseif-else

Локация:

sex

Была найдена ветка:
```QSP
elseif picrand >= 77 and picrand <= 80:
    gt 'house'
if picrand >= 35 and picrand <= 37:gt'house'

```
Статический анализ показал, что значения 77..80 для picrand фактически не достигаются.

Локация:

npc_veronika:1213

```QSP
	!act 'Смотреть как Ника работает': gt 'hostel_veronika14'
```
удалено

# 7. Ренейминг переменных

energy -> food

son -> energy

manna -> mood

cumfrot -> cumcloth

mop -> makeup

vital -> endurance