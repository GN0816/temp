
VsCode窗口右击列表绑定
---------------------
1. 目的
    实现了主窗口右击追加自定义选项。

2. 功能需求
    在主窗口右键展示自定义功能。
 
3. 概括性介绍
    在主窗口点击右键可以找到并快速运行所需功能。

4. 详细设计过程
- 添加主窗口列表
        在package.json中配置menus添加editor/context的属性when(注：文件类型)和command(注：绑定的事件);
- 添加主窗口右上角快捷键
        在package.json中配置menus添加editor/title性when(注：文件类型)和command(注：绑定的事件)

        如：
        ::
            "editor/context": [
				{
					"when": "editorTextFocus && editorLangId == qrunes",
					"command": "qurator-vscode.runQRunesCode"
				}
			],
			"editor/title": [
				{
					"when": "editorTextFocus && editorLangId == qrunes",
					"command": "qurator-vscode.runQRunesCode",
					"group": "navigation"
				}
			]
