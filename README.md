1. ТИТУЛЬНЫЙ ЛИСТ
   АВТОР: Наумов Дмитрий Сергеевич
   ГРУППА: СА-1-25
   ДАТА ВЫПОЛНЕНИЯ: 10.09.2026
   ЦЕЛЬ РАБОТЫ: изучить и освоить перенаправление стандартных потоков ввода/вывода, работу в разных командных интерпритаторах (bash, sh, zsh, fish), создание алиасов и переменных окружения (временных и постоянных), а также объединение команд и конвейеры.
   1.1 Теоретическая справка 
1.11. Стандартные потоки и их перенаправление 
В Linux каждый процесс имеет три стандартных потока: 
stdin (0) – стандартный ввод (обычно клавиатура); 
stdout (1) – стандартный вывод (обычно экран); 
stderr (2) – стандартный вывод ошибок (обычно экран). 
Перенаправление потоков: 
> – перенаправить stdout в файл (перезапись); 
>> – перенаправить stdout в файл (добавление); 
2> – перенаправить stderr; 
&> – перенаправить и stdout, и stderr; 
< – взять stdin из файла; 
1.1.2. Командные интерпретаторы (оболочки) 
bash – наиболее распространённая оболочка (Bourne Again SHell). 
sh – упрощённая оболочка (часто ссылается на dash в Debian/Ubuntu). 
zsh – расширенная оболочка с мощными возможностями автодополнения и настройки. 
fish – «дружественная» оболочка с подсветкой синтаксиса и интерактивностью по 
умолчанию. 
1.1.3. Алиасы (псевдонимы команд) 
Алиас позволяет создать короткое имя для длинной команды. 
Временный – действует только в текущей сессии (alias ll='ls -la'). 
Постоянный – прописывается в конфигурационном файле оболочки (.bashrc, .zshrc, 
config.fish для fish). 
Удаление алиаса – unalias ll. 
1.1.4. Переменные окружения 
Переменные окружения хранят параметры системы и пользовательской среды. 
Локальная переменная – видна только в текущем процессе оболочки: MYVAR=value. 
Переменная окружения – наследуется дочерними процессами: export MYVAR=value. 
2.1. Подготовка 
![sc1](https://github.com/user-attachments/assets/d0bd6998-8d8f-4032-96cf-f3d9b313f234)
проверяем, что текущая оболочка - bash
![sc2](https://github.com/user-attachments/assets/77367860-44d5-48ee-9945-5e7cc4334a7a)
2.2. Перенаправление потоков ввода/вывода 
2.2.1 Создать data.txt через heredoc
![sc3](https://github.com/user-attachments/assets/a4be9e4d-57df-41c2-ae35-2ff67cc40172)
2.2.2 Вывести содержимое
![sc4](https://github.com/user-attachments/assets/1506408a-a87b-4d26-91c0-e6dfef247c7a)
2.2.3 Запишите вывод команды ls -l в файл list.txt
![sc5](https://github.com/user-attachments/assets/f734b897-65cb-433e-b69c-b5c08a56b21a)
2.2.4 Выполните команду ls /nonexistent. Перенаправьте только stdout в out.txt, а 
stderr – в err.txt: 
![sc6](https://github.com/user-attachments/assets/a0d89ac7-8036-4fdc-ab8c-a5304de472f7)
2.2.5 Используя grep, отфильтруйте из data.txt строки, содержащие "a", и запишите 
результат в filtered.txt: 
![sc7](https://github.com/user-attachments/assets/bcc736dd-96bf-4f00-aa38-cd8f0e7eee3d)
2.2.6 Добавить строку в конце файла
![sc8](https://github.com/user-attachments/assets/49222aa4-610c-4f05-8384-92e8c5d549e5)
2.3. Работа с разными интерпретаторами 
2.3.1 Оболочка sh
![sc9](https://github.com/user-attachments/assets/1f3cf4eb-e8ce-4e2c-a87d-8a111b0cdd92)
2.3.2 Оболочка zsh
![sc10](https://github.com/user-attachments/assets/9e6f355c-1c17-4464-a979-0c461fc21efc)
2.3.2.1 Временный Алиас
![sc11](https://github.com/user-attachments/assets/2ff0d454-6150-4380-9fe2-44cf46556616)
2.3.2.2 Переменная окружения
![sc12](https://github.com/user-attachments/assets/ff9cc686-88b4-49e7-807d-3b7134ee182c)
2.3.2.3 Проверка видимости переменной в дочернем bash
![sc13](https://github.com/user-attachments/assets/c4400bd7-b8fe-4583-bba1-660e8cd66dd2)
2.3.3 Оболочка fish
![sc14](https://github.com/user-attachments/assets/0ea9ce7a-03b3-48f1-8bc9-eb0766fbb897)
2.3.3.1 Алиас в fish
![sc15](https://github.com/user-attachments/assets/c8d7d072-6244-4b00-9f33-480678d347f3)
2.3.3.2 Переменная окружения в fish
![sc16](https://github.com/user-attachments/assets/fe9f329a-cc3b-4b04-84d0-365ead9d34b6)
2.3.4 Проверка
![sc17](https://github.com/user-attachments/assets/5e95d72c-a5a2-4c75-9ab9-e967a7bfb70d)
2.3.5 Отчёт:
В fish синтаксис Алиасов и переменных принципиально другой (alias имя 'команда' без =, set -x ИМЯ значение вместо export ИМЯ=значение), тогда как bash/zsh используют POSIX-подобный синтаксис alias имя='команда' и export ИМЯ=значение.
2.4 Объединение команд и конфейеры
2.4.1 Последовательное выполнение через ;
![sc18](https://github.com/user-attachments/assets/61d96348-2d11-4055-b248-669b60af5ece)
2.4.2 && - вторая команда только при успехе первой
![sc19](https://github.com/user-attachments/assets/313439a9-862c-438c-8ff5-37363e76adde)
2.4.3 || - вторая команда только при ошибке первой 
![sc20](https://github.com/user-attachments/assets/1ef86c72-2cb4-47df-bc77-6f90021f186c)
2.4.4 Конвейер из трёх команд
![sc21](https://github.com/user-attachments/assets/e27ef1f6-1870-4106-a7ed-ca239f049d81)
Отчёт: cat /etc/passwd выводит файл grep "/bin/bash" оставляет только строки с Bash-оболочкой у пользователя(cut -d: -f1) - вырезает первое поле(имя пользователя), разделитель :.
2.4.5 Количество процессов пользователя
![sc22](https://github.com/user-attachments/assets/9353af43-f917-4212-8ce7-efd2899a0b56)
Отчёт: число на единицу больше реального, потому что сам процесс grep &USER тоже попадает в список процессов и подсчитывается.
2.5 Временные алиасы
2.5.1 Алиас, показывающий только каталоги
![sc23](https://github.com/user-attachments/assets/99e38b7a-319b-48b6-be75-5736f0c98698)
2.5.2 Выполнить в Lab2
![sc24](https://github.com/user-attachments/assets/a787e155-7443-42e2-82e5-660d9b9ddb51)
2.5.3 Алиас для внешнего ip
![sc25](https://github.com/user-attachments/assets/248da05e-9ee5-4445-adb3-e3a4dbd2e940)
2.5.4 Проверка: закрыть терминал и открыть заново
![sc26](https://github.com/user-attachments/assets/ca16f11a-41fe-4e36-8d26-6fc873c94643)
2.6 Постоянные алиасы
2.6.1 Добавить в конец ~/.bashrc
![sc27](https://github.com/user-attachments/assets/832963bf-19ef-4adf-89de-9f565d88b7d0)
2.6.2 Применить изменения
![sc28](https://github.com/user-attachments/assets/c503b29c-cfaf-4501-8b07-86f7eec2ef3e)
2.6.3 Проверка
![sc29](https://github.com/user-attachments/assets/e866a74b-dcdc-4bf7-af4d-cf6a5b43fdb0)
![sc30](https://github.com/user-attachments/assets/59c3b3ee-7aa9-422b-b9fc-766094768bde)
2.6.4 Для zsh - аналогично в ~/zshrc
![sc31](https://github.com/user-attachments/assets/d7d7b121-62b4-43c9-8079-29cfc6ef9399)
2.6.5 Для fish - в ~/.config/fish/config.fish
![sc32](https://github.com/user-attachments/assets/bfe44fd4-d705-44b8-bd28-00793539b0c5)
2.7 Временные переменные окружения
2.7.1 Локальная переменная
![sc33](https://github.com/user-attachments/assets/8e77a584-df68-4eaf-90d4-39ce6372a38d)
2.7.2 Проверка
![sc34](https://github.com/user-attachments/assets/b1e022c0-1288-4d03-a31f-544f69adca37)
2.7.3 В дочернем Bash переменная не видна (локальная, не экспортирована)
![sc35](https://github.com/user-attachments/assets/9449f6cf-3dad-4973-a80c-f7095241910a)
2.7.4 Экспортируемая переменная
![sc36](https://github.com/user-attachments/assets/5289ed9a-767d-4662-b704-b39b637fd48f)
2.7.5 В дочернем Bash она видна
![sc37](https://github.com/user-attachments/assets/628f0e27-2289-481b-a30f-958c48be991f)
2.7.6 Удалить переменную
![sc38](https://github.com/user-attachments/assets/ba78c8ab-9ff2-46a6-a5a5-9ec951d7b1af)
2.8 Постоянные переменные окружения
2.8.1 Добавить в ~/.bashrc
![sc39](https://github.com/user-attachments/assets/7a9b3c61-359e-421e-b489-94a8c11afc1d)
2.8.2 Применить
![sc40](https://github.com/user-attachments/assets/0b744a68-fc0c-4e63-b316-062e287c9938)
2.8.3 Проверить
![sc41](https://github.com/user-attachments/assets/d8b95ab6-388f-4b1b-a78f-832b8daf73a7)
2.8.4 Добавить еще одну переменную
![sc42](https://github.com/user-attachments/assets/10b494bb-c131-4808-bb8e-9fb891f6395a)
2.8.5 Закрыть, и снова открыть терминал, проверить переменную заново
![sc43](https://github.com/user-attachments/assets/ee692d26-2074-475d-8206-5f9ed1131e9f)
2.9 Комплексный скрипт 
![sc44](https://github.com/user-attachments/assets/aaf511d7-16ae-4295-8782-277229502e88)
2.9.1 Добавлю содержимое скрипта (через режим вставки(i))
![sc45](https://github.com/user-attachments/assets/f7d07fb0-6886-42f7-838f-de295335d061)
2.9.2 Сохраню, выйду, и выполню через bash:
![sc46](https://github.com/user-attachments/assets/c4be19e9-c54a-48bd-a28c-e332d7ff57ee)
теперь Bash:
![sc47](https://github.com/user-attachments/assets/c1d0a147-6662-4100-b17a-a8fff08f4cb3)
4. Ответы на контрольные вопросы:
4.1 > - перезапись, >> - дописывание в конец
4.2 ; - выполняются независимо; && - вторая только при успехе первой.
4.3 команда &> файл (или > файл 2>&1).
4.4 Короткое имя для команды; постоянный - прописать alias в ~/.bashrc/~/.zshrc/config.fish+source.
4.5 export делает переменную видимой дочерним процессам; постоянная - та же строка в ~/.bashrc + source.
4.6 env или printenv.
4.7 | - stdout левой команды становится stdin правой.
4.8 fish: alias ll 'cmd'(без=),set -x ИМЯ значение вместо export.
4.9 Команда < in.txt >our.txt.
>> Выводы: освоены перенаправление потоков ввода/вывода, работа в разных оболочках, создание алиасов и переменных окружения, а также объединение команд и конвейеры.






































