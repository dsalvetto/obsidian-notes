
## Estructuras de control 

### Clasificación
Instrucciones simples
- Asignación
- Llamada a procedimiento
Instrucciones compuestas
- Secuencia.
- Selección (if, case)
- Repetición (for, while, repeat)

### La secuencia
**Diagrama:**
![[diagrama_la_secuencia.png]]

### La secuencia (cont)

**BNF**
`secuencia = 'begin' instrucción { ';' instrucción} 'end'`
**Ejemplo:**
```pascal
begin
read(v);
v:= v * 4;
writeln(v)
end
```

## Selección

### La instrucción if-then-else
Ejemplo: Determinar si un número es par o impar.
```pascal
program ParImpar;
var
numero : integer;
begin
(* Ingresar numero *)
write('Ingrese numero: ');
readln(numero);
(* analizar el numero*)
if numero mod 2 = 0 then
writeln('El numero ingresado es par')
else
writeln('El numero ingresado es impar')
end.
```

### Sintaxis
**Diagrama**
![[if-then-else.png]]
Observaciones:
- if, then, else son palabras reservadas.
- expresión debe ser una expresión booleana.
- Observar que no lleva ; en ninguna parte.

### Semántica de la instrucción if-then-else
La ejecución de:
```pascal
if expresión
	then instrucción1
	else instrucción2
```
involucra los siguientes pasos:
 1. Se evalúa la expresión booleana; sea b su valor.
 2. Si b es true se ejecuta instrucción1
 3. Si b es false se ejecuta instrucción2.

### Semántica de if-then
La ejecución de:
```pascal
if expresión
	then instrucción1
```
involucra los siguientes pasos:
1. Se evalúa la expresión booleana; sea b su valor.
2. Si b es true se ejecuta instrucción1
3. Si b es false no se ejecuta nada.

### Anidamiento de instrucciones.
Las instrucciones dentro del if pueden ser simples o compuestas:
```pascal
if i > 0 then
begin
i:= i+1;
writeln('Es positivo')
end
else
begin
i:= i*4;
writeln('Es negativo')
end
```
En este ejemplo se anidan secuencias dentro de una sentencia if.

### Indentación de sentencias anidadas
**Indentación:** Es la cantidad de espacios que se dejan al principio de una línea de programa.
- El compilador no toma en cuenta la indentación.
- Sin embargo es muy importante para la legibilidad y mantenimiento de un programa.
- La indentación debe ayudar a entender la estructuración lógica del programa.

### Indentación de if-then-else
Existen muchas maneras de indentar una instrucción if:

```pascal
if expresion then (* estilo Wirth *)
begin
...
end else
begin
...
end
```

### Indentación de if-then-else (cont)

```pascal
if expresion (* estilo Konvalina *)
then begin
...
end
else begin
	...
	end
if expresion then begin (* estilo Kernighan-Ritchie *)
	...
end else begin
	...
end (*if*)
```

### Sentencias if anidadas
Las instrucciones asociadas con el then y/o else pueden ser a su vez instrucciones if
``` pascal
if exp1 then (* 1 *)
	if exp2 then (* 2 *)
		inst1
else (* cierra 2 *)
	inst2
else (* cierra 1 *)
	if exp3 then (* 3 *)
		inst3
else (* cierra 3 *)
	inst4
```
Regla: Cada else se asocia con el último if que no esté cerrado.