=============
Examples
=============

We demonstrate how to use the MAESTRO to generate the required results using one of the provided mapping file in the repository.

- Go to maestro directory.


.. note::
   For more information, please see
   :ref:`Installation`.

- For this demonstration purposes, we will be using the following mapping file : **Resnet50_kcp.m**.

	- *All the default mapping files are provided here:*

	.. code-block:: default

		data/mapping

.. note::
   For more information on the Mapping Description, please see
   :ref:`Mapping Definition`.

- For this demonstration purposes, we will be using the following hardware description file : **accelerator_1.m**.

  - *All the default hardware description files are provided here:*

  .. code-block:: default

    data/hw

.. note::
      For more information on the Hardware Description, please see
      :ref:`Hardware Description`.


- Change the contents of "run_example.sh" to use the given mapping file

.. code-block:: default

	   --Mapping_file='data/mapping/Resnet50_kcp.m'

.. code-block:: default

     --HW_file='data/hw/accelerator_1.m'

.. note::
   For more information on the parameters in the run_example.sh, please see
   :ref:`Parameters Input to MAESTRO`.

- Run MAESTRO

.. code:: bash

	./run_example.sh

- The result will be generated in the maestro directory as : **Resnet50_kcp.csv** giving results per layer for the given Mapping file.

.. note::
   For more information on the result analysis, please see
   :ref:`Result Analysis`.
