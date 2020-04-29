.. include:: <isonum.txt>

Visão geral do Hardware do Sistema de Controle de FRC\ |reg|
============================================================

O objetivo desse documento é fornecer uma breve visão geral dos componentes de hardware que compõem o Sistema de Controle de FRC\ |reg|. Cada componente vai conter uma breve descrição da função do componente, uma breve lista de conexões críticas, e um link para mais documentação se disponível.

.. note:: Para instruções/diagramas de fiação completos, acesse o documento :doc:`Fiação do Sistema de Controle <how-to-wire-a-robot>`.

National Instruments roboRIO
----------------------------

.. image:: images/control-system-hardware/roborio.png

O NI-roboRIO é o principal controlador de robô usado para FRC. O roboRIO inclui um processador dual-core ARM Cortex™-A9 e FPGA que executa os elementos confiáveis ​​para controle e segurança, bem como o código gerado pela equipe. O Controlador integrado I/O inclui uma variedade de protocolos de comunicação (Ethernet, USB, CAN, SPI, I2C, e serial) como PWM, servo, digital I/O, e canais analógicos I/O usados para conectar os periféricos do robô para detecção e controle. O roboRIO deve conectar-se à porta de 12V no power distribuition panel. A comunicação com fio está disponível via USB ou Ethernet. Informações detalhadas sobre o roboRIO podem ser encontradas no `Manual do Usuário do roboRIO <https://www.ni.com/pdf/manuals/374474a.pdf>`__.

Power Distribution Panel
------------------------

.. image:: images/control-system-hardware/power-distribution-panel.png

A Power Distribution Panel (PDP) foi projetada para distribuir energia de uma bateria 12VDC para vários componentes do robô por meio de disjuntores com redefinição automática e um pequeno número de conexões com funções especiais. A PDP oferece 8 pares de saída classificados para corrente contínua de 40A e 8 pares classificados para corrente contínua de 30A. A PDP oferece conectores dedicados de 12V para o roboRIO, bem como conectores para o Voltage Regulator Module (VRM) e para o Pneumatics Control Module (PCM). Ela também inclui uma interface CAN para registrar a corrente, temperatura e tensão da bateria. Para informações mais detalhadas, consulte o `PDP User Manual <https://www.ctr-electronics.com/downloads/pdf/PDP%20User's%20Guide.pdf>`__.

Pneumatics Control Module
-------------------------

.. image:: images/control-system-hardware/pneumatics-control-module.png

A PCM é um dispositivo que contém todas as entradas e saídas necessárias para operar solenóides pneumáticas de 12V ou 24V e o compressor. A PCM é ativada/desativada pelo roboRIO através da interface CAN. A PCM contém uma entrada para o sensor de pressão e controlará o compressor automaticamente quando o robô estiver ativado e uma solenóide tiver sido criado no código. O dispositivo também coleta informações de diagnóstico, como o estado das solenóides, o estado do sensor de pressão, e o estado do compressor. O módulo inclui LEDs de diagnóstico para os canais de solenóide e CAN individualmente. Para mais informações, consulte o `Manual do Usuário da PCM <https://www.ctr-electronics.com/downloads/pdf/PCM%20User's%20Guide.pdf>`__.

Voltage Regulator Module
------------------------

.. image:: images/control-system-hardware/voltage-regulator-module.png

O VRM é um módulo independente que é alimentado por 12 volts. O dispositivo está conectado a um conector dedicado a ele na PDP. O módulo possui várias saídas reguladas de 12V e 5V. O objetivo do VRM é fornecer energia regulada para o rádio do robô, circuitos personalizados e câmeras de visão IP. Os dois pares de conectores associados a cada etiqueta têm uma classificação combinada do que a etiqueta indica (por exemplo, 5V / 500mA total para ambos os pares, não para cada par). O limite de 12V / 2A é uma classificação de pico, a fonte não deve ser carregada com mais de 1,5A de corrente contínua. Para mais informações, consulte o `Manual do Usuário do VRM <https://www.ctr-electronics.com/VRM%20User's%20Guide.pdf>`__.

Motor Controllers
-----------------

Há uma variedade de motor controllers diferentes que funcionam com o sistema de controle FRC e são aprovados para uso. Esses dispositivos são usados ​​para fornecer controle de tensão variável dos brushed DC motors usados ​​na FRC. Eles estão listados aqui em ordem alfabética.

DMC-60 and DMC-60C Motor Controller
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/control-system-hardware/dmc-60c-motor-controller.png

The DMC-60 is a PWM motor controller from Digilent. The DMC-60 features integrated thermal sensing and protection including current-foldback to prevent overheating and damage, and four multi-color LEDs to indicate speed, direction, and status for easier debugging. For more information, see the `DMC-60 reference manual <https://reference.digilentinc.com/_media/dmc-60/dmc60_rm.pdf>`__

The DMC-60C adds CAN smart controller capabilities to the DMC-60 controller. This enables closed loop control features and other intelligent control options. For more information see the `DMC-60C Product Page <https://store.digilentinc.com/dmc60c-digital-motor-controller-approved-for-first-robotics/>`__

Jaguar Motor Controller
^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/control-system-hardware/jaguar-motor-controller.png

The Jaguar Motor Controller from VEX Robotics (formerly made by Luminary Micro and Texas Instruments) is a variable speed motor controller for use in FRC. For FRC, the Jaguar may only be controlled using the PWM interface.

SD540B and SD540C Motor Controllers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/control-system-hardware/sdb540-motor-controller.png

The SD540 Motor Controller from Mindsensors is a variable speed motor controller for use in FRC. The SD540B is controlled using the PWM interface. The SD540C is controllable over CAN. Limit switches may be wired directly to the SD540 to limit motor travel in one or both directions. Switches on the device are used to flip the direction of motor travel, configure the wiring polarity of limit switches, set Brake or Coast mode, and put the device in calibration mode. For more information see the `Mindsensors FRC page <http://www.mindsensors.com/68-frc>`__

SPARK Motor Controller
^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/control-system-hardware/spark-motor-controller.png

The SPARK Motor Controller from REV Robotics is a variable speed motor controller for use in FRC. The SPARK is controlled using the PWM interface. Limit switches may be wired directly to the SPARK to limit motor travel in one or both directions. The RGB status LED displays the current state of the device including whether the device is currently in Brake mode or Coast mode. For more information, see the `REV Robotics SPARK product page <https://www.revrobotics.com/rev-11-1200/>`__

SPARK MAX Motor Controller
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/control-system-hardware/spark-max-motor-controller.png

The SPARK MAX Motor Controller from REV Robotics is a variable speed motor controller for use in FRC. The SPARK MAX is capable of controlling either the traditional brushed DC motors commonly used in FRC or the new brushless REV Robotics NEO Brushless Motor. The SPARK MAX can be controlled over PWM, CAN or USB (for configuration/testing only). The controller has a data port for sensor input and is capable of closed loop control modes when controlled over CAN or USB. For more information see the `REV Robotics SPARK MAX product page <https://www.revrobotics.com/rev-11-2158/>`__.

Talon Motor Controller
^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/control-system-hardware/talon-motor-controller.png

The Talon Motor Controller from Cross the Road Electronics is a variable speed motor controller for use in FRC. The Talon is controlled over the PWM interface. The Talon should be connected to a PWM output of the roboRIO and powered from the Power Distribution Panel. For more information see the `Talon User Manual <https://ctr-electronics.com/Talon_User_Manual_1_1.pdf>`__.

Talon SRX
^^^^^^^^^

.. image:: images/control-system-hardware/talonsrx-motor-controller.png

The Talon SRX motor controller is a CAN-enabled “smart motor controller” from Cross The Road Electronics/VEX Robotics. The Talon SRX has an electrically isolated metal housing for heat dissipation, making the use of a fan optional. The Talon SRX can be controlled over the CAN bus or PWM interface. When using the CAN bus control, this device can take inputs from limit switches and potentiometers, encoders, or similar sensors in order to perform advanced control such as limiting or PID(F) closed loop control on the device. For more information see the `Talon SRX User Manual <https://www.ctr-electronics.com/talon-srx.html>`__.

.. note:: CAN Talon SRX has been removed from WPILib. See this `blog <https://www.firstinspires.org/robotics/frc/blog/2017-control-system-update>`__ for more info and find the CTRE Toolsuite installer `here <https://www.ctr-electronics.com/Talon%20SRX%20User's%20Guide.pdf>`__.

Victor 888 Motor Controller / Victor 884 Motor Controller
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/control-system-hardware/victor-888-motor-controller.png

The Victor 888 Motor Controller from VEX Robotics is a variable speed motor controller for use in FRC. The Victor 888 replaces the Victor 884, which is also usable in FRC. The Victor is controlled over the PWM interface. The Victor should be connected to a PWM output of the roboRIO and powered from the Power Distribution Panel. For more information, see the `Victor 884 User Manual <https://content.vexrobotics.com/docs/ifi-v884-users-manual-9-25-06.pdf>`__ and `Victor 888 User Manual <https://content.vexrobotics.com/docs/217-2769-Victor888UserManual.pdf>`__.

Victor SP
^^^^^^^^^

.. image:: images/control-system-hardware/victor-sp-motor-controller.png

The Victor SP motor controller is a PWM motor controller from Cross The Road Electronics/VEX Robotics. The Victor SP has an electrically isolated metal housing for heat dissipation, making the use of the fan optional. The case is sealed to prevent debris from entering the controller. The controller is approximately half the size of previous models.

Victor SPX
^^^^^^^^^^

.. image:: images/control-system-hardware/victor-spx-motor-controller.png

The Victor SPX motor controller is a CAN or PWM controlled motor controller from Cross The Road Electronics/VEX Robotics. The device is connectorized to allow easy connection to the roboRIO PWM connectors or a CAN bus chain. When controlled over the CAN bus, the device has a number of the closed loop features also present in the Talon SRX. The case is sealed to prevent debris from entering the controller. For more information, see the `Victor SPX Webpage <https://www.vexrobotics.com/217-9191.html>`__.

.. note:: Victor SPX CAN control is not supported from WPILib. See `this blog <https://www.firstinspires.org/robotics/frc/blog/2017-control-system-update>`__ for more info and find the CTRE Toolsuite installer `here <https://www.ctr-electronics.com/control-system/hro.html#product_tabs_technical_resources>`__.

Spike H-Bridge Relay
--------------------

.. image:: images/control-system-hardware/spike-relay.png

The Spike H-Bridge Relay from VEX Robotics is a device used for controlling power to motors or other custom robot electronics. When connected to a motor, the Spike provides On/Off control in both the forward and reverse directions. The Spike outputs are independently controlled so it can also be used to provide power to up to 2 custom electronic circuits. The Spike H-Bridge Relay should be connected to a relay output of the roboRIO and powered from the Power Distribution Panel. For more information, see the `Spike User’s Guide <https://content.vexrobotics.com/docs/spike-blue-guide-sep05.pdf>`__.

Servo Power Module
------------------

.. image:: images/control-system-hardware/servo-power-module.png

The Servo Power Module from Rev Robotics is capable of expanding the power available to servos beyond what the roboRIO integrated power supply is capable of. The Servo Power Module provides up to 90W of 6V power across 6 channels. All control signals are passed through directly from the roboRIO. For more information, see the `Servo Power Module webpage <https://www.revrobotics.com/rev-11-1144/>`__.

Axis M1013/M1011/206 Ethernet Camera
------------------------------------

.. image:: images/control-system-hardware/axis-camera.png

The Axis M1013, M1011 and Axis 206 Ethernet cameras are used for capturing images/control-system-hardware for vision processing and/or sending video back to the Driver Station laptop. The camera should be wired to a 5V power output on the Voltage Regulator Module and an open ethernet port on the robot radio. For more information, see :ref:`Configuring an Axis Camera <docs/software/vision-processing/introduction/configuring-an-axis-camera:Configuring an Axis Camera>` and the `Axis 206 <https://www.axis.com/en-us/products/axis-206>`__, `Axis M1011 <https://www.axis.com/en-us/products/axis-m1011>`__, `Axis M1013 pages <https://www.axis.com/en-us/products/axis-m1013>`__.

Microsoft Lifecam HD3000
------------------------

.. image:: images/control-system-hardware/microsoft-lifecam.png

The Microsoft Lifecam HD3000 is a USB webcam that can be plugged directly into the roboRIO. The camera is capable of capturing up to 1280x720 video at 30 FPS. For more information about the camera, see the `Microsoft product page <https://www.microsoft.com/accessories/en-us/products/webcams/lifecam-hd-3000/t3h-00011#support>`__. For more information about using the camera with the roboRIO, see the :ref:`Vision Processing <docs/software/vision-processing/index:Vision Processing>` section of this documentation.

OpenMesh OM5P-AN or OM5P-AC Radio
---------------------------------

.. image:: images/control-system-hardware/openmesh-radio.png

Either the OpenMesh OM5P-AN or OpenMesh OM5P-AC wireless radio is used as the robot radio to provide wireless communication functionality to the robot. The device can be configured as an Access Point for direct connection of a laptop for use at home. It can also be configured as a bridge for use on the field. The robot radio should be powered by one of the 12V/2A outputs on the VRM and connected to the roboRIO controller over Ethernet. For more information, see :ref:`Programming your Radio <docs/getting-started/getting-started-frc-control-system/radio-programming:Programming your Radio>`.

The OM5P-AN `is no longer available for purchase <https://www.firstinspires.org/robotics/frc/blog/radio-silence>`__. The OM5P-AC is slightly heavier, has more cooling grates, and has a rough surface texture compared to the OM5P-AN.

120A Circuit Breaker
--------------------

.. image:: images/control-system-hardware/circuit-breaker.png

The 120A Main Circuit Breaker serves two roles on the robot: the main robot power switch and a protection device for downstream robot wiring and components. The 120A circuit breaker is wired to the positive terminals of the robot battery and Power Distribution boards. For more information, please see the `Cooper Bussmann 18X Series Datasheet (PN: 185120F) <http://www.cooperindustries.com/content/dam/public/bussmann/Transportation/Circuit%20Protection/resources/datasheets/BUS_Tns_DS_18X_CIRCUITBREAKER.pdf>`__

Snap Action Circuit Breakers
----------------------------

.. image:: images/control-system-hardware/snap-action-circuit-breaker.png

The Snap Action circuit breakers, MX5-A40 and VB3 series, are used with the Power Distribution Panel to limit current to branch circuits. The MX5-A40 40A MAXI style circuit breaker is used with the larger channels on the Power Distribution Panel to power loads which draw current up to 40A continuous. The VB3 series are used with the smaller channels on the PDP to power circuits drawing current of 30A or less continuous. For more information, see the Datasheets for the `MX5 series <http://www.snapaction.net/pdf/MX5%20Spec%20Sheet.pdf>`__ and `VB3 Series <http://www.snapaction.net/pdf/vb3.pdf>`__.

Robot Battery
-------------

.. image:: images/control-system-hardware/robot-battery.png

The power supply for an FRC robot is a single 12V 18Ah battery. The batteries used for FRC are sealed lead acid batteries capable of meeting the high current demands of an FRC robot. For more information, see the Datasheets for the `MK ES17-12 <https://www.batteryuniverse.com/msds/sealed-lead-acid-msds.pdf>`__ and `nersys NP18-12 <https://www.enersys.com/WorkArea/DownloadAsset.aspx?id=488>`__.

.. note:: Other battery part numbers may be legal, consult the `FRC Manual <https://www.firstinspires.org/resource-library/frc/competition-manual-qa-system>`__ for a complete list.

Image Credits
-------------

Image of roboRIO courtesy of National Instruments. Image of DMC-60 courtesy of Digilent. Image of SD540 courtesy of Mindsensors. Images of Jaguar Motor Controller, Talon SRX, Victor 888, Victor SP, Victor SPX, and Spike H-Bridge Relay courtesy of VEX Robotics, Inc. Image of SPARK MAX courtesy of REV Robotics. Lifecam, PDP, PCM, SPARK, and VRM photos courtesy of *FIRST*\ |reg|. All other photos courtesy of AndyMark Inc.
