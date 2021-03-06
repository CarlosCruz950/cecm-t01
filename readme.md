# Tarea 01

| Asignatura | Descripción |
| ------ | ----------- |
| Temas Selectos de Mecatrónica  | 03 |
| TSM-2022-I| Tarea 01 |
| Robotica-2022-I   | Tarea 01 |
| Carlos Cruz   | ROS Simulación|

## OBJETIVOS

* Hacer que un robot modifique su comportamiento a partir de los siguientes comandos de texto: 
-Avanza [velocidad lineal] 
-Gira [velocidad angular] 
-Detente

* Hacer uso de publicadores y suscriptores únicamente para lograr la solución a la problemática

## INTRODUCCIÓN

En ROS sabemos que ya esta basado ene un patrón de diseño los cuales son problemas ya caracterizados con soluciones ya caracterizadas y encontramos múltiples elementos que nos ayudan a resolverlos. Por ejemplo tenemos a los nodos, tópicos y mensajes que en esta tarea nos ayudan a entablar esa comunicación entre paquetes de datos para sincronizarlos y realizar otras acciones que no están establecidas en el programa original.

Tópico: Sirve para hacer referencia a un nodo. Utilizan diferentes mensajes para transmitir la información entre los nodos. Mensajes: Es un formato serializado(conjunto de datos tipo cadena que puede ser convertido). Permite a los nodos programados en C++ y Python comunicarse entre ellos.

A través de la implementación de los tópicos podemos hacer referencia a los nodos y con ello transmitimos la información entre más nodos con el fin de establecer una tarea o acción que nosotros estamos deseando implementar en el robot.

## DESARROLLO

Básicamente hice uso de los elementos que habiamos aplicado con anterioridad en la clase, solamente tenía cambios muy pequeños e implemente nuevas líneas de código, en este caso de raw_input que permite la lectura de una cadena para que al leerla, inmediatamente realice la tarea que deseamos que haga, en este caso sea avanzar, girar o detener por completo el robot Turtle Bot 3. Esto mediante la ayuda de elementos como Velocidad lineal, que es la que permite el avance de forma normal, la velocidad angular que permite el giro en radianes y finalmente con una instrucción que permite que tanto la velocidad lineal como angular se vayan a 0 y el robot se detenga por completo.

```python
while(1):
            key=input("--> ")# Aqui la función recibe nuestro string
            # Preguntamos la accion y dependiendo de eso hacemos lo que nos indica
            if key == 'Avanza' or key == "avanza" :
                target_linear_vel = checkLinearLimitVelocity(target_linear_vel + LIN_VEL_STEP_SIZE)
                status = status + 1
                print("\nEl robot se encuentra avanzando\n")
            elif key == 'Gira' or key == "gira" :
                target_angular_vel = checkAngularLimitVelocity(target_angular_vel + ANG_VEL_STEP_SIZE)
                status = status + 1
                print("\nEl robot se encuentra girando\n")
            elif key == 'Detente' or key == 'detente' :
                target_linear_vel   = 0.0
                control_linear_vel  = 0.0
                target_angular_vel  = 0.0
                control_angular_vel = 0.0
                print("\nProceso completo. Robot estático\n")
            elif key == "Exit" or key == "exit":
                exit()
            else:
                print("\nPor favor ingresa bien las claves para realizar las acciones\n")
```

Ya después únicamente lo que se hace es inicializar el nodo para que pueda lograr el cometido de forma adecuada, esto mediante un suscriptor y un publicador que permitirán este intercambio de información.

## CONCLUSIONES

Se pudieron cumplir de forma satisfactoria los objetivos anteriormente planteados, ya que con el manejo correcto de la programación así como de los elementos como los nodos, tópicos y mensajes que deseamos mandar con ayuda de los publicadores y suscriptores el intercambio de información de un lugar a otro se logró además de que dejó una idea más clara para que futuros propósitos pueden servir el implementar estos elementos. Podría mejorar en otros elementos además de que me causo conflicto la implementación de las actualizaciones en GitHub porque de pronto me arrojaba errores que no podía implementar de forma adecuada estas actualizaciones.

## AUTOR 

Cruz Montero Carlos Enrique GitHubProfile: https://github.com/CarlosCruz950 
kcruzmontero@gmail.com

## BIBLIOGRAFÍA

Sánchez,Sandra. El Framework ROS. Escuela Politécnica Superior, Sevilla, 2019. URL(https://core.ac.uk/download/pdf/266365197.pdf).
