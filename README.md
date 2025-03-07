# Diagrama_de_estados

    @startuml
    [*] --> standby
    standby --> validar_tarjeta: tarjeta introducida
    validar_tarjeta --> solicita_pin: tarjeta correcta
    validar_tarjeta --> standby: tarjeta incorrecta.
    
    solicita_pin --> elegir_transaccion: Pin correcto
    solicita_pin --> solicita_pin: Pin incorrecto(intento < 3)
    solicita_pin --> solicita_pin: pin incorrecto (3 intentos)
    solicita_pin --> standby: ingreso mal el pin 3 veces.
    
    elegir_transaccion --> realizar_transaccion: Usuario elige una transaccion
    realizar_transaccion --> elegir_transaccion: Ha elegido realizar otra transaccion
    realizar_transaccion --> standby: Ha elegido finalizar.
    @enduml

## Funcionamiento
- Está en stand by hasta que el usuario interectúe, donde este introduce la tarjeta, y si se valida se continuará con el proceso, pidiendo un pin.
- Si el pin da error, tendrá 3 oportunidades, pudiendo cancelar el proceso antes de que terminen dichas 3 oportunidades.
- Cuando se introduce correctamente, se podrá realizar la transacción, cuando esta se haga, se podrá hacer otra o salir del sistema, aunque solo cuando se termine el programa.

## Interpretación
- Hata que el usuario interactue se mantendrá en stand by.
- Pedirá hasta 3 veces el pin si no es correcto, si lo ingresa mal 3 veces volverá al stand by, igual que con la tarjeta.
- El usuario elijirá una transacción, y se le preguntará si quiere elegir otra o salir del sistema.
- Si elije salir, el cajero volverá a estar en un stand by.
