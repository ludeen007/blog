+++
title = "VSCode launch"
+++



## 调试bash脚本

```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [{
            "type": "bashdb",
            "request": "launch",
            "name": "Bash-Debug (select script from list of sh files)",
            "cwd": "${workspaceFolder}",
            "program": "${command:SelectScriptName}",
            "args": []
        }    ]
}
```

## launch.json文件模板

```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [{
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceFolder}/consumerWorker.js",
            "args": [
                "--port",
                "800",
                "--debug",
                "yes",
                "--flags",
                "w"
            ],
            "env": {
                "NODE_ENV": "development"
            },
            "skipFiles": [
                "<node_internals>/**",
                "async_hooks.js",
                "inspector_async_hook.js"
            ],
            "console": "integratedTerminal",
            "preLaunchTask": "eslint"
        },
        {
            "type": "node",
            "request": "launch",
            "name": "Mocha All",
            "program": "${workspaceFolder}/node_modules/mocha/bin/_mocha",
            "args": [
                "--timeout",
                "999999",
                "--colors",
                "${workspaceFolder}/test",
                "--port",
                "800",
                "--debug",
                "yes",
                "--flags",
                "w"
            ],
            "env": {
                "NODE_ENV": "development"
            },
            "skipFiles": [
                "<node_internals>/**",
                "async_hooks.js",
                "inspector_async_hook.js"
            ],
            "console": "integratedTerminal",
            "internalConsoleOptions": "neverOpen"
        },
        {
            "type": "node",
            "request": "launch",
            "name": "Mocha Current File",
            "program": "${workspaceFolder}/node_modules/mocha/bin/_mocha",
            "args": [
                "--timeout",
                "999999",
                "--colors",
                "${file}",
                "--port",
                "800",
                "--debug",
                "yes",
                "--flags",
                "w"
            ],
            "env": {
                "NODE_ENV": "development"
            },
            "skipFiles": [
                "<node_internals>/**",
                "async_hooks.js",
                "inspector_async_hook.js"
            ],
            "console": "integratedTerminal",
            "internalConsoleOptions": "neverOpen"
        }
    ],
}
```
