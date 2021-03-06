.. _molecular.orbitals.statistics-d3e33861:

molecular.orbitals.statistics
=============================

.. table:: Implementation level

   +-----------------------------------+-----------------------------------+
   | Type                              | Status                            |
   +===================================+===================================+
   | CML extraction template           | |image0|                          |
   +-----------------------------------+-----------------------------------+
   | HTML5 representation              | |image1|                          |
   +-----------------------------------+-----------------------------------+

.. table:: Template attributes

   +-----------------------------------+-----------------------------------+
   | Attribute                         | Value                             |
   +===================================+===================================+
   | *source*                          | Turbomole log                     |
   +-----------------------------------+-----------------------------------+
   | id                                | molecular.orbitals.statistics     |
   +-----------------------------------+-----------------------------------+
   | name                              | Molecular orbital statistic       |
   |                                   | section                           |
   +-----------------------------------+-----------------------------------+
   | pattern                           | \\s*M                             |
   |                                   | olecular\sOrbital\sStatistic:\s\* |
   +-----------------------------------+-----------------------------------+
   | endPattern                        | \\s*                              |
   |                                   | all\stogether\s*:.*$\s*-{20,}\s\* |
   +-----------------------------------+-----------------------------------+
   | endOffset                         | 2                                 |
   +-----------------------------------+-----------------------------------+
   | repeat                            | \*                                |
   +-----------------------------------+-----------------------------------+
   | xml:base                          | molecularorbital                  |
   |                                   | s/molecular.orbital.statistic.xml |
   +-----------------------------------+-----------------------------------+

**Input.**

::

      Molecular Orbital Statistic:
      ============================


      ---------------------
       irred. repres.:    a
      ---------------------
      frozen occupied:    0
      active occupied:   16
      active virtual :  132
      frozen virtual :    0
      ---------------------


      -----------------------------
      orbitals in total:
      -----------------------------
       frozen occupied :      0
       active occupied :     16
       active virtual  :    132
       frozen virtual  :      0
       all together    :    148
      -----------------------------    
       

**Output text.**

.. code:: xml

   <comment class="example.output" name="molecular.orbitals.statistics">
           <module cmlx:templateRef="molecular.orbitals.statistics">
               <scalar dataType="xsd:integer" dictRef="t:frozenocc">0</scalar>
               <scalar dataType="xsd:integer" dictRef="t:activeocc">16</scalar>
               <scalar dataType="xsd:integer" dictRef="t:activevirt">132</scalar>
               <scalar dataType="xsd:integer" dictRef="t:frozenvirt">0</scalar>
               <scalar dataType="xsd:integer" dictRef="t:orbitalsum">148</scalar>
           </module>   
      </comment>

**Template definition.**

.. code:: xml

   <templateList>  <template pattern="\s*orbitals\sin\stotal:\s*" endPattern="\s*all\stogether\s*:.*$\s*-{20,}\s*" endOffset="1">    <record repeat="2" />    <record>\s*frozen\soccupied\s*:{I,t:frozenocc}</record>    <record>\s*active\soccupied\s*:{I,t:activeocc}</record>    <record>\s*active\svirtual\s*:{I,t:activevirt}</record>    <record>\s*frozen\svirtual\s*:{I,t:frozenvirt}</record>    <record>\s*all\stogether\s*:{I,t:orbitalsum}</record>    <transform process="pullup" xpath=".//cml:scalar" repeat="2" />    <transform process="delete" xpath=".//cml:list" />    <transform process="delete" xpath=".//cml:list" />         
           </template>       
       </templateList>

.. |image0| image:: ../../imgs/Total.png
.. |image1| image:: ../../imgs/None.png
