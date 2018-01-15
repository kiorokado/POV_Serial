[![AlexGyver YouTube](http://alexgyver.ru/git_banner.jpg)](https://www.youtube.com/channel/UCgtAOyEQdAyjvm9ATCi_Aig?sub_confirmation=1)
# POV писалка - рисовалка с настройкой по UART
* [Описание проекта](#chapter-0)
* [Папки проекта](#chapter-1)
* [Схемы подключения](#chapter-2)
* [Материалы и компоненты](#chapter-3)
* [Как скачать и прошить](#chapter-4)
* [FAQ](#chapter-5)
* [Полезная информация](#chapter-6)

<a id="chapter-0"></a>
## Описание проекта
Простейшая POV рисовалка на 8 светодиодах
- Ввод текста для отрисовки через монитор порта или Bluetooth
- Отрисовка всех символов, латинских и русских букв (все битмапы в памяти)
- Изменение скорости анимации
- Изменение направления анимации
- Включение-выключение зацикленности анимации
- Сохранение настроек в EEPROM
- Отрисовка графики 8 пикселей в высоту и неограниченно в длину
- Подробности в видео: https://youtu.be/hCPOQI-eFYs

<a id="chapter-1"></a>
## Папки
**ВНИМАНИЕ! Если это твой первый опыт работы с Arduino, читай [инструкцию](#chapter-4)**
- **libraries** - библиотеки проекта. Заменить имеющиеся версии
- **POV_display** - прошивка для Arduino, файл в папке открыть в Arduino IDE ([инструкция](#chapter-4))
- **schemes** - схемы

<a id="chapter-2"></a>
## Схемы
![SCHEME](https://github.com/AlexGyver/PCdisplay/blob/master/schemes%26PCBs/scheme_fritzing.png)
![SCHEME](https://github.com/AlexGyver/PCdisplay/blob/master/schemes%26PCBs/scheme_EasyEDA.png)

<a id="chapter-3"></a>
## Материалы и компоненты
* Arduino NANO http://ali.pub/20o35g  http://ali.pub/20o36t
* Дисплей 2004 синий с драйвером http://ali.pub/20o3dt  http://ali.pub/20o3el
* Дисплей 1602 синий с драйвером http://ali.pub/21wqmn http://ali.pub/21wqla
* Драйвер дисплея отдельно http://ali.pub/21wqos
* Дисплеи 1602 БЕЗ ДРАЙВЕРА (купить отдельно):
  - Синий фон, белые буквы http://ali.pub/21wr11
  - Зелёный фон, чёрные буквы http://ali.pub/21wqv7  
  - Чёрный фон, рыжие буквы http://ali.pub/21wr27
  - Чёрный фон, белые буквы http://ali.pub/21wr3y
  - Серый фон, чёрные буквы http://ali.pub/21wrhr
* Провод http://ali.pub/20oa1k  http://ali.pub/20oa3w
* Датчик температуры http://ali.pub/20o3fk  http://ali.pub/20o3gc
* Лента светодиодная http://ali.pub/20o51w  http://ali.pub/20o53u
* Макетная плата http://ali.pub/20o3nj  http://ali.pub/20o3nx
* Клеммники винтовые http://ali.pub/20o3ty
* 10 МОСФЕТов http://ali.pub/20o1yh
* 100 Ом http://ali.pub/20o33b
* 10 кОм http://ali.pub/20o334
* Кнопки ищите на радиорынке, у китайцев можно 500 штук только купить
* Или тут смотрите http://alexgyver.ru/electronics/
* Или такие http://ali.pub/20o4vo
* Корпус http://ali.pub/20ocky  http://ali.pub/20ocpm

РАССЫПУХА В РОССИИ
* Светодиод https://www.chipdip.ru/product/irf3205
* Резистор https://www.chipdip.ru/product/irfz24n
* Кнопка https://www.chipdip.ru/product0/47324

## Вам скорее всего пригодится
* [Всё для пайки (паяльники и примочки)](http://alexgyver.ru/all-for-soldering/)
* [Недорогие инструменты](http://alexgyver.ru/my_instruments/)
* [Все существующие модули и сенсоры Arduino](http://alexgyver.ru/arduino_shop/)
* [Электронные компоненты](http://alexgyver.ru/electronics/)
* [Аккумуляторы и зарядные модули](http://alexgyver.ru/18650/)

<a id="chapter-4"></a>
## Как скачать и прошить
* [Первые шаги с Arduino](http://alexgyver.ru/arduino-first/) - ультра подробная статья по началу работы с Ардуино, ознакомиться первым делом!
* Скачать архив с проектом
> На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Clone or download**, вот её жми, там будет **Download ZIP**
* Установить библиотеки в  
`C:\Program Files (x86)\Arduino\libraries\` (Windows x64)  
`C:\Program Files\Arduino\libraries\` (Windows x86)
* Подключить Ардуино к компьютеру
* Запустить файл прошивки (который имеет расширение .ino)
* Настроить IDE (COM порт, модель Arduino, как в статье выше)
* Настроить что нужно по проекту
* Нажать загрузить
* Пользоваться  
  
**Управление POV рисовалкой через монитор порта или Bluetooth**
* Любой обычный текст (не команда) будет записан в память для отрисовки
* Команда .customNUM, где NUM = 0-7: загрузка символа под номером NUM (пример .custom3)
* Команда .speedVALUE, где VALUE = 0-100 установить скорость анимации (пример .speed40)
* Команда .reverse0 для анимации слева направо и .reverse1 справа налево
* Команла .loop0 отключить зацикливание и .loop1 включить
* Удерживай кнопку при подаче питания, чтобы войти в оффлайн-режим


## Настройки в коде
    #define TRIGGER 12        // пин кнопки запуска анимации
    #define SPACE 2           // интервал между буквами
    #define CUSTOM_AMOUNT 8   // число спецсимволов
    #define BLUETOOTH_MODE 0  // если схема с bluetooth модулем (1 да, 0 нет)

<a id="chapter-5"></a>
## FAQ
### Основные вопросы
В: Как скачать с этого грёбаного сайта?  
О: На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Clone or download**, вот её жми, там будет **Download ZIP**

В: Скачался какой то файл .zip, куда его теперь?  
О: Это архив. Можно открыть стандартными средствами Windows, но думаю у всех на компьютере установлен WinRAR, архив нужно правой кнопкой и извлечь.

В: Я совсем новичок! Что мне делать с Ардуиной, где взять все программы?  
О: Читай и смотри видос http://alexgyver.ru/arduino-first/

В: Компьютер никак не реагирует на подключение Ардуины!  
О: Возможно у тебя зарядный USB кабель, а нужен именно data-кабель, по которому можно данные передавать

В: Ошибка! Скетч не компилируется!  
О: Путь к скетчу не должен содержать кириллицу. Положи его в корень диска.

В: Сколько стоит?  
О: Ничего не продаю.

### Вопросы по этому проекту

<a id="chapter-6"></a>
## Полезная информация
* [Мой сайт](http://alexgyver.ru/)
* [Основной YouTube канал](https://www.youtube.com/channel/UCgtAOyEQdAyjvm9ATCi_Aig?sub_confirmation=1)
* [YouTube канал про Arduino](https://www.youtube.com/channel/UC4axiS76D784-ofoTdo5zOA?sub_confirmation=1)
* [Мои видеоуроки по пайке](https://www.youtube.com/playlist?list=PLOT_HeyBraBuMIwfSYu7kCKXxQGsUKcqR)
* [Мои видеоуроки по Arduino](http://alexgyver.ru/arduino_lessons/)