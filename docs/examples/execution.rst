Execution Libraries
===================

Many execution libraries can be used to display the output of IPyhton cells. We used ``MySTnb`` to parse and display the outputs presented in :doc:`./pydata`. In this section we'll show alternatives that runs code for you using a Jupyter like kernel.

Jupyterlite
-----------

.. warning::
    The jupyterLite lib is not yet providing a handle to switch from light to dark theme. If you consider using it in your documentation you should also enforce the light theme to your users.
    Follow https://github.com/jupyterlite/jupyterlite-sphinx/issues/69 for more information.

``jupyterlite-sphinx`` brings the power of `JupyterLite <https://jupyterlite.readthedocs.io/en/latest/>`__ to your Sphinx documentation. It makes a full JupyterLite deployment in your docs and provide some utilities for using that deployment easily.

This section demonstrate how it displays in a **pydata-sphinx-theme** context:

.. replite::
    :kernel: python
    :height: 600px
    :prompt: Try Replite!

    print("it's a test")

jupyter-sphinx
--------------

Another common library is ``jupyter-sphinx``.
This section demonstrates a subset of functionality to make sure it behaves as expected.

.. jupyter-execute::

    import matplotlib.pyplot as plt
    import numpy as np

    rng = np.random.default_rng()
    data = rng.standard_normal((3, 100))
    fig, ax = plt.subplots()
    ax.scatter(data[0], data[1], c=data[2], s=3)

.. jupyter-execute::

    import matplotlib.pyplot as plt
    import numpy as np

    # define a list of markevery cases to plot
    cases = [
        None,
        8,
        (30, 8),
        [16, 24, 32],
        [0, -1],
        slice(100, 200, 3),
        0.1,
        0.4,
        (0.2, 0.4)
    ]

    # data points
    delta = 0.11
    x = np.linspace(0, 10 - 2 * delta, 200) + delta
    y = np.sin(x) + 1.0 + delta

    fig, axs = plt.subplots(3, 3, figsize=(10, 6), layout='constrained')
    for ax, markevery in zip(axs.flat, cases):
        ax.set_title(f'markevery={markevery}')
        ax.plot(x, y, 'o', ls='-', ms=4, markevery=markevery)
