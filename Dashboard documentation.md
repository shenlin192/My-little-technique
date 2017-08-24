# Dashboard 

## Usage

### development

1. Clone this repository
2. Install all the dependencies `npm install`
3. Start the application in localhost `npm start`

### deployment

1. Build for production `npm run build`
2. Copy and paste the built folder `build` to server under path `\static\dashboard`, and then rename `index.html` to `dashboard.html` 


## Architecture

Dashboard follows the Model–view–viewmodel (MVVM) architectural pattern. View layer is managed by React and the model layer is 
managed by Redux. Based on this MVVM architecture, a library called Antd is used. It provides a powerful Grid system and 
a large amount of rich feature build-in components. The role of `antd` in our `React-Redux` architecture is somehow similar as the role of
`bootstrap` in the classical usage of `HTML, CSS, JS, Jquery`.
 
### React Redux Architecture

The following image shows how Redux manage communication amount different React components.  

<img src="http://i.imgur.com/DUiL9yn.png" width="650">

Whenever information (state) in the store changes, components will be re-rendered automatically. 
If there is any user action that will make change to state, such action will be firstly dispatched to all the Reducers.
And then, these Reducers will match the action and make changes to the store accordingly. 
Once again, since the store is changed, corresponding components will get updated automatically.

### Antd

Antd is a React library that contains a set of high quality components for building rich, interactive user interfaces. It’s an open source project maintained by Alibaba Group.


From the usage point of view, the role of Antd in “React-Redux” architecture is somehow similar to the role of Bootstrap in classical “HTML, CSS and JS” technology stack. Because Antd has a very powerful grid system for page layout and provides a large amount of build-in components. Moreover, Antd can better adapt to the development of React application since it aims at React when it was designed.


More info about Antd can be found [here](https://ant.design/docs/react/introduce).


### Component Tree
![](https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/dashboard_architecture_1%20.png)
![](https://github.com/shenlin192/myNotes/blob/master/Images/dashboard/dashboard_%20architecture_2.png)
