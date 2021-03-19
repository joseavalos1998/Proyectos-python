# Proyectos-python
P.R2 Avalos Villanueva Jose de la Luz
Para hacer la interfaz gráfica necesaria para la ventana, colocar los botones y el campo donde visualizaremos los números vamos a usar Tkinter, ya viene incluida en la instalación de Python(no importa el IDE)
1 Crearemos una ventana
2 Haremos todos los botones que contendrá la ventana incluyendo números, botones con operadores como el de suma, resta, división, multiplicación y el botón de igual para hacer el cálculo, en cada botón pasaremos un comando para identificarlo.
3 Procesaremos los datos porque una cosa es hacer los botones y otra cosa es darles funcionamiento, este tercer paso no es tan difícil como parece se hace con una sola función llamada eva
La ventana se hace con la función TK() le tenemos que dar un nombre a la variable de esta ventana y ningún nombre más clásico que ventana, pueden ponerle el que gusten posteriormente pero por ahora recomiendo no cambiar cosas porque luego puede no funcionarles si olvidan cambiarlo en todos los sitios que aparece.
Como pueden ver además de crear la ventana con la función tk incluí varios parámetros extra llamados métodos, el primero es configure donde le asigné un color al background esto es al fondo de la ventana, pueden usar otros colores como gray, yellow, blue, red, green y asi sucesivamente, con el método title como su nombre lo indica coloqué entre comillas el nombre que tendrá la ventana, este es el nombre visible de nuestro programa, el nombre también pueden cambiarlo, y es que al final la parte grafica de los programas o aplicaciones es muy importante para que el usuario se sienta cómodo o perciba que está haciendo uso de una aplicación seria, el método geometry básicamente sirve para dar el tamaño en medida de pixeles a la ventana, tanto su altura como su anchura, también pueden jugar con estos parámetros, al final le aplique a la ventana una llamada a la funcion mainloop(), sin esto el programa si se ejecutará pero se cerraría de inmediato tan pronto como lee el código, como su nombre lo indica mainloop sirve para crear un loop es decir un bucle que se repite una y otra vez pasando por este código así evitaremos que nuestro programa se cierre hasta que cerremos la ventana manualmente.
Se crea un controlador de tipo button yo le llamare al primero boton1 el primer valor a pasar es el nombre de la ventana a la que pertenecerá, ¿recuerdan que le habíamos puesto el nombre ventana?, bien pues ese usaremos, el segundo parámetro llamado text este incluirá el texto que veremos en el botón como estamos haciendo el botón con el numero 1 ese es el texto que incluimos, cuando hagamos el de igual incluiremos el símbolo = y así con cada uno, el tercer parámetro llamado fg que significa foreground sirve para colocar el color de frente en otras palabras el del texto, en este caso será negro y bg significa background para el color de fondo que será blanco, el siguiente parámetro es importante en el command utilizaremos lambda que es un tipo de expresión que nos permite pasar distintos parámetros a una sola función, a la función le llamaré digito e incluirá el numero 1, para finalizar height es la altura y width es la anchura en pixeles.
Espero que no intentaran todavía ejecutar lo anterior porque de ser así aunque si verán la ventana les lanzara errores por cuanto no hemos creado todavía la función digito(), pero si ya entendieron el código anterior solo queda crear los otros botones repitiendo el código anterior y se ve de la siguiente forma (todos los botones juntos).
Este es todo el código grafico ahora solo queda crear 3 funciones que atienden al punto número 3 es decir el de procesamiento de datos, para decirlo de otra forma es el código que se encarga de hacer las operaciones típicas de una calculadora.
La función digito sirve para guardar toda la expresión matemática por ejemplo "8+4+5*20/2", digito lo guardará y de inmediato lo mostrara el campo de datos que habíamos creado haciendo uso del método set en la variable calculo, limpiar hace algo similar nada más que en lugar de enviar dígitos reemplaza el texto existente por un valor vacío, y la función igual procesa todo con la función matemática eval() como es de esperar evaluando la expresión y mostrando el resultado.
Ahora si pueden ejecutarlo y verificar que todo esté en orden, ya tienen su primer calculadora en Python y a partir de ahí pueden ampliarle funciones o cambiarle el diseño, que de hecho a mi parecer este diseño no es muy bueno por lo básico que es, a continuación va el código entero por si confundieron algún paso.
En la programación muy poco está hecho, la mayoría hay que ir haciéndolo, con el código anterior pueden utilizar la calculadora pero si presionan la tecla enter(intro) para obtener el resultado no obtendrán esultado, además apenas abren la calculadora es necesario que den click en el campo input para empezar a escribir los dígitos con el teclado, porque si intentan digitar sin haber dado click en dicho campo simplemente no captará los números, esto se debe a que en verdad la ventana entera ha de capturar los eventos del teclado, con el siguiente código les enseño como capturar los eventos del teclado para que sea el usuario quien decida como utilizará su calculadora pues es muy molesto tener una calculadora donde es necesario clickar el botón "=" en lugar de usar la tecla intro.
La función la llamaremos teclado y capturará los eventos que se enviaran desde la llamada, a su vez esta función hace una llamada a la función digito(), y dentro de esta función enviamos los datos contenidos en event.char, char es el método que sirve para indicar que lo que queremos enviar es el carácter del objeto event. Muy bien ahora hagamos la llamada a esta función cada vez que se presione una tecla, esto con ayuda del método bind contenido en el objeto de nuestra ventana agregando una línea de código casi al final del código, justo antes de la última línea que dice ventana.mainloop(), el código es este.
Como iba diciendo bind es el objeto al cual le decimos que capture "<Key>" es decir cualquier key(tecla), y que cuando lo haga añada una llamada a la función que creamos anteriormente llamada "teclado", con esto ya no es necesario clicar primero en el campo input antes de digitar los números, pero todavía tenemos que ligar la tecla enter a la función igual() que es para obtener el resultado y así nuestra tecla enter será como clicar en "=", como ya la función igual() existe no tenemos que crear más funciones solo tenemos que detectar cuando se presione la tecla enter y llamar esta vez a la función teclado, la siguiente línea de código nos permite hacer esto, solo asegúrese incluirla justo antes de la sentencia anterior , es decir antes de ventana.bind("<Key>",teclado)
