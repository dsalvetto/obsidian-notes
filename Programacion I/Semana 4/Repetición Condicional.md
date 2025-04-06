#semana4 
### La instrucción while

#### Ejemplo

Leer números naturales de la entrada y calcular su suma. El fin de la entrada está indicado por un número negativo.

```pascal
var
  numero, suma: integer;
begin
  (* lectura inicial *)
  readln(numero);

  (* inicialización *)
  suma := 0;

  while numero >= 0 do
  begin
    (* acumulación *)
    suma := suma + numero;
    (* siguiente lectura *)
    readln(numero);
  end;

  (* mostrar resultado *)
  writeln('La suma de los números es: ', suma);
end.
```

### Sintaxis de la instrucción while

```
while e do instrucción
```

Donde:
- `e` es una expresión de tipo booleano.
- `instrucción` es cualquier instrucción.
- `while` y `do` son palabras reservadas.

### Semántica

La ejecución de una instrucción:

```
while e do instr
```

procede de la siguiente manera:

1. Evaluar la expresión (la condición del while).
   - Si resulta `false`, terminar.
2. Ejecutar la instrucción `instr`.
3. Volver al paso 1.

### Indentación

```pascal
(* correcto *)
while condición do
begin
  hacer_algo;
  hacer_otra_cosa;
end;

(* incorrecto *)
while condición do
begin
hacer_algo;
hacer_otra_cosa;
end;
```

### Lectura con centinela

Un centinela es un valor especial usado para indicar el final de una lista de datos.

```pascal
(* lectura adelantada *)
readln(dato);

{inicialización de acumuladores }
...
(* iteración *)
while "dato no es centinela" do
begin
  (* procesar dato *)
  ...
  (* acumular *)
  ...
  (* siguiente lectura *)
  readln(dato);
end;
```

### Determinar si un número es primo

Un número natural es primo si es mayor que uno y es divisible únicamente entre sí mismo y la unidad.

```pascal
var
  fin, numero, divisor: integer;
begin
  readln(numero);
  if numero < 2 then
    writeln('El número ', numero, ' no es primo')
  else
  begin
    fin := trunc(sqrt(numero));
    divisor := 2;
    while (divisor <= fin) and (numero mod divisor <> 0) do
      divisor := divisor + 1;

    if divisor <= fin then
      writeln('El número ', numero, ' no es primo')
    else
      writeln('El número ', numero, ' es primo');
  end;
end.
```

### La instrucción repeat

```pascal
repeat
  instrucción;
  ...
  instrucción;
until expresión;
```

### Semántica del repeat

1. Se ejecuta el cuerpo (siempre al menos una vez).
2. Se evalúa la expresión. Si es `false`, se vuelve al paso 1. Si es `true`, termina.

### Relación con while

```pascal
repeat
  S;
until C;
```

Es equivalente a:

```pascal
S;
while not C do
begin
  S;
end;
```

### Procesamiento de palabras

Deseamos contar las palabras contenidas en un texto. Las palabras están separadas por espacios. El final del texto se señaliza con un carácter de punto `.`.

```pascal
const
  ESPACIO = ' ';
  FIN = '.';

var
  caracter: Char;
  cantidadPalabras: Integer;
begin
  cantidadPalabras := 0;
  (* avanzar comienzo de palabra *)
  repeat
    read(caracter);
  until caracter <> ESPACIO;

  while caracter <> FIN do
  begin
    (* leer palabra *)
    repeat
      read(caracter);
    until caracter = ESPACIO;
    
    (* incrementar contador *)
    cantidadPalabras := cantidadPalabras + 1;

    (* avanzar siguiente palabra *)
    repeat
      read(caracter);
    until caracter <> ESPACIO;
  end;

  writeln('La cantidad de palabras es: ', cantidadPalabras);
end.
