﻿[![logo](../../logo.png)](../../docs.md "documentation") 

[H]: ../../docs.md        "родитель"
[P]: ../../icons/progress.png  "в процессе..."
[S]: ../../icons/success.png   "ошибок не обнаружено"
[E]: ../../icons/empty.png     "нет данных"
    
[![S]][H] Управляющие переменные v0.0.1
=======================================

## Интерфейс управления

|     переменная      |                      значение                    |
|:-------------------:|:------------------------------------------------:|
| eTRACE              | Максимально подробный вывод логов (трассировка)  |
| eDEBUG              | Включает отладочный вывод логов                  |
| eWORKSPACE_SYMPTOMS | Симптомы WorkSpace: `3rd_party;programs;scripts` |
| eDIR_OWNER          | Каталог, откуда изначально был запущен движок    |
| eDIR_WORKSPACE      | Путь к каталогу WorkSpace                        |
| eDIR_VBS_ENGINE     | Каталог Vbs-Engine: `scripts\vbs_engine`         |

## Командная строка

|    переменная       |                      значение                    |
|:-------------------:|:------------------------------------------------:|
| eCOMMAND            | Имя запущенной команды                           |
| eARGUMENT           | Аргумент запущенной команды                      |
| eNAME_PROJECT       | Имя проекта                                      |
| eVERSION            | Версия проекта. например: `1.2.x`                |
| eDIR_SOURCE         | Путь к каталогу с исходниками                    |
| eDIR_BUILD          | Путь к каталогу сборки                           |
| eDIR_PRODUCT        | Каталог, в котором размещаются результаты сборки |
| eDIR_PROJECT        | Зарезервированно для будущего использования      |
| eDIR_CMAKE_LIST     | Каталог, в котором расположен `CMakeLists.txt`   |
| eCONFIGURATIONS     | Список конфигураций, которые нужно собрать       |
| eSUFFIX             | Суффикс файловых путей                           |
| eDEFINES            | Список дефайнов препроцессора                    |
| eEXCLUDE            | Список исключающих масок                         |

## Конфигурация

|    переменная       |                      значение             |     Пример      |
|:-------------------:|:-----------------------------------------:|:---------------:|
| eALL_COMPILERS      | Список используемых компиляторов          | msvc, mingw     |
| eALL_ADDRESS_MODELS | Список доступных адресных моделей         | 32, 64          |
| eALL_BUILD_TYPES    | Список доступных типажей конфигураций     | debug, release  |
| eALL_RUNTIME_CPPS   | Список вариантов линковки с рантаймом с++ | dynamic, static |

|   переменная   |                      значение            |       Пример       |
|:--------------:|:----------------------------------------:|:------------------:|
| eCOMPILER_TAG  | название компилятора с указанием версии  | msvc2019, mingw810 |
| eGROUP_TAG     | Название компилятора без указания версии | msvc, mingw        |
| eADDRESS_MODEL | 32х или 64х битная сборка                | 32, 64             |
| eBUILD_TYPE    | Тип конфигурации: debug или release      | debug, release     |
| eRUNTIME_CPP   | Способ линковки с рантаймом с++          | dynamic, static    |

## Компоненты движка

|    переменная    |                             значение                          |
|:----------------:|:-------------------------------------------------------------:|
| eVBS_VERSION     | Версия движка                                                 |
| eVBS_SETTINGS    | Путь к файлу настроек `_cache/settings_{User}-{Computer}.bat` |
| eDIR_SCRIPTS     | Каталог `scripts`, скрипты и утилиты WorkSpace                |
| eDIR_COMMANDS    | Каталог `scripts/cmd`, утилиты workspace                      |
| eDIR_MINIMALIST  | Каталог `scripts/cmake/minimalist`                            |
| eDIR_BAT_CMAKE   | Каталог `bat/cmake`                                           |
| eDIR_BAT_GIT     | Каталог `bat/git`                                             |
| eDIR_BAT_7Z      | Каталог `bat/7z`                                              |

## Оперативные переменные

|    переменная           |                         значение                    |
|:-----------------------:|:---------------------------------------------------:|
| eLOOP_ITERATOR          | Задаёт режим работы loop.bat                        |
| eINIT_COMPILER          | Используется для инициализации компилятора          |
| eEXPANDED_SUFFIX        | Суффикс после раскрытия                             |
| eEXPAND_VARIABLES       | Список переменных, участвующих в раскрытии суффикса |
| eINCLUDE_CONFIGURATIONS | Список поддерживаемых конфигураций                  |
| eEXCLUDE_CONFIGURATIONS | Список неподдерживаемых конфигураций                |

<br/>


История изменений 
-----------------

| *ID* |    дата    | время |     ветка      | version |  
|:----:|:----------:|:-----:|:--------------:|:-------:|  
| 0001 | 2025-02-27 | 19:30 | [#1-rep-first] |  0.0.1  |  

*ПРИМЕЧАНИЕ: под version подразумевается версия `project.root`*  

[#1-rep-first]: ../../history.md#-v001-rep
