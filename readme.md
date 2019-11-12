# Installing jupyter notebook with a c# kernel 

- Check if you installed python with visual studio. 

Go to the start menu and start typing Python

![img1](img/python_installed.png)

Right click on python and follow the Open File Location until you find the place where python is installed. 

![img2](img/python_installed_location.png)

- Or type: ```where python``` in the command line. 

- If so, add python to the PATH of your environment. On my installation, the paths to Python were as follows. I had to add the Scripts path for the pip installation to be in the command line. 
  - ```C:\Program Files (x86)\Microsoft Visual Studio\Shared\Python37_64\```
  - ```C:\Program Files (x86)\Microsoft Visual Studio\Shared\Python37_64\Scripts```

- install jupyter using pip which was installed with visual studio, make sure to run in an **administrator** shell
  - ```pip install jupyter```

- check that jupyter now starts
  - jupyter notebook

- Now get the list of installed jupyter kernels: 
  - ```jupyter kernelspec list```

```
Available kernels:
  c:\program files (x86)\microsoft visual studio\shared\python37_64\share\jupyter\kernels\python3  
```

- Install the latest version of .net try 
```dotnet tool install dotnet-try -g```

- finally install the .net kernel for jupyter with the command: 
```dotnet try jupyter install```

- test the kernel is now installed with ```jupyter kernelspec list```

![img3](img/jupyter_kernels.png)

# launch jupyter notebook
In the command line, type: 
```jupyter notebook```

A browser window should open and the terminal should display: 

```
C:\Repos\noteb>jupyter notebook
[I 22:14:55.617 NotebookApp] JupyterLab extension loaded from c:\program files (x86)\microsoft visual studio\shared\python37_64\lib\site-packages\jupyterlab
[I 22:14:55.618 NotebookApp] JupyterLab application directory is c:\program files (x86)\microsoft visual studio\shared\python37_64\share\jupyter\lab
[I 22:14:55.625 NotebookApp] Serving notebooks from local directory: C:\Repos\noteb
[I 22:14:55.626 NotebookApp] The Jupyter Notebook is running at:
[I 22:14:55.627 NotebookApp] http://localhost:8888/?token=XXXXXXXXXXXXXXXXXXXc1ee1dfccc0a6624263d584b8ca4c
[I 22:14:55.628 NotebookApp]  or http://127.0.0.1:8888/?token=XXXXXXXXXXXXXXXXXXXc1ee1dfccc0a6624263d584b8ca4c
[I 22:14:55.629 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).  [C 22:14:55.737 NotebookApp]

    To access the notebook, open this file in a browser:
        file:///C:/Users/xxxxxx/AppData/Roaming/jupyter/runtime/nbserver-17608-open.html
    Or copy and paste one of these URLs:
        http://localhost:8888/?token=XXXXXXXXXXXXXXXXXXXc1ee1dfccc0a6624263d584b8ca4c
     or http://127.0.0.1:8888/?token=XXXXXXXXXXXXXXXXXXXc1ee1dfccc0a6624263d584b8ca4c
[I 22:15:16.852 NotebookApp] Kernel started: be6910a0-92f0-4ec0-a26c-d8274b44cd6d
```

The main page of the Jupyter notebook allows you to see the notebooks available in the folder and to create new ones. 

![img4](img/jupyter_create_csharp.png)

# Hello world 

Create a new C# notebook. Then type
```CSharp
using System; 
```
in the first cell. I executed it and then typed: 
```CSharp
Console.WriteLine("Hello World"); 
```
in the second cell. Executing it shows us that the C# Kernel is working.

![imgHello](img/jupyter_hello_world_csharp.png)

```#r``` is used to reference a dll or a nuget package. If you prefix the command with "nuget:" then the jupyter notebook will download the nuget and add it as a reference. Then as in usual c#, you must reference it. 

# Installing an R kernel for jupyter notebook

To install R Tools for Visual Studio, install the Visual Studio Extension R Tools for Visual Studio 2019, which was in preview when I looked. Once this is installed, you must install the Microsoft R client. This option will be presented if you go to the "R Interactive" window. 

![img5](img/install_R_vs.png)

I have R installed with visual studio, so I launched visual studio in **admin mode** to be able to have my R directory writable, went to the R Tools menu at the top and selected "R Interactive". 

![img6](img/r_interactive_vs.png)

From the command line of R, I typed in the following commands. [Installation guide R](https://irkernel.github.io/installation/)

![img6](img/r_interactive_kernel_install.png)

```
install.packages('IRkernel')
IRkernel::installspec(user = FALSE)
```

I got the following output after installing the IRKernel into Jupyter ```[InstallKernelSpec] Installed kernelspec ir in C:\ProgramData\jupyter\kernels\ir```. Following this, you can check on the command line that the R kernel appears in the list of Jupyter Kernels with ```jupyter kernelspec list```, this should show the ir kernel installed: 

```
Available kernels:
  ir             C:\ProgramData\jupyter\kernels\ir
```

## Use R to show a some math

Create a new R notebook and type in the first cell: 
```R
demo(plotmath)
```
Executing this should show you the following long list of tables with mathematical symbols. 

![img7](img/jupyter_R.png)