# Angular Tutorial


# Data Binding (video 10)

### data transfer from file.ts to file.html in same component


>file.ts

```javascript
import { Component, OnInit } from '@angular/core';


@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.css']
})
export class HomeComponent implements OnInit {
  homeTitle = "this data from homeComponent class";

  constructor() { }

  ngOnInit(): void {
  }

}
```

>file.html  

```html
<p>{{homeTitle}}</p>
```

# Property Binding (video 11)

### data transfer from file.ts to file.html in same component

This thing can do with previous method too.    
```html
<input value="{{myString}}" />
```
But as a improvment here we are use '[property_name ]' to get this property name's value from file.ts.    
```html
<input [property_name ]="value_variable_located_in_ts_file" />
```

### Binding to HTML properties
  * Native HTML properties: [value]="express"   
      ```html
         <input value="type some thing" />
      ```
  * Custom-made properties: [myProp]="express"   
      ```html
         <input count="true" />
      ```
  * Built in angular directives: [ngClass]="express"   
      ```html
         <input count="true" />  ????
      ```

### Binding to HTML properties  


>file.ts

```javascript
import { Component, OnInit } from '@angular/core';


@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.css']
})
export class HomeComponent implements OnInit {
  myString = "Enter value here";

  constructor() { }

  ngOnInit(): void {
  }

}
```

>file.html  

```html
<input [value]=myString/>
```

# Two Way Data Binding (video 13)

### Here dynamically changing value from shared variable(ninja) that located in file.ts .(Binding in same component)

>file.ts

```javascript
import { Component, OnInit } from '@angular/core';


@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.css']
})
export class HomeComponent implements OnInit {

  public ninja = {
      name:"Yoshi",
      belt:"Black"
  };

  constructor() { }

  ngOnInit(): void {
  }

}
```

>file.html  

```html
<input [(ngModel)]="ninja.name" />
<p>{{ninja.name}}</p>
```
*  *space required ( "ninja.name" /> )*

* In html file when value change of input field then dynamically it change value of p tags.    
* "ngModel" is unique name binder for make communicate between file.ts and file.html .



# Native Event Binding (video 12)

### Here we send click event from file.html to file.ts in same component. (Binding in same component)

>file.ts

```javascript
import { Component, OnInit } from '@angular/core';


@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.css']
})
export class HomeComponent implements OnInit {

  alertMe(val){
    alert(val);
  };

  constructor() { }

  ngOnInit(): void {
  }

}
```

>file.html  

```html
<button (click)="alertMe('i am good person')" > Click Me</button>
```


# Custom Property Binding (video 14)

### Here we transfer data between two components.

we are using data sender component's html file as media of transferring between two components.

>app.ts

```javascript
import { Component } from '@angular/core';
import { NgModule } from '@angular/core';

//import { ROUTER_DIRECTIVES } from "@/angular/router";

@Component({
  selector: 'app-root', /* selector of index.html*/
  templateUrl: './app.component.html', /**/
  /*template : '<h1>{{title}}</h1>',*/
  styleUrls: ['./app.component.css'],
  //directives : [ ROUTER_DIRECTIVES ]
})
export class AppComponent {

  public school ={
    name:"Asoka Collage",
    adress:"Colombo 10"
  };

}

```

>root.html  

```html
<app-home [prop]="school"  >Loading..</app-home>
```


>file.ts

```javascript
import { Component, OnInit , Input} from '@angular/core';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.css']
})
export class HomeComponent implements OnInit {

  @Input() prop;

  constructor() { }

  ngOnInit(): void {
  }

}
```

>file.html  

```html
<p>{{prop.name}}</p>
<p>{{prop.adress}}</p>
```
Finally we can represent data values from app.component.ts on home.component.html
