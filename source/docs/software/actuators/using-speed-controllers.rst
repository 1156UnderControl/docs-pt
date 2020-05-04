Usando controladores de motor no código
=======================================
Os controladores de motores têm dois tipos principais: CAN e PWM. Um controlador CAN pode enviar informações de status mais detalhadas de volta ao roboRIO, enquanto um controlador PWM pode ser definido apenas como um valor. Para obter informações sobre o uso desses motores com as classes de transmissão WPI, consulte :doc:`wpi-drive-classes`.

Usando controladores de velocidade PWM
--------------------------------------
Os controladores de velocidade PWM podem ser controlados da mesma forma que um controlador de velocidade CAN. Para obter um plano de fundo mais detalhado sobre *how* eles funcionam, consulte :doc:`pwm-controllers`. Para usar um controlador de velocidade PWM, basta usar a classe de controlador de velocidade apropriada fornecida pela WPI e fornecer a porta na qual os controladores de velocidade estão conectados no roboRIO. Todos os controladores de motor aprovados têm classes WPI fornecidas para eles.

Controladores CAN motor
-----------------------
Um punhado de controladores de velocidade CAN está disponível em fornecedores como CTR Electronics e REV Robotics.

SPARK MAX
^^^^^^^^^
Para obter informações sobre o SparkMAX CAN Speed ​​Controller, que pode ser usado no modo CAN ou PWM, consulte os  `software resources <https://www.revrobotics.com/sparkmax-software/>`_
e `example code. <https://github.com/REVrobotics/SPARK-MAX-Examples>`_

Controladores de motor CTRE CAN
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Consulte a documentação da CTR de terceiros no software Phoenix para obter informações mais detalhadas. A documentação está disponível `here. <https://phoenix-documentation.readthedocs.io/en/latest/>`_
