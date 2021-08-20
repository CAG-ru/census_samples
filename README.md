# Russian Census Samples

В данном репозитории представлены результаты подготовки сэмплов на микроданных российских переписей 2002 и 2010 годов.


## Методология сэмплирования

Для подготовки сэмплов используется процедура **двухэтапного систематического сэмплинга**:

- На первом этапе путем систематического сэмплинга отбираются частные домохозяйства, соответствующие выбранному критерию по числу лиц, проживающих в этих домохозяйствах.
- На втором этапе отбираются все индивиды из этих домохозяйств.

Отбор домохозяйств происходит по следующему алгоритму:

1. Исключаются наблюдения, которые касаются временно пребывающих на территории России и лиц из коллективных домохозяйств (по правилу: ***p1_5_institutioncode = -1***). Временно пребывающих в исходных данных: 489 357 наблюдений, лиц из коллективных домохозяйств (включая бездомных): 1 832 386 наблюдений. Остается 141 024 150 наблюдений из 143 345 893 исходных, по которым генерируются сэмплы.

2. К микроданным добавляются добавляются атрибуты по географической привязке: название федерального округа, код федерального округа, название региона, код региона, название муниципального образования, код муниципального образования.

3. Генерируется уникальный идентификатор домохозяйства по комбинации из шести атрибутов: L1_00_1_CensusDistrictNumber, L1_00_2_InstructorsDistrictNumber, L1_00_3_CalculatingDistrictNumber, L1_00_6_LodgementNumber, L1_00_8_HouseholdNumber, N_TersonMO. Значения разделяются пробелами!

4. Выделяется уникальная выборка домохозяйств со следующими атрибутами:

номер домохозяйства - создать как хеш L1_00_1_CensusDistrictNumber, L1_00_2_InstructorsDistrictNumber, L1_00_3_CalculatingDistrictNumber, L1_00_6_LodgementNumber, L1_00_8_HouseholdNumber, N_TersonMO;

федеральный округ (join со словарем ТЕРСОН);

регион (join со словарем ТЕРСОН);

муниципальное образование или городской округ (join со словарем ТЕРСОН);

тип населенного пункта (город/село) (n_1_1_istown);

количество членов в домохозяйстве (p3_2_peoplequantity);

идентификатор домохозяйства.

Происходит последовательное упорядочивание перечня домохозяйств по указанным выше атрибутам (b-g).

Выбирается случайное число от 1 до 10. С шагом, заданным для конкретного муниципального образования (по домохозяйствам, не индивидам), отбираются номера домохозяйств, и далее все индивиды, которые были в этих домохозяйствах.

## Лицензия

MIT license

## Контакты разработчиков

[Центр перспективных управленческих решений](https://cpur.ru/)

Николай Давыдов, [n.davydov@cpur.ru]  
Витовт Копыток, [v.kopytok@cpur.ru]    
Юлия Кузьмина, [y.kuzmina@cpur.ru]  
Сергей Тихонов, [s.tihonov@cpur.ru]

[Российская экономическая школа](https://www.nes.ru/)
