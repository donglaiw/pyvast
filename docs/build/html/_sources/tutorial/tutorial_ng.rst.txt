Neuroglancer
==========================

3D image stack and segmentation visualization
    
#. (Windows Only) Install `Microsoft Visual C++
   <https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017>`_ (Community version)

#. Install Python back-end and add jupyter kernel
    
    .. code-block:: none 

        conda create -n ng
        conda activate ng
        conda install pip ipykernel imageio h5py numpy
        pip install neuroglancer
        python -m ipykernel install --user --name ng --display-name "ng"

#. Usage: 

   #. (Optional) `Download <http://hp03.mindhackers.org/rhoana_product/dataset/snemi.zip>`_ SNEMI neuron segmentation dataset
   
   #. Open a jupyter notebook (choose "ng" kernel) or `python -i THIS_FILE.py` (in "ng" conda env)

    .. code-block:: python
        
        import neuroglancer
        import numpy as np
        import imageio

        ip='localhost' # or public IP of the machine for sharable display
        port=98092 # change to an unused port number
        neuroglancer.set_server_bind_address(bind_address=ip,bind_port=port)
        viewer=neuroglancer.Viewer()

        # SNEMI
        D0='path/to/download/'
        res=[6,6,30]; # resolution of the data
        print('load im')
        im = imageio.volread(D0+'image/train-input.tif')
        with viewer.txn() as s:
            s.layers.append(
                name='im',
                layer=neuroglancer.LocalVolume(
                    data=im,
                    voxel_size=res
                ))

        print('load gt')
        gt = imageio.volread(D0+'seg/train-labels.tif')
        with viewer.txn() as s:
            s.layers.append(
                name='gt',
                layer=neuroglancer.LocalVolume(
                    data=gt.astype(np.uint16),
                    voxel_size=res
                ))

        print(viewer)
