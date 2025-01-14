.. Copyright (c) Jupyter Development Team.
.. Distributed under the terms of the Modified BSD License.

Frequently Asked Questions (FAQ)
================================

Below are some frequently asked questions. Click on a question to be directed to
relevant information in our documentation or our GitHub repo.

General
-------

-  :ref:`What is JupyterLab? <overview>`
-  :ref:`What will happen to the classic Jupyter Notebook? <classic>`
-  `Where is the official online documentation for JupyterLab? <https://jupyterlab.readthedocs.io>`__
-  :ref:`How can you report a bug or issue? <issue>`

Usage
-----

Notebook
^^^^^^^^

My notebook is displaying cell outputs in an `iframe <https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe>`__. They are reset when scrolling back and forth.

    Since JupyterLab v4, notebook rendering is optimized to display only the cells needed.
    This has side effects with iframes.

    Workaround: Set the settings *Notebook* => *Windowing mode* to ``defer`` or ``none``.
    Note: This may negatively impact performance when working with long notebooks or many files.

My notebook injects customized CSS that results in unexpected scrolling issues (e.g., it fails to scroll to the active cell).

    JupyterLab v4 optimizations do not support changing CSS `margin <https://developer.mozilla.org/en-US/docs/Web/CSS/margin>`__ for cells.

    Workaround: Use customized `padding <https://developer.mozilla.org/en-US/docs/Web/CSS/padding>`__ instead of margins. 
    If margins are unavoidable, set *Notebook* => *Windowing mode* to ``defer`` or ``none``, keeping in mind potential performance impacts.

Attributes Sanitization
^^^^^^^^^^^^^^^^^^^^^^^

Why are `id` and `name` attributes removed from Markdown?

    JupyterLab sanitizes these attributes to prevent security risks like DOM clobbering attacks. See the [GHSA-9q39-rmj3-p4r2] (https://github.com/jupyterlab/jupyterlab/security/advisories/GHSA-9q39-rmj3-p4r2) guide on [DOM Clobbering Prevention](https://cheatsheetseries.owasp.org/cheatsheets/DOM_Clobbering_Prevention_Cheat_Sheet.html).

    Workarounds:
    - Use headings in Markdown cells to create anchor points safely.
    - Optionally, enable the "Allow named properties" setting in **Settings** -> **Settings Editor** -> **Sanitizer** (not recommended for untrusted sources).

Tips and Tricks
---------------

- How do I start JupyterLab with a clean workspace every time?

    Add ``c.ServerApp.default_url = '/lab?reset'`` to your ``jupyter_server_config.py``.
    See `How to create a jupyter_server_config.py <https://jupyter-server.readthedocs.io/en/latest/users/configuration.html>`__ for more information.

Development
-----------

-  `How can you contribute? <https://github.com/jupyterlab/jupyterlab/blob/4.3.x/CONTRIBUTING.md>`__
-  :ref:`How can you extend or customize JupyterLab? <user_extensions>`
-  In the classic Notebook, I could use custom JavaScript outputted by a cell to programmatically control the Notebook. Can I do the same thing in JupyterLab?

    JupyterLab supports extensive customization through extensions. For dynamic behavior based on notebook outputs, write a custom JupyterLab extension. Using custom mimetypes (:ref:`rendermime`) is a recommended approach. For more details, see issues `#4623 <https://github.com/jupyterlab/jupyterlab/issues/4623>`__ and `#5789 <https://github.com/jupyterlab/jupyterlab/issues/5789>`__.
