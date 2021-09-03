# Russian Census Samples

В данном репозитории представлены результаты подготовки сэмплов на микроданных российской переписи 2010 года.

Скачать файлы с сэмплами в формате csv можно по ссылкам:
- [Открытый набор]() в виде единого csv-файла (~6.5 Гб);
- [Открытый набор]() в виде csv-файлов, разбитых по федеральным округам (от 300 Мб до 1.7 Гб).
- [Кодбук]() к открытому набору в формате html (можно открыть в любом браузере).

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

4. Выбирается случайное число от 1 до 10. С шагом, заданным для конкретного муниципального образования (по домохозяйствам, не индивидам), отбираются номера домохозяйств, и далее все индивиды, которые были в этих домохозяйствах.

## Лицензия

Ограниченный доступ для участников бета-тестирования.

## Контакты разработчиков

[Центр перспективных управленческих решений](https://cpur.ru/)

Николай Давыдов, [n.davydov@cpur.ru]  
Витовт Копыток, [v.kopytok@cpur.ru]    
Юлия Кузьмина, [y.kuzmina@cpur.ru]  
Сергей Тихонов, [s.tikhonov@cpur.ru]

[Российская экономическая школа](https://www.nes.ru/)
