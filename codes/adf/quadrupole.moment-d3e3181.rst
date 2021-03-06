.. _quadrupole.moment-d3e3181:

quadrupole.moment
=================

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
   | id                                | quadrupole.moment                 |
   +-----------------------------------+-----------------------------------+
   | pattern                           | \\s*Quadrupole Moment.\*          |
   +-----------------------------------+-----------------------------------+
   | endPattern                        | \\s*This molecular quadrupole     |
   |                                   | moment.\*                         |
   +-----------------------------------+-----------------------------------+
   | endOffset                         | 1                                 |
   +-----------------------------------+-----------------------------------+
   | repeat                            | \*                                |
   +-----------------------------------+-----------------------------------+
   | xml:base                          | results/quadrupole.moment.xml     |
   +-----------------------------------+-----------------------------------+

**Input.**

::

    Quadrupole Moment (Buckingham convention)  ***  (a.u.)  ***
    =========================================
        quad-xx        quad-xy        quad-xz        quad-yy        quad-yz        quad-zz
        54.58446200     0.00000000     0.00000000    54.58446200     0.00000000  -109.16892399

    This molecular quadrupole moment is calculated with analytic integration   
       

**Output text.**

.. code:: xml

   <comment class="example.output" id="quadrupole.moment">
           <module cmlx:lineCount="7" cmlx:templateRef="quadrupole.moment">
               <array dataType="xsd:double" size="6" dictRef="cc:quadrupole">54.584462 0.0 0.0 54.584462 0.0 -109.16892399</array>
           </module>
       </comment>

**Template definition.**

.. code:: xml

   <record repeat="4" />
   <record id="quadval">\s*{1_6F,cc:quadrupole}\s*</record>
   <record repeat="4" />
   <transform process="pullup" xpath=".//cml:array" />
   <transform process="delete" xpath=".//cml:list[count(*)=0]" />
   <transform process="delete" xpath=".//cml:list[count(*)=0]" />

.. |image0| image:: ../../imgs/Total.png
.. |image1| image:: ../../imgs/Total.png
