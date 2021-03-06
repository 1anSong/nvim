# 1anSong`s vim user guide
## vim viki的使用
 **normnal模式下** 
| 命令            | 说明                                           |
|-----------------|------------------------------------------------|
| `<Leader>`ww    | 打开默认的 wiki 目录文件                       |
| `<Leader>`wt    | 在新标签（Tab）中打开 wiki 目录文件            |
| `<Leader>`ws    | 在多个 wiki 中选择并打开该 wiki 的目录文件     |
| `<Leader>`wd    | 删除当前 wiki 文件                             |
| `<Leader>`wr    | 重命名当前 wiki 文件                           |
| `<Enter>`       | 创建或打开 wiki 链接                           |
| `<Shift-Enter>` | 先上下分屏再打开 wiki 链接（若非链接则先创建） |
| `<Ctrl-Enter>`  | 先左右分屏再打开 wiki 链接（若非链接则先创建） |
| `<Backspace>`   | 返回之前浏览的 wiki 文件                       |
| `<Tab>`         | 跳到本文件中下一个 wiki 链接                   |
| `<Shift-Tab> `  | 跳到本文件中上一个 wiki 链接                   |
## vim surround 的使用
 **normal** 	

| 命令                 | 说明 + 示例                                                                     |
|----------------------|---------------------------------------------------------------------------------|
| ds                   | 删除括号                                                                        |
| `ds` `"`             | `"Hello world!"` =><br> `Hello world!`                                          |
| cs                   | 替换括号                                                                        |
| `cs` `"(`            | `"Hello world!"` =><br> `(Hello world!)`                                        |
| cS                   | 替换括号，括号内文本做新一行                                                    |
| `cS` `"{`            | `"Hello world!"` =><br> `{` <br> &nbsp;&nbsp;&nbsp;&nbsp;`Hello world!` <br> `} |
| ys                   | 添加括号(配合vim光标移动)                                                       |
| `ys` `w` `[`         | `Hello world!` =><br> `[Hello] world!`                                          |
| `ys` `w` `<em` Enter | `Hello world!` =><br> `<em>Hello<em> world!`                                    |
| yS                   | 添加括号，括号内文本做新一行                                                    |
| `yS` `w` `[`         | `Hello world!` =><br> `[` <br> &nbsp;&nbsp;&nbsp;&nbsp; `Hello` <br> `] world!` |
| yss                  | 整行括起来                                                                      |
| `yss` `(`            | `Hello world!` =><br> `( Hello world! )`                                        |
| ySS                  | 整行括起来，括号内文本做新一行                                                  |
| `ySS` `{`            | `Hello world!` =><br> `{` <br> &nbsp;&nbsp; `Hello world! ` <br> `}`            |
| `ySS` `<div` Enter   | `Hello world!` =><br> `<div>` <br> &nbsp;&nbsp; `Hello world! ` <br> `<div>`    |
| ySs                  | 与ySs功能相同                                                                   |

**visual**


| 命令             | 说明 + 示例                                                           |
|------------------|-----------------------------------------------------------------------|
| S                | 选中的括起来                                                          |
| 选中world: `S(`  | `Hello world!` =><br> `Hello (world)!`                                |
| gS               | 选中的括起来，括号内文本做新一行                                      |
| 选中world: `gS{` | `Hello world!` =><br> `Hello {` <br> &nbsp;&nbsp; ` world` <br> `}! ` |

## vim常用快捷键
| 命令   | 说明                             |
|--------|----------------------------------|
| ctrl+# | 查找本文件中所有的光标所在的单词 |
| :vs    | 垂直分屏操作                     |
| :sv    | 水平分屏操作                     |
| >      | 增加缩进                         |


## NERDTree快捷键
| 命令 | 说明                                             |
|------|--------------------------------------------------|
| q    | 关闭NERDTree                                     |
| o    | 在已有窗口中打开文件或目录,并将光标跳到该窗口    |
| O    | 递归打开选中节点下的所有目录                     |
| x    | 合拢选中节点的父目录                             |
| X    | 递归合拢选中结点下的所有目录                     |
| p    | 跳到根节点                                       |
| P    | 跳到父节点                                       |
| u    | 设置上级目录为根路径                             |
| U    | 设置上级目录为跟路径，但是维持原来目录打开的状态 |
| r    | 刷新光标所在的目录                               |
| R    | 刷新当前根路径                                   |
| I    | 显示或者不显示隐藏文件                           |
| f    | 打开和关闭文件过滤器                             |
| A    | 全屏显示 NERDTree，或者关闭全屏                  |
| C    | 将根路径设置为光标所在的目录                     |

- 如何切换磁盘
```
:NERDTree C:/ 打开C盘
:NERDTree D:/ 打开D盘
```
- 如何打开(多个)文件
```

1. :将光标移到到目标文件上
2. :i 竖屏打开多个文件
    	<Enter> 竖屏打开多个文件,无法打开同一个文件
    	s 横屏打开文件,无法打开同一个文件
```	

## vimtex
| 命令                               | 说明                                                                                    |
|------------------------------------|-----------------------------------------------------------------------------------------|
| `<leader>ll`                       | 使用默认编译器（latexmk）开始监听`.tex` 文件的变化，编译 LaTeX 项目并打开 PDF 预览界面 |
| `<leader>lk` or 第二次`<leader>ll` | 停止编译器监听文件变动，停止编译                                                        |
| `<leader>lv`                       | 正向从 Neovim 光标位置同步 PDF 显示区域                                                 |
| `<leader>lc`                       | 清理编译生成的中间文件                                                                  |

- 具体请参见 [vimtex](https://github.com/lervag/vimtex)
### issues
1. 无法书写中文。
解决办法: 将以下内容加入init.vim
```
	let g:vimtex_compiler_latexmk_engines={
	\ '_':'-xelatex',
	\'xelatex':'-xelatex',
	\'pdflatex':'-pdf',
 	\}
```
2. coc补全相关
```
可以选择 coc-vimtex 或 coc-texlab
```
