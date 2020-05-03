Operando cilindros pneumáticos
==============================

Usando o sistema de controle da FRC para controlar a pneumática
---------------------------------------------------------------
.. note:: Pneumatics Control Module (PCM) é a um dispositivo que utiliza a comunicação CAN que tem controle total do compressor  e até 8 módulos solenóides . A PCM é integrada em WPILib através de uma série de classes que simplificam o uso. O controle de circuito fechado do compressor e pressão é tratado pelo hardware da PCM e dos solenóides são manipulados pela Solenóide atualizada, que agora, controla os canais do solenóide na PCM. Além disso, um módulo PCM pode ser usado onde os módulo correspondentes aos solenóides são diferenciados pelo número do módulo nos construtores das classes de Solenóide e Compressor.


.. image:: images/pcm.jpg
    :width: 400

O Módulo de Controle Pneumático da CTR Electronics é responsável por regular a pressão
do robô usando um switch de pressão e um compressor e ligando e desligando os solenóides.
A PCM se comunica com o roboRIO através do CAN. Para obter mais informações, consulte a
Visão geral do hardware do sistema de controle FRC.

Números de módulos PCM
----------------------
Os módulos da PCM são identificados pelo seus Node ID. O padrão Node ID para
PCMs é 0. Se estiver usando um único PCM na linha CAN é recomendado deixá-lo
no padrão Node ID.

Gerando e armazenando pressão
-----------------------------
Na FRC, a pressão é criada usando um compressor pneumático e armazenada em tanques pneumáticos.
O compressor não precisa necessariamente estar no robô, mas deve ser alimentado pela PCM
do robô. O modo de “Closed Loop” no compressor é ativado por padrão, e é ele não recomenda que
as equipes de alterar essa configuração. Quando o "closed loop control" está ativado, o PCM liga
automaticamente o compressor quando o switch pressão está fechado (abaixo do limiar de pressão) e o
desliga quando o switch pressão está aberto (~ 120PSI). Quando o "loop control" está
desativado, o compressor não liga. Usando um compressor, os usuários podem consultar o status
do compressor. O estado (atualmente ativado ou desativado), o estado do switch pressão e a
corrente do compressor podem ser consultados no objeto Compressor.

.. note:: A PCM da Cross the Road Electronics permite para integrar closed loop control do compressor. Criando qualquer instância de um objeto Solenóide ou Solenóide Duplo habilitará o controle Compressor no PCM correspondente. O objeto Compressor é necessário apenas se você desejar desativar o compressor ou consultar o status do compressor.


Controle Solenóide
------------------
As equipes da FRC usam solenóides para realizar várias tarefas, desde a troca de caixas de velocidades até a operação de mecanismos de robô. Um solenóide é uma válvula usada para ativar eletronicamente uma linha de ar pressurizada "ligada" ou "desligada". Para obter mais informações sobre solenóides, consulte este artigo da Wikipedia <https://en.wikipedia.org/wiki/Solenoid_valve>`__.. Os solenóides são controlados pelo módulo de controle pneumático do robô, ou PCM, que por sua vez é conectado ao roboRIO do robô via CAN. A maneira mais fácil de ver o estado de um solenóide é através do pequeno LED vermelho (que indica se a válvula está "ligada" ou não), e os solenóides podem ser acionados manualmente quando não forem energizados com o pequeno botão adjacente ao LED.


Os solenóides de ação simples aplicam ou liberam a pressão de uma única porta de saída. Eles geralmente são usados ​​quando uma força externa fornece a ação de retorno do cilindro (mola, gravidade, mecanismo separado) ou em pares para atuar como um solenóide duplo. Um solenóide duplo alterna o fluxo de ar entre duas portas de saída (muitas também têm uma posição central em que nenhuma saída é ventilada ou conectada à entrada). As válvulas solenóides duplas são comumente usadas quando você deseja controlar as ações de extensão e retração de um cilindro usando a pressão do ar. As válvulas solenóides duplas têm duas entradas elétricas que se conectam novamente a dois canais separados na ruptura do solenóide.

Os módulos PCM são identificados pelo seu ID de dispositivo CAN. O ID CAN padrão para PCMs é 0. Se você estiver usando um único PCM no barramento, é recomendável deixá-lo no ID CAN padrão. Esse ID pode ser alterado com o aplicativo Phoenix Tuner, além de outras informações de depuração. O Phoenix Tuner pode ser baixado no GitHub.<https://github.com/CrossTheRoadElec/Phoenix-Releases>`_ Para obter mais informações sobre como definir IDs CAN do PCM, consulte Atualização e configuração do módulo de controle pneumático e do painel de distribuição de energia.

Solenóides únicos no WPILib
---------------------------
Solenóides únicos no WPILib são controlados usando a classe Solenóide. Para construir um objeto Solenóide, simplesmente passe o número da porta desejada (assume CAN ID 0) ou CAN ID e número da porta ao construtor. Para definir o valor do conjunto de chamadas do solenóide (true) para ativar ou definir (false) para desativar a saída do solenóide.


Double Solenoids in WPILib
--------------------------
Double solenoids are controlled by the DoubleSolenoid class in WPILib.
These are constructed similarly to the single solenoid but there are now
two port numbers to pass to the constructor, a forward channel (first)
and a reverse channel (second). The state of the valve can then be set
to kOff (neither output activated), kForward (forward channel enabled)
or kReverse (reverse channel enabled). Additionally, the PCM CAN ID can
be passed to the DoubleSolenoid if teams have a non-standard PCM CAN ID

.. tabs::

   .. code-tab:: java

        // Using "import static an.enum.or.constants.inner.class.*;" helps reduce verbosity
        // this replaces "DoubleSolenoid.Value.kForward" with just kForward
        // further reading is available at https://www.geeksforgeeks.org/static-import-java/
        import static edu.wpi.first.wpilibj.DoubleSolenoid.Value.*;

        DoubleSolenoid exampleDouble = new DoubleSolenoid(1, 2);
        DoubleSolenoid anotherDoubleSolenoid = new DoubleSolenoid(/* The PCM CAN ID */ 9, 4, 5);


        exampleDouble.set(kOff);
        exampleDouble.set(kForward);
        exampleDouble.set(kReverse);

   .. code-tab:: c++

        frc::DoubleSolenoid exampleDouble {1, 2};
        frc::DoubleSolenoid exampleDouble {/* The PCM CAN ID */ 9, 1, 2};

        exampleDouble.Set(frc::DoubleSolenoid::Value::kOff);
        exampleDouble.Set(frc::DoubleSolenoid::Value::kForward);
        exampleDouble.Set(frc::DoubleSolenoid::Value::kReverse);
