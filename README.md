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
banda_studioQW:996

Было:

```QSP
gt 'dressing_room' 
```

Стало:

```QSP
gt 'zz_pornstudio','dressing_room' 
```

`market_work:545`

Было:
```QSP
gt 'rinwork','start'
```
Стало:
```QSP
gt 'market_work','start'
```
npc_veronika:107

Было:
```QSP
gt 'veronika_ev5'
```
Стало:
```QSP
gt 'npc_veronika','veronika_ev5'
```
npc_veronika:363

Было:
```QSP
gt 'veronika_ev7'
```
Стало:
```QSP
gt 'npc_veronika','veronika_ev7'
```
Natasha_events:37

Было:
```QSP
gs 'Reaction Natasha Gossip'
```
Стало:
```QSP
gs 'Natasha_events','Reaction Natasha Gossip'
```
Natasha_events:38

Было:
```QSP
gs 'Actions talk in Progress'
```
Стало:
```QSP
gs 'Natasha_events','Actions talk in Progress'
```
# 3. Исправления переменных
fn:59

Было:
```QSP
if _tmp_dickkrand >= 99:
```
Стало:
```QSP
if _tmp_dickrand >= 99:
```
fn:67

Было:
```QSP
elseif dickrand >= 25:
```
Стало:
```QSP
elseif _tmp_dickrand >= 25:
```
zz_funcs:491

Было использование:
```QSP
_tmp1_dick - 2 > vagina
```
Исправлено на использование функции:
```QSP
_set_gape_dick
```
То есть логика передана в существующий механизм _set_gape_dick, вместо ошибочной проверки.

zz_pornstudio_films:185

Было:
```QSP
_studio['rating']
```
Стало:
```QSP
studio['rating']
```
shop:215

Было:
```QSP
$_item_count
```
Стало:
```QSP
item_count
```
Исправление применено в двух местах.

casino:908, 978, 979

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
banda_studioQW — ofis

В обработчике ofisdialog1 были два перехода:
```QSP
gt 'ofis'
```
Оба заменены на:
```QSP
gt 'zz_pornstudio','main'
```
Причина: отдельной рабочей ofis в актуальной структуре нет, а zz_pornstudio,'main' является существующим входом в офис.

motherQW — gaptek

Было найдено 3 перехода:
```QSP
gt 'gaptek','start'
```
Все три заменены на:
```QSP
gt 'apteka'
```
Важное уточнение, которое мы подтвердили:

gaptek,'start' соответствует именно apteka, а не apteka,'init'.

# 5. Удаление zz_boys

Локация:

zz_boys

была удалена.

Перед удалением статический анализ показал отсутствие входящих вызовов из других локаций; обнаруженный self-edge не считался внешним входом.

Также не создавались фиктивные _en-локации.

# 6. Удаление "мертвой" ветви блока if-elseif-else

Локация:

sex

Была найдена ветка:
```QSP
elseif picrand >= 77 and picrand <= 80:
    gt 'house'
```
Статический анализ показал, что значения 77..80 для picrand фактически не достигаются.

# 7. Ренейминг переменных

energy -> food

son -> energy

manna -> mood