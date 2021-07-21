ParaView
--------

[ParaView](https://www.paraview.org/) is a high-performance 3D
visualisation tool. The headless versions only provide ParaView Server,
which can operate in batch mode, as well as in client-server operation.

 

### Available Modules

  ------------------------------------------- ------------- ---------------- -------------- ---------
  **Module Name**                             **Mahuika**   **Māui Ancil**   **Headless**   **GUI**
  Paraview/5.5.2-gimpi-2018a-Server-EGL                     ✔                ✔               
  Paraview/5.5.2-gimpi-2018b-GUI-Mesa                       ✔                               ✔
  Paraview/5.5.2-gimpi-2018b-Server-OSMesa                  ✔                ✔               
  ParaView/5.3.0-gimkl-2017a                  ✔                              ✔               
  ParaView/5.4.1-gimkl-2017a-Python-2.7.14                                   ✔               
  ParaView/5.4.1-gimkl-2018b-Python-2.7.16                                   ✔               
  ParaView/5.4.1-gimpi-2018b                                                 ✔               
  ParaView/5.6.0-gimkl-2018b-Python-3.7.3                                    ✔               
  ParaView/5.6.0-gimpi-2017a-Server-OSMesa                                   ✔               
  ParaView/5.6.0-gimpi-2018b                                                 ✔               
  ------------------------------------------- ------------- ---------------- -------------- ---------

> ### Note {#warn}
>
> The ParaView server loaded must be the same version as the client you
> have installed locally.

###  

### Setting up Client-Server Mode

If you want to use ParaView in client-server mode, use the following
setup:

-   Load one of the ParaView Server modules listed above and launch the
    server in your interactive visualisation session on the HPC using;

        module load ParaView

<!-- -->

-   To start the ParaView server run;\

        pvserver

-   You should see;

        Waiting for client...
        Connection URL: cs://mahuika02:11111
        Accepting connection(s): mahuika02:11111

<!-- -->

-   Create an SSH tunnel for port \"11111\" from your local machine to
    the cluster. e.g.

        ssh mahuika -L 11111:mahuika02:11111

    Make sure the host name and socket match those given by the server
    earlier!

-   Launch the ParaView GUI on your local machine and go to \"File \>
    Connect\" or click
    the ![mceclip0.png](https://support.nesi.org.nz/hc/article_attachments/360002161075/mceclip0.png) button.
-   Click on \"Add Server\", choose server type \"Client / Server\",
    host \"localhost\" (as we will be using the SSH tunnel), and port
    \"11111\", then click on \"Configure\" .
-   ![mceclip1.png](https://support.nesi.org.nz/hc/article_attachments/360002269756/mceclip1.png)
-   Select the new server and click on \"Connect\"

### Parallelisation

The CPU based versions of ParaView use the OpenSWR rasteriser as well as
the OSPRay ray tracer for rendering graphics. These support parallel
operation for better performance, but are configured to only use a
single core by default. Run the following commands *before* launching
ParaView GUI or ParaView Server if you want to use more cores (depending
on the number of cores available in your session):

    export KNOB_MAX_WORKER_THREADS=<number of cores>
    export OSPRAY_THREADS=<number of cores>

ParaView Server also supports parallel execution using MPI.