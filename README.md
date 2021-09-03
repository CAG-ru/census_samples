# Russian Census Samples

В данном репозитории представлены результаты подготовки сэмплов на микроданных российской переписи 2010 года.

Скачать файлы с сэмплами в формате csv можно [по ссылке](https://nc.cloud.cpur.ru/s/eBHwoyiWGyc5ytB). Доступны:
- Открытый сэмпл в виде единого csv-файла (архив: 650 Мб, файл: ~6.5 Гб, ***census_sample_open_2010_full***) или в виде csv-файлов, разбитых по федеральным округам (архив: 650 Мб, файлы: от 300 Мб до 1.7 Гб, ***census_sample_open_2010_parts***). Для того, чтобы скачать архив, нужно перейти по ссылке, ввести пароль и выбрать файл для скачивания. В csv в качестве разделителя исползуется точка с запятой, кодировка - UTF-8. ***Пароль для скачивания выслан отдельно***.
- [Кодбук](кодбук_открытый_сэмпл.html) (***кодбук_открытый_сэмпл***) к открытому 10% сэмплу в формате html (можно открыть в любом браузере).
- [Кодбук](кодбук_продвинтый_сэмпл.html) (***кодбук_продвинутый_сэмпл***) к продвинутому 20% сэмплу в формате html (можно открыть в любом браузере).
- Доступ к 20% сэмплу можно получить только через ВРМ без возможности выгрузить себе. Для этого напишите на v.kopytok@cpur.ru. Состав и значения атрибутов 20% сэмпла можно посмотреть в кодбуке.

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

4. Выбирается случайный старт (диапазон для выбора - от 1 до n, где n зависит от размера сэмпла). С шагом 5 (продвинутый) или 10 (открытый) отбираются номера домохозяйств, и далее все индивиды, которые были в этих домохозяйствах.

## Обратная связь

Любые комментарии, пожелания и замечания по методологии сэмплирования, составу и уровню детализации атрибутов, другим вопросам можно направлять на электронную почту [v.kopytok@cpur.ru] (Витовт Копыток).

## Лицензия

Ограниченный доступ для участников бета-тестирования.

## Контакты разработчиков

[Центр перспективных управленческих решений](https://cpur.ru/)

Николай Давыдов, [n.davydov@cpur.ru]  
Витовт Копыток, [v.kopytok@cpur.ru]    
Юлия Кузьмина, [y.kuzmina@cpur.ru]  
Сергей Тихонов, [s.tikhonov@cpur.ru]

[Российская экономическая школа](https://www.nes.ru/)
