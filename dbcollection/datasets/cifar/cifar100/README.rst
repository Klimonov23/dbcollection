.. _cifar_100_readme:

=========
CIFAR-100
=========

This dataset is just like the **CIFAR-10**, except it has 100 classes containing 600
images each. There are 500 training images and 100 testing images per class.
The 100 classes in the **CIFAR-100** are grouped into 20 superclasses.
Each image comes with a "fine" label (the class to which it belongs) and a "coarse"
label (the superclass to which it belongs).


Use cases
=========

Image classification.


Properties
==========

- ``name``: cifar100
- ``keywords``: image_processing, classification
- ``dataset size``: 355,3 MB
- ``is downloadable``: **yes**
- ``tasks``: :ref:`classification (default) <cifar100_readme_classification>`


Tasks
=====

.. _cifar100_readme_classification:

classification (default)
------------------------

- :ref:`How to use <classification_how_to_use>`
- :ref:`Properties <classification_properties>`
- :ref:`HDF5 file structure <classification_hdf5_file_structure>`
- :ref:`Fields <classification_fields>`

.. _classification_how_to_use:

How to use
^^^^^^^^^^

.. code-block:: python

    >>> # import the package
    >>> import dbcollection as dbc
    >>>
    >>> # load the dataset
    >>> cifar100 = dbc.load('cifar100')
    >>> cifar100
    DataLoader: "cifar100" (classification task)


.. _classification_properties:

Properties
^^^^^^^^^^

- ``primary use``: image classification
- ``description``: Contains image tensors and label annotations for image classification.
- ``sets``: train, test
- ``metadata file size in disk``: 177,8 MB
- ``has annotations``: **yes**
    - ``which``:
        - labels for each image class/category.
- ``available fields``:
    - :ref:`classes <classification_fields_classes>`
    - :ref:`superclasses <classification_fields_superclasses>`
    - :ref:`images <classification_fields_images>`
    - :ref:`labels <classification_fields_labels>`
    - :ref:`coarse_labels <classification_fields_coarse_labels>`
    - :ref:`object_fields <classification_fields_object_fields>`
    - :ref:`object_ids <classification_fields_object_ids>`
    - :ref:`list_images_per_class <classification_fields_list_images_per_class>`
    - :ref:`list_images_per_superclass <classification_fields_list_images_per_superclass>`


.. _classification_hdf5_file_structure:

HDF5 file structure
^^^^^^^^^^^^^^^^^^^

::

    /
    ├── train/
    │   ├── classes        # dtype=np.uint8, shape=(100,18)  (note: string in ASCII format)
    │   ├── superclasses   # dtype=np.uint8, shape=(20,31)   (note: string in ASCII format)
    │   ├── images         # dtype=np.uint8, shape=(50000,32,32,3)
    │   ├── labels         # dtype=np.uint8, shape=(50000,)
    │   ├── coarse_labels  # dtype=np.uint8, shape=(50000,)
    │   ├── object_fields  # dtype=np.uint8, shape=(3,13)    (note: string in ASCII format)
    │   ├── object_ids     # dtype=np.int32, shape=(50000,3)
    │   ├── list_images_per_class        # dtype=np.int32, shape=(100,500))
    │   └── list_images_per_superclass   # dtype=np.int32, shape=(20,2500))
    │
    └── test/
        ├── classes        # dtype=np.uint8, shape=(100,18)  (note: string in ASCII format)
        ├── superclasses   # dtype=np.uint8, shape=(20,31)   (note: string in ASCII format)
        ├── images         # dtype=np.uint8, shape=(10000,32,32,3)
        ├── labels         # dtype=np.uint8, shape=(10000,)
        ├── coarse_labels  # dtype=np.uint8, shape=(10000,)
        ├── object_fields  # dtype=np.uint8, shape=(3,13)    (note: string in ASCII format)
        ├── object_ids     # dtype=np.int32, shape=(10000,3)
        ├── list_images_per_class        # dtype=np.int32, shape=(100,100))
        └── list_images_per_superclass   # dtype=np.int32, shape=(20,500))


.. _classification_fields:

Fields
^^^^^^

.. _classification_fields_classes:

- ``classes``: class descriptions
    - ``available in``: train, test
    - ``dtype``: np.uint8
    - ``is padded``: True
    - ``fill value``: 0
    - ``note``: strings stored in ASCII format

.. _classification_fields_superclasses:

- ``superclasses``: super class names. It is composed of groups of classes per super class
    - ``available in``: train, test
    - ``dtype``: np.uint8
    - ``is padded``: True
    - ``fill value``: 0
    - ``note``: strings stored in ASCII format

.. _classification_fields_images:

- ``images``: images tensor
    - ``available in``: train, test
    - ``dtype``: np.uint8
    - ``is padded``: False
    - ``fill value``: -1

.. _classification_fields_labels:

- ``labels``: class ids
    - ``available in``: train, test
    - ``dtype``: np.uint8
    - ``is padded``: False
    - ``fill value``: -1

.. _classification_fields_coarse_labels:

- ``coarse_labels``: superclass ids
    - ``available in``: train, test
    - ``dtype``: np.uint8
    - ``is padded``: False
    - ``fill value``: -1

.. _classification_fields_object_fields:

- ``object_fields``: list of field names of the object id list
    - ``available in``: train, test
    - ``dtype``: np.uint8
    - ``is padded``: True
    - ``fill value``: 0
    - ``note``: strings stored in ASCII format
    - ``note``: key field (*field name* aggregator)

.. _classification_fields_object_ids:

- ``object_ids``: list of field ids
    - ``available in``: train, test
    - ``dtype``: np.int32
    - ``is padded``: False
    - ``fill value``: -1
    - ``note``: key field (*field id* aggregator)

.. _classification_fields_list_images_per_class:

- ``list_images_per_class``: list of image ids per class
    - ``available in``: train, test
    - ``dtype``: np.int32
    - ``is padded``: True
    - ``fill value``: -1
    - ``note``: pre-ordered list

.. _classification_fields_list_images_per_superclass:

- ``list_images_per_superclass``: list of image ids per superclass
    - ``available in``: train, test
    - ``dtype``: np.int32
    - ``is padded``: True
    - ``fill value``: -1
    - ``note``: pre-ordered list


Disclaimer
==========

All rights reserved to the original creators of **CIFAR-100**.

For information about the dataset and its terms of use, please see this `link <https://www.cs.toronto.edu/~kriz/cifar.html>`_.
