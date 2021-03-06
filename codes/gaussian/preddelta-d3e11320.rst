preddelta
-------------------------------------- 

.. toctree::
   :maxdepth: 5    
      
   /codes/gaussian/l103.catchall-d3e11331

=========

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
   | *source*                          | Gaussian log                      |
   +-----------------------------------+-----------------------------------+
   | id                                | preddelta                         |
   +-----------------------------------+-----------------------------------+
   | repeat                            | \*                                |
   +-----------------------------------+-----------------------------------+
   | name                              | Predicted change in Energy        |
   +-----------------------------------+-----------------------------------+
   | pattern                           | \\s*Predicted change in Energy.\* |
   +-----------------------------------+-----------------------------------+
   | endPattern                        | \\s*.\*                           |
   +-----------------------------------+-----------------------------------+
   | endPattern2                       | ~                                 |
   +-----------------------------------+-----------------------------------+
   | xml:base                          | l103/l103.preddelta.xml           |
   +-----------------------------------+-----------------------------------+

**Input.**

::

    Predicted change in Energy=-9.782485D-04
     

**Output text.**

.. code:: xml

   <comment class="example.output" id="l103.preddelta">
       <module cmlx:templateRef="preddelta">
         <list cmlx:templateRef="predicted">
           <scalar dataType="xsd:double" dictRef="g:predchange">-9.782485E-4</scalar>
         </list>
       </module>
     </comment>

**Template definition.**

.. code:: xml

   <record id="predicted">\s*Predicted change in Energy={E,g:predchange}.*</record>
   <templateList>  <xi:include href="l103/l103.catchall.xml" />
     </templateList>

.. |image0| image:: ../../imgs/Total.png
.. |image1| image:: ../../imgs/None.png
