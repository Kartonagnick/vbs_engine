[![logo](../logo.png)](../docs.md "documentation") 

[H]: ../docs.md        "родитель"
[P]: ../icons/progress.png  "в процессе..."
[S]: ../icons/success.png   "ошибок не обнаружено"
[E]: ../icons/empty.png     "нет данных"

[git]: https://git-scm.com/downloads
[7z]: https://www.7-zip.org
    
[![P]][H] Первая сборка v0.0.1
==============================
1. Для начала нужно [скачать и установить](get_started.md) сам движок.  
   Для примера, пусть он будет установлен в каталог `C:\vbs_engine`  
2. Теперь нам нужен проект, который можно собрать при помощи cmake.  
   Например:  
   ```
   C:\
    |---vbs_engine
     `--example_project
         |--- исходники
          `-- CMakeLists.txt
   ```
3. Заходим в каталог проекта, и добавляем батник `make.bat`  
   ```
   C:\
    |---vbs_engine
     `--example_project
         |--- исходники
         |--- make.bat
          `-- CMakeLists.txt
   ```
4. Содержимое файла `make.bat`  
   ```
   set "eDIR_OWNER=%~dp0."
   set "eDIR_BAT_ENGINE=C:\vbs_engine"
   call "%eDIR_BAT_ENGINE%\run.bat" ^
        "--build: cmake-makefiles"  ^
        "--configurations: all"
   ```
5. Запускаем батник, и наслаждаемся сборкой.  
<br/>

История изменений 
-----------------

| *ID* |    дата    | время |     ветка      | version |  
|:----:|:----------:|:-----:|:--------------:|:-------:|  
| 0001 | 2025-02-27 | 19:30 | [#1-rep-first] |  0.0.1  |  

*ПРИМЕЧАНИЕ: под version подразумевается версия `project.root`*  

[#1-rep-first]: ../history.md#-v001-rep
