## Excepciones

### Indice

#### [1. Definición de error y excepcion](https://github.com/patoba/Curso-Java/blob/master/Java%20Intermedio/Excepciones/README.md#1-definicion-de-error-y-excepción)

#### [2. Clase Exception](https://github.com/patoba/Curso-Java/blob/master/Java%20Intermedio/Excepciones/README.md#2-clase-exception-1)

>* Excepciones basicas
>* Palabras reservadas try, catch y finally

#### [3. Clase Throwable](https://github.com/patoba/Curso-Java/blob/master/Java%20Intermedio/Excepciones/README.md#3-clase-throwable-1) 
>*  Palabras reservadas throw y throws

#### [4. Creacion de excepciones propias](https://github.com/patoba/Curso-Java/blob/master/Java%20Intermedio/Excepciones/README.md#4-creación-de-excepciones-propias)

### Retornos
1. [Curso Java](https://github.com/patoba/Curso-Java 'Curso Java')
2. [Java Intermedio](https://github.com/patoba/Curso-Java/tree/master/Java%20Intermedio 'Java Intermedio')
- - - -


### 1. Definicion de error y excepción
#### 1.1 Introducción
En la documentación de Java se define excepción cómo *Un evento, el cual ocurre durante la ejecución de un programa, que interrumpe el flujo normal de las instrucciones del programa.* . 

Cuando un error ocurre dentro de un método, el método crea un objeto llamado excepción. El objeto excepción contiene información del error, incluyendo el tipo de error y el estado del programa cuando el error ocurrió. Después de ue un metodo arroja una excepción Java intenta encontrar un manejador de excepcion, a este proceso se le llama *call stack*.

![](img/img_01.gif)

Se dice que el sistema cacha la excepción si después de realizar una busqueda exhaustiva, no encuentra una manejador de excepción adecuado.

#### 1.2 Definiciones

La clase throwable es la superclase de todos los errores y excepciones, solo las instancias de esta clase pueden ser arrojadas con throw y throws. Exception y error son clases hijas de la clase Throwable. Un objeto Throwable contiene la información del hilo en el momento que fue arrojado.

Tanto exception como error son utilizadas para representar excepciones, situaciones que interrumpen el flujo del programa, pero son usadas para tratar excepciones distintas.

* **Error** : Situaciones que no pueden ser manejables. Por ejemplo: poca memoria RAM, error en el disco duro. 
* **Exception** : Situaciones que pueden ser manejables.  
![](img/img_00.gif)

Las excepciones más comunes están contenidas en dos clases hijas de Exception, IOException y RuntimeException. También llamadas comprobadas o no comprobadas. 

* **Comprobadas** : Situaciones provocadas por el programador. Ejemplo : Errores lógicos. 
* **No Comprobadas** : Situaciones aparte del código del programa. Ejemplo: Ausencia de un archivo o un input mal puesto.

### 2. Clase Exception
#### 2.1 Introducción
La clase Exception es la clase padre de todos las Excepciones manejables. Algunos de los metodos más importante de Exception se muestran a continuación.

| Dato de Retorno | Cabecera                         | Descripción                                                                                                                    |
|-----------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| void            | addSuppresed(Throwable objeto)   | Describe la excepción exacta que se arrojó                                                                                    |
| void            | getMessage()                     | Retorna el mensaje de los detalles de este objeto Throwable                                                                    |
| Throwable       | getCause()                       | Retorna la causa por la cual el throwable fue arrojado (La causa es el throwable que causo que este throwable fuera arrojado) |
| void            | printStackTrace()                | Imprime la ruta de donde surgio la excepción.                                                                                  |

En el tema anterior, vimos que las situaciones de la clase Exception son las manejables y que se dividen en 2 tipos. Existe una gran variedad de excepciones, podemos verlas en la imagen siguiente. 
![](img/img_02.gif)

#### 2.2 Excepciones Básicas 
En la imagen anterior observamos una gran mayoria de las excepciones en Java. A continuación definiremos unas cuantas de ellas.


| Excepción                       | Descripción                                                                               | Ejemplo                          |
|---------------------------------|-------------------------------------------------------------------------------------------|----------------------------------|
| Arithmetic Exception            | Es arrojada cuando ocurre una excepción una operación aritmética.                         | División entre cero.             |
| ArrayIndexOutOfBoundException   | Es arrojada cuando se acceso a un indice ilegal de un arreglo.                            | Arreglo[-3]                      |
| ClassNotFoundException          | Es arrojada cuando se intenta acceder a una clase que no esta definida.                   | Class a = new ClaseNoExistente() |
| FileNotFoundException           | Esta excepción se genera cuando un archivo no es accesible o no se abre.                  |                                  |
| IOException                     | Se lanza cuando una operación de input/output falla o se interrumpe.                      |                                  |
| InterruptedException            | Se lanza cuando un hilo está esperando, durmiendo o procesando, y se interrumpe.          |                                  |
| NoSuchMethodException           | Se lanza cuando se accede a un método que no se encuentra.                                |                                  |
| NullPointerException            | Es arrojada cuando se hace referencia a los miembros de un objeto nulo.                   |                                  |
| Exception                       | Es arrojada cuando una excepción ocurre                                                   |                                  |
| StringIndexOutOfBoundsException | Arrojado por la clase String cuando un índice es negativo o mayor al tamaño de la cadena. |                                  |
| RuntimeException                | Esto representa cualquier excepción que se produce durante el tiempo de ejecución.        |                                  |


                           
#### 2.3 Palabras reservadas try, catch y finally
Hasta el momento sabemos que las excepciones se pueden manejar pero para manejarlas. Son manejadas para evitar la interrupción del flujo  del programa y para eso utilizamos tres bloques que son fundamentales para su manejo. 

##### Try
Para poder manejar una excepción lo primero que tenemos que hacer es definir en que parte del código puede sucitar. Esa parte es encerrada por un bloque try. 

```
try {
    codigo
}
bloque catch  . . .
```

##### Catch

Al bloque try le podemos asociar el bloque catch el cual define que hacer al detectar la excepcion. Cada bloque de catch define una excepcion definida como argumento. Esta excepción debe ser hija de la clase throwable. 

```
try {

} catch (ExceptionType name) {

} catch (ExceptionType name) {

}
```

También es posible cachar varios objetos en la misma sentencia,  utilizando el simbolo '|' en el argumento.

```
  catch (IOException|SQLException ex) {
      logger.log(ex);
      throw ex;
  }
```

##### Finally

El bloque finally siempre se ejecuta al terminar de ejecutarse el bloque try. Esto asegura que sin importar que se encuentre una excepcion o no el bloque finally siempre sera ejecutado.


```
  finally{
  
  }
```


### 3. Clase Throwable 
#### 3.1 Introducción 
Para evitar que exista una excepción , primero se tiene que arrojar desde alguna parte del código. Cualquier bloque de código puede arrojar excepciones. Pero existe una manera de definir en que momento en se va a arrojar una excepción en particular. 

#### 3.2 Palabras reservadas throw y throws 

##### throw
La palabra reservada throw es utilizada para arrojar explicitamente una excepción desde un bloque de código o un metodo. Solo se puede utilizar con clases que hereden de throwable. 

```
  public Object pop() {
    Object obj;

    if (size == 0) {
        throw new EmptyStackException();
    }
  }
```

Puede ayudar a prevenir el mal funcionamiento de un programa, al arrojar la excepción por una condición creada.

##### throws 
La palabra reservada throws es utilizada en metodos en los que puede surgir una excepción. 

```
  class tst { 
    public static void main(String[] args)throws InterruptedException 
    { 
        Thread.sleep(10000); 
        System.out.println("Hello Geeks"); 
    } 
  } 
```
Tabla de diferencias de throw y throws

| throw                                                                                        | throws                                                                                                     |
|----------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| La palabra clave de lanzamiento de Java se utiliza para lanzar explícitamente una excepción. | La palabra clave de Java se utiliza para declarar una excepción.                                           |
| La excepción marcada no se puede propagar usando solo lanzar.                                | Excepción comprobada se puede propagar con tiros.                                                          |
| El lanzamiento es seguido por una instancia.                                                 | Los lanzamientos son seguidos por clase.                                                                   |
| El tiro se utiliza dentro del método.                                                        | El tiro se utiliza dentro del método.                                                                      |
| No puedes lanzar múltiples excepciones.                                                      | Puede declarar múltiples excepciones, por ejemplo.  public void method () lanza IOException, SQLException. |
### 4. Creación de excepciones propias
En el caso que no existiria una excepción especifica para un problema que se tenga, se puede crear una excepción propia. Esta excepción tiene que heredar de la clase Exception, para que pueda ser arrojable. 

```
  public class Clase extends Exception{
    public Clase(){
      super();
    }
    
    public Clase(String message){
      super(message + "mensaje propio")
    }
  }
```



