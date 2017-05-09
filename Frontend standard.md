# Frontend standard

The propose of this standard is to ensure every developper write the frontend code in a way that can 
  - improve code readability
  - imporve code maintainability
  - improve SEO performance
  - reduce code redudency
  - avoid common mistakes

If you know what you are doing exactly, ignore all the standards listed here.
Feel free to modify or add more rules into the standard. 



## HTML

1. never use inline style in HTML tags
2. never use inline js in HTMl tags 
	eg. 

```
// It's not good
 <button id="ImportContactButtonDetail" class="btn" style="color:black;display:none;" onclick='voirDetail()'>
      <span class="glyphicon glyphicon-info-sign"> </span> 
      Détail de chargement vos contacts
 </button>

```
3. Think about to use `<main>`, `<section>` ,`<article>` rather than `<div>` to seperate different parts of the code. It will be much readable if you do so.

## CSS

1. Remember the mobile first princple and never use max-width along in css code! Use `min-width` instead
2. Don't hestate to read HaoWen's charte-graphique
3. Do not write breakpoint randomly. The suggested breakpoints are

  - 0 ~ 480px
  - 480 ~ 768px
  - 768px ~ 998px
  - 998px ~ 1280px
  
4. Do not use 'cm' as CSS style unit
5. Do not use !important if not absolutly necessary.
6. If you are writing a complicated page, do not mix all `@media` logic together, seperate them according to the HTML structure.
7. If you are writing a simply page, do not seperate all `@media` logic in little pieces, mix them according to different section of the HTML structure.
8. Do not leave the unused style code in your css files. Remember to delete them after your test
9. Think about to code in less. It can help you better organise your code. 

A good example to use breakpoints

```
// Defaut style seting for `example` class
.example{
   rule 1;
   rule 2;
   ...
}
```

```
// For screens lager than 768px
@media (min-width:768px){
  .example{
  // If rule 1 is the same, you don't need to repeat it here
   rule 2; // rule 2 is overwrite when screens is lager than 768px
  }
}
```

```
// For screens between 768px and 998px
@media (min-width:768px) and (max-width:998px){
  .example{
   rule 2; // rule 2 is overwrite between 768px and 998px
  }
}
```

For screen larger than 998px, the second code snippet rule 2 will be apply.


## Jquery

1. Think about to write only once `$(document).ready` function in js code.
2. Do not put every thing inside `$(document).ready` because:
   
	- It's just for initialization of a page.
	- most of the function definition should be outside `$(document).ready` 
	- most of the immidiately excute functions should be `$(document).ready`  

3. Use a variable to store the jQuery selected elements in order to avoid code redudunce  

```
// This is ok
$('#notifComm').show();
$('#notifComm').html("Votre campagne a bien été créée!");
```

```
// This is better
var notifComm = $('#notifComm');
notifComm.show();
notifComm.html("Votre campagne a bien été créée!");
```

4. If possible, use jQuery `addClass()` function instead of `css()` to change the elements style in your JS code. 

## Bootstrap
1. The correct way to use colum classes is:

```	
<div class="container">
    <div class="row">
        <div class="col-xs-6">
            <div class="big-box">image</div>
        </div>
    </div>
</div>
```

A `container` class is needed whenever you use a row class;
A `row` class is needed whenever you use a `col-*-*` class


2. The correct way to write nested row is:

``` 
<div class="container">
    <div class="row">
        <div class="col-xs-6">
            <div class="big-box">image</div>
        </div>
        <div class="col-xs-6">
            <div class="row">
                <div class="col-xs-6"><div class="mini-box">1</div></div>
                <div class="col-xs-6"><div class="mini-box">2</div></div>
                <div class="col-xs-6"><div class="mini-box">3</div></div>
                <div class="col-xs-6"><div class="mini-box">4</div></div>
            </div>
        </div>
    </div>
</div>

```

[This](http://stackoverflow.com/questions/24659471/nested-rows-with-bootstrap-grid-system
) article explains how to use bootstrap nested row correctly. 


