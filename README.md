# my-vimrc
本人的 vimrc 配置只限于 Python，需要其它语言配置的盆友，请Google谢谢

根据 chxuan 的[ vim自动配置程序](https://github.com/chxuan/vimplus) 修改，有兴趣可以了解一下

### vim-plug
[vim-plug](https://github.com/junegunn/vim-plug)：极简主义的Vim插件管理器

下载`plug.vim`并将其放在`autoload`目录中
`curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim`

### 插件列表

| 插件                                                         | 说明                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [YouCompleteMe](https://github.com/Valloric/YouCompleteMe)   | 史上最强大的基于语义的自动补全插件，支持C/C++、C#、Python、PHP等语言 |
| [NerdTree](https://github.com/scrooloose/nerdtree)           | 代码资源管理器                                               |
| [nerdtree-syntax-highlight](https://github.com/tiagofumo/vim-nerdtree-syntax-highlight) | NerdTree文件类型高亮                                         |
| [Tomorrow-theme](https://github.com/chriskempson/vim-tomorrow-theme) | Tomorrow主题                                                 |
| [Airline](https://github.com/vim-airline/vim-airline)        | 轻盈如空气的标签栏                                           |
| [Airline-themes](https://github.com/vim-airline/vim-airline-themes) | Airline的主题包                                              |
| [vim-edit](https://github.com/chxuan/vim-edit)               | 方便的文本编辑插件                                           |
| [auto-pairs](https://github.com/jiangmiao/auto-pairs)        | 自动补全引号、圆括号、花括号等                               |
| [indentpython](https://github.com/vim-scripts/indentpython.vim) | Python缩进                                                   |
| [CtrlP](https://github.com/ctrlpvim/ctrlp.vim)               | 全路径模糊搜索工具                                           |
| [SimpylFold](https://github.com/tmhedberg/SimpylFold)        | No-BS Python代码折叠                                         |
| [vim-devicons](https://github.com/ryanoasis/vim-devicons)    | 文件类型图标                                                 |

### 每个插件的用法
github 上都有相关的解释，有 bug 也可以给作者提交 Issues
