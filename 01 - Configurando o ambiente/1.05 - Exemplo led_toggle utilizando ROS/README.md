# ROS Led Toggle

* Adicione o exemplo [Blink]() da biblioteca do ros_lib na pasta **src/** que stá dentro de seu pacote do Workspace.

![alt text](https://github.com/LuisHBM/curso-piloto-MR01/blob/main/01%20-%20Configurando%20o%20ambiente/1.05%20-%20Exemplo%20led_toggle%20utilizando%20ROS/img/Blink.png)

O Blink nesse caso é um pouco diferente do que o que já vimos anteriromente, nesse a função a seguir é responsável por determinar se o led será ligado ou desligado:
```
void messageCb( const std_msgs::Empty& toggle_msg){
  digitalWrite(LED_BUILTIN, HIGH-digitalRead(LED_BUILTIN));
}
```
Se ficou cok dificuldade de entender basicamente funciona como no código a seguir:

![alt text](https://github.com/LuisHBM/curso-piloto-MR01/blob/main/01%20-%20Configurando%20o%20ambiente/1.05%20-%20Exemplo%20led_toggle%20utilizando%20ROS/img/Blink%20alterado.png)

```
void messageCb( const std_msgs::Empty& toggle_msg){
  if (digitalRead(LED_BUILTIN) == 0) {
     digitalWrite(LED_BUILTIN, 1);
  }else{
     delay(2000)
     digitalWrite(LED_BUILTIN, 0);
   }
}
```

* Carregue o código na ESP32.

* Execute o rosserial em seu terminal:

```
$ rosrun rosserial_arduino serial_node.py
```
* Envie um comando para o led ligar/desligar:

```
$ rostopic pub /toggle_led std_msgs/Empty "{}"
```