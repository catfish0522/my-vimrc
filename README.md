# my-vimrc
本人的 vimrc 配置只限于 Python，需要其它语言配置的盆友，请Google谢谢
根据 chxuan 的[ vim自动配置程序](https://github.com/chxuan/vimplus) 修改，有兴趣可以了解一下
### vim-plug
[vim-plug](https://github.com/junegunn/vim-plug)：极简主义的Vim插件管理器
下载`plug.vim`并将其放在`autoload`目录中。
```bash
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
##### 用法
添加一个`vim-plug`部分给你的 `~/.vimrc`
```bash
call plug#begin('~/.vim/plugged')	"用这个部分开始
"需要的插件放这里
call plug#end()		"用这个部分结束
```
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

### 配置 vimrc
```bash
colorscheme Tomorrow-Night	"选择vim主题

"================ 基础设置 ================
set nu		"显示行号
"set mouse=a	"启用鼠标
filetype plugin on
set encoding=UTF-8
set clipboard=unnamed
set cursorline
let base16colorspace=256

"================ python补全 ==============
let g:ycm_keep_logfiles = 1
let g:ycm_log_level = 'debug'
let g:ycm_key_invoke_completion = '<c-space>'
let g:ycm_python_interpreter_path = '/usr/bin/python'
let g:ycm_python_sys_path = []
let g:ycm_extra_conf_vim_data = [
  \  'g:ycm_python_interpreter_path',
  \  'g:ycm_python_sys_path'
  \]
let g:ycm_global_ycm_extra_conf = '~/.global_extra_conf.py'
let g:ycm_confirm_extra_conf=0
let g:ycm_add_preview_to_completeopt = 0
set completeopt=longest,menu,menuone
let g:ycm_seed_identifiers_with_syntax=1
let g:ycm_min_num_of_chars_for_completion=2
let g:ycm_complete_in_strings=1
let g:ycm_semantic_triggers =  {
			\ 'c,cpp,python,java,go,erlang,perl': ['re!\w{2}'],
			\ 'cs,lua,javascript': ['re!\w{2}'],
			\ }

"================ vim-devicons ============
" change the default character when no match found
let g:WebDevIconsUnicodeDecorateFileNodesDefaultSymbol = 'ƛ'
" enable folder/directory glyph flag (disabled by default with 0)
let g:WebDevIconsUnicodeDecorateFolderNodes = 1

"=============== 代码折叠 =====================
" Enable folding
set foldmethod=indent
set foldlevel=99
" Enable folding with the spacebar
nnoremap <space> za
let g:SimpylFold_docstring_preview=1

"=============== 代码高亮 =====================
let python_highlight_all=1
syntax on

"=============== 状态栏配置 ===================
let g:airline#extensions#tabline#enabled = 1
let g:airline#extensions#tabline#formatter = 'unique_tail'
let g:airline#extensions#tabline#left_sep = ' '
let g:airline#extensions#tabline#left_alt_sep = '|'
let g:airline_powerline_fonts = 1

"=============== 拆分布局 =====================
" sp <filename> 垂直拆分(在当前文件下方打开新文件)
" vs <filename> 水平拆分(在当前文件右侧打开新文件)
set splitbelow
set splitright

"=============== 分割导航 =====================
nnoremap <C-J> <C-W><C-J>
nnoremap <C-K> <C-W><C-K>
nnoremap <C-L> <C-W><C-L>
nnoremap <C-H> <C-W><C-H>

"=============== nerdtree 配置 ================
map <C-n> :NERDTreeToggle<CR>
let g:NERDTreeDirArrowExpandable = '▸'
let g:NERDTreeDirArrowCollapsible = '▾'
"隐藏 .pyc 文件
let NERDTreeIgnore=['\.pyc$', '\~$'] "ignore files in NERDTree
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif

"================ python缩进,PEP 8标准 =================
au BufNewFile,BufRead *.py
    \ set tabstop=4 |
    \ set softtabstop=4 |
    \ set shiftwidth=4 |
    \ set textwidth=79 |
    \ set expandtab |
    \ set autoindent |
    \ set fileformat=unix |

"=============== 全栈开发缩进 ================
au BufNewFile,BufRead *.js,*.html,*.css
    \ set tabstop=2 |
    \ set softtabstop=2 |
    \ set shiftwidth=2 |

"============== 标记不必要的空白 =============
hi BadWhitespace guifg=gray guibg=red ctermfg=gray ctermbg=red
au BufRead,BufNewFile *.py,*.pyw,*.c,*.h match BadWhitespace /\s\+$/

"============== 支持虚拟环境 =================
py << EOF
import os
import sys
if 'VIRTUAL_ENV' in os.environ:
    project_base_dir = os.environ['VIRTUAL_ENV']
    activate_this = os.path.join(project_base_dir, 'bin/activate_this.py')
    execfile(activate_this, dict(__file__=activate_this))
EOF
```