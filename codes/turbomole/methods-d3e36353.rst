.. _methods-d3e36353:

methods
=======

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
   | *source*                          | Turbomole control file            |
   +-----------------------------------+-----------------------------------+
   | id                                | methods                           |
   +-----------------------------------+-----------------------------------+
   | name                              | Method section                    |
   +-----------------------------------+-----------------------------------+
   | pattern                           | \\s*\u0024(?i:(dft|uhf))\s\*      |
   +-----------------------------------+-----------------------------------+
   | endPattern                        | \\s*\u0024.\*                     |
   +-----------------------------------+-----------------------------------+
   | endOffset                         | 0                                 |
   +-----------------------------------+-----------------------------------+
   | repeat                            | \*                                |
   +-----------------------------------+-----------------------------------+
   | xml:base                          | methods.xml                       |
   +-----------------------------------+-----------------------------------+

**Input.**

::

   $dft
    functional pbe0
    gridsize   6
    weight derivatives 
       

**Output text.**

.. code:: xml

   <comment class="example.output" id="methods">
           <module cmlx:lineCount="4" cmlx:templateRef="methods">
               <scalar dataType="xsd:string" dictRef="cc:method">dft</scalar>
               <scalar dataType="xsd:string" dictRef="cc:functional">pbe0</scalar>
           </module>
       </comment>

**Template definition.**

.. code:: xml

   <templateList>  <template pattern="\s*\u0024(dft|uhf)\s*" endPattern="~">    <record>\s*\u0024{A,cc:method}.*</record>    <templateList>      <template pattern="\s*(?i:functional).*" endPattern=".*" endPattern2="~">        <record>\s*(?i:functional){X,cc:functional}</record>
                   </template>      <template pattern="\s*(?i:gridsize).*" endPattern=".*" endPattern2="~">        <record>\s*(?i:gridsize){X,t:dftgridsize}</record>
                   </template>
               </templateList>                       
           </template>
       </templateList>
   <transform process="move" xpath=".//cml:scalar" to="." />
   <transform process="delete" xpath=".//cml:module" />

.. |image0| image:: ../../imgs/Total.png
.. |image1| image:: ../../imgs/None.png
