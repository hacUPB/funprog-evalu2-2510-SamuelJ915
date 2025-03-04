# Actividad 4: de algoritmo a código fuente
> Pregunta orientadora:
> 
> - ¿Por qué crees que el pseudocódigo es útil antes de escribir un programa en C?
_Es útil porque nos ayuda a entender el codigo de la forma mas detallada posible y sin tener que pensar en el formato de codigo en un lenguaje en especifico_

> Actividad
> 
> - Toma un pseudocódigo de un ejercicio anterior o escribe tu propio pseudocódigo, similar al mostrado en el ejemplo 2.
_INICIO
    Leer valor1
    Leer valor2
    producto = valor1 * valor2
    Mostrar producto
FIN_

> Pregunta orientadora
> 
> - ¿Por qué es importante declarar el tipo de variable (int, float, etc.) antes de usarla en C?
_A parte de servir para optimizar el codigo, dandole una variable adecuada al tipo de valor que vamos a usar, sirve para consumir la cantidad adecuada de memoria para los valores adecuados._

> Actividad
> 
> - Escribe tu propio pseudocódigo para calcular el promedio de una lista de calificaciones y tradúcelo a C.

Inicio 
- Mostrar mensaje: "Ingrese la cantidad de notas:"
- Leer cantidad_notas
- Para i = 1 hasta cantidad_notas, hacer:
- Mostrar mensaje: "Ingrese la nota ", i
- Leer nota
- suma = suma + nota
- promedio = suma / cantidad_notas
- Mostrar mensaje: "El promedio es:", promedio

Fin

### Traducción a C

```#include <stdio.h>

int main() {
    // Declararo las variables que voy a utilizar
    int cantidad_notas;
    float suma = 0, promedio, nota;

    // Le pido al usuario la cantidad de notas que quiera ingresar
    printf("Ingrese la cantidad de notas: ");
    scanf("%d", &cantidad_notas);

    // Bucle para ingresar las notas una a una
    for (int i = 1; i <= cantidad_notas; i++) {
        printf("Ingrese la nota %d: ", i);
        scanf("%f", &nota);
        suma = suma + nota; // Acumulo la suma de las notas
    }

    // formula para el promedio
    promedio = suma / cantidad_notas;

    // termino mostrando el resultado
    printf("El promedio de las notas es: %.2f\n", promedio);

    return 0;
}
```
## > Pregunta orientadora
> 
> - ¿Por qué es importante comentar el código, aunque sea breve y conciso? _Indicarle al lector del codigo que hace cada parte del codigo hace que tanto el desarrollador le de a saber al lector que es lo que hace y el lector entiendo que es lo que el codigo hace en cada parte, sea programador o no._
## 6. Reto final

### Reto: toma el pseudocódigo de los 5 primeros ejercicios del Reto y realiza la traducción a C:

1. Revisa el pseudocódigo y verifica que no contenga errores.
2. **Traduce** ese pseudocódigo a C.
3. **Comenta** tu código para explicar los pasos principales.

### Primer Reto
```
#include <stdio.h>
#include <math.h>

int main() {
    // Declaro que variables voy a utilizar, en este caso double porque la distancia tambien puede darse en decimales
    double x1, y1, x2, y2;

    // le pido al usuario que ingrese las coordenadas del primer punto, el %lf es para escanear el dato double
    printf("Ingrese las coordenadas del primer punto (x1 y1): ");
    scanf("%lf %lf", &x1, &y1);

    // le pido al usuario que ingrese las coordenadas del segundo punto
    printf("Ingrese las coordenadas del segundo punto (x2 y2): ");
    scanf("%lf %lf", &x2, &y2);

    // ingreso la formula de distancia enter 2 puntos, sqrt() es para raíces y pow(,x) para potencias
    double distancia = sqrt(pow(x2 - x1, 2) + pow(y2 - y1, 2));

    // Display the calculated distance
    printf("La distancia entre el primer punto (%.2f, %.2f) y el segundo (%.2f, %.2f) es: %.2f\n", x1, y1, x2, y2, distancia);

    return 0;
}
```
### Segundo Reto
```
#include <stdio.h>

int main() {
    // Definino la constante para la conversión de metros a pulgadas
    const double PULGADAS_POR_METRO = 1 / 0.0254; // 1 metro = 39.3701 pulgadas

    // Declaro la variable para almacenar los metros
    double metros;

    // Le pido a la modista que ingrese la cantidad de metros
    printf("Ingrese la cantidad de metros: ");
    scanf("%lf", &metros);

    // Hago la conversión de metros a pulgadas
    double pulgadas = metros * PULGADAS_POR_METRO;

    // Muestro el resultado
    printf("Debes de pedir %.2f pulgadas.\n", pulgadas);

    return 0;
}
```
### Tercer Reto
```
#include <stdio.h>
#include <math.h>  // Sin esta no me deja usar la función sqrt()

int main() {
    // Declaro las variables
    double A, B, C;

    // Solicito al usuario los valores de los catetos
    printf("Ingrese el valor del cateto A: ");
    scanf("%lf", &A);

    printf("Ingrese el valor del cateto B: ");
    scanf("%lf", &B);

    // Uso el teorema de Pitágoras
    C = sqrt(A * A + B * B);

    // Muestro la respuesta
    printf("La hipotenusa del triángulo rectángulo es: %.1lf\n", C);

    return 0;
}
```
### Cuarto Reto
```
#include <stdio.h>

int main() {
    // Declaro las variables para la fecha de nacimiento
    int dia_cumple, mes_cumple, año_cumple;
    
    // Declaro las variables para la fecha actual
    int dia_hoy, mes_hoy, año_hoy;
    
    // Pido la fecha de nacimiento
    printf("Ingrese su fecha de nacimiento (dd mm aaaa): ");
    scanf("%d %d %d", &dia_cumple, &mes_cumple, &año_cumple);
    
    // Solicito la fecha actual
    printf("Ingrese la fecha actual (dd mm aaaa): ");
    scanf("%d %d %d", &dia_hoy, &mes_hoy, &año_hoy);
    
    // Calculo la edad
    int edad = año_hoy - año_cumple;
    
    // Verificar si ya cumplió años, edad-- es lo mismo que edad=edad-1 por si no ha cumplido
    if (mes_hoy < mes_cumple) {
        edad--;     
    } else if (mes_hoy == mes_cumple) {
        if (dia_hoy < dia_cumple) {
            edad--;
        }
    }
    
    // Determinar si hoy es su cumpleaños, el && significa "y" 
    if (mes_hoy == mes_cumple && dia_hoy == dia_cumple) {
        printf("Feliz Cumpleaños!\n");
    } else {
        if (mes_hoy > mes_cumple) {
            printf("Ya cumplió.\n");
        } else if (mes_hoy == mes_cumple) {
            if (dia_hoy > dia_cumple) {
                printf("Ya cumplió.\n");
            } else {
                printf("Aún no cumple.\n");
            }
        } else {
            printf("Aún no cumple.\n");
        }
    }
    
    // Imprimir la edad
    printf("Tu edad actual es: %d años.\n", edad);
    
    return 0;
}
```
### Quinto Reto
``` 
#include <stdio.h>

int main() {
    int horas_trabajadas;
    float pago_por_hora, sueldo_semanal;

    // Solicito al usuario las horas trabajadas y valor hora
    printf("Ingrese las horas trabajadas en la semana: ");
    scanf("%d", &horas_trabajadas);

    printf("Ingrese el pago por hora: ");
    scanf("%f", &pago_por_hora);

    // Calculo el sueldo semanal 
    if (horas_trabajadas <= 40) {
        sueldo_semanal = horas_trabajadas * pago_por_hora;
    } else if (horas_trabajadas <= 45) {
        sueldo_semanal = 40 * pago_por_hora + (horas_trabajadas - 40) * pago_por_hora * 2;
    } else if (horas_trabajadas <= 50) {
        sueldo_semanal = 40 * pago_por_hora + 5 * pago_por_hora * 2 + (horas_trabajadas - 45) * pago_por_hora * 3; // Acá se supone que si ha trabajado mas de 45 pero menos de 50, ya lleva las 5 horas extras dobles ganadas
    } else {
        printf("Error: No se permite trabajar más de 50 horas.\n");
        return 1; // Salgo del programa con código de error
    }

    // Mostrar el sueldo semanal
    printf("El sueldo semanal es: %.2f\n", sueldo_semanal);

    return 0;
}
```
> Pregunta final
> 
> - Después de este tutorial, ¿qué puntos crees que deberías reforzar para sentirte más seguro al traducir pseudocódigo a C? _Sin duda la parte que mas se me dificulta es la sintaxis, todos los codigos que hice arriba fueron a partir de paginas web, tutoriales en youtube y muchisimo ensayo y error, hasta la fecha no hemos aprendido en clase a programar como tal y todos estos temas no me quedan muy claros, la mayor dificultad es sobretodo declarar variables en las funciones en general._
