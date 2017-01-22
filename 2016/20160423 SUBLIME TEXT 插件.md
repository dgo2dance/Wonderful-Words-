### 支持浏览器中预览 ###
1） 点击Tools -> New Plugin，在创建好的py文件中输入如下内容：

import webbrowser
 
url_map = {
    '/Users/jerry/Sites/test/' : 'http://test/',
}
 
class OpenBrowserCommand(sublime_plugin.TextCommand):
    def run(self,edit):
        window = sublime.active_window()
        window.run_command('save')
        url = self.view.file_name()
        for path, domain in url_map.items():
            if url.startswith(path):
                url = url.replace(path, domain).replace('\\', '\/')
                break
 
        webbrowser.open_new(url)

文件保存至Packages/User 文件名随意
 
2） 分配快捷键
点菜单Tools -> Command Palette…，或者f12，打开命令集，选择“key Bindings – User”打开个人快捷键配置，输入下列内容：

[{ "keys": ["f12"], "command": "open_browser" }]