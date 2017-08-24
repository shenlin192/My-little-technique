# Dashboard 
This documentation aims at presenting usage, technology stack and architecure of dashboard.

## Usage
The usage of dashboard includes two parts: local development and server side deployment.

### development

1. Clone this repository
2. Install all the dependencies `npm install`
3. Start the application in localhost `npm start`

If you want to add dependecies, run:
`npm install package-name -S`

If you want to delete or upgrade (e.g. modify the version) an existing package (dependency), the safest way is to delete the entire `node_modules` folder and then run `npm install` again. 

Warning: Do not change the version of any package related to `react-route` unless you know exactly what they are. 

### deployment

1. Build for production `npm run build`
2. Copy and paste the built folder `build` to server under path `\static\dashboard`, and then rename `index.html` to `dashboard.html` 
3. Add the path of the project after build ('/home/utilisateur/hoolders/static/dashboard/build') to `setting.py`'s `TEMPLATES` 

```
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
               #    'django.contrib.auth.context_processors.auth',
        'DIRS': [
            '/home/utilisateur/hoolders/interactive_funding_platform/templates',
            '/home/utilisateur/hoolders/static/dashboard/build',
        ],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

```

## Technology stack
This section willl explain 

### Dependencies
All the dependencies of dashboard is written a `package.json` file. You can find libraries like `Antd`, pugins like `izitoast` and model architecture like `react-redux` in this file. There are more than 30 dependencies used in dashboard.

### [React](https://facebook.github.io/react/)
React is an open-source JavaScript library created and maintained by Facebook for building user interfaces.  It handles the view layer of web pages and altogether with Redux, which handles the models, we can be a MVVM framework. React tries to merge CSS and HTML into JavaScript so a pre-processor called JSX is used. You can organize the code in the level of components with React, which is very helpful for future maintenance and group development. Moreover, the technology of  virtual DOM makes React really fast to re-render a page when the data of a react application is updated.

In short, with React, we can improve development efficiency, make it easier for group development and provide better user experience. 

### [Redux](http://redux.js.org/)
“Redux is a predictable state container for JavaScript apps” as introduced by it’s official site. In our project, Redux plays the role of “Model” in the “React-Redux MVVM” architecture. In another word, Redux is used to manage the status of information in a React application, which also means to manage the communication between different components. 

Following figure is the work flow of React-Redux architecture. React deals with the layout of components and user actions (view layer) and Redux deals with the change of information state underneath (model layer). Store is like a database that contains all the information an application needs. Provider is an interface that makes those store data available to all components. Whenever information (state) in the store changes, components will be re-rendered automatically. If there is any user action that will make change to state, such action will be firstly dispatched to all the Reducers. And then, these Reducers will match the action and make changes to the store accordingly. Once again, since the store is changed, corresponding components will get updated automatically.

![React Redux Architecture](https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/React-redux.png)

The following image is a more detailed illustion of React-Redux architecture. It seperates the concepte of `container` and `component`. In fact, we can consider `container` as a special `component`, which connects a normal `React component` with the `Redux store`. 

<img src="http://i.imgur.com/DUiL9yn.png" width="650">

### [Antd](https://ant.design/docs/react/introduce)

Antd is a React library that contains a set of high quality components for building rich, interactive user interfaces. It’s an open source project maintained by Alibaba Group.


From the usage point of view, the role of Antd in “React-Redux” architecture is somehow similar to the role of Bootstrap in classical “HTML, CSS and JS” technology stack. Because Antd has a very powerful grid system for page layout and provides a large amount of build-in components. Moreover, Antd can better adapt to the development of React application since it aims at React when it was designed.


### Summary
The following figure shows the relationship among React, Redux and Antd. React deals with the view layer, Redux deals with the model layer and Antd provides build-in components to accelerate our development.


## Dashboard Architecture
Dashboard follows the Model–view–viewmodel (MVVM) architectural pattern mentioned above. View layer is managed by React and the model layer is managed by Redux. Based on this MVVM architecture, Antd is used. It provides a powerful Grid system and 
a large amount of rich feature build-in components. The role of `antd` in our `React-Redux` architecture is somehow similar as the role of `bootstrap` in the classical usage of `HTML, CSS, JS, Jquery`.
 
### Component tree of dashboard

![Component tree of dashboard 1](https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/dashboard_architecture_1%20.png)

![Component tree of dashboard 2](https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/dashboard_%20architecture_2.png)

### File sturecture
![File sturecture](https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/oie_sZ5owoJdaMvB.png)
## Appendix

This section shows some example code of dashboard project.

### Store  


### Reducer


### Action


### Compoennt


### Container


