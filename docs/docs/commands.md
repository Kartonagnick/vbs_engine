[![logo](../logo.png)](../docs.md "documentation") 

[H]: ../docs.md        "родитель"
[P]: ../icons/progress.png  "в процессе..."
[S]: ../icons/success.png   "ошибок не обнаружено"
[E]: ../icons/empty.png     "нет данных"

[запуск без аргументов]: commands.md#запуск-движка-без-аргументов "обновляет настройки движка" 
[--update]:   commands.md#--update   "обновляет настройки движка"  
[--initial]:  commands.md#--initial  "обновляет настройки и запчасти движка"
[--version]:  commands.md#--version  "печатает в консоль версию движка"
[--clean]:    commands.md#--clean    "удаление MakeFiles для всех указанных конфигураций"
[--generate]: commands.md#--generate "генерирует MakeFiles для всех указанных конфигураций"
[--build]:    commands.md#--build    "выполняет сборку MakeFiles для всех указанных конфигураций"
[--install]:  commands.md#--install  "выполняет исталляцию результатов сборки для всех указанных конфигураций"
[--runTests]: commands.md#--runtests "запускает тесты для указанных конфигураций"
[--custom]:   commands.md#--custom   "запуск произвольного батника"
[--runIDE]:   commands.md#--runide   "запускает IDE"

    
[![P]][H] Cписок поддерживаемых команд v0.0.1
=============================================
Список предустановленных команд:
   1) [запуск без аргументов]  
   2) [--update]  
   3) [--initial]  
   4) [--version]  
   5) [--clean]  
   6) [--generate]  
   7) [--build]  
   8) [--install]  
   9) [--runTests]  
  10) [--custom]  
  11) [--runIDE]  
<br/>  


Запуск движка без аргументов
----------------------------
Обновляет настройки:  
```
C:\bat\engine\run.bat
```
<br/>


--update
--------
Тоже самое, что и запуск без аргументов: обновление настроек.  
```
C:\bat\engine\run.bat --update
```
<br/>


--initial
---------
Обновляет настройки движка, и все его запчасти.  
```
C:\bat\engine\run.bat --initial
```
<br/>


--version
---------
Печатает в консоль версию движка.  
```
C:\bat\engine\run.bat --version
```
<br/>


--clean
-------
Удаляет MakeFile для всех указанных конфигураций.  
```
    call "%eDIR_BAT_ENGINE%\run.bat" ^
        "--clean: all"
```
`АргументКоманды` задает список [конфигураций][4], которые нужно удалить.  
<br/>


--generate
----------
Генерирует MakeFiles для указанных конфигураций:  
```
    call "%eDIR_BAT_ENGINE%\run.bat"      ^
        "--generate: cmake-makefiles"     ^
        "--dir_sources: C:\game"          ^
        "--dir_cmake_list: C:\game\cmake" ^
        "--dir_build:   C:\game\build"    ^
        "--dir_product: C:\game\product"  ^
        "--name_project: "game:"          ^
        "--configurations: all"           ^
        "--defines: STABLE_RELEASE"
```
[Более детальная информация](commands/generate.md)  
<br/>


--build
-------
Сборка MakeFiles для всех указанных конфигураций.  
```
    call "%eDIR_BAT_ENGINE%\run.bat"      ^
        "--build: cmake-makefiles"        ^
        "--dir_sources: C:\game"          ^
        "--dir_cmake_list: C:\game\cmake" ^
        "--dir_build:   C:\game\build"    ^
        "--dir_product: C:\game\product"  ^
        "--name_project: "game:"          ^
        "--configurations: all"           ^
        "--defines: STABLE_RELEASE"
```
[Более детальная информация](commands/build.md)  
<br/>


--install
---------
Инсталяция результатов сборки для всех указанных конфигураций.  
```
    call "%eDIR_BAT_ENGINE%\run.bat"      ^
        "--install: cmake-makefiles"      ^
        "--dir_sources: C:\game"          ^
        "--dir_cmake_list: C:\game\cmake" ^
        "--dir_build:   C:\game\build"    ^
        "--dir_product: C:\game\product"  ^
        "--name_project: "game:"          ^
        "--configurations: all"           ^
        "--defines: STABLE_RELEASE"
```
[Более детальная информация](commands/install.md)  
<br/>


--runTests
----------
Запускает тесты для указанных конфигураций.  
```
    call "%eDIR_BAT_ENGINE%\run.bat"           ^
        "--runTests: *.exe"                    ^
        "--exclude: mingw*-dynamic;msvc2013*"  ^
        "--configurations: all"
```
- `АргументКоманды` Задаёт список [файловых масок][5],  
   определяющих какие тестовые программы нужно запустить.  
   По умолчанию: `*.exe`  

- `exclude` Задаёт список [файловых масок][5], определяющих,  
  какие тестовые программы нужно исключить из запуска.  
  По умолчанию значение не используется.  

`Примечание`  
В корневом каталоге исходного кода может находиться файл [project.root][7]  
В этом файле, в переменных `INCLUDE_CONFIGURATIONS` и `EXCLUDE_CONFIGURATIONS`  
задаются ограничения поддерживаемых конфигураций.  
Итоговый список конфигураций,  
для которых будет произведен запуск тестовых программ,  
формируется с учетом этих ограничений.  


--custom
--------
Запускает произвольное приложение.  
Например: консольную утилиту, или батник.  
```
    call "%eDIR_BAT_ENGINE%\run.bat" ^
        "--custom: имяПриложения"    ^
        "--configurations: конфигурация"
```

- аргумент команды - путь к батнику.  
  - если путь задан относительный,  
    тогда он считается относительным `eDIR_OWNER`.  

- `configurations` Задаёт список [конфигураций][4].  
  По умолчанию используется значение `all`  

<br/>


--runIDE
--------
Запускает указанную IDE.  

Например, Visual Studio:  
```
    call "%eDIR_BAT_ENGINE%\run.bat"  ^
        "--runIDE: VisualStudio"      ^
        "--configurations: %IDE%"
```

Или QtCreator:  
```
    call "%eDIR_BAT_ENGINE%\run.bat"  ^
        "--runIDE: QtCreator"
```

- `АргументКоманды` имя запускаемой IDE.  
- `configurations` здесь указывается одна единственная конфигурация  
  для которой нужно запустить IDE.  
  Указывать нужно все 4ре тэга.  
  
`Примечание`  
При запуске `QtCreator` атрибут `configurations` можно не указывать (он игнорируется).  
<br/>

[1]: reference/symptoms.md#поиск-каталога-исходного-кода "поиск каталога, который содержит опреленные файлы или подкаталоги"  
[2]: reference/symptoms.md#поиск-cmakeliststxt  "поиск каталога, который содержит CMakeLists.txt"  
[3]: settings.md#форматирование-файловых-путей  "настройки движка"  
[4]: reference/request.md                       "формат запроса конфигураций"  
[5]: reference/filemask.md                      "определение файловой маски"  
[6]: customize.md#кастомизация-запуска-cmake    "кастомизация запуска cmake"  
[7]: project_root.md                            "определяет глобальные свойства проекта"
<br/>

История изменений 
-----------------

| *ID* |    дата    | время |     ветка      | version |  
|:----:|:----------:|:-----:|:--------------:|:-------:|  
| 0001 | 2025-02-27 | 19:30 | [#1-rep-first] |  0.0.1  |  

*ПРИМЕЧАНИЕ: под version подразумевается версия `project.root`*  

[#1-rep-first]: ../history.md#-v001-rep
