
**TEMA 1 Procedimientos y Funciones** 

+ **Procedimientos** 
Un procedimiento almacenado es un grupo de una o varias instrucciones, en nuestro caso Transact-SQL para SQL server, que se ejecutan secuencialmente algunas de sus caracteristicas son:

1. Aceptan parámetros de entrada y pueden devolver varios valores en forma de parámetros de salida al programa que realiza la llamada.

2. Contener instrucciones de programación que realicen operaciones en la base de datos, como también pueden contener llamadas a otros procedimientos.

3. Devolver un valor de estado a un programa que realiza una llamada para indicar si la operación se ha realizado correctamente o se han producido errores, y el motivo de estos.


**Ventajas de usar procedimientos almacenados**

* Tráfico de red reducido entre el cliente y el servidor: los comandos de un procedimiento se ejecutan en un único lote de código. Esto puede reducir significativamente el tráfico de red entre el servidor y el cliente porque únicamente se envía a través de la red la llamada que va a ejecutar el procedimiento.

* Mayor seguridad: varios usuarios y programas cliente pueden realizar operaciones en los objetos de base de datos subyacentes a través de un procedimiento, aunque los usuarios y los programas no tengan permisos directos sobre esos objetos subyacentes. El procedimiento controla qué procesos y actividades se llevan a cabo y protege los objetos de base de datos subyacentes. Esto elimina la necesidad de conceder permisos en cada nivel de objetos y simplifica los niveles de seguridad.

* Reutilización del código: el código de cualquier operación de base de datos redundante resulta un candidato perfecto para la encapsulación de procedimientos. De este modo, se elimina la necesidad de escribir de nuevo el mismo código, se reducen las inconsistencias de código y se permite que cualquier usuario o aplicación que cuente con los permisos necesarios pueda acceder al código y ejecutarlo.

* Mantenimiento más sencillo: cuando las aplicaciones cliente llaman a procedimientos y mantienen las operaciones de base de datos en la capa de datos, solo deben actualizarse los cambios de los procesos en la base de datos subyacente.

* Rendimiento mejorado: de forma predeterminada, un procedimiento se compila la primera vez que se ejecuta y crea un plan de ejecución que vuelve a usarse en posteriores ejecuciones. Como el procesador de consultas no tiene que crear un nuevo plan, normalmente necesita menos tiempo para procesar el procedimiento.

+ **Funciones** 
Al igual que las funciones de los lenguajes de programación, las funciones definidas por el usuario de SQL Server son rutinas que aceptan parámetros, realizan una acción y devuelven el resultado de esa acción como un valor. El valor devuelto puede ser un valor escalar único o un conjunto de resultados.

**Ventajas de las funciones definidas por el usuario**

* Programación modular: puede crear la función una vez, almacenarla en la base de datos y llamarla desde el programa tantas veces como desee.

* Ejecución más rápida: com pasa con los procedimientos almacenados, las funciones definidas por el usuario de Transact-SQL reducen el costo de compilación del código de Transact-SQL almacenando los planes en la caché y reutilizándolos para ejecuciones repetidas.

* Reducción del tráfico de red: una operación que filtra datos basándose en restricciones complejas que no se puede expresar en una sola expresión escalar se puede expresar como una función.

**Tipos de funciones**

* Funciones escalares : las funciones escalares definidas por el usuario devuelven un único valor de datos del tipo definido en la cláusula RETURNS. El tipo devuelto puede ser de cualquier tipo de datos excepto text, ntext, image, cursory timestamp.

* Funciones con valores de tabla: las funciones con valores de tabla definidas por el usuario devuelven un tipo de datos table. La tabla es el conjunto de resultados de una sola instrucción SELECT.

* Funciones del sistema : SQL Server proporciona numerosas funciones del sistema que se pueden usar para realizar diversas operaciones, estas no se pueden modificar.

* Funciones deterministas y no deterministas: las funciones deterministas siempre devuelven el mismo resultado cada vez que se llama con un conjunto específico de valores de entrada y tienen el mismo estado de la base de datos. Las funciones no deterministas pueden devolver resultados diferentes cada vez que se les llama con un conjunto específico de valores de entrada, incluso si el estado de la base de datos al que acceden sigue siendo el mismo.


**Diferencias entre procedimientos y funciones**

1. Tipo de retorno: una función siempre devuelve un valor, mientras que un procedimiento almacenado no es obligatorio que lo haga.

2. Parámetros: un procedimiento almacenado puede tener parámetros de entrada y salida, mientras que una función no puede tener parámetros de salida.

3. Llamadas: una función se puede llamar desde un procedimiento almacenado, pero no al revés.

4. Instrucciones :una función solo permite una instrucción SELECT, mientras que un procedimiento almacenado permite SELECT, INSERT, UPDATE y DELETE.

5. Transacciones: un procedimiento almacenado puede administrar transacciones, pero una función no.

6. Uso en declaraciones SELECT: una función se puede incrustar en una declaración SELECT, pero un procedimiento almacenado no. 
 

-------
**Desarrollo TEMA 1 Procedimientos y Funciones** 

Para el desarrollo de este tema se realizaron en primer lugar 3 procedimientos, uno que realiza un insert sobre la tabla gasto de nuestra base de dados del proyecto, otro que realiza un update sobre la tabla gasto y por último uno que realiza un delete sobre la tabla gasto.
Luego se pasa a las funciones que se realizaron 3 funciones que devuelven una tabla, en la que cada una realiza una operacion sobre la tabla gasto para un determinado consorcio, variando si se busca en un determinado año, si se busca entre un rango de fechas o si se busca discriminar por tipo de gasto.
Para finalizar se realizó un procedimiento y una funcion en la que ambos reciben un mismo tipo de parámetro, un id que refiere a un conserje, y la idea a probar es que ambas devuelvan los mismos resultados y comparando la eficiencia entre ellas.

En el siguiente enlace se encuentra el script sql referido a este tema

[Script Procedimientos y Funciones](https://github.com/TongaCasla/Proyecto_Consorcio_BaseDatos1/blob/main/script/Prodecimiento%20y%20Funciones/Prodecimientos.sql)

**Resultados**
+ Estructura del procedimiento InsertGasto

![Proced-InsertGasto](https://github.com/TongaCasla/Proyecto_Consorcio_BaseDatos1/blob/main/doc/Procedimientos_Funciones/Procedimiento.jpg)

+ Estructura de la función FuncionCalcularEdad

![FuncionCalcularEdad](https://github.com/TongaCasla/Proyecto_Consorcio_BaseDatos1/blob/main/doc/Procedimientos_Funciones/Funcion.jpg)

+ Ubicación de los procedimientos y funciones dentro de la base de datos

![Programabilidad](https://github.com/TongaCasla/Proyecto_Consorcio_BaseDatos1/blob/main/doc/Procedimientos_Funciones/ubicacionProceYFunc.jpg)

+ Comparación de los planes de ejecución de una funcion y de un procedimiento que devuelven el mismo resultado

    * Plan de ejecución de la función FuncionCalcularEdad

    ![Plan-Funcion](https://github.com/TongaCasla/Proyecto_Consorcio_BaseDatos1/blob/main/doc/Procedimientos_Funciones/PlanFuncion.jpg)

    * Plan de ejecución del procedimiento sp_CalcularEdadConBucle

    ![Plan-Procedimiento](https://github.com/TongaCasla/Proyecto_Consorcio_BaseDatos1/blob/main/doc/Procedimientos_Funciones/PlanProcedimiento.jpg)

    * Resultado de ambas querys

        * Querys

        -Procedimiento 

        exec dbo.sp_CalcularEdadConBucle @idconserje=1

        -Funcion

        select c.apeynom ,dbo.FuncionCalcularEdad(c.idconserje) as edad  from conserje c


        ![Resultado](https://github.com/TongaCasla/Proyecto_Consorcio_BaseDatos1/blob/main/doc/Procedimientos_Funciones/Resultado.jpg)

----
Respecto al tema de procedimientos y funciones se puede concluir que ambos reducen el tráfico de red , favorecen la reutilización de código y por ende una reducción en el costo de procesamiento al ejecutar las sentencias.
Ahora bien también tienen sus diferencias y el uso de uno u otro va a depender de la necesidad o de lo que se deba realizar. Por ejemplo en el desarrollo se vio que se puede hacer que un procedimiento simule la ejecución de una función, pero como se pudo observar el costo de ejecución es mucho mayor que el de la función y eso se traduce también en la cantidad y complejidad de las sentencias de código, en la que ejecutando la función se obtiene un resultado igual con menos costo de procesamiento y un grado de complejidad mucho menor en su estrucura.



-----

[Procedimientos-Microsoft](https://learn.microsoft.com/es-es/sql/relational-databases/stored-procedures/stored-procedures-database-engine?view=sql-server-ver16)

[Funciones-Microsoft](https://learn.microsoft.com/es-es/sql/relational-databases/user-defined-functions/user-defined-functions?view=sql-server-ver16)