# hse_hw1_meth

# Ссылка на гугл колаб
https://colab.research.google.com/drive/10wilXQdO5nGC9V09WWekQS1uaN64PmO_?usp=sharing

# 1 Проведем сравнение отчетов fastqc одного из наших образцов(8 cell) и образца бактерии из одного из прошлых дз  

Общая статистика
>> ![image](https://user-images.githubusercontent.com/65420132/154361139-f3467508-ce3f-4ce7-910d-3f81164afa0d.png)  
>> ![image](https://user-images.githubusercontent.com/65420132/154361306-af7ce620-bfeb-4af4-bc51-4b00e08a61fb.png)
>> Видно, что у нашего образца проуент GC меньше  

Соотношение нуклеотидов
>> ![image](https://user-images.githubusercontent.com/65420132/154363457-a0001a4a-36eb-4059-829a-cd0ee298e5d9.png)
>>![image](https://user-images.githubusercontent.com/65420132/154363481-23cd928f-43d6-44ac-bd05-60297714cc43.png)
>> У бактреии соотношение нуклеотидов друг у другу практически одинаковое, в то время как в нашем образце есть заметное проседание цитозина и избыток тимина. Это может быть связано с тем, что заметилированный цитозин легко превращается в тимин

Распредение GC
>> ![image](https://user-images.githubusercontent.com/65420132/154363873-f39618fb-460f-4b12-a29e-722fb41d6cce.png)
>> ![image](https://user-images.githubusercontent.com/65420132/154363849-3ad64712-c64f-47f4-a385-60d2a105c9db.png)
>> У бактерии фактическое распредение совпадает с теоритечесим и есть один пик GC, в нашем случае мы видим два пика GC

Других существенных отличий не наблюдается. Оба отчета лежат в папке data

# Количество ридов, которые пришлись на каждый целевой регион  

|  | 11347700-11367700 | 40185800-40195800 |
| :---: | :---: | :---: |
| 8 Cell | 1090 | 464 |
| Epiblast | 2328 | 1062 |
| ICM | 1456 | 630 |

# Количество дуплицированных чтений для каждого образца  

|  | duplicated | duplicated % |
| :---: | :---: | :---: |
| 8 Cell | 521904 | 18.31% |
| Epiblast | 205258| 2.92% |
| ICM | 377882 | 9.08% |

# bash-срипт для выполнения дедупликации для всех образцов одновременно
>> Используем ls -1 для получение нужных файлов, далее передаем эти файлы по одному при помощи xargs  
>> ! ls -1 *1_bismark_bt2_pe* | xargs -tI{} deduplicate_bismark  --bam  --paired -o s_{} {}

# Анализ M-bias plot
8 cell  
>>![image](https://user-images.githubusercontent.com/65420132/154369366-d9eb1ffd-a1c6-4824-a34a-a1373ccc5bd8.png)
Epiblast  
>> ![image](https://user-images.githubusercontent.com/65420132/154369479-2d6354e3-9723-488c-b679-cfb2133cb9ad.png)
ICM  
>>![image](https://user-images.githubusercontent.com/65420132/154369523-a52b705c-1f36-4923-9ba6-18baa5ac811f.png)

Видно, что уровень метелирования CpG у певрого образца порядка 40%, у второго вырастает до 77 и затем у последнего падает до 23


