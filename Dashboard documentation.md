# Dashboard 
This documentation aims at presenting usage, technology stack and architecure of dashboard.

## Usage
The usage of dashboard includes two parts: local development and server side deployment.

### development

1. Clone this repository
2. Install all the dependencies `npm install`
3. Start the application in localhost `npm start`

If you want to add dependencies, run:
`npm install package-name -S`

If you want to delete or upgrade (e.g. modify the version) an existing package (dependency), the safest way is to delete the entire `node_modules` folder and then run `npm install` again. 

Warning: Do not change the version of any package related to `react-route` unless you know exactly what they are. 

### deployment

1. Build for production `npm run build`
2. Copy and paste the built folder `build` to server under path `\static\dashboard`, and then rename `index.html` to `dashboard.html` 
3. Add the path of the project after build ('/home/utilisateur/hoolders/static/dashboard/build') to `setting.py`'s `TEMPLATES` 

```python
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
This section will explain the technology stack of the dashboard. The pillar technologies are React, Redux, and Antd, which supports an entire structure of dashboard. Based on these three technologies, almost 30 dependencies are used to build up a dynamic and easy-to-use development environment. 



### [React](https://facebook.github.io/react/)
React is an open-source JavaScript library created and maintained by Facebook for building user interfaces.  It handles the view layer of web pages and altogether with Redux, which handles the models, we can be an MVVM framework. React tries to merge CSS and HTML into JavaScript so a pre-processor called JSX is used. You can organize the code in the level of components with React, which is very helpful for future maintenance and group development. Moreover, the technology of virtual DOM makes React really fast to re-render a page when the data of a react application is updated.

In short, with React, we can improve development efficiency, make it easier for group development and provide better user experience. 

### [Redux](http://redux.js.org/)
“Redux is a predictable state container for JavaScript apps” as introduced by its official site. In our project, Redux plays the role of “Model” in the “React-Redux MVVM” architecture. In another word, Redux is used to manage the status of information in a React application, which also means to manage the communication between different components. 

The following figure is the work flow of React-Redux architecture. React deals with the layout of components and user actions (view layer) and Redux deals with the change of information state underneath (model layer). A store is like a database that contains all the information an application needs. A provider is an interface that makes those store data available to all components. Whenever information (state) in the store changes, components will be re-rendered automatically. If there is any user action that will make the change to state, such action will be firstly dispatched to all the Reducers. And then, these Reducers will match the action and make changes to the store accordingly. Once again, since the store is changed, corresponding components will get updated automatically.

<p align="center">
  <img src="https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/React-redux.png"/>
</p>

The following image is a more detailed illustration of React-Redux architecture. It separates the concept of `container` and `component`. In fact, we can consider `container` as a special `component`, which connects a normal `React component` with the `Redux store`. There will be some example code on the `React-Redux` architecture.

<p align="center">
   <img src="http://i.imgur.com/DUiL9yn.png" width="650">
</p>

### [Antd](https://ant.design/docs/react/introduce)

Antd is a React library that contains a set of high-quality components for building rich, interactive user interfaces. It’s an open source project maintained by Alibaba Group.


From the usage point of view, the role of Antd in “React-Redux” architecture is somehow similar to the role of Bootstrap in classical “HTML, CSS and JS” technology stack. Because Antd has a very powerful grid system for page layout and provides a large amount of build-in components. Moreover, Antd can better adapt to the development of React application since it aims at React when it was designed.


### Pillar technologies
The following figure shows the relationship among React, Redux, and Antd. React deals with the view layer, Redux deals with the model layer and Antd provides build-in components to accelerate our development.

<p align="center">
    <img src="https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/front-end%20summary%202.png">
</p>


### Dependencies
All the dependencies of dashboard is written in a `package.json` file. Dependency is a huge concept including "libirary", "pre-complier", "plugin", "model", "framework", etc. Following is a list of dependencies uesd by dashboard. Do not change the versions of dependencies unless you know exactly what you are doing.

```javascript
"dependencies": {
    "antd": "^2.11.2",
    "axios": "^0.16.2",
    "country-data": "0.0.31",
    "intl": "^1.2.5",
    "izitoast": "^1.1.5",
    "libphonenumber": "0.0.10",
    "libphonenumber-js": "^0.4.19",
    "node-less": "^1.0.0",
    "react": "^15.5.4",
    "react-bootstrap": "^0.31.0",
    "react-dom": "^15.5.4",
    "react-highcharts": "^12.0.0",
    "react-image-fallback": "^5.0.0",
    "react-intl": "^2.3.0",
    "react-intl-universal": "^1.2.1",
    "react-number-format": "^2.0.0-alpha3",
    "react-redux": "^5.0.5",
    "react-router": "^4.1.1",
    "react-router-bootstrap": "^0.24.2",
    "react-router-dom": "^4.1.1",
    "react-slick": "^0.14.11",
    "react-telephone-input": "^4.0.1",
    "react-truncate": "^2.1.4",
    "redux": "^3.6.0",
    "redux-logger": "^3.0.6",
    "redux-promise-middleware": "^4.3.0",
    "redux-thunk": "^2.2.0"
  },
  "devDependencies": {
    "babel-plugin-module-resolver": "^2.7.1",
    "node-sass-chokidar": "0.0.3",
    "npm-run-all": "^4.0.2",
    "react-scripts": "1.0.7"
  },
```



## Dashboard Architecture
Dashboard follows the Model–view–viewmodel (MVVM) architectural pattern mentioned above. View layer is managed by React and the model layer is managed by Redux. Based on this MVVM architecture, Antd is used. It provides a powerful Grid system and a large amount of rich feature build-in components. The role of `antd` in our `React-Redux` architecture is somehow similar to the role of `bootstrap` in the classical usage of `HTML, CSS, JS, Jquery`.
 
### Component tree of dashboard


<p align="center">
    <img src="https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/dashboard_architecture_1%20.png">
</p>

Continue with the profile component above. 

<p align="center">
    <img src="https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/dashboard_%20architecture_2.png">
</p>


### File sturecture

![File sturecture](https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/oie_sZ5owoJdaMvB.png) 

1. Folder `build`
2. Folder `node_modules`
3. Folder `public`
4. Folder `src`
    1. Folder `actions`
    2. Folder `components`
    3. Folder `media`
    4. Folder `reducers`
    5. Folder `translate`
    6. File `index.js`
    7. File `App.js`
    8. File `store.js`
    
5. `package.json`

## Appendix
This section shows some example code of dashboard project.

### Store  


### Reducer


### Action


### Compoennt


### Container


