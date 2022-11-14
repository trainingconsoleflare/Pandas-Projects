# Indexing and Slicing In Pandas

## Indexing And Slicing In Pandas <a href="#indexing-and-slicing-in-pandas" id="indexing-and-slicing-in-pandas"></a>

### Loading Libraries : <a href="#loading-libraries" id="loading-libraries"></a>

In \[1]:

```
import pandas as pd
```

### Loading Dataset : <a href="#loading-dataset" id="loading-dataset"></a>

In \[8]:

```
heroes=pd.read_csv('heroes.csv')
heroes.head()
```

Out\[8]:

|   | sr | name        | Gender | Eye color | Race              | Hair color | Height | Publisher         | Skin color | Alignment | Weight |
| - | -- | ----------- | ------ | --------- | ----------------- | ---------- | ------ | ----------------- | ---------- | --------- | ------ |
| 0 | 0  | A-Bomb      | Male   | yellow    | Human             | No Hair    | 203.0  | Marvel Comics     | -          | good      | 441.0  |
| 1 | 1  | Abe Sapien  | Male   | blue      | Icthyo Sapien     | No Hair    | 191.0  | Dark Horse Comics | blue       | good      | 65.0   |
| 2 | 2  | Abin Sur    | Male   | blue      | Ungaran           | No Hair    | 185.0  | DC Comics         | red        | good      | 90.0   |
| 3 | 3  | Abomination | Male   | green     | Human / Radiation | No Hair    | 203.0  | Marvel Comics     | -          | bad       | 441.0  |
| 4 | 4  | Abraxas     | Male   | blue      | Cosmic Entity     | Black      | -99.0  | Marvel Comics     | -          | bad       | -99.0  |

**We will perform indexing and slicing operation on this Dataset.**

**First we will have to learn how to set and remove indexes.**

## Setting and Remove Indexes : <a href="#setting-and-remove-indexes" id="setting-and-remove-indexes"></a>

### Setting an index : <a href="#setting-an-index" id="setting-an-index"></a>

**pandas allows us to set column as an index. Say , if we want to set 'Publisher' as an index.**

In \[18]:

```
heroes_publisher = heroes.set_index('Publisher')
heroes_publisher.head()
```

Out\[18]:

|                   | sr | name        | Gender | Eye color | Race              | Hair color | Height | Skin color | Alignment | Weight |
| ----------------- | -- | ----------- | ------ | --------- | ----------------- | ---------- | ------ | ---------- | --------- | ------ |
| Publisher         |    |             |        |           |                   |            |        |            |           |        |
| Marvel Comics     | 0  | A-Bomb      | Male   | yellow    | Human             | No Hair    | 203.0  | -          | good      | 441.0  |
| Dark Horse Comics | 1  | Abe Sapien  | Male   | blue      | Icthyo Sapien     | No Hair    | 191.0  | blue       | good      | 65.0   |
| DC Comics         | 2  | Abin Sur    | Male   | blue      | Ungaran           | No Hair    | 185.0  | red        | good      | 90.0   |
| Marvel Comics     | 3  | Abomination | Male   | green     | Human / Radiation | No Hair    | 203.0  | -          | bad       | 441.0  |
| Marvel Comics     | 4  | Abraxas     | Male   | blue      | Cosmic Entity     | Black      | -99.0  | -          | bad       | -99.0  |

### Resetting index to default : <a href="#resetting-index-to-default" id="resetting-index-to-default"></a>

In \[19]:

```
heroes_default = heroes.reset_index()
heroes_default
```

Out\[19]:

|     | index | sr  | name            | Gender | Eye color | Race              | Hair color       | Height | Publisher         | Skin color | Alignment | Weight |
| --- | ----- | --- | --------------- | ------ | --------- | ----------------- | ---------------- | ------ | ----------------- | ---------- | --------- | ------ |
| 0   | 0     | 0   | A-Bomb          | Male   | yellow    | Human             | No Hair          | 203.0  | Marvel Comics     | -          | good      | 441.0  |
| 1   | 1     | 1   | Abe Sapien      | Male   | blue      | Icthyo Sapien     | No Hair          | 191.0  | Dark Horse Comics | blue       | good      | 65.0   |
| 2   | 2     | 2   | Abin Sur        | Male   | blue      | Ungaran           | No Hair          | 185.0  | DC Comics         | red        | good      | 90.0   |
| 3   | 3     | 3   | Abomination     | Male   | green     | Human / Radiation | No Hair          | 203.0  | Marvel Comics     | -          | bad       | 441.0  |
| 4   | 4     | 4   | Abraxas         | Male   | blue      | Cosmic Entity     | Black            | -99.0  | Marvel Comics     | -          | bad       | -99.0  |
| ... | ...   | ... | ...             | ...    | ...       | ...               | ...              | ...    | ...               | ...        | ...       | ...    |
| 729 | 729   | 729 | Yellowjacket II | Female | blue      | Human             | Strawberry Blond | 165.0  | Marvel Comics     | -          | good      | 52.0   |
| 730 | 730   | 730 | Ymir            | Male   | white     | Frost Giant       | No Hair          | 304.8  | Marvel Comics     | white      | good      | -99.0  |
| 731 | 731   | 731 | Yoda            | Male   | brown     | Yoda's species    | White            | 66.0   | George Lucas      | green      | good      | 17.0   |
| 732 | 732   | 732 | Zatanna         | Female | blue      | Human             | Black            | 170.0  | DC Comics         | -          | good      | 57.0   |
| 733 | 733   | 733 | Zoom            | Male   | red       | -                 | Brown            | 185.0  | DC Comics         | -          | bad       | 81.0   |

734 rows × 12 columns

## Reset Index and drop previous index: <a href="#reset-index-and-drop-previous-index" id="reset-index-and-drop-previous-index"></a>

In \[22]:

```
heroes_publisher.reset_index(drop=True)
```

Out\[22]:

|     | sr  | name            | Gender | Eye color | Race              | Hair color       | Height | Skin color | Alignment | Weight |
| --- | --- | --------------- | ------ | --------- | ----------------- | ---------------- | ------ | ---------- | --------- | ------ |
| 0   | 0   | A-Bomb          | Male   | yellow    | Human             | No Hair          | 203.0  | -          | good      | 441.0  |
| 1   | 1   | Abe Sapien      | Male   | blue      | Icthyo Sapien     | No Hair          | 191.0  | blue       | good      | 65.0   |
| 2   | 2   | Abin Sur        | Male   | blue      | Ungaran           | No Hair          | 185.0  | red        | good      | 90.0   |
| 3   | 3   | Abomination     | Male   | green     | Human / Radiation | No Hair          | 203.0  | -          | bad       | 441.0  |
| 4   | 4   | Abraxas         | Male   | blue      | Cosmic Entity     | Black            | -99.0  | -          | bad       | -99.0  |
| ... | ... | ...             | ...    | ...       | ...               | ...              | ...    | ...        | ...       | ...    |
| 729 | 729 | Yellowjacket II | Female | blue      | Human             | Strawberry Blond | 165.0  | -          | good      | 52.0   |
| 730 | 730 | Ymir            | Male   | white     | Frost Giant       | No Hair          | 304.8  | white      | good      | -99.0  |
| 731 | 731 | Yoda            | Male   | brown     | Yoda's species    | White            | 66.0   | green      | good      | 17.0   |
| 732 | 732 | Zatanna         | Female | blue      | Human             | Black            | 170.0  | -          | good      | 57.0   |
| 733 | 733 | Zoom            | Male   | red       | -                 | Brown            | 185.0  | -          | bad       | 81.0   |

734 rows × 10 columns



## Subsetting with .loc\[] <a href="#subsetting-with-.loc-5b-5d" id="subsetting-with-.loc-5b-5d"></a>

**We use .loc\[] over the standard square bracket subsetting because .loc\[] is convenient, easy to read & understand by other developer. Now, we will see the difference between both the subsetting then you will be able to understand how .loc\[] works.**

In \[24]:

```
# Making a list of publishers to subset on
publishers=['Marvel Comics','DC Comics']
# Subset heroes using standard square brackets
heroes[heroes['Publisher'].isin(publishers)]
```

Out\[24]:

|     | sr  | name            | Gender | Eye color | Race              | Hair color       | Height | Publisher     | Skin color | Alignment | Weight |
| --- | --- | --------------- | ------ | --------- | ----------------- | ---------------- | ------ | ------------- | ---------- | --------- | ------ |
| 0   | 0   | A-Bomb          | Male   | yellow    | Human             | No Hair          | 203.0  | Marvel Comics | -          | good      | 441.0  |
| 2   | 2   | Abin Sur        | Male   | blue      | Ungaran           | No Hair          | 185.0  | DC Comics     | red        | good      | 90.0   |
| 3   | 3   | Abomination     | Male   | green     | Human / Radiation | No Hair          | 203.0  | Marvel Comics | -          | bad       | 441.0  |
| 4   | 4   | Abraxas         | Male   | blue      | Cosmic Entity     | Black            | -99.0  | Marvel Comics | -          | bad       | -99.0  |
| 5   | 5   | Absorbing Man   | Male   | blue      | Human             | No Hair          | 193.0  | Marvel Comics | -          | bad       | 122.0  |
| ... | ... | ...             | ...    | ...       | ...               | ...              | ...    | ...           | ...        | ...       | ...    |
| 728 | 728 | Yellowjacket    | Male   | blue      | Human             | Blond            | 183.0  | Marvel Comics | -          | good      | 83.0   |
| 729 | 729 | Yellowjacket II | Female | blue      | Human             | Strawberry Blond | 165.0  | Marvel Comics | -          | good      | 52.0   |
| 730 | 730 | Ymir            | Male   | white     | Frost Giant       | No Hair          | 304.8  | Marvel Comics | white      | good      | -99.0  |
| 732 | 732 | Zatanna         | Female | blue      | Human             | Black            | 170.0  | DC Comics     | -          | good      | 57.0   |
| 733 | 733 | Zoom            | Male   | red       | -                 | Brown            | 185.0  | DC Comics     | -          | bad       | 81.0   |

603 rows × 11 columns

## Using .loc\[] <a href="#using-.loc-5b-5d" id="using-.loc-5b-5d"></a>

In \[28]:

```
heroes_publisher.loc[publishers]
```

Out\[28]:

|               | sr  | name          | Gender | Eye color | Race              | Hair color | Height | Skin color | Alignment | Weight |
| ------------- | --- | ------------- | ------ | --------- | ----------------- | ---------- | ------ | ---------- | --------- | ------ |
| Publisher     |     |               |        |           |                   |            |        |            |           |        |
| Marvel Comics | 0   | A-Bomb        | Male   | yellow    | Human             | No Hair    | 203.0  | -          | good      | 441.0  |
| Marvel Comics | 3   | Abomination   | Male   | green     | Human / Radiation | No Hair    | 203.0  | -          | bad       | 441.0  |
| Marvel Comics | 4   | Abraxas       | Male   | blue      | Cosmic Entity     | Black      | -99.0  | -          | bad       | -99.0  |
| Marvel Comics | 5   | Absorbing Man | Male   | blue      | Human             | No Hair    | 193.0  | -          | bad       | 122.0  |
| Marvel Comics | 8   | Agent 13      | Female | blue      | -                 | Blond      | 173.0  | -          | good      | 61.0   |
| ...           | ... | ...           | ...    | ...       | ...               | ...        | ...    | ...        | ...       | ...    |
| DC Comics     | 715 | Wildfire      | Male   | -         | -                 | -          | -99.0  | -          | good      | -99.0  |
| DC Comics     | 720 | Wonder Girl   | Female | blue      | Demi-God          | Blond      | 165.0  | -          | good      | 51.0   |
| DC Comics     | 722 | Wonder Woman  | Female | blue      | Amazon            | Black      | 183.0  | -          | good      | 74.0   |
| DC Comics     | 732 | Zatanna       | Female | blue      | Human             | Black      | 170.0  | -          | good      | 57.0   |
| DC Comics     | 733 | Zoom          | Male   | red       | -                 | Brown      | 185.0  | -          | bad       | 81.0   |

603 rows × 10 columns

## Setting multi-level indexes <a href="#setting-multi-level-indexes" id="setting-multi-level-indexes"></a>

**Indexes can also be made out of multiple columns, forming a multi-level index (sometimes called a hierarchical index). The benefit is that multi-level indexes make it more natural to reason about nested categorical variables. Let's make multi-index in our data and subset it.**

### Index heroes by Alignment & Publisher <a href="#index-heroes-by-alignment-and-publisher" id="index-heroes-by-alignment-and-publisher"></a>

In \[29]:

```
heroes_multi = heroes.set_index(['Alignment','Publisher'])
heroes_multi.head()
```

Out\[29]:

|                   |               | sr         | name        | Gender | Eye color     | Race              | Hair color | Height | Skin color | Weight |
| ----------------- | ------------- | ---------- | ----------- | ------ | ------------- | ----------------- | ---------- | ------ | ---------- | ------ |
| Alignment         | Publisher     |            |             |        |               |                   |            |        |            |        |
| good              | Marvel Comics | 0          | A-Bomb      | Male   | yellow        | Human             | No Hair    | 203.0  | -          | 441.0  |
| Dark Horse Comics | 1             | Abe Sapien | Male        | blue   | Icthyo Sapien | No Hair           | 191.0      | blue   | 65.0       |        |
| DC Comics         | 2             | Abin Sur   | Male        | blue   | Ungaran       | No Hair           | 185.0      | red    | 90.0       |        |
| bad               | Marvel Comics | 3          | Abomination | Male   | green         | Human / Radiation | No Hair    | 203.0  | -          | 441.0  |
| Marvel Comics     | 4             | Abraxas    | Male        | blue   | Cosmic Entity | Black             | -99.0      | -      | -99.0      |        |

In \[31]:

```
# List of tuples: neutral, Marvel Comics & neutral, DC Comics
rows_to_keep = [('neutral','Marvel Comics'),('neutral','DC Comics')]

# Subset for rows to keep
heroes_multi.loc[rows_to_keep]
```



```
	sr	name	Gender	Eye color	Race	Hair color	Height	Skin color	Weight
```

| neutral       | Marvel Comics | 185             | Copycat | Female | red               | Mutant  | White | 183.0      | blue  | 67.0 |
| ------------- | ------------- | --------------- | ------- | ------ | ----------------- | ------- | ----- | ---------- | ----- | ---- |
| Marvel Comics | 212           | Deadpool        | Male    | brown  | Mutant            | No Hair | 188.0 | -          | 95.0  |      |
| Marvel Comics | 272           | Galactus        | Male    | black  | Cosmic Entity     | Black   | 876.0 | -          | 16.0  |      |
| Marvel Comics | 284           | Gladiator       | Male    | blue   | Strontian         | Blue    | 198.0 | purple     | 268.0 |      |
| Marvel Comics | 373           | Juggernaut      | Male    | blue   | Human             | Red     | 287.0 | -          | 855.0 |      |
| Marvel Comics | 410           | Living Tribunal | -       | blue   | Cosmic Entity     | No Hair | -99.0 | gold       | -99.0 |      |
| Marvel Comics | 503           | One-Above-All   | -       | -      | Cosmic Entity     | -       | -99.0 | -          | -99.0 |      |
| Marvel Comics | 549           | Red Hulk        | Male    | yellow | Human / Radiation | Black   | 213.0 | red        | 630.0 |      |
| Marvel Comics | 574           | Sandman         | Male    | brown  | Human             | Brown   | 185.0 | -          | 203.0 |      |
| Marvel Comics | 585           | Sentry          | Male    | blue   | Mutant            | Blond   | 188.0 | -          | 87.0  |      |
| Marvel Comics | 672           | Toad            | Male    | black  | Mutant            | Brown   | 175.0 | green      | 76.0  |      |
| DC Comics     | 92            | Bizarro         | Male    | black  | Bizarro           | Black   | 191.0 | white      | 155.0 |      |
| DC Comics     | 99            | Black Flash     | Male    | -      | God / Eternal     | -       | -99.0 | -          | -99.0 |      |
| DC Comics     | 151           | Captain Cold    | Male    | brown  | Human             | Brown   | -99.0 | -          | -99.0 |      |
| DC Comics     | 215           | Deathstroke     | Male    | blue   | Human             | White   | 193.0 | -          | 101.0 |      |
| DC Comics     | 245           | Etrigan         | Male    | red    | Demon             | No Hair | 193.0 | yellow     | 203.0 |      |
| DC Comics     | 341           | Indigo          | Female  | -      | Alien             | Purple  | -99.0 | -          | -99.0 |      |
| DC Comics     | 413           | Lobo            | Male    | red    | Czarnian          | Black   | 229.0 | blue-white | 288.0 |      |
| DC Comics     | 427           | Man-Bat         | Male    | brown  | Human             | Brown   | -99.0 | -          | -99.0 |      |
| DC Comics     | 544           | Raven           | Female  | indigo | Human             | Black   | 165.0 | -          | 50.0  |      |
| DC Comics     | 548           | Red Hood        | Male    | blue   | Human             | Black   | 183.0 | -          | 81.0  |      |
| DC Comics     | 567           | Robin VI        | Female  | green  | Human             | Red     | -99.0 | -          | -99.0 |      |
| DC Comics     | 603           | Sinestro        | Male    | black  | Korugaran         | Black   | 201.0 | red        | 92.0  |      |
| DC Comics     | 659           | The Comedian    | Male    | brown  | Human             | Black   | 188.0 | -          | 101.0 |      |

## Slicing index values <a href="#slicing-index-values" id="slicing-index-values"></a>

**Slicing lets you select consecutive elements of an object using first:last syntax. DataFrames can be sliced by index values or by row/column number, we will start with the first case. This involves slicing inside the .loc\[] method.**

In \[33]:

```
heroes_srt=heroes_multi.sort_index()
heroes_srt.head()
```

Out\[33]:

|               |           | sr              | name      | Gender | Eye color     | Race   | Hair color | Height | Skin color | Weight |
| ------------- | --------- | --------------- | --------- | ------ | ------------- | ------ | ---------- | ------ | ---------- | ------ |
| Alignment     | Publisher |                 |           |        |               |        |            |        |            |        |
| -             | DC Comics | 676             | Trickster | Male   | blue          | Human  | Blond      | 183.0  | -          | 81.0   |
| Image Comics  | 426       | Man of Miracles | -         | blue   | God / Eternal | Silver | -99.0      | -      | -99.0      |        |
| Marvel Comics | 33        | Anti-Venom      | Male      | blue   | Symbiote      | Blond  | 229.0      | -      | 358.0      |        |
| Marvel Comics | 110       | Blackwulf       | Male      | red    | Alien         | White  | 188.0      | -      | 88.0       |        |
| Marvel Comics | 692       | Venompool       | Male      | -      | Symbiote      | -      | 226.0      | -      | -99.0      |        |

## Subset rows from 'bad' to 'good' <a href="#subset-rows-from-bad-to-good" id="subset-rows-from-bad-to-good"></a>

In \[34]:

```
heroes_srt.loc['bad':'good']
```

Out\[34]:

|               |               | sr           | name             | Gender | Eye color     | Race    | Hair color | Height | Skin color | Weight |
| ------------- | ------------- | ------------ | ---------------- | ------ | ------------- | ------- | ---------- | ------ | ---------- | ------ |
| **Alignment** | **Publisher** |              |                  |        |               |         |            |        |            |        |
| bad           | DC Comics     | 19           | Amazo            | Male   | red           | Android | -          | 257.0  | -          | 173.0  |
| DC Comics     | 31            | Anti-Monitor | Male             | yellow | God / Eternal | No Hair | 61.0       | -      | -99.0      |        |
| DC Comics     | 48            | Atlas        | Male             | blue   | God / Eternal | Brown   | 198.0      | -      | 126.0      |        |
| DC Comics     | 59            | Bane         | Male             | -      | Human         | -       | 203.0      | -      | 180.0      |        |
| DC Comics     | 80            | Big Barda    | Female           | blue   | New God       | Black   | 188.0      | -      | 135.0      |        |
| ...           | ...           | ...          | ...              | ...    | ...           | ...     | ...        | ...    | ...        | ...    |
| good          | NaN           | 381          | Katniss Everdeen | Female | -             | Human   | -          | -99.0  | -          | -99.0  |
| NaN           | 389           | King Kong    | Male             | yellow | Animal        | Black   | 30.5       | -      | NaN        |        |
| NaN           | 393           | Kool-Aid Man | Male             | black  | -             | No Hair | -99.0      | red    | -99.0      |        |
| NaN           | 542           | Rambo        | Male             | brown  | Human         | Black   | 178.0      | -      | 83.0       |        |
| NaN           | 658           | The Cape     | Male             | -      | -             | -       | -99.0      | -      | -99.0      |        |

```
# heroes_srt.loc[('good','DC Comics'):('neutral','Marvel Comics')]
```

## Subset rows from 'good','DC Comics' to 'neutral','Marvel Comics' <a href="#subset-rows-from-good-dc-comics-to-neutral-marvel-comics" id="subset-rows-from-good-dc-comics-to-neutral-marvel-comics"></a>

```
 heroes_srt.loc[('good','DC Comics'):('neutral','Marvel Comics')]
```

\


## Slicing time series <a href="#slicing-time-series" id="slicing-time-series"></a>

### Subsetting by row/column number <a href="#subsetting-by-row-column-number" id="subsetting-by-row-column-number"></a>

**It is useful to subset rows with their row numbers. This is done with .iloc\[], and like .loc\[] it can take two arguments to let you subset by rows and columns.**

### To get the 5th row and 2nd column Value <a href="#to-get-the-5th-row-and-2nd-column-value" id="to-get-the-5th-row-and-2nd-column-value"></a>

In \[42]:

```
heroes.iloc[4,1]
```

Out\[42]:

```
'Abraxas'
```

![](<.gitbook/assets/image (59).png>)

### To get First 5 Rows <a href="#to-get-first-5-rows" id="to-get-first-5-rows"></a>

In \[43]:

```
heroes.iloc[:5]
```

Out\[43]:

|   | sr | name        | Gender | Eye color | Race              | Hair color | Height | Publisher         | Skin color | Alignment | Weight |
| - | -- | ----------- | ------ | --------- | ----------------- | ---------- | ------ | ----------------- | ---------- | --------- | ------ |
| 0 | 0  | A-Bomb      | Male   | yellow    | Human             | No Hair    | 203.0  | Marvel Comics     | -          | good      | 441.0  |
| 1 | 1  | Abe Sapien  | Male   | blue      | Icthyo Sapien     | No Hair    | 191.0  | Dark Horse Comics | blue       | good      | 65.0   |
| 2 | 2  | Abin Sur    | Male   | blue      | Ungaran           | No Hair    | 185.0  | DC Comics         | red        | good      | 90.0   |
| 3 | 3  | Abomination | Male   | green     | Human / Radiation | No Hair    | 203.0  | Marvel Comics     | -          | bad       | 441.0  |
| 4 | 4  | Abraxas     | Male   | blue      | Cosmic Entity     | Black      | -99.0  | Marvel Comics     | -          | bad       | -99.0  |

## To get All rows of Column 'name','Gender','Eye color': <a href="#to-get-all-rows-of-column-name-gender-eye-color" id="to-get-all-rows-of-column-name-gender-eye-color"></a>

In \[44]:

```
heroes.iloc[:,1:4]
```

Out\[44]:

|     | name            | Gender | Eye color |
| --- | --------------- | ------ | --------- |
| 0   | A-Bomb          | Male   | yellow    |
| 1   | Abe Sapien      | Male   | blue      |
| 2   | Abin Sur        | Male   | blue      |
| 3   | Abomination     | Male   | green     |
| 4   | Abraxas         | Male   | blue      |
| ... | ...             | ...    | ...       |
| 729 | Yellowjacket II | Female | blue      |
| 730 | Ymir            | Male   | white     |
| 731 | Yoda            | Male   | brown     |
| 732 | Zatanna         | Female | blue      |
| 733 | Zoom            | Male   | red       |

734 rows × 3 columns

## To get 10 rows of Column 'name','Gender','Eye color': <a href="#to-get-10-rows-of-column-name-gender-eye-color" id="to-get-10-rows-of-column-name-gender-eye-color"></a>

In \[45]:

```
heroes.iloc[:5,1:4]
```

Out\[45]:

|   | name        | Gender | Eye color |
| - | ----------- | ------ | --------- |
| 0 | A-Bomb      | Male   | yellow    |
| 1 | Abe Sapien  | Male   | blue      |
| 2 | Abin Sur    | Male   | blue      |
| 3 | Abomination | Male   | green     |
| 4 | Abraxas     | Male   | blue      |

![](<.gitbook/assets/image (87).png>)
