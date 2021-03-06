# Russian Census Samples

![alt text](https://github.com/CAG-ru/census_samples/blob/main/births.png)

В данном репозитории представлены результаты подготовки сэмплов на микроданных российской переписи 2010 года.

Скачать файлы с сэмплами в формате csv и другие материалы можно [по ссылке](https://nc.cloud.cpur.ru/s/eBHwoyiWGyc5ytB). Доступны:

- Открытый сэмпл в виде единого csv-файла (архив: 650 Мб, файл: ~6.5 Гб, ***census_sample_open_2010_full***) или в виде csv-файлов, разбитых по федеральным округам (архив: 650 Мб, файлы: от 300 Мб до 1.7 Гб, ***census_sample_open_2010_parts***). Для того, чтобы скачать архив, нужно перейти по ссылке, ввести пароль и выбрать файл для скачивания. В csv в качестве разделителя исползуется точка с запятой, кодировка - UTF-8. ***Пароль для скачивания выслан отдельно***.
- [Кодбук](кодбук_открытый_сэмпл.html) с описанием атрибутов и методологии (***кодбук_открытый_сэмпл***) к открытому 10% сэмплу в формате html (можно открыть в любом браузере).
- [Кодбук](кодбук_продвинтый_сэмпл.html) с описанием атрибутов и методологии (***кодбук_продвинутый_сэмпл***) к продвинутому 20% сэмплу в формате html (можно открыть в любом браузере).
- Доступ к 20% сэмплу можно получить только через ВРМ без возможности выгрузить данные себе. Для того, чтобы получить доступ, нужно написать на [v.kopytok@cpur.ru] (Витовт Копыток). Состав и значения атрибутов 20% сэмпла можно посмотреть в кодбуке.
- В папке ***Распределения по МО*** размещены файлы, в которых сопоставлены доли наблюдений в открытом сэмпле и полной выборке с микроданными в разрезе:
    + муниципальных образований и числа лиц в домохозяйстве (***mo_c1_05_peoplequantity_share***);
    + муниципальных образований и гендера (***mo_l1_02_gendertype_share***);
    + муниципальных образований и возраста (***mo_l1_03_4_age_share***);
    + муниципальных образований и уровня образования (***mo_l1_08_1_education_share***).

## Методология сэмплирования

Для подготовки сэмплов используется процедура **двухэтапного систематического сэмплинга**:

- На первом этапе путем систематического сэмплинга отбираются частные домохозяйства, соответствующие выбранному критерию по числу лиц, проживающих в этих домохозяйствах.
- На втором этапе отбираются все индивиды из этих домохозяйств.

Отбор домохозяйств происходит по следующему алгоритму:

1. Исключаются наблюдения, которые касаются временно пребывающих на территории России и лиц из коллективных домохозяйств. Временно пребывающих в исходных данных: 489 357 наблюдений, лиц из коллективных домохозяйств (включая бездомных): 1 832 386 наблюдений. Остается 141 024 150 наблюдений из 143 345 893 исходных, по которым генерируются сэмплы.

2. К микроданным добавляются добавляются атрибуты по географической привязке: название федерального округа, код федерального округа, название региона, код региона, название муниципального образования, код муниципального образования.

3. Уникальная выборка домохозяйств последовательно упорядочивается по следующим атрибутам:

- федеральный округ;
- регион;
- муниципальное образование или городской округ;
- тип населенного пункта (город/село);
- количество членов в домохозяйстве;
- идентификатор домохозяйства.

4. Выбирается случайный старт (диапазон для выбора - от 1 до 5 или 10 в зависимости от типа сэмпла). С шагом 5 (продвинутый) или 10 (открытый) отбираются номера домохозяйств, и далее все индивиды, которые проживают и в этих домохозяйствах.

## Атрибуты для родственников

К исходным атрибутам о домохозяйствах и инивидах добавлены атрибуты, характеризующие родство внутри домохозяйств. Они сгенерированы на основе информации, указанной
при ответах на первый вопрос первого переписного листа («Первому по порядку члену домохозяйства отметьте 'записан первым'. Остальным членам домохозяйства отметьте, кем он (она) приходится тому, кто записан первым»).

### Разница между приемным и кровным родством

При создании переменных не проводится различий между биологическим и приемным родительством. Только некоторые приемные родители могут быть идентифицированы по данным переписи. Таким образом, их представленность в данных будет меньше относительно их фактического числа среди населения.

### Уже существующие в данных переписи атрибуты
1. Отношение члена домохозяйства к записанному в нем первому члену: l1_01_1_affinitivetype.
2. Порядковый номер супруга: l1_05_3_spousenumber.
3. Порядковый номер одного из родителей: l1_01_2_parentnumber. В комментариях к соответствующей переменной указано «Номер матери (отца)», поэтому можно предполагать, что номер матери будет указан чаще номера отца.

### Методология включения дополнительных атрибутов по родству
* Для идентификации домохозяйств используется сгенерированный уникальный идентификатор i1_00_1_householdid.
* Атрибуты родительства привязываются только внутри домохозяйства. В том случае, если один или оба родителя для ребенка оказывается членами другого домохозяйства в момент переписи, то такие родственная связь не может быть идентифицирована.  
* Для идентификации первого родителя используется переменная l1_01_2_parentnumber, значение которой равно номеру l1_00_9_personnumber. Родитель записывается как мать или как отец (соответственно в переменные c1_00_momloc и c1_01_poploc) согласно его полу из переменной l1_02_gendertype.  
* Второй родитель идентифицируется на основании супружеской связи с первым согласно значению переменной l1_05_3_spousenumber первого родителя. Мать это или отец определяется опять же по полу второго родителя.  
* Переменная c1_02_stepmom содержит информацию о потенциальном некровном материнстве. Используется два критерия: (1) потенциально неподходящий возраст для родительства (для этого вычисляется разница между возрастом матери и ребенка. Если она меньше 15 или больше 69, то такое родительство считается приемным; (2) явное указание на отсутствие у матери детей (в том случае, если числе детей женщины из переменной l2_13_1_childrenquantity  меньше одного, то такое родство считается потенциально приемным). Значение переменной c1_02_stepmom в первом случае равно 1, во втором — 2.  
* Переменная c1_03_steppop содержит информацию о потенциальном некровном отцовстве. Используется два критерия: (1) потенциально неподходящий возраст для родительства (здесь логика вычисления полностью аналогична такой для переменной  c1_02_stepmom); (2) супружеские отношения с матерью (если в качестве родителя указана мать, то ее супруг помечается как потенциально неродной отец). Значение переменной c1_03_steppop в первом случае равно 1, во втором — 2.
* Переменная c1_04_adopted содержит информацию об отсутствия связи с родителем у несовершеннолетних. Она получена в том случае если одновременно (1) ребенок является несовершеннолетним; (2) он не единственный член домохозяйства; (3) нет указания ни на одного родителя. В таком случае мы можем считать, что такой несовершеннолетний не имеет родственной связи с домохозяйством и не связан с ним кровным родством.

## Географическая привязка наблюдений

В переписи для географической привязки используются справочники ТЕРСОН (территориальная единица разработки статистики о населении). При подготовке сэмплов с микроданными используется справочник ТЕРСОН-МО, действующий на момент проведения переписи. Этот справочник имеет множество уровней административного деления. Для генерации сэмпла к исходным данным о коде ТЕРСОН-МО населенного пункта привязавается код ТЕРСОН-МО муниципалитета (совпадает с ОКТМО за 2010 год), код ТЕРСОН-МО региона, код ТЕРСОН-МО федерального округа.

### Объединение малонаселенных муниципалитетов

В исходных микроданных 59 муниципалитетов имеют население менее 5 000 жителей. Эти небольшие муниципалитеты объединяются в пары с их ближайшими географическими соседями-муниципалитетами в том же регионе, имеющих наименьшее число жителей. В переменной g_00_8_mun_combined_names_terson указан код ТЕРСОН-МО (ОКТМО) для всех муниципалитетов; в случае, если муниципалитеты были объединены -- указан код муниципалитета, в котором проживало больше жителей на момент проведения переписи. 

## Обратная связь

Любые комментарии, пожелания и замечания по методологии сэмплирования, составу и уровню детализации атрибутов, другим вопросам можно направлять на электронную почту [v.kopytok@cpur.ru] (Витовт Копыток).

## Лицензия

Ограниченный доступ для участников бета-тестирования. Убедительная просьба не распространять полученные в ходе тестирования данные.

## Контакты разработчиков

[Центр перспективных управленческих решений](https://cpur.ru/)

Николай Давыдов, [n.davydov@cpur.ru]  
Витовт Копыток, [v.kopytok@cpur.ru]    
Юлия Кузьмина, [y.kuzmina@cpur.ru]  
Сергей Тихонов, [s.tikhonov@cpur.ru]

[Российская экономическая школа](https://www.nes.ru/)
