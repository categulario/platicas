# ¿Qué va y qué no va en un proyecto git?

* .DS_Store
* vendor/
* node_modules/
* requirements.txt
* composer.json
* composer.lock
* Pipfile.lock
* Cargo.toml
* Cargo.lock
* backup-2015-07-18.sql
* bin.exe / a.o
* build/dist
* backup.zip
* model.xlsx, docx, odt, ...
* archive/*.png, pdf, jpg...
* classes_2015-07-14.php
* __pycache__
* *.pyc *.class
* .env
* config.php, settings.py, settings.js

## Cómo hacerlo bien

$ git add -p
$ git add -i
$ git add well/known/file.txt
