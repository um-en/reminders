# **Handling clashes on imports within VSCode**
In VSCode, some elements can be confusing around handling imports, and may result in noModuleFound error frequently. In general, to write python with absolute import, the core issue is that the top-level directory needs to be added to the `PYTHONPATH` variable: This will make every packages / folders under this path discoverable for import statments. While PyCharm adds by default the top-level directory to this variable, this is not the case in VSCode. Hence the workspace needs manually defined files to ensure `PYTHONPATH` is extended at runtime. This is done differently depending on whether the code is run in debug mode or as a simple "file run", and both situations are defined below.


### **"Debug" setup**
This is a setup that will be used when pressing the F5 shortcut, and serves for debugging a file. When doing so, VSCode .env is loaded at runtime. Extending the *PYTHONPATH* can be done in this file:

``` py
PYTHONPATH=C:\Users\...\project_folder
# Absolute path to the project folder
```
The file should be added to the root of the workspace.


### **"Run Python File" setup**
When simply running a file, the `.env` file is not loaded. Instead, configuration will be loaded from a *settings.json* file, which should be added under *.vscode* at the root of the project:

├── workspace

│   ├── .vscode

│   │   ├── settings.json

The content of the *settings* file should be as follows:
```json
{
    "terminal.integrated.env.windows":{
        "PYTHONPATH":"${workspaceFolder}"
    },
    "python.envFile": "${$workspaceFolder}/.env"
}
```