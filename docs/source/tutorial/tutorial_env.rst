Anaconda
==========================

This tutorial teaches how to setup the python programming environment:
Anaconda (back-end) + JupyterLab (front-end)


#. Install Anacoda

   #. `Download <https://www.anaconda.com/distribution/#download-section>`_
         (python 3.7)

   #. Follow the installer instructions


#. Install JupyterLab
   
   #. Open the commnad line interface (Linux: terminal, Windows: Anaconda Prompt)

   #. Create and enter a new environment

       .. code-block:: none

            conda create -n jlab
            conda activate jlab

   #. Install JupyterLab

       .. code-block:: none

            conda install -c conda-forge jupyterlab

   #. `Start JupyterLab <https://jupyterlab.readthedocs.io/en/stable/getting_started/starting.html>`_

       .. code-block:: none

            jupyter lab
