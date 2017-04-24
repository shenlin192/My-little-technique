# Documentation on using Django Static Precompiler 2

Before you read this article, please read [Documentation on using Django Static Precompiler 1](https://github.com/shenlin192/myNotes/blob/master/DjangoWithLess.md) first.

## Install babel compiler in your computer

`$ npm install -g babel-cli`

`$ npm install -g babel-preset-es2015`

##  Configurations on setting.py

Add the following code into `STATIC_PRECOMPILER_COMPILERS`

```
 ('static_precompiler.compilers.Babel', {
        "executable": "/usr/bin/babel",
        "presets": "es2015",
    }),
```

## Usage of Babel in Django static precompiler
`<script src="{% static 'js/platform_project_management/page_entreprise/pageEntrepriseB3V2.es6'|compile %}"></script>`
