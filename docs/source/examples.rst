=============
Examples
=============

We demonstrate how to use the MAESTRO to generate the required results using one of the provided mapping file in the repository.

- Go to maestro directory.


.. note::
   For more information, please see
   :ref:`Installation`.

- For this demonstration purposes, we will be using the following mapping file : **Resnet50_dla.m**. 

	- *All the default mapping files are provided here:*
	
	.. code-block:: default

		data/mapping

.. note::
   For more information on the Mapping, please see
   :ref:`Mapping Definition`.
   
   
- Change the contents of "run.sh" to use the given mapping file

.. code-block:: default
		
	--Mapping_file='data/mapping/Resnet50_dla.m'

.. note::
   For more information on the parameters in the run.sh, please see
   :ref:`Parameters Input to MAESTRO`.
	
- Run MAESTRO

.. code:: bash

	./run.sh
	
- The result will be generated in the maestro directory as : **Resnet50_dla.csv** giving results per layer for the given Mapping file.

.. note::
   For more information on the result analysis, please see
   :ref:`Result Analysis`.

	



