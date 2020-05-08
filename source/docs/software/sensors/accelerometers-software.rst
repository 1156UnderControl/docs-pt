Acelerômetros - Software
========================

.. note:: Esta seção abrange acelerômetros em software. Para obter um guia de hardware para acelerômetros, consulte :ref:`docs/hardware/sensors/accelerometers-hardware:Accelerometers - Hardware`.

Um acelerômetro é um dispositivo que mede a aceleração.

Os acelerômetros geralmente vêm em dois tipos: eixo único e 3 eixos. Um acelerômetro de eixo único mede a aceleração ao longo de uma dimensão espacial; um acelerômetro de 3 eixos mede a aceleração ao longo das três dimensões espaciais de uma só vez.

O WPILib suporta acelerômetros de eixo único através da  `AnalogAccelerometer`_ .

Os acelerômetros de três eixos geralmente exigem protocolos de comunicação mais complicados (como SPI ou I2C) para enviar dados multidimensionais. O WPILib possui suporte nativo para os seguintes acelerômetros de 3 eixos:
- `ADXL345_I2C`_
- `ADXL345_SPI`_
- `ADXL362`_
- `BuiltInAccelerometer`_

Acelerômetro analógico
----------------------

The :code:`AnalogAccelerometer`  (`Java <https://first.wpi.edu/FRC/roborio/release/docs/java/edu/wpi/first/wpilibj/AnalogAccelerometer.html>`__, `C++ <https://first.wpi.edu/FRC/roborio/release/docs/cpp/classfrc_1_1AnalogAccelerometer.html>`__) permite que os usuários leiam valores de um acelerômetro de eixo único conectado a uma das entradas analógicas do roboRIO.

Se os usuários tiverem um acelerômetro analógico de 3 eixos, poderão usar três instâncias dessa classe, uma para cada eixo.

A interface do acelerômetro
---------------------------

Todos os acelerômetros de 3 eixos no WPILib implementam a :code:`Accelerometer` interface (`Java <https://first.wpi.edu/FRC/roborio/release/docs/java/edu/wpi/first/wpilibj/interfaces/Accelerometer.html>`__, `C++ <https://first.wpi.edu/FRC/roborio/release/docs/cpp/classfrc_1_1Accelerometer.html>`__). Essa interface define a funcionalidade e as configurações comuns a todos os acelerômetros de 3 eixos suportados.

O :code:`Accelerometer` interface contém getters para a aceleração ao longo de cada direção cardinal (x, ye z), bem como um setter para o intervalo de acelerações que o acelerômetro medirá.

.. warning:: Nem todos os acelerômetros são capazes de medir todas as faixas.

ADXL345_I2C
^^^^^^^^^^^

A :code:`ADXL345_I2C` (`Java <https://first.wpi.edu/FRC/roborio/release/docs/java/edu/wpi/first/wpilibj/ADXL345_I2C.html>`__, `C++ <https://first.wpi.edu/FRC/roborio/release/docs/cpp/classfrc_1_1ADXL345__I2C.html>`__) fornece suporte para o acelerômetro ADXL345 através do barramento de comunicação I2C.

ADXL345_SPI
^^^^^^^^^^^

A :code:`ADXL345_SPI` (`Java <https://first.wpi.edu/FRC/roborio/release/docs/java/edu/wpi/first/wpilibj/ADXL345_SPI.html>`__, `C++ <https://first.wpi.edu/FRC/roborio/release/docs/cpp/classfrc_1_1ADXL345__SPI.html>`__) fornece suporte para o acelerômetro ADXL345 por meio do barramento de comunicações SPI communications.

ADXL362
^^^^^^^

A :code:`ADXL362` (`Java <https://first.wpi.edu/FRC/roborio/release/docs/java/edu/wpi/first/wpilibj/ADXL362.html>`__, `C++ <https://first.wpi.edu/FRC/roborio/release/docs/cpp/classfrc_1_1ADXL362.html>`__) fornece suporte para o acelerômetro ADXL362 através do barramento de comunicações SPI.

BuiltInAccelerometer
^^^^^^^^^^^^^^^^^^^^

A :code:`BuiltInAccelerometer` (`Java <https://first.wpi.edu/FRC/roborio/release/docs/java/edu/wpi/first/wpilibj/BuiltInAccelerometer.html>`__, `C++ <https://first.wpi.edu/FRC/roborio/release/docs/cpp/classfrc_1_1BuiltInAccelerometer.html>`__) fornece acesso ao próprio acelerômetro interno do roboRIO:

Third-party accelerometers
--------------------------
Embora o WPILib forneça suporte nativo para vários acelerômetros disponíveis no kit de peças ou através da FIRST Choice, existem alguns dispositivos populares AHRS (Sistema de Referência de Atitude e Direção) comumente usados ​​no FRC que incluem acelerômetros. Eles geralmente são controlados por meio de bibliotecas de fornecedores, embora, se tiverem uma saída analógica simples, possam ser usados ​​com `AnalogAccelerometer`_

Usando acelerômetros no código
------------------------------

.. note:: Acelerômetros, como o próprio nome sugere, medem a aceleração. Acelerômetros precisos podem ser usados ​​para determinar a posição através da dupla integração (já que a aceleração é a segunda derivada da posição), da mesma maneira que os giroscópios são usados ​​para determinar a direção. No entanto, os acelerômetros disponíveis para uso em FRC não têm qualidade suficientemente alta para serem usados ​​dessa maneira.

Recomenda-se o uso de acelerômetros no FRC para qualquer aplicação que precise de uma medição aproximada da aceleração atual. Isso pode incluir a detecção de colisões com outros robôs ou elementos de campo, para que os mecanismos vulneráveis ​​possam ser retraídos automaticamente. Eles também podem ser usados ​​para determinar quando o robô está passando por terrenos acidentados para uma rotina autônoma (como atravessar as defesas no FIRST Stronghold).

Para detectar colisões, geralmente é mais robusto medir o empurrão do que a aceleração. O empurrão é a derivada (ou taxa de mudança) da aceleração e indica a rapidez com que as forças do robô estão mudando - o impulso repentino de uma colisão causa um aumento acentuado no empurrão. Jerk pode ser determinado simplesmente tomando a diferença das medições de aceleração subsequentes e dividindo pelo tempo entre elas:

A maioria dos acelerômetros legais para o uso de FRC é bastante barulhenta e geralmente é uma boa ideia combiná-los com a :code:`LinearFilter`  (`Java <https://first.wpi.edu/FRC/roborio/release/docs/java/edu/wpi/first/wpilibj/filters/LinearDigitalFilter.html>`__, `C++ <https://first.wpi.edu/FRC/roborio/release/docs/cpp/classfrc_1_1LinearDigitalFilter.html>`__) para reduzir o ruído.
