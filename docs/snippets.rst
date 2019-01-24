
Snippets功能技术总结
-------------------
1. 目的
    实现了vscode自定义提示功能。

2. 功能需求
    自定义提示片段代码。
 
3. 概括性介绍
    根据首字符展示代码片段。

4. 详细设计过程
    在package.json中添加snipperts功能，配置language（后缀名）、path(提示模板的路径)；创建该路径，书写json格式的提示语。

    ::
 
    "sqs": {
        "prefix": "sqs",
        "body": [ 
            "@settings:",
            "\t",
            "@qcodes:",
            "\t",
            "@script:"
        ],
        "description": "Code snippet for the basic qcodes imports"
    }

