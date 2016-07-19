---
layout: post
title:  "Introduction to ECMAScript 6 Pt. 1"
date:   2016-07-14 05:00:00
categories: javascript
lang: en
ref: es6pt1
<!-- tags: featured  -->
image: /assets/article_images/es6intro1/es6photo.jpg
---
Well, what's the best way to start the blog if not with a post about Javascript uh?

First of all, *__What do I mean with ECMAScript 6?__*, to make it simple, ECMAScript 6 (es6 to make it short), is the new javascript standart (well, to tell you the truth is a little old by now, but it's the current "thing"), es6 brings a lot of optimizations and new features to what we already know, there are so many that this topic deserves more than a single post, in the following article I will cover the `"esential"` features about es6.

<p style="text-align: center;"><image src="/assets/article_images/es6intro1/okay.jpg"></image></p>
<center style="margin-top: -30px;">	<h2> Variables (var, let and const) </h2> </center>
____

A pesar de seguir siendo *dinámicamente tipeado*, ES6 nos introduce una nueva forma de declarar variables aparte del ya conocido `var`, estos son *let* y *const*.

La primera forma, *let* se utiliza de la misma forma que el *var*, y prácticamente tienen un escenario de uso muy similar, pero este tipo de variable se introdujo para solventar el problema de los *Scopes*, de manera que esta variable solo tiene un alcance local, es decir, **solo se inicia la variable en el bloque de código actual**. 

La segunda forma, *const* se introdujo para optimizar el uso de memoria de Javascript (¿Quien no quiere que su código sea más eficiente?), se utiliza para declarar **constantes** y este tipo de "variables" se tienen que declarar con un valor que no podrá ser reasignado (javascript lanzara un error en caso de).
**OJO:** a pesar de que la variable no puede ser reasignada, las propiedades del objeto si pueden variar.  

¿Entendieron?, supongo que no, así que vamos con un ejemplo:

{% highlight js linenos %}
var a = 5; // Manera tradicional, el alcance es toda la función
let b = 10; // Alcance de bloque local, solo el bloque que lo declara
 // No se puede reasignar, pero si modificar propiedades
const c = {
	test: 'Por defecto'
};

if (true) {
	var a = 30; // a = a
	let b = 5; // Solo dentro del bloque "if" b != b

	console.log(a); // 30
	console.log(b); // 5
}

console.log(a); // 30
console.log(b); // 10
c.test = 'hola'; // ok
c = 50; // TypeError: Assignment to constant variable.
{% endhighlight %}

Como se puede apreciar en el ejemplo, la variable `b` declarada con **let** dentro del bloque `if` no es igual a la que fue declarada en el bloque exterior, a diferencia de la variable `a` declarada con **var** donde si son la misma. Con respecto a la variable `c` declarada con **const**, con esta pudimos reasignar su propiedad "test" sin ningún problema, pero al momento de tratar de volver a asignarla salto un error *(ugh)*.

*__En conclusión__:* Javascript nos ofrece dos maneras eficientes y seguras de declarar variables, por lo cual no veo razón para seguir utilizando `var` de manera general, en mi caso, me inclino más a utilizar `const` para declarar módulos, utilidades, etc, en una variable que se que no volveré a asignar, mientras para el resto, utilizare `let` para prevenir errores de *Scope*, tipo... *oh la función x me cambio el valor de la variable! acabo de perder 2 horas buscando el error...*, hmm me suena familiar.