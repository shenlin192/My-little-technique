# Django front-end framework research report
The propose of this report is to record my research results on finding a front-end framewok that could well cooperate with Django.

## Preamble
If we can't figure out how to deploy these front-end frameworks with Django, all the discussions are meaningless. If we can find out at least one framework that works with Django, no matter which one, any of them is much better than jQuery. 

## Why do we need framework
Using pure javascript is like walking on your own feet. You can go anywhere without any constrain, but you will get tired soon and can't go far. jQuery is like a bicycle. You can learn how to ride it in less than a day and it will help you go further with less effort. But it's still not far enough. Frameworks are like cars. It will take you a month or longer to learn to drive. And you may need weeks of time just to be familiar with starting the car. It wouble be difficult at the beginning. Once you overcome those difficulities, all the beautiful scenery in distance are now yours. 

### Reduce the number of requests
#### Example
Image that we have the following code in the Django template. Notice that there is a `intcomma` django filter for the variable `project.sum_reservations`. And then, we want to create a same piece of code dynamically in the browser.  


```
# example 1
<span class="comma-to-space">
    {{ project.sum_reservations|intcomma }}
</span> 
```

If we don't use front-end frameworks, the best solution is to send a request to our server and the server responses a rendered HTML to the browser. But can we finish this task without communication with the server? The answer is no or at least very costly. Because we need to implement the functionality of `intcomma` filter in JavaScript.

On the contraty, with front-end frameworks, variables are decorated by those frameworks' filter. That is to say, variables are decorated in the client side rather than server side. And when we want to create a same `span`, every filter are available for the JavaScript.

#### Conclusion
Front-end frameworks can largely reduce the number of requests and responses between server and client. And therefore improve web performance as well as user experience.

### Reduce the volume of response
#### Example
The following code snippet is the template that will be rendered and then be sent to a browser, each time after a user click on `poser une question` from pageEntreprise. You don't need to completely understand its logic just have a look.

```
# example 2
<li class="media-list">
    {% if superUser %}
    <button data-question-id={{questionData.question.questionId}} class="deleteQuestion isAuthor">
        Hide this question
    </button>
    {% endif %}
    <div class="media-left">
        <img class="media-object" src="{{userPhoto}}" alt="{{userFirstname}}{{userLastname}}">
    </div>
    <div class="media-body">
        <span class="padding-0 margin-bottom-0 font-weight-semibold">
         {{userFirstname}}   
         {{userLastname}}  
        </span>
        <span class="margin-0">{{date|timesince}}</span>
        <br class="visible-xs">
        <div class="rem-12 text-brown content">
            {{content}}
        </div>
        <!-- reply area -->
        <ul class="media-list replies">
            <!-- new reply area -->
            <div class="media btn-reply-container">
                <button href="#" class="btn btn-xs btn-flat btn-reply">Répondre à ce commentaire ...</button>
            </div>
            <li class="media reply reply-area">
                <div class="media-left">
                    <img class="media-object" src="{{userPhoto}}" alt=" {{userFirstname}}   
         {{userLastname}} ">
                </div>
                <div class="media-body">
                    <form class="form-group" data-question-id={{questionId}}>
                        {% csrf_token %}
                        <textarea onkeydown="auto_grow(this)" maxlength="1024" contentEditable name="reply" class="form-control"></textarea>
                        <button type="submit" class="btn btn-sm btn-poster" data-loading-text="Envoi...">Poster</button>
                        <button type="reset" class="btn btn-sm btn-annuler">Annuler</button>
                    </form>
                </div>
            </li>
        </ul>
    </div>
</li>

```

Let's anaylse this example. This time, we will communicate with the server because we need to get the newly created question's `id`, `datatime` and some other information from the database. But that's all we need! A json variable as below is enough, which is 10~100 times smaller than a rendered HTML in our case. 
```
{
    "question":{
        "id": 1,
        "content" "...."
    },
    "user":{
        "name":"...",
    }
    ...
}
```

#### Conclusion
With front-end framework, all `HTML` templates are availabe in the client-side but not the server side. All that we need is communication with a server in the form of JSON. Therefore front-end framework can highly reduce the volume of an HTTP response.

### Reduce possible bugs
#### Example
Read carefully the following example and think about what will this code snippet do.
```
Example 3 
$('.exampleClass').on('click', () => {
    console.log(123)
})
```
Whenever we click on an HTML element with a class attribute "exampleClass", the `console.log(123)` will then be executed. Very easy!?

If that's the answer, then you may be not very familiar with jQuery. 
The code of example 3 will not have any effect to a newly created element with class attribute "exampleClass". There are some solutions but they are out of the target of this article.

With front-end templates, there will not be problems like that as we are not dealing with the HTML element directly but the **data** of the website.  Look at example 4, if we want to creat a new `item`, just add the data in the `items`' array. And whenevery we click on the first `<li>` inside an item, the `function` will be execuded.    
```
Example 4 
 <template v-for="item in items">
    <li v-on:click = "function">{{ item.msg }}</li>
    <li class="divider"></li>
 </template>
```
Moreover, you don't need to worry about things like `$(document).ready()` and other jQuery tricky things.

#### Conclusion
Front-end framework can help us write stable code and avoid possible bugs.

### Improve maintainability
#### Example
** Case 1 **

Please review example 2. This code snippet is for the purpose to create a new question. It's a separated HTML template file that will be rendered and be sent back to the click when a user click on `poser une question`. But in fact, this template alse exists in another HTML file which is used to describe the entire page of pageEntreprise for the first time a client visit our site. Thus, if we want to modify some structure of the layout of `question`, 2 files needed to be changed in our case.

With front-end frameworks, we use only one template as mentioned in the section "Reduce the volume of response". So only one file needs to be changed.

** Case 2 **

Imagine we have the HTML code sturcture as example 5. With Django, if we want to change the  `variable` in JavaScript, 3 jQuery causes are needed in order to find these 3 dispersed elements.

However, with front-end framework, the `variable` is a JavaScript variable rather than a Django varibale. So that we can modify it directly with a cause like `variable=newValue`.
```
# example 5
<div>
    Some where in a page{{ variable }}
</div>
.....

<span>
    Some where else in a page
    {{ variable }}
</span>
......
<section>
    <p>
    Some where else in a page
    {{ variable }}
    </p>
</section>
```
If the variable is repeated 100 times everywhere in the page, then we will need 100 jQuery cause to find out where they are. A better solution is to add 100 times a class to these elements. With front-end framework, all you need is to change the value of the `variable` for once.


** Case 3 **

Front-end frameworks structure the code in different components as shown in the figure below. We can define our JavaScript and StyleSheet in different granularities( global level, root component level, sub component level ... ). And we will not need to centralize `less` anymore. Because the framework has provided you the ability to centralize everything (html, Js, Css...) in all granularities.

![Alt](https://camo.githubusercontent.com/14e5f4477f49cf0fc0d8f228facb17772a0b1025/687474703a2f2f626c6f672e6576616e796f752e6d652f696d616765732f7675652d636f6d706f6e656e742e706e67)

#### Conclusion
Front-end frameworks can largely reduce code redundancy and improve code maintainability.


### Separation of the front-end and back-end
Separation of the front-end and back-end is **not** the tradictional way django does. 
A real separation is: the server (web service provider) provides only APIs and the client (web service consumer) can be a browser, a mobile application, other servers, or even a coffee machine, a car, etc. Whatever techniques the client uses will **not** have **any** effect on the server.

This book may help you understand more.
[Api for dummies] ftp://public.dhe.ibm.com/software/uk/pdf/api-service/WSM14025USEN.pdf ( May at least finish reading the table of content)

