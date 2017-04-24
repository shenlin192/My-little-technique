# Documentation on using Django Static Precompiler 1
There are three main steps to automatically compile less files into css files of our project 
1. Install the less compiler in your machine
2. Install Django Static Precompiler
3. Configuration and usage of Django Static Precompiler

## Install less compiler

### Prerequests

1. The nodejs npm (node package management is needed to install less compiler)
    
    Step 1.1 to 1.2 are obligatory
    
    1.1 `$sudo apt-get install nodejs`
    
    1.2 `$sudo apt-get install npm`
    
    Step 1.3 to 1.6 are recommanded but sometimes optional. They are used to install the lastest stable version of nodejs
    
    1.3 `$sudo npm cache clean -f`
    
    1.4 `$ sudo npm install -g n`
    
    1.5 `$ sudo n stable`
    
    1.6 `$ node -v` 
    
    Step 1.7 is optional but recommended
    
    1.7. link nodejs with node. 
    
    `$ ln -s /usr/bin/nodejs /usr/bin/node`

### Install less
1. `$ npm install -g less`

remember the path you install less compiler. By default it will be "/usr/local/bin/lessc"

This path will be used in your setting.py


## Install Django Static Precompiler

### Prerequest

We neede `pip` to install django-static-precompiler

`/path/to/projectRoot/$ sudo easy_install pip`

### Install django-static-precompiler

`/path/to/projectRoot/$ pip install django-static-precompiler`

## Using Django Static Precompiler
1. Modify the setting.py

    1.1 Add `static_precompiler` to `INSTALLED_APPS` setting.

    1.2 Add `StaticPrecompilerFinder` to `STATICFILES_FINDERS`
    
    ```
    STATICFILES_FINDERS = (
        'django.contrib.staticfiles.finders.FileSystemFinder',
        'django.contrib.staticfiles.finders.AppDirectoriesFinder',
        "static_precompiler.finders.StaticPrecompilerFinder",
    )
    ```
    
    1.3 Specify the path to your less compiler 
    ```
    STATIC_PRECOMPILER_COMPILERS = (
        ('static_precompiler.compilers.LESS', {"executable": "/usr/local/bin/lessc"}),
    )
    ```

2. migrate static_precompiler to database
`$ ./manage.py migrate static_precompiler`

3. Import to view
`from static_precompiler.utils import compile_static`

4. Usage in template 
    ```
    {% load compile_static %}
    {% load static %}
    <link rel="stylesheet" href="{% static "path/to/styles1.less"|compile %}" />
    ```
    
5. You may need to give permission to the static folder (beacause the complied css files will be placed in /static/COMPILED folder by default)

`$ chmod -R 777 static`


## More information

[nodejs](https://nodejs.org/en/download/package-manager/)

[less](http://lesscss.org/)

[django-static-precompiler](http://django-static-precompiler.readthedocs.io/en/stable/)


