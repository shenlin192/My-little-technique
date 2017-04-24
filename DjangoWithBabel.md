# Documentation on using Django Static Precompiler 2

Before you read this article, please read [Documentation on using Django Static Precompiler 1](https://github.com/shenlin192/myNotes/blob/master/DjangoWithLess.md) first.

Similar to using Less in Django Static Precompiler, you will need to 

1. install a babel compiler 
2. make configurations on `setting.py` file

## Install babel compiler in your computer

`$ npm install -g babel-cli`

Remember the path babel installed. You will need it in the `setting.py` 

`$ npm install -g babel-preset-es2015`

> Out of the box Babel doesn’t do anything. It basically acts like const babel = code => code; by parsing the code and then generating the same code back out again.

You will need to add some plugins for Babel to do anything (they affect the 2nd stage, transformation).

##  Configurations on setting.py

Add the following code into `STATIC_PRECOMPILER_COMPILERS`

```
 ('static_precompiler.compilers.Babel', {
        "executable": "/usr/bin/babel",
        "presets": "es2015",
    }),
```

Example code with less and babel
```
STATIC_PRECOMPILER_COMPILERS = (
    ('static_precompiler.compilers.LESS', {"executable": "/usr/local/bin/lessc"}),
    ('static_precompiler.compilers.Babel', {
        "executable": "/usr/bin/babel",
        "presets": "es2015",
    }),
)
```


## Usage of Babel in Django static precompiler
`<script src="{% static 'js/platform_project_management/page_entreprise/pageEntrepriseB3V2.es6'|compile %}"></script>`

Notice: the extension name needs to be changed into `.es6`

## More information
[babel](https://babeljs.io/)
