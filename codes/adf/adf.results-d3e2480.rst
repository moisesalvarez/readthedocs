adf.results
-------------------------------------- 

.. toctree::
   :maxdepth: 5    
      
   /codes/adf/orbital.energies.spin.zora-d3e2487
   /codes/adf/orbital.energies.zora-d3e2587
   /codes/adf/orbital.energies-d3e2689
   /codes/adf/orbital.energies.spin-d3e2732
   /codes/adf/fit.test-d3e2777
   /codes/adf/mulliken-d3e2828
   /codes/adf/multipole-d3e3018
   /codes/adf/quadrupole.moment-d3e3181
   /codes/adf/s2-d3e3211
   /codes/adf/bonding.energy-d3e3240
   /codes/adf/sfo.population-d3e3344
   /codes/adf/excitation.energy-d3e3767

===========

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
   | id                                | adf.results                       |
   +-----------------------------------+-----------------------------------+
   | pattern                           | \\s                               |
   |                                   | *\*\s*R\sE\sS\sU\sL\sT\sS\s*\*.\* |
   +-----------------------------------+-----------------------------------+
   | endPattern                        | \\s*\W*\s                         |
   |                                   | *$\s*\*{20,}.*$(\s*|\s*LOGFILE.*) |
   +-----------------------------------+-----------------------------------+
   | offset                            | -1                                |
   +-----------------------------------+-----------------------------------+
   | endOffset                         | 2                                 |
   +-----------------------------------+-----------------------------------+
   | repeat                            | \*                                |
   +-----------------------------------+-----------------------------------+
   | xml:base                          | adf/results/results.xml           |
   +-----------------------------------+-----------------------------------+

**Comment.**

::

                                                   *******************
                                                   *  R E S U L T S  *
                                                   *******************
    
    
    Orbital Energies, all Irreps
    ========================================

    Irrep        no.  (spin)   Occup              E (au)                E (eV)
    ---------------------------------------------------------------------------
    F             1            14.00       -0.36757674632897E+00       -10.0023
    D             2             0.00        0.59810837659445E-01         1.6275
   ...
                                                   
    Orbital Energies, all Irreps, both Spins
    ========================================

    Irrep        no.  (spin)   Occup              E (au)                E (eV)
    ---------------------------------------------------------------------------
    A1            1     A       1.00       -0.22582773237906E+01       -61.4509
    A1            1      B      1.00       -0.22573719983754E+01       -61.4262
    A1            2     A       1.00       -0.22570204339745E+01       -61.4167
   ...

    =======================================================
    S F O   P O P U L A T I O N S ,   M O   A N A L Y S I S
    =======================================================
    ...

                                                   
    Fit test: (difference of exact and fit density, squared integrated, result summed over spins)
            Sum-of-Fragments:                             0.00000604855883
            Orthogonalized Fragments:                     0.01126932738939
            SCF:                                          0.00379056264226
   ...
    
    =======================================
    M U L L I K E N   P O P U L A T I O N S
    =======================================
   ...

    =========================================
    Quadrupole Moment (Buckingham convention)  ***  (a.u.)  ***
    =========================================
   ...

    ==========
    S**2 value  ***  see also R. Bulo et al., J.Am.Chem.Soc., 124 (2002) 13903-13910, note (29)  ***
    ==========
   ...

    ===========================
    B O N D I N G   E N E R G Y  ***  (decomposition)  ***
    ===========================
   ...

    ***************************************************************************************************    
       

**Template definition.**

.. code:: xml

   <templateList>  <xi:include href="results/orbital.energies.spin.zora.xml" />  <xi:include href="results/orbital.energies.zora.xml" />  <xi:include href="results/orbital.energies.xml" />  <xi:include href="results/orbital.energies.spin.xml" />  <xi:include href="results/fit.test.xml" />  <xi:include href="results/mulliken.xml" />  <xi:include href="results/multipole/multipole.xml" />  <xi:include href="results/quadrupole.moment.xml" />  <xi:include href="results/s2.xml" />  <xi:include href="results/bonding.energy.xml" />  <xi:include href="results/sfopopulation/sfo.population.xml" />  <xi:include href="results/excitationenergy/excitation.energy.xml" />     
       </templateList>

.. |image0| image:: ../../imgs/Total.png
.. |image1| image:: ../../imgs/None.png
