Visão geral dos atuadores
=========================
Essa sessão discute sobre o controle de motor e pneumático
através de rápidos controladores, solenóides e pneumático, e
sua interface com C++ e Java WPILib.

Controladores de velocidade
---------------------------
Um controlador de velocidade é responsável em seu robô para fazer os motores mover.
Para brushed DC motors como também para CIMs ou 775s, o controlador de velocidade regula
a voltagem do que o motor recebe, muito parecido com uma lâmpada. Para
o controlador de velocidade Brushless como também para o Spark MAX, os controladores regulam
a energia entregue para cada "fase" do motor.

.. .. hint::
..     One can make a quick, non-competition-legal speed controller by
..     removing the motor from a cordless BRUSHED drill and attaching
..     PowerPoles or equivalents to the motor's leads. Make sure that
..     the voltage supplied by the drill will not damage the motor,
..     but note that the 775 is fine at up to 24 volts.

.. warning::
Conectando um  controlador de motor BRUSHLESS direto a energia, como também
para a convencional  controlador de motor brushed, irá destruir o motor!


Controladores de motores permitidos na FRC
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Controladores de velocidade vêm em muitas formas, tamanhos e conjuntos de recursos. Isso
é a lista completa de Controladores de Velocidade permitidos na FRC como de Janeiro 2020:

- DMC 60/DMC 60c Motor Controller (P/N: 410-334-1, 410-334-2)
- Jaguar Motor Controller (P/N: MDL-BDC, MDL-BDC24, and 217-3367) connected to PWM only
- Nidec Dynamo BLDC Motor with Controller to control integral actuator only (P/N 840205-000, am-3740)
- SD540 Motor Controller (P/N: SD540x1, SD540x2, SD540x4, SD540Bx1, SD540Bx2, SD540Bx4, SD540C)
- Spark Motor Controller (P/N: REV-11-1200)
- Spark MAX Motor Controller (P/N: REV-11-2158)
- Talon FX Motor Controller (P/N: 217-6515, 19-708850, am-6515, am-6515_Short) for controlling integral Falcon 500 only
- Talon Motor Controller (P/N: CTRE_Talon, CTRE_Talon_SR, and am-2195)
- Talon SRX Motor Controller (P/N: 217-8080, am-2854, 14-838288)
- Victor 884 Motor Controller (P/N: VICTOR-884-12/12)
- Victor 888 Motor Controller (P/N: 217-2769)
- Victor SP Motor Controller (P/N: 217-9090, am-2855, 14-868380)
- Victor SPX Motor Controller (P/N: 217-9191, 17-868388, am-3748)
- Venom Motor with Controller (P/N BDC-10001) for controlling integral motor only​

Pneumática
----------
Pneumática é um caminho rádido e fácil para fazer alguma coisa que é em um
estado ou outro usando compressão de ar. Para informações em operando
pneumática, veja :doc:`pneumatics`.



 Relay Modules permitidos na FRC
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- Spike H-Bridge Relay (P/N: 217-0220 and SPIKE-RELAY-H)
- Automation Direct Relay (P/N: AD-SSR6M12-DC200D, AD-SSR6M25-DC200D, AD-SSR6M40-DC200D)


Controladores pneumáticos permitidos na FRC
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- Pneumatics Control Module (P/N: am-2858, 217-4243)
