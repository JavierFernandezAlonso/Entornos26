# Entornos26
# Informe técnico

## 0. Proyecto
BuggyWebApp es una aplicación Java que simula el procesamiento de un formulario de 
contacto.

## 1. Descripción del problema
Al compilar la aplicación en Eclipse, el formulario se procesa correctamente, pero quedan campos vacíos. La variable name sí se recoge al principio del formulario, pero la variable email no es asimilada. 

## 2. Análisis técnico
- En MainApp: 
línea 13: userController.createUser("Juan", "juan@mail.com");
línea 17: contactController.submitContactForm("", "");
-En la clase Validator se incluye el método para validar el email, que contiene:
return email.contains("@");

El primer valor de submitContactForm es el nombre y el segundo es el email. Como el valor del email es "" y este no contiene "@", el programa no asimila el valor del correo electrónico. Al no estar contemplada la excepción para valores nulos o vacíos, el programa simplemente deja el valor en blanco. 

## 3. Propuesta de solución
Hay más de una solución posible para el problema:
a) Cambiar submitContactForm("", "") para introducir los valores: submitContactForm("Juan", "juan@mail.com")
b) Incluir en el método para validar el email un boolean falso si el valor del email es nulo o vacío. 
