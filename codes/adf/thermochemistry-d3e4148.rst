.. _thermochemistry-d3e4148:

thermochemistry
===============

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
   | *source*                          | ADF log                           |
   +-----------------------------------+-----------------------------------+
   | id                                | thermochemistry                   |
   +-----------------------------------+-----------------------------------+
   | pattern                           | \\s*                              |
   |                                   | Statistical\sThermal\sAnalysis.\* |
   +-----------------------------------+-----------------------------------+
   | endPattern                        | \\s*\*{10}+\s\*                   |
   +-----------------------------------+-----------------------------------+
   | endPattern2                       | \                                 |
   |                                   | \s*={10,}+\s*$\s*\S+.*$\s*={10,}+ |
   +-----------------------------------+-----------------------------------+
   | endPattern3                       | ~                                 |
   +-----------------------------------+-----------------------------------+
   | endOffset                         | 0                                 |
   +-----------------------------------+-----------------------------------+
   | xml:base                          | freq                              |
   |                                   | uencyanalysis/thermochemistry.xml |
   +-----------------------------------+-----------------------------------+

**Input.**

::

       
    ============================
    Statistical Thermal Analysis  ***  ideal gas assumed  ***
    ============================
     
    Pressure:                  1.000000 atm.
    Temperature:             300.000000 K



    Moments of Inertia (and direction vectors)
    ==========================================

          41342.8675      42584.1405      47497.7524
    ------------------------------------------------
              0.9979          0.0640          0.0012
              0.0640         -0.9973         -0.0372
              0.0012         -0.0372          0.9993


    The rotational contribution to the molecular entropy includes
    a term, dependent on the symmetry number sigma. The results 
    reported below were computed using sigma = 1, determined
    from the point group symmetry of the input geometry (NOSYM).
    If this is not the correct symmetry, please contact SCM to 
    report a bug.


        Temp                                                       Transl     Rotat    Vibrat     Total
        ----                                                       ------     -----    ------     -----

        300.00   Entropy (cal/mole-K):                             47.312    39.674   110.986   197.972
                 Internal Energy (Kcal/mole):                       0.894     0.894   335.070   336.859
                 Constant Volume Heat Capacity (cal/mole-K):        2.981     2.981   179.493   185.455
    
    ************************************************************************************************
       

**Output text.**

.. code:: xml

   <comment class="example.output" id="thermochemistry"> 
           <module cmlx:lineCount="35" cmlx:templateRef="thermochemistry">       
               <scalar dataType="xsd:double" dictRef="cc:press" units="nonsi:atm">1.0</scalar>
               <scalar dataType="xsd:double" dictRef="cc:temp" units="si:k">300.0</scalar>
               <module cmlx:lineCount="6" cmlx:templateRef="energies">
                  <scalar dataType="xsd:double" dictRef="cc:temp" units="nonsi2:cal.mol-1.K-1">300.0</scalar>
                  <list cmlx:templateRef="entropy">               
                     <scalar dataType="xsd:double" dictRef="cc:transl" units="nonsi2:cal.mol-1.K-1">47.312</scalar>
                     <scalar dataType="xsd:double" dictRef="cc:rotat" units="nonsi2:cal.mol-1.K-1">39.674</scalar>
                     <scalar dataType="xsd:double" dictRef="cc:vibrat" units="nonsi2:cal.mol-1.K-1">110.986</scalar>
                     <scalar dataType="xsd:double" dictRef="cc:total" units="nonsi2:cal.mol-1.K-1">197.972</scalar>
                  </list>
                  <list cmlx:templateRef="internalEnergy">
                     <scalar dataType="xsd:double" dictRef="cc:transl" units="nonsi2:kcal.mol-1">0.894</scalar>
                     <scalar dataType="xsd:double" dictRef="cc:rotat" units="nonsi2:kcal.mol-1">0.894</scalar>
                     <scalar dataType="xsd:double" dictRef="cc:vibrat" units="nonsi2:kcal.mol-1">335.07</scalar>
                     <scalar dataType="xsd:double" dictRef="cc:total" units="nonsi2:kcal.mol-1">336.859</scalar>
                  </list>
                  <list cmlx:templateRef="heat">
                     <scalar dataType="xsd:double" dictRef="cc:transl" units="nonsi2:cal.mol-1.K-1">2.981</scalar>
                     <scalar dataType="xsd:double" dictRef="cc:rotat" units="nonsi2:cal.mol-1.K-1">2.981</scalar>
                     <scalar dataType="xsd:double" dictRef="cc:vibrat" units="nonsi2:cal.mol-1.K-1">179.493</scalar>
                     <scalar dataType="xsd:double" dictRef="cc:total" units="nonsi2:cal.mol-1.K-1">185.455</scalar>
                  </list>
               </module>
           </module> 
       </comment>

**Template definition.**

.. code:: xml

   <templateList>  <template id="temppressure" pattern="\s*Pressure:.*" endPattern="\s*Temperature:.*" endOffset="1">    <record id="pressure">\s*Pressure:{F,cc:press}.*</record>    <record id="temperature">\s*Temperature:{F,cc:temp}.*</record>    <transform process="pullup" xpath=".//cml:scalar" />
           </template>  <template id="energies" pattern="\s*Temp\s*Transl.*" endPattern="\s*Constant\sVolume\sHeat.*" endOffset="1" repeat="*">    <record repeat="3" />    <record id="entropy">{F,cc:temp}Entropy\s*\(cal/mole-K\):{F,cc:transl}{F,cc:rotat}{F,cc:vibrat}{F,cc:total}</record>    <record id="internalEnergy">\s*Internal\sEnergy\s\(Kcal/mole\):{F,cc:transl}{F,cc:rotat}{F,cc:vibrat}{F,cc:total}</record>    <record id="heat">\s*Constant\sVolume\sHeat\sCapacity\s\(cal/mole-K\):{F,cc:transl}{F,cc:rotat}{F,cc:vibrat}{F,cc:total}</record>
           </template>   
       </templateList>
   <transform process="pullup" xpath=".//cml:scalar" />
   <transform process="addUnits" xpath="./cml:scalar[@dictRef='cc:temp']" value="si:k" />
   <transform process="addUnits" xpath="./cml:scalar[@dictRef='cc:press']" value="nonsi:atm" />
   <transform process="addUnits" xpath=".//cml:list[@cmlx:templateRef='entropy' or @cmlx:templateRef='heat']/cml:scalar" value="nonsi2:cal.mol-1.K-1" />
   <transform process="addUnits" xpath=".//cml:list[@cmlx:templateRef='internalEnergy']/cml:scalar" value="nonsi2:kcal.mol-1" />
   <transform process="pullup" xpath=".//cml:list[@cmlx:templateRef='entropy']/cml:scalar[@dictRef='cc:temp']" />
   <transform process="delete" xpath=".//cml:list[count(*)=0]" />
   <transform process="delete" xpath=".//cml:list[count(*)=0]" />
   <transform process="delete" xpath=".//cml:module[count(*)=0]" />

.. |image0| image:: ../../imgs/Total.png
.. |image1| image:: ../../imgs/Total.png
