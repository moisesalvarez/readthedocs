.. _vasp.kpoints-d3e39887:

vasp.kpoints
============

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
   | *source*                          | VASP KPOINTS                      |
   +-----------------------------------+-----------------------------------+
   | id                                | vasp.kpoints                      |
   +-----------------------------------+-----------------------------------+
   | name                              | VASP KPOINTS                      |
   +-----------------------------------+-----------------------------------+
   | xml:base                          | topTemplate.xml                   |
   +-----------------------------------+-----------------------------------+

**Input.**

::

    Automatic generation mesh
    0
   Gamma
    3  3  1 
    0. 0. 0.
       

**Output text.**

.. code:: xml

   <comment class="example.output" id="vasp.kpoints">
           <module id="vasp.contcar">
               <scalar dataType="xsd:string" dictRef="v:meshScheme">Gamma</scalar>
               <array dataType="xsd:integer" dictRef="v:subdivisionN" size="3">3 3 1</array>
               <array dataType="xsd:double" dictRef="v:shiftS" size="3">0. 0. 0.</array>
           </module>
       </comment>

**Template definition.**

.. code:: xml

   <record repeat="2" />
   <record>{X,v:meshScheme}</record>
   <record>{3I,v:subdivisionN}</record>
   <record>{3F,v:shiftS}</record>
   <transform process="pullup" xpath=".//cml:scalar" />
   <transform process="pullup" xpath=".//cml:array" />
   <transform process="delete" xpath=".//cml:list" />

.. |image0| image:: ../../imgs/Total.png
.. |image1| image:: ../../imgs/Partial.png
