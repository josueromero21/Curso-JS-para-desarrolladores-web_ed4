# Clase 3

### Dudas y preguntas de la clase anterior

- [Cachear pass y user de Git en consola (c9, etc..)](https://github.com/UlisesGascon/curso-js-web-developers-112015/issues/1)
- [Trabajando con Git desde la terminal (c9, etc...)](https://github.com/UlisesGascon/curso-js-web-developers-112015/issues/2)
- [GreaseMonkey - TamperMonkey](https://github.com/UlisesGascon/curso-js-web-developers-112015/issues/3)

### Reintroducción a JS

**If... else**

- Estructura:
    ```javascript
    /* IF ...ELSE
    if (-algo verdadero-) {
        -ejecutaremos este código-
    } else {
        -Si lo anterior no era verdadero, se ejecutara este código-
    };
    */
    ```

- Documentación:
    - [If... else en w3schools](http://www.w3schools.com/js/js_if_else.asp)
    - [If... else en MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)

- Ejemplo:
    ```javascript
    if (true) {
        console.log("true, por eso me ejecuto");
    } else {
        console.log("false, por eso me ejecuto");
    }
    ```


**Else if...**

```javascript
function testCondiccion (condicion){
    if (condicion == 1) {
        console.log("1, por eso me ejecuto");
    } else if (condicion == 2){
        console.log("2, por eso me ejecuto");
    } else {
        console.log("no es 1 o 2, por eso me ejecuto");
    }
}
```


**AND(&&)**

Elemento 1 | Elemento 2 | Resultado
------------ | ------------- | -------------
true | true | true
true | false | false
false | false | false
false | true | false


**OR(||)**

Elemento 1 | Elemento 2 | Resultado
------------ | ------------- | -------------
true | true | true
true | false | true
false | false | false
false | true | true


```javascript
var ex1 = true && true; // true
var ex2 = (2 == 2) && (3 >= 6); // false
var ex3 = (2>3) || (17 <= 40); // true
var ex4 = false || false; // false

function condicionalAvanzado ( paraComparar ) {
    if (paraComparar) {
        console.log("Verdadero!");
    } else {
        console.log("falso!");
    };
};
```


**Interacción Básica con el Usuario**

- alert():
    ```javascript
    alert("¡Bienvenido a esta web!");
    ```

- confirm():
    ```javascript
    confirm("¿Esta seguro que desea abandonar esta web?");
    ```


- Ejemplo:
    ```javascript
    var respuesta = confirm("presiona un botón!");
    if (respuesta === true) {
        console.log("Has aceptado!");
    } else {
        console.log("Has cancelado");
    }
    ```

- prompt():
    ```javascript
    prompt("¿Como te llamas?");
    ```

- Registremos los datos en una variable:
    ```javascript
    var nombre = prompt("¿Como te llamas?");
    ```


**Arrays**

- Creando un array:
    ```javascript
    var arreglo = [];
    arreglo = [1, "platano", "piscina", "manzana", true];
    ```

- Usando el Índice:
    ```javascript
    arreglo[1];
    ```

- Cambiar un valor del Índice:
    ```javascript
    arreglo[0] = "fresa";
    arreglo[4] = "pera";
    arreglo[2] = "limón";
    ```

- Índice total:
    ```javascript
    arreglo.length;
    ```

- .push() *Añadir elemento al índice*:
    ```javascript
    arreglo.push("nuevo");
    ```

- .pop() *Eliminar el último elemento del índice*:
    ```javascript
    arreglo.pop();
    ```

- .shift() *Eliminar el primer elemento*:
    ```javascript
    arreglo.shift();
    ```

- delete *sobrescribe a undefined*
    ```javascript
    delete arreglo[0];
    ```

- Elementos vacios:
    ```javascript
    arreglo[0] = undefined;
    ```

- .splice() *Borrar*:
    ```javascript
    var manzana = arreglo.splice(3, 1);
    ```

- .map():
    ```javascript
    var arreglo = ["plátano", "fresa", "lima", "manzana"];
    var resultado = arreglo.map(function (elemento){return elemento + " modificado!"});
    console.log(resultado);
    ```



**Arreglos avanzados**
```javascript
var arreglo1 = ["plátano", "fresa", "lima", "manzana"];
var arreglo2 = ["entrante", "primero", "segundo", "postre"];

var juntandoArreglos = [arreglo1, arreglo2];

function testArreglos () {
    console.log(juntandoArreglos[0][0]);
    console.log(juntandoArreglos[1][3]);
};
```


**Ejercicios**

8 - **#simplifiquemos!** Quiero solo un bucle para todo.

```javascript
    var trenesOperativos = 8;
    var totalTrenes = 12;

    function estadoDetalle () {
    	for(var numeroTren = 1; numeroTren <= totalTrenes; numeroTren++) {
    		if (numeroTren <= trenesOperativos) {
    			console.log("El tren número "+numeroTren+" esta funcionando");
    		}else {
    			console.log("El tren número "+numeroTren+" esta parado");
    		};		
    	};
    };
```

9 - **#compliquemos!** Servicio nocturno en el tren 10.
*Nota: Frente al ejercicio anterior, en este caso queremos que siempre que hablemos del
tren 10 se especifique que es nocturno. Independientemente de si esta parado o funcionando.*

```javascript
    var trenesOperativos = 8;
    var totalTrenes = 12;

    function estadoDetalle () {
    	for(var numeroTren = 1; numeroTren <= totalTrenes; numeroTren++) {
    		if ((numeroTren <= trenesOperativos) && (numeroTren != 10)) {
    			console.log("El tren numero "+numeroTren+" esta funcionando");
    		} else if (numeroTren == 10){
    			console.info("IMPORTANTE: El tren número "+numeroTren+" es nocturno");
    		} else {
    			console.log("El tren numero "+numeroTren+" esta parado");
    		};		
    	};
    };
```


10 - Refactoricemos - ¿Y si todos los trenes están en las vías funcionando o por el contrario si ninguno de los trenes esta funcionando?.

```javascript
    var trenesOperativos = 8;
    var totalTrenes = 12;

    function estadoDetalle () {
    	if (trenesOperativos > 0) {
    		if(trenesOperativos == totalTrenes){
    			console.log("Todos los trenes estan funcionando");
    		} else {
    			for(var numeroTren = 1; numeroTren <= totalTrenes; numeroTren++) {
    				if ((numeroTren <= trenesOperativos)  && (numeroTren != 10)) {
    					console.log("El tren numero "+numeroTren+" esta funcionando");
    				} else if (numeroTren == 10){
    					console.log("IMPORTANTE: El tren numero "+numeroTren+" es nocturno");
    				} else {
    					console.log("El tren numero "+numeroTren+" esta parado");
    				};		
    			};
    		};
    	} else {
    		console.log("IMPORTANTE: Ningún tren esta funcionando");
    	};
    };
```

11 - El servicio nocturno se queda un poco corto y necesitamos añadir un nuevo tren de refuerzo.
El 12 será destinado a cubrir esta necesidad, exactamente igual que el 10 anteriormente.

```javascript
    var trenesOperativos = 8;
    var totalTrenes = 12;

    function estadoDetalle () {
    	if (trenesOperativos > 0) {
    		if(trenesOperativos == totalTrenes){
    			console.log("Todos los trenes están funcionando");
    		} else {
    			for(var numeroTren = 1; numeroTren <= totalTrenes; numeroTren++) {
    				if ((numeroTren <= trenesOperativos) && (numeroTren != 10) && (numeroTren != 12)) {
    					console.log("El tren numero "+numeroTren+" esta funcionando");
    				} else if (numeroTren == 10 || numeroTren == 12){
    					console.log("IMPORTANTE: El tren numero "+numeroTren+" es nocturno");
    				} else {
    					console.log("El tren numero "+numeroTren+" esta parado");
    				};		
    			};
    		};
    	} else {
    		console.log("IMPORTANTE: Ningún tren esta funcionando");
    	};
    };
```


12 - El departamento de Marketing ha decidido lanzar un nuevo servicio los sábados.
 El "tren fiestero" será un tren adaptado a un público más intrépido y funcionará solo en los sábados.
 Este tren será el número 3.

*NOTA: EL TREN 3 SOLO FUNCIONA LOS SÁBADOS. Es necesario incluir el día de la semana en tu código*

```javascript
    var trenesOperativos = 8;
    var totalTrenes = 12;
    var diaSemana = "Sabado";
    function estadoDetalle () {
    	if (trenesOperativos > 0) {
    		if(trenesOperativos == totalTrenes){
    			console.log("Todos los trenes están funcionando");
    		} else {
    			for(var numeroTren = 1; numeroTren <= totalTrenes; numeroTren++) {
    				if (numeroTren <= trenesOperativos  && numeroTren != 3 && numeroTren != 10 && numeroTren != 12) {
    					console.log("El tren numero "+numeroTren+" esta funcionando");
    				} else if (numeroTren == 10 || numeroTren == 12){
    					console.info("IMPORTANTE: El tren numero "+numeroTren+" es nocturno");
    				} else if (numeroTren == 3 && diaSemana == "Sabado"){
    					console.info("El tren fiestero("+numeroTren+") esta funcionando.")
    				} else if (numeroTren == 3 && diaSemana != "Sabado"){
    					console.info("El tren fiestero("+numeroTren+") funcionará el sabado.")
    				} else {
    					console.log("El tren numero "+numeroTren+" esta parado");
    				};		
    			};
    		};
    	} else {
    		console.log("IMPORTANTE: Ningún tren esta funcionando");
    	};
    };
```

**Funciones**

- Propiedad *name*:
    ```javascript
	function miFuncion (){
		// vacia
	};

	console.log(miFuncion.name);
    ```


- Declaración y ejecución:
    ```javascript
	function dameTrue (){
		return true
	};

	function dameFalse () {
		return false
	};

	dameTrue();
	dameFalse();
    ```

- Invocación e introducción a *this*:
	- como función (*this* contexto *window*)
		```javascript
		function ambitoGlobal () {
			return this;
		}
		
		ambitoGlobal()
		```
	- como método en un objeto (*this* contexto objeto al que pertenece el método)
		```javascript
		var objeto = {};
		
		objeto.miMetodo = function () {
			return this;
		}
		
		objeto.miMetodo();
		```		
	- como constructor de un objeto (*this* contexto objeto creado)
	- .apply() y .call() (modificación explícita de *this*)

- Argumentos:
	- El exceso de argumentos no es un problema
	- La falta de argumento crea un valor indefinido
    - El Objeto Arguments no es un Array, solo es similar.
    ```javascript    
	
	function pruebaArguemntos () {
	console.log(arguments);
	console.info(arguments[0]);
	console.info(arguments[1]);
	}
	
	pruebaArguemntos (1, "vale", true);
	
	```


- [Objeto Arguments](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Funciones/arguments)


- Sumar cuadrados.

```javascript
	function sumaCuadrados (a, b) {
		return (a*a) + (b*b);
	};
```



**Funciones (Scope)**

- Declaración y ejecución:
    ```javascript
	var numero = 450;
	var otroNumero = 23;

	function sumaCuadrados (a, b) {
		var numero = a;
		var otroNumero = b;
		var calculo = (numero*numero) + (otroNumero*otroNumero);
		console.log("\"numero\" es \""+numero+"\", local");
		console.log("\"otroNumero\" es \""+otroNumero+"\", local");
	};

	function verificarGlobales() {
		console.log("\"numero\" es \""+numero+"\", global");
		console.log("\"otroNumero\" es \""+otroNumero+"\", global");
	};
    ```


**Atacando la lógica**

- Divide y venceras (determina la estructura de afuera hacia dentro)
    ![Divide et impera](http://orig12.deviantart.net/467f/f/2009/257/9/9/divide_y_venceras___cesar_by_horusart.jpg)

- Los comentarios son tu aliado. 

- [Introduction to Pseudocode de Damian Gordon](http://www.slideshare.net/DamianGordon1/pseudocode-10373156?qid=2ccda58e-4c14-4685-ba31-2b3ae9196e4a&v=qf1&b=&from_search=1)
    ![ejemplo_pseudocodigo](http://rockbotic.com/wp-content/uploads/2014/01/pseudocodigo-para-dormir.jpg)

- [Blocky](https://blockly-demo.appspot.com/static/demos/code/index.html?lang=es)
    - Exportación en PHP, JS, Python, etc...
    - Verificación de la lógica
    - [Opensource](https://github.com/google/blockly)


**Funciones (Avanzadas)**

- Anónimas (expresiones):
    ```javascript
	var sumaCuadrados = function (a, b) {
		return (a*a) + (b*b);
	};
    
    console.log("El .name de sumaCuadrados es "+sumaCuadrados.name)
    ```

- Funciones como dato:
    ```javascript
	function saludo () {
		console.log("hola!");
	};

	function lanzar (funcion){
		funcion();
	};
    ```

- Funciones anónimas autoejecutables:
    ```javascript
	(function() {
		console.log("hola Amigo/a")

	}) (); //ex:Jquery
    ```


- Funciones anónimas con parámetros:
    ```javascript
	( function(quien){
	   console.log("hola " + quien);
	})("Amigo/a");
    ```


- Función que devuelve una función anónima:
	- Asignando una variable:
    ```javascript
	function saludo(quien){
	        return function(){
	                alert("hola " + quien);
	        }
	}
	var saluda = saludo("Amigo/a");
	saluda();
    ```

	- Sin asignar una variable:
    ```javascript
	function saludo(quien){
	        return function(){
	                alert("hola " + quien);
	        }
	}
	saludo("Amigo/a")();
    ```


**Funciones (Anidación)**

- Anidación:
    ```javascript
	function saludar(quien){
	        function alertasaludo(){
	                console.log("hola " +  quien);
	        }
	        return alertasaludo;
	}
	var saluda = saludar("Amigo/a");
	saluda();
    ```

- Anidación:
    ```javascript
	function saludar(quien){
	        function alertasaludo(){
	                console.log("hola " +  quien);
	        }
	        return alertasaludo;
	}
	saludar("Amigo/a")();
    ```
    
**Funciones (recursión)**

- Calcular el [factorial](https://www.wikiwand.com/es/Factorial).
	
    ```javascript
		function factorial(n){
			if(n <= 1){
		    	return 1
		  	} else {
		    	return n * factorial(n-1)
			}
		}
		
		factorial(0); // n! = 1
		factorial(1); // n! = 1
		factorial(2); // n! = 2
		factorial(3); // n! = 6 (3*2*1)
		factorial(4); // n! = 24 (4*3*2*1)
		factorial(5); // n! = 120 (5*4*3*2*1)
		factorial(6); // n! = 720 (...)
		// ...
    ```


- Saber si hoy es un día par o impar.

```javascript
	var miDiaEs = function() {
	    if (new Date().getDate() % 2 == 0) {
	        console.info("hoy es un día par");
	    } else {
	        console.info("hoy es un día impar");
	    }
	}
	miDiaEs();
```



**Funciones (Closures)**

> Los closures son funciones que manejan variables independientes. En otras palabras, la función definida en el closure "recuerda" el entorno en el que se ha creado.

> No es aconsejable crear innecesariamente funciones dentro de otras funciones si no se necesitan los closures para una tarea particular ya que afectará negativamente el rendimiento del script tanto en consumo de memoria como en velocidad de procesamiento.
> [Closures MDN](https://developer.mozilla.org/es/docs/Web/JavaScript/Closures)

- Fábrica de función:
    ```javascript
	function sumador(x) {
	  return function(y) {
	    return x + y;
	  };
	}

	var sum1 = sumador(10); //Closure
	var sum2 = sumador(30);	//Closure

	console.log(sum1(2)); // Devuelve 12
	console.log(sum2(2)); // Devuelve 32
	console.log(sumador(20)(2)); //Devuelve 22
    ```

- Otro ejemplo, ahora temporizado:
    ```javascript
	function saludar(segundos){
		var hola = "Hola, Hola!";

		setTimeout(function(){
			console.info(hola);
		},segundos*1000);
	}

	saludar(2);
    ```

- Otro ejemplo... más útil:
    ```javascript
      var varGlobal = "Soy un dato Global";
      var burbuja;

      function nivel1() {
        var varInterna = "Soy un dato interno. -> nivel1";

        function nivel2() {
          console.log("Estoy dentro de la funcion -> nivel2")
          console.log("Estoy dentro de la funcion -> nivel2 y puedo acceder al nivel1: "+varInterna)
        }

        burbuja = nivel2;

      }

      nivel1();

      burbuja();
      console.log("Burbuja recuerda su contexto original")
    ```


**Switch**

- Estructura:
    ```javascript
    /* Switch
	switch(expresión) {
	    case n:
	        //Código
	        break;
	    case n:
	        //Código
	        break;
	    default:
	        //Código
	}
    */
    ```

- Documentación:
    - [Switch en w3schools](http://www.w3schools.com/js/js_switch.asp)
    - [Switch en MDN](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/switch)

- Casos únicos:
    ```javascript
	var nombre = "";
	switch (nombre) {
	  case "Pepe":
	    console.log("Hola Pepe");
	    break;
	  case "Luis":
	    console.log("Hola Luis");
	    break;
	  case "Antonio":
	    console.log("Hola Antonio");
	    break;
	  default:
	    console.log('Ninguno de los nombres que pensamos... es '+nombre);
	}
    ```

- Multiples coincidencias:
    ```javascript
	var nombre = "";
	switch (nombre)
	{
	   case "Pepe":
	   case "Luis":
	   case "Antonio":
	       alert('Hola '+nombre);
	       break;

	   default:
	       console.log('Ninguno de los nombres que pensamos... es '+nombre);
	}
    ```


**Ejercicios**

13 - Hagamos una lista de pasajeros (min. 6)

```javascript
    // Tu solución
```


14 - Hagamos una lista de pasajeros efectiva usando Arrays

```javascript
    var pasajeros = ["Alicia Gutierrez", "Alfonso Gomez", "Luis Navarro", "Oscar Garcia", "Andres Fernandez", "Lucia Mellado"];
```


15 - Imprimamos cada pasajero de la lista y su número de asiento (basado en el orden del índice).
*Nota: El primer asiento del tren es el 1 y no el 0.*

```javascript
    var pasajeros = ["Alicia Gutierrez", "Alfonso Gomez", "Luis Navarro", "Oscar Garcia", "Andres Fernandez", "Lucia Mellado"];

    function listaPasajeros(){
        for (var i = 0; i < pasajeros.length; i++) {
            console.log("El pasajero "+pasajeros[i]+" tiene reservado el asiento "+(i+1));
        };
    };
```

- Respuesta esperada (consola):

```
	El pasajero Alicia Gutierrez tiene reservado el asiento 1
	El pasajero Alfonso Gomez tiene reservado el asiento 2
	El pasajero Luis Navarro tiene reservado el asiento 3
	El pasajero Oscar Garcia tiene reservado el asiento 4
	El pasajero Andres Fernandez tiene reservado el asiento 5
	El pasajero Lucia Mellado tiene reservado el asiento 6
```


16 - Necesitamos una función para agregar y otra para borrar pasajeros de la lista.
*Nota: Pensemos que a la larga pueden existir más listas.*

```javascript
    	var pasajeros = ["Alicia Gutierrez", "Alfonso Gomez", "Luis Navarro", "Oscar Garcia", "Andres Fernandez", "Lucia Mellado"];

	function agregarPasajero(nombre, lista) {
		lista.push(nombre);
		return lista
	};

	function quitarPasajero(nombre, lista) {
		if (lista.length == 0) {
			console.log("La lista \""+lista+"\" esta vacía.");
		} else {
			for (var i = 0; i < lista.length; i++) {
				if(lista[i] == nombre){
					lista.splice(i, 1);
					return lista;
				} else if (i == lista.length -1){
					console.log("El pasajero \""+nombre+"\" no encontrado!")
				};
			};
		};
	};
```


17 - La compañía de trenes ha decidido que los viajeros podrán reservar el asiento asignado, pero quiere evitar que los pasajeros cambien de asiento constantemente cuando se anula un o varios billetes.
*Nota: Al borrar en el ejercicio anterior las posiciones de los pasajeros cambiaban y los billetes quedaban desactualizados.*

```javascript
    var pasajeros = ["Alicia Gutierrez", "Alfonso Gomez", "Luis Navarro", "Oscar Garcia", "Andres Fernandez", "Lucia Mellado"];

	function agregarPasajero(nombre, lista) {
		if(lista.length == 0){
			lista.push(nombre);
			console.log("El pasajero "+nombre+" añadido con éxito, asiento asignado 0");
		}else {
			for (var i = 0; i < lista.length; i++) {
				if (lista[i] == undefined) {
					lista[i] = nombre;
					console.log("El pasajero "+nombre+" añadido con éxito, asiento asignado "+(i+1));
					return true
				} else if (i == lista.length -1){
					lista.push(nombre);
					console.log("El pasajero "+nombre+" añadido con éxito, asiento asignado "+(i+1));
					console.log("INFO: En esta lista no quedan asientos pendientes de asignación.")
					return true
				};
			};
		};
	};


	function quitarPasajero(nombre, lista) {
		if (lista.length == 0) {
			console.log("La lista \""+lista+"\" esta vacía.");
			return false
		} else {
			for (var i = 0; i < lista.length; i++) {
				if(lista[i] == nombre){
					lista[i] = undefined;
					console.log("El pasajero \""+nombre+"\" eliminado con éxito!")
					return true;
				} else if (i == lista.length -1){
					console.log("El pasajero \""+nombre+"\" no encontrado!");
					return false
				};
			};
		};
	};
	
```


18 - Una de las vías principales esta en obras. Así que nuestra compañía decidió usar antiguas vías para hacer transbordos directos entre las estaciones afectadas.

Nuestra Misión es añadir el tiempo estimado en los billetes para las estaciones afectadas Tetuán,
Moncloa y Hortaleza. Es necesario incluir un texto informativo y el nombre del usuario también en el billete.

*Nota: Intenta utilizar Closures*

Info: 	
	- Tetuán (12)
   	- Moncloa (19)
   	- Hortaleza (21)

```javascript
	var nuevasRutas = [ ["Tetuán", 12], ["Moncloa", 19], ["Hortaleza", 21] ];

	function constructorDeTickets (estacion, tiempo) {
		return function (nombre) {
			console.log("Sr/a. "+nombre+".\n Muchas gracias por adquirir este ticket gratuito en el "+estacion+" express.\n El tiempo estimado de llegada es de "+tiempo+" minutos.\n Estamos trabajando en la mejora de nuestra vía principal, disculpe las molestias!");
		};
	}

	var tetuanExpress = constructorDeTickets ("Tetuán", 12);
	var moncloaExpress = constructorDeTickets (nuevasRutas[1][0], nuevasRutas[1][1]);
	var hortalezaExpress = constructorDeTickets (nuevasRutas[2][0], nuevasRutas[2][1]);

	tetuanExpress ("Pepe");
	moncloaExpress ("Luis");
	hortalezaExpress ("Hector");

```


**Funciones (Callbacks)**

> En programación de computadoras, una devolución de llamada o retrollamada (en inglés: callback) es una función "A" que se usa como argumento de otra función "B". Cuando se llama a "B", ésta ejecuta "A". Para conseguirlo, usualmente lo que se pasa a "B" es el puntero a "A".
> [Callbacks en Wikiwand](https://www.wikiwand.com/es/Callback_(inform%C3%A1tica))

- Ejemplo condensado:
    ```javascript
	var quieroCallback = function(parametro, callback){
	    if ((callback) && (typeof callback === 'function')){
	        callback(parametro);
	    }
	    else
	        console.log(parametro, callback);
	}
	 
	quieroCallback('a', 'b');
	 
	quieroCallback('a', function(val){
	    console.log(val);
	});
    ```


- Ejemplo con Jquery:
    ```javascript
    $('#elemento').fadeIn('slow', function() {
    	// código del callback
	});
    ```


- Otro ejemplo:
    ```javascript
    function comerSandwich(elemento1, elemento2, callback) {
	    console.info('ñam ñam... empiezo con el sándwich.\n\nMe gusta porque tiene tiene ' + elemento1 + ', ' + elemento2);
	    callback();
	}

	comerSandwich('jamón', 'queso', function() {
	    console.info('Ya terminé...');
	});
    ```


- Ejemplo con Callback opcional:
    ```javascript
    function comerSandwich(elemento1, elemento2, callback) {
	    console.info('ñam ñam... empiezo con el sándwich.\n\nMe gusta porque tiene tiene ' + elemento1 + ', ' + elemento2);
	    
	    if (callback) {
	        callback();
	    }

	}

	comerSandwich('jamón', 'queso');
    ```


- Sanitizar el Callback:
    ```javascript
    function comerSandwich(elemento1, elemento2, callback) {
	    console.info('ñam ñam... empiezo con el sándwich.\n\nMe gusta porque tiene tiene ' + elemento1 + ', ' + elemento2);
	    
	    if (callback && typeof(callback) === "function") {
	        callback();
	    }

	}

	comerSandwich('jamón', 'queso');
    ```


- Asincronia:
    ```javascript
    function comerSandwich(elemento1, elemento2, callback) {
	    console.info('ñam ñam... empiezo con el sándwich.\n\nMe gusta porque tiene tiene ' + elemento1 + ', ' + elemento2);
	  
		setTimeout(alarma, 5000);
		function alarma(){
			console.log("ring! ring!.. pasaron los 5 segundos!");
		};

	  
	    if (callback && typeof(callback) === "function") {
	        callback();
	    }
	}

	comerSandwich('jamón', 'queso', function() { 
	    console.log('Ya terminé...');
	});
    ```


- Más información: 
	- [Callback Functions in JavaScript de Louis Lazaris](http://www.impressivewebs.com/callback-functions-javascript/)
	- [Creando y utilizando callbacks de Pablo Novas en fernetjs](https://fernetjs.com/2011/12/creando-y-utilizando-callbacks/)