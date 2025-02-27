[![logo](../logo.png)](../docs.md "documentation") 

[H]: ../docs.md        "родитель"
[P]: ../icons/progress.png  "в процессе..."
[S]: ../icons/success.png   "ошибок не обнаружено"
[E]: ../icons/empty.png     "нет данных"

[обновит ещё и собственные запчасти]: get_started.md 
    
[![S]][H] Настройки движка v0.0.1
=================================
Полностью автоматизированы. Вручную ничего настраивать не нужно.  
По сути, настройки движка - это просто кэш, который нужен только для ускорения работы.  

Файл настроек создаётся автоматически при первом запуске движка.  
И включает в себя:  
- списки обнаруженых компиляторов.  
- дефолтные значения управляющих переменных.

Иногда настройки нужно обновить.  
Например, вы установили на машину новую версию Visual Studio, и хотите, 
что бы движок узнал о её существовании.  

Для этого можно просто запустить движок без аргументов:  
```
C:\bat\engine\run.bat
```

Или указать команду `--update`  
```
C:\bat\engine\run.bat --update
```

Если указать команду `--initial`  
```
C:\bat\engine\run.bat --initial
```

Тогда, помимо файла настроек, движок [обновит ещё и собственные запчасти]  
<br/>


Описания файла настроек  
-----------------------

В переменных вида:  
```
set "eDIR_7Z=C:/Program Files/7-Zip" 
set "eDIR_CMAKE=C:/Program Files/CMake/bin" 
set "eDIR_GIT=C:/Program Files/SmartGit/git/bin" 
```
Закэшированы пути к полезным для движка программам.  

Переменные вида:  
```
set "eMINGW_32_VERSIONS=810 730 720" 
set "eMINGW_64_VERSIONS=810 730 720" 
set "eMSVC_32_VERSIONS=2019 2017 2015 2013 2012 2010 2008" 
set "eMSVC_64_VERSIONS=2019 2017 2015 2013 2012 2010 2008" 
```
Хранят списки версий обнаруженных компиляторов.  

В переменных вида:  
```
set "eMINGW_32_LAST=810" 
set "eMINGW_64_LAST=810" 
set "eMSVC_32_LAST=2019" 
set "eMSVC_64_LAST=2019" 
```
Закэшированы версии самых новых компиляторов.  

Так же, обратите внимание на переменные вида:  
```
set "eMINGW810_64=C:\long\workspace\programs\x64\mingw-w64\x86_64-8.1.0-posix-seh-rt_v6-rev0\mingw64\bin" 
```
Такие переменные имеют формат: `{Комилятор}{Версия}_{Битность}={Путь/к/компилятору}`  
В них кэшируются пути к каталогам, которые содержат запускаемый файл компилятора.  

Для VisualStudio:  
```
set "eMSVC2019_64=C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat" 
``` 
Кэшируются пути к батникам, которые настраивают окружение для конкретного компилятора.  

Переменые:  
```
set "eALL_COMPILERS=msvc mingw" 
set "eALL_BUILD_TYPES=debug release" 
set "eALL_ADDRESS_MODELS=32 64" 
set "eALL_RUNTIME_CPPS=dynamic static" 
```
Определяют из каких тэгов может состоять [конфигурация сборки](lang_request.md)

Переменные:  
```
if not defined eCOMPILER_TAG  (set "eCOMPILER_TAG=msvc2019") 
if not defined eBUILD_TYPE    (set "eBUILD_TYPE=release"   ) 
if not defined eADDRESS_MODEL (set "eADDRESS_MODEL=64"     ) 
if not defined eRUNTIME_CPP   (set "eRUNTIME_CPP=dynamic"  ) 
```
Содержат значения тэгов конфигурации, принятые по умолчанию.  
Если пользователь не указал конфигурацию,  
то по умолчанию будет использована конфигурация,  
составленная из этих тэгов.  
<br/>


Форматирование файловых путей  
-----------------------------

Переменные:  
```
set "eDIR_BUILD={DIR_WORKSPACE}\_build\{NAME_PROJECT}" 
set "eDIR_PRODUCT={DIR_WORKSPACE}\_products\{NAME_PROJECT}" 
set "eSUFFIX={COMPILER_TAG}-{BUILD_TYPE}-{ADDRESS_MODEL}-{RUNTIME_CPP}/{TARGET_TYPE}-{TARGET_NAME}" 
```
Задают форматирование путей:  
`eDIR_BUILD` - для каталога сборки.  
`eDIR_PRODUCT` - для каталога с результатами сборки.  
`eSUFFIX` - задаёт разные пути для разных конфигураций сборки.  

Когда осуществляется сборка уже непосредственно конкретной конфигурации,  
и значения всех тэгов известны, то `eSUFFIX` раскрывается в `eEXPANDED_SUFFIX`.  
Который в свою очередь добавляется в конец `eDIR_BUILD` и `eDIR_PRODUCT`.  
Таким образом, сборки разных конфигураций располагаются по разным итоговым путям,  
что позволяет им не смешиться друг с другом.  
<br/>


История изменений 
-----------------

| *ID* |    дата    | время |     ветка      | version |  
|:----:|:----------:|:-----:|:--------------:|:-------:|  
| 0001 | 2025-02-27 | 19:30 | [#1-rep-first] |  0.0.1  |  

*ПРИМЕЧАНИЕ: под version подразумевается версия `project.root`*  

[#1-rep-first]: ../history.md#-v001-rep
