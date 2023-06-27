# **Standard template of settings used in VSCode**

This lists personal template used to set up any project worked on in VS Code

1. If not installed already, add the following plugins:
   - ms-python.python
   - ms-python.vscode-pylance
   - ms-toolsai.jupyter
   - wayou.vscode-todo-highlight
   - yzhang.markdown-all-in-one

2. Add a .vscode/settings.json file at the root of the project, with the following content 

```json
{
    "terminal.integrated.env.windows":{
        "PYTHONPATH":"${workspaceFolder}"
    },
    "python.envFile": "${$workspaceFolder}/.env",
    "todohighlight.include": ["**/*.py"],
    "todohighlight.exclude": ["venv/*"],
    "python.analysis.typeCheckingMode": "basic",
    "python.analysis.importFormat": "absolute",
    "python.analysis.diagnosticSeverityOverrides": {
        "reportUndefinedVariable": "error",
        "reportMissingModuleSource": "error",
        "reportUnusedVariable": "warning",
        "reportGeneralTypeIssues": "information"
    }
}
```

3. Create a .env file at the root of the project, with the PYTHONPATH variable defined
```
PYTHONPATH="absolute/path/to/project/root
```
4. Create a scratchpad folder (hosting jupyter notebook and other temporary files) and add it to .gitignore