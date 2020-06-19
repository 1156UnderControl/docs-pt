Potenciômetros analógicos - Software
====================================

.. note:: Esta seção aborda potenciômetros analógicos em software. Para obter um guia de hardware para potenciômetros analógicos, consulte  :ref:`docs/hardware/sensors/analog-potentiometers-hardware:Analog Potentiometers - Hardware`.

Potenciômetros são resistores variáveis ​​que permitem converter informações sobre a posição em um sinal de tensão analógico. Esse sinal pode ser lido pelo roboRIO para controlar qualquer dispositivo conectado ao potenciômetro.

Embora seja possível ler informações de um potenciômetro diretamente com um :doc:`analog-inputs-software`, o WPILib fornece uma :code:`AnalogPotentiometer` explicação (`Java <https://first.wpi.edu/FRC/roborio/release/docs/java/edu/wpi/first/wpilibj/AnalogPotentiometer.html>`__, `C++ <https://first.wpi.edu/FRC/roborio/release/docs/cpp/classfrc_1_1AnalogPotentiometer.html>`__) que lida com a redimensionamento dos valores em unidades significativas para o usuário. É altamente recomendável usar esta explicação.

De fato, o :code:`AnalogPotentiometer` nome é um nome impróprio - essa classe deve ser usada para a grande maioria dos sensores que retornam seu sinal como uma tensão analógica simples, em escala linear.

Explicação dos Potenciômetros analógicos
----------------------------------------

.. note:: Os parâmetros "faixa completa" ou "escala" no :code:`AnalogPotentiometer` construtor são fatores de escala de um intervalo de 0-1 ao intervalo real, não de 0-5. Ou seja, eles representam uma escala fracionária nativa, em vez de uma escala de tensão.

Personalizando o Potenciômetro analógico subjacente
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. note:: Se o usuário alterar a escala da :code:`AnalogInput` com superamostragem, isso deve ser refletido na configuração de escala passada para o

Usando potenciômetros analógicos no código
----------------------------------

Os sensores analógicos podem ser usados ​​no código da mesma maneira que outros sensores que medem a mesma coisa. Se o sensor analógico for um potenciômetro medindo um ângulo do braço, ele poderá ser usado de maneira semelhante a um :doc:`encoder <encoders-software>`.  Se for um sensor ultrassônico, pode ser usado de maneira semelhante a outros  :doc:`ultrasonics <ultrasonics-software>`.

É muito importante ter em mente que os potenciômetros físicos reais geralmente têm uma amplitude de movimento limitada. As salvaguardas devem estar presentes tanto no mecanismo físico quanto no código, para garantir que o mecanismo não quebre o sensor passando seu lance máximo.
