# Python Program Framework
### Незамышлённый фреймворк для разработки своих больших и не только, проектов на Python
### Описание:
#### Представляет из себя гибкую и простую структуру файлов и папок. А так же, этот фреймворк имеет систему сборки проекта.

#

### Краткая инструкция по использованию:

#### Хорошо, а как скачать этот ваш фреймворк?

Перейдите в [релизы](https://github.com/LukovDev/Python-Program-Framework/releases) и выберите последний релиз. Там будут архивы (варианты этого фреймворка).

На данный момент, официально фреймворк работает на: **Windows**, **MacOS**.

Разницы между фреймворком под **Windows** и **MacOS** в разработке и работе нет, кроме некоторых нюансов (см. настройку для [macos](#%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0-%D1%81-macos))

#### Окей, вот я скачал, и что дальше?

А дальше, разархивируйте архив и переместите из полученной папки содержимое (все файлы и папки) в другую папку, или переименуйте её так как вам удобнее. Обычно, это название вашего проекта.

Типа так:</br>
![](https://github.com/LukovDev/Python-Program-Framework/assets/103067811/37fdbc7e-59c4-43ae-afae-81db53b3de3e)

#### А потом что?

Теперь, откройте эту папку как папку проекта в редакторе кода.
Все исходные скрипты и коды должны находиться в папке ```src```!</br>
![](https://github.com/LukovDev/Python-Program-Framework/assets/103067811/4d4a4d5a-9812-443f-8dfb-27fb378c8973)

#

### Важно! Проверьте что Python доступен в консоли, запустите файл ```pypi.bat``` в папке проекта (фреймворка), чтобы установить все необходимые библиотеки для работы фреймворка.

#

### Теперь поясню за структуру фреймворка и её работы (Это Важно!)

- Python Program Framework содержит такую структуру:</br>
  - ```build```</br>
  - ```data```</br>
  - ```src```</br>
  - ```build.bat```</br>
  - ```pypi.bat```</br>
  - ```run.bat```</br>

Давайте по порядку.</br>

#

#### Папка ```build```:
Структура этой папки такая:</br>
- ```build```</br>
  - ```tools```</br>
  - ```config.json```</br>
  - ```pypi.txt```</br>

- Папку ```tools``` не трогайте, там всего лишь находится python скрипт сборки вашей программы, и в ней же будут храниться</br>
временные файлы и папки при сборке проекта. Просто игнорируйте эту папку. Пожалуйста.</br>

- Файл ```config.json``` содержит настройки сборки вашей программы в виде JSON файла.</br>
Позже вернёмся к содержимому этого файла.

- Файл ```pypi.txt``` по своему названию говорит всё за себя. Этот файл используется сценарием ```pypi.bat``` для установки всех нужных ```pypi``` библиотек.
Пожалуйста, записывайте название всех отдельно-устанавливаемых библиотек в этот файл.</br>
Это надо, чтобы другой человек смог установить все зависимости для запуска проекта у себя на компьютере.</br>

#### Вернёмся к ранее упомянутому файлу ```config.json``` и разберём его содержимое, и узнаем что за что отвечает.

По умолчанию, его содержимое должно быть примерно таким:</br>
```json
{
    "program-name": "Python Program Framework",

    "main-file":    "/src/main.py",

    "data-folder":  "/data/",

    "program-icon": "/data/icons/build-icon.ico",

    "console-disabled": false,

    "pyinstaller-flags": [
        "--onefile", "--log-level WARN"
    ]
}
```

Страшно? Сейчас разберёмся как это настраивать под себя.</br>

- ```"program-name":``` - Это параметр, который хранит текст в двойных кавычках, в которых записано название, которое примет итоговый бинарный файл.
  Ничего сверхъестественного тут нет. Потому что вы сами потом сможете просто напросто переименовать итоговый бинарный файл. Это сделано для удобства!</br>

- ```"main-file":``` - Это очень важный параметр. Он хранит путь в двойных кавычках до основного запускаемого файла вашей программы.
  Он нужен чтобы система сборки поняла, какой файл является основным, и какой файл будет запускаться первым при запуске бинарника.</br>

- ```"data-folder":``` - Просто указывает путь в двойных кавычках до папки в которой вы храните данные программы. Система сборки просто скопирует эту папку
  в папку ```out``` которая появится в основной папке ```build``` после окончания сборки.</br>

- ```"program-icon":``` - Параметр, который хранит путь до иконки бинарного файла с расширением ```.ico```. Путь указывается в двойных кавычках, и обычно,
  иконка программы хранится в папке ```/data/```, вместе с другими файлами программы.</br>

- ```"console-disabled":``` - Параметр, который указывает системе сборки, выключить ли окно консоли программы при запуске бинарного файла, или нет.
  Важно! Если ваша программа использует консольные команты по типу ```os.system("какая то команда")```, то окно консоли может появляться на несколько миллисекунд!</br>
  ```true``` = Отключить консольное окно.</br>
  ```false``` = Оставить консольное окно.</br>

- ```"pyinstaller-flags":``` - Это список дополнительных флагов при компиляции программы. Эти флаги встраиваются в основную команду компиляции программы,
  и вы можете вписать сюда что то своё. Например, ```"--onefile"``` и ```"--log-level WARN"``` это команды которые будут отдельно добавлены в ход компиляции.</br>
  ```--onefile``` - Сделает так, чтобы все файлы программы были в одном исполняемом файле (не касается файлов которые будут загружаться отдельно в программе).</br>
  ```--log-level``` - Устанавливает уровень логирования сборки.</br>
  Всего есть вот столько уровней: ```TRACE, DEBUG, INFO, WARN, ERROR, FATAL```</br>
  Каждые из них, указывают, какие сообщения выводить во время компиляции.</br>
  ```TRACE``` - Выводит абсолютно все сообщения и действия компилятора.</br>
  ```DEBUG``` - Выводит отладочные сообщения.</br>
  ```INFO``` - Выводит информационные сообщения компилятора.</br>
  ```WARN``` - Выводит предупреждения при компиляции.</br>
  ```ERROR``` - Выводит ошибки при компиляции.</br>
  ```FATAL``` - Выводит фатальные ошибки, при которых продолжать компиляцию невозможно.</br>

Вот и всё! Вы сами можете изменить любой из этих параметров под себя!</br>
Тут ничего сложного.</br>

Едем дальше.</br>

#

#### Папка ```data```:

Ну, тут всё просто. Я сделал эту папку как основную папку для хранения всех ресурсов программы.</br>
В этой папке может храниться абсолютно всё, что как-то подгружается программой.</br>
Например, спрайты, иконки, шейдеры, текстуры, модельки и так далее...</br>
Эта папка по умолчанию копируется системой сборки, и размещается в папке ```/build/out/```</br>
Вы можете изменить папку данных программы в конфигурационном файле системы сборки, которое мы обсудили выше.</br>

#

#### Папка ```src```:

Это папка в которой хранятся все файлы с исходным кодом программы.</br>

Структура этой папки такая:</br>
- ```src```</br>
  - ```main.py```</br>

- Файл ```main.py``` - Является основным запускаемым файлом по умолчанию, который вы можете изменить в конфигурационном файле системы сборки.</br>

#

#### Файл ```build.bat```:

Запускает систему сборки проекта.</br>
В папке ```/build/tools/``` создаются всеменные файлы сборки, но после её окончания или ошибки, они удаляются автоматически.
Также, на последнем этапе сборки проекта, после удаления временных файлов, идёт копирование папки ```data``` в папку ```build/out```.
Вообщем, если хотите собрать свою игру в бинарный вид, запустите этот файл.

##### Важно! Во время компиляции проекта, у вас может вывестись предупреждения по типу таких:</br>
![](https://github.com/LukovDev/PyGDF/assets/103067811/3fd15368-edf8-4e53-bc40-71e39d2c6f6b)</br>
Если вы получили такие предупреждения, то просто игнорьте их. Ничего страшного не будет. Это просто предупреждения в библиотеках NumPy и Numba.

##### Весь результат сборки, находится в папке ```build/out```

#

#### Файл ```pypi.bat```:

Устанавливает все используемые внешние библиотеки, которые необходимо установить для запуска проекта из исходного кода.</br>
Этот файл устанавливает все библиотеки из файла ```build/pypi.txt```

##### Важно! Библиотеки будут установлены только если все из них были установлены без ошибок.

#

#### Файл ```run.bat```:

Самый простой файл. Просто запускает файл ```src/main.py``` и ничего другого не делает.</br>

После того, как вы установили все нужные библиотеки для работы фреймворка, и попытаетесь запустить программу, вы должны увидеть что-то типа такого:</br>
![](https://github.com/LukovDev/Python-Program-Framework/assets/103067811/c15bbf89-ac5d-41dc-b2dc-033acba61d00)</br>

#

### Работа с MacOS:

На самом деле большой разницы между фреймворком под **Windows** и **MacOS** нет. Но есть несколько нюансов:</br>
1. После скачивания архива и попытки запустить файлы с расширением ```.command``` (аналог ```.bat``` на windows) может возникнуть такая проблема:</br>
  ![](https://github.com/user-attachments/assets/49c36c50-2d5d-47f6-a1f9-4e335ab5d7f1)</br>
  Чтобы её решить, откройте папку с фреймворком в терминале как показано ниже:</br>
  ![](https://github.com/user-attachments/assets/2b69bbc6-1a98-486b-982a-dbb01e580583)</br>
  В открывшимся терминале введите команду ниже:
  ```bash
  chmod +x build/tools/build.sh build/tools/pypi.sh build/tools/run.sh build.command pypi.command run.command
  ```

2. Для создания графических программ или программ без консоли:
  - Понадобится указать иконку приложения. Для этого вам нужна ваша иконка в формате ```.icns``` (можно сконвертировать в терминале с помощью таких утилит как: ```sips```, ```ImageMagick``` или в онлайн конверторах).
  - Обязательно укажите новую иконку в конфигурации сборки (```config.json```) по типу: ```"program-icon": "data/icons/build-icon.icns```

#

### Вот и всё. Вы только что прошли краткое обучение о структуре и использовании этого фреймворка.

#

### Связь со мной:
#### [Telegram](https://t.me/mr_lukov)
