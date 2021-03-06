Quickstart (classic mode)
===============================================================================

This page provides a good introduction to Simple Azure in classic mode.

Deploying Azure Virtual Machine
-------------------------------------------------------------------------------

.. code-block:: python

   from simpleazure import SimpleAzure

   azure = SimpleAzure()
   azure.asm.create_vm()
   
You can change an operating system image by the ``set_image()`` function. For
example, *Ubuntu 12.04 distribution* can be selected like as follows:

.. code-block:: python

   azure.asm.set_image(label="Ubuntu Server 12.04.2 LTS")

This allows you to create a vm with the selected image. Note that
``set_image()`` must be used before calling the ``create_vm()`` function.

Deploying several machines
-------------------------------------------------------------------------------

``create_cluster()`` function allows you to create multiple machines at once.
``num=`` parameter can be used to specify the number of nodes.

.. code-block:: python

   azure = SimpleAzure()
   azure.asm.create_cluster(num=4)
   
   my-cluster-vm-0-87412
   {'request_id': '88c94c00288d42acaf877783f09c4558'}
   my-cluster-vm-1-61293
   {'request_id': 'abfd563c2c4f4926872b6b1dba27a93b'}
   my-cluster-vm-2-96085
   {'request_id': '29b55f6cb5e94cfdbf244a7c848c854d'}
   my-cluster-vm-3-46927
   {'request_id': 'b1a3446ebafe47a295df4c9d1b7d743c'}
   
Deploying a Virtual Machine from the community images (VM DEPOT)
-------------------------------------------------------------------------------

Personalized and preconfigured virtual machines images can be imported from the
community repository (http://vmdepot.msopentech.com).  This example explains as
how to deploy a virtual machine with the community image, Azure Data Science
Core.

.. code-block:: python

   azure = SimpleAzure()
   q = azure.asm.get_registered_image(name="Azure-Data-Science-Core")
   azure.asm.set_image(image=q)
   azure.asm.create_vm()
   
Simple Azure on Command Line Interface (CLI) (TBD)
-------------------------------------------------------------------------------

Simple Azure supports commands on a linux shell. For example, you can create
clusters of virtual machines on Windows Azure like `StarCluster
<http://star.mit.edu/cluster/index.html>`_ like as follows: (StarCluster is a
cluster-computing toolkit for Amazon EC2)

.. code-block:: console

   $ simpleazure-cluster start mycluster
