Much of the software installed on the NeSI cluster have multiple
versions available as shown
[here](https://support.nesi.org.nz/hc/en-gb/sections/360000040076-Supported-Applications)
or by using the `module avail` or `module spider` commands.

If only the application name is given a default version will be chosen,
generally the most recent one. However it is good practice to load
modules using the specific version so you can ensure consistent
execution of your job even after the default version has been changed.

If you need a specific version of software, feel free to ask support and
we may install it.

Example
-------

    module load ANSYS

Will load the default version of ANSYS, in this case ANSYS/19.2, however
this may change.

    module load ANSYS/18.1

Will always load that version specifically.