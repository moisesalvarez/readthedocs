electricproperties
=====================================

.. toctree::
   :maxdepth: 5  

   /codes/orca/dipole-d3e27226
   /codes/orca/quadrupole-d3e27289

==================

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
   | *source*                          | Orca log                          |
   +-----------------------------------+-----------------------------------+
   | id                                | electricproperties                |
   +-----------------------------------+-----------------------------------+
   | name                              | Electric Properties Calculation   |
   +-----------------------------------+-----------------------------------+
   | pattern                           | \\s*-+\s*$\s*ORCA\sELECTRIC\sPRO  |
   |                                   | PERTIES\sCALCULATION\s*$\s*-+\s\* |
   +-----------------------------------+-----------------------------------+
   | endPattern                        | \\s*(\*{20,}\s*)?$\s*-{40,}.\*    |
   +-----------------------------------+-----------------------------------+
   | endPattern2                       | \\s*Timings.\*                    |
   +-----------------------------------+-----------------------------------+
   | endPattern3                       | ~                                 |
   +-----------------------------------+-----------------------------------+
   | repeat                            | \*                                |
   +-----------------------------------+-----------------------------------+
   | endOffset                         | 0                                 |
   +-----------------------------------+-----------------------------------+
   | xml:base                          | job/electric                      |
   |                                   | properties/electricproperties.xml |
   +-----------------------------------+-----------------------------------+

**Input.**

::

   ------------------------------------------------------------------------------
                          ORCA ELECTRIC PROPERTIES CALCULATION
   ------------------------------------------------------------------------------

   Dipole Moment Calculation                       ... on
   Quadrupole Moment Calculation                   ... on
   Polarizability Calculation                      ... off
   GBWName                                         ... run.gbw
   Electron density file                           ... run.scfp.tmp

   -------------
   DIPOLE MOMENT
   -------------
                                   X             Y             Z
   Electronic contribution:     -2.73052      -4.20537       0.24659
   Nuclear contribution   :      3.48724       4.50131      -0.28886
                           -----------------------------------------
   Total Dipole Moment    :      0.75672       0.29593      -0.04226
                           -----------------------------------------
   Magnitude (a.u.)       :      0.81363
   Magnitude (Debye)      :      2.06808


   ------------------------
   QUADRUPOLE MOMENT (A.U.)
   ------------------------

                   XX           YY           ZZ           XY           XZ           YZ
     NUC       309.71894    532.88655      1.56654    194.61613    -18.36476    -25.54123
     EL       -336.59758   -568.46250    -37.10241   -194.83123     18.01215     25.52800
     TOT       -26.87864    -35.57595    -35.53587     -0.21510     -0.35261     -0.01323


   Timings for individual modules: 
       

**Output text.**

.. code:: xml

   <comment class="example.output" id="electricproperties">
           <module cmlx:templateRef="electricproperties" dictRef="cc:userDefinedModule">
             <array dataType="xsd:double" dictRef="cc:dipole" size="9">3.48724 -2.73052 0.75672 4.50131 -4.20537 0.29593 -0.28886 0.24659 -0.04226</array>
             <array dataType="xsd:double" dictRef="cc:quadrupole" size="18">309.71894 -336.59758 -26.87864 532.88655 -568.46250 -35.57595 1.56654 -37.10241 -35.53587 194.61613 -194.83123 -0.21510 -18.36476 18.01215 -0.35261 -25.54123 25.52800 -0.01323</array>
             <scalar dataType="xsd:double" dictRef="o:magnitude" units="nonsi2:au">0.81363</scalar>
             <scalar dataType="xsd:double" dictRef="o:magnitude" units="nonsi2:debye">2.06808</scalar>
          </module>
       </comment>

**Template definition.**

.. code:: xml

   <templateList>  <xi:include href="electricproperties/dipole.xml" />  <xi:include href="electricproperties/quadrupole.xml" />      
       </templateList>
   <transform process="move" xpath=".//cml:array" to="." />
   <transform process="move" xpath=".//cml:scalar" to="." />

.. |image0| image:: ../../imgs/Total.png
.. |image1| image:: ../../imgs/Partial.png
