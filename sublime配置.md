# sublime配置

## 安装常用插件
- 按Ctrl+`调出console <br>
- 粘贴以下代码到底部命令行并回车：
  ```
  import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())
  ```
- 重启Sublime，如果在Perferences -> Package Settings中看到package control这一项，则安装成功。
- 按下Command+Shift+P调出命令面板
- 输入install 调出 Install Package 选项并回车，然后在列表中选中要安装的插件。 <br>
  ### 常用插件
  - A File Icon
  - BracketHighlighter
  - HTML-CSS-JS Prettify
  - Material Theme (安装完需要设置并在Perferences -> Package Settings -> Material Theme -> Activite)
  - Pug
  - Sass
  - Vue Syntax Highlight
  - zzz A File Icon zzz

## sublime设置
- Perferences->Settings
```
{
  "always_show_minimap_viewport": true,
  "bold_folder_labels": false,
  "color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",
  "draw_white_space": "all",
  "ensure_newline_at_eof_on_save": true,
  "folder_exclude_patterns":
  [
    "node_modules",
    ".git"
  ],
  "font_face": "Monaco",
  "font_options":
  [
    "gray_antialias"
  ],
  "font_size": 13,
  "highlight_line": true,
  "ignored_packages":
  [
    "Vintage"
  ],
  "line_padding_bottom": 2,
  "line_padding_top": 2,
  "material_theme_disable_fileicons": false,
  "material_theme_disable_tree_indicator": true,
  "material_theme_panel_separator": true,
  "material_theme_small_statusbar": true,
  "material_theme_small_tab": true,
  "material_theme_tabs_autowidth": true,
  "material_theme_tabs_separator": true,
  "overlay_scroll_bars": "enabled",
  "tab_size": 2,
  "theme": "Material-Theme.sublime-theme",
  "translate_tabs_to_spaces": true,
  "trim_trailing_white_space_on_save": true,
  "word_separators": "./\\()\"':,.;<>~!@#$%^&*|+=[]{}`~?",
  "word_wrap": "false"
}
```
