# VIM 的使用与配置

> Vim 是从 vi 发展出来的一个文本编辑器。 代码补完、编译及错误跳转等方便编程的功能特别丰富，
> 在程序员中被广泛使用。和 Emacs 并列成为类 Unix 系统用户最喜欢的编辑器。
> Vim的第一个版本由布莱姆·米勒在 1991 年发布。最初的简称是 Vi IMitation，
> 随着功能的不断增加，正式名称改成了 Vi IMproved。现在是在开放源代码方式下发行的自由软件。

## 安装

    $ sudo apt-get install vim

## 基本使用

vim 有两种模式最为常用，分别是普通模式和编辑模式。

在 Terminal 中输入 `vim` 打开 vim，进入的就是普通模式。此时无法编辑任何文档，
但是您可以输入指令进行操作。

您可以通过方向键，或是 `h`(左) `j`(下) `k`(上) `l`(右) 键移动光标。
编辑配置文件后您还可以使用鼠标移动光标。

紧接着您可以按动 `a` 向光标后添加字符，按动 `i` 向光标前添加字符，
按动 `x` 删除当前字符。一旦按动 `a` 或 `i`，vim 就会进入编辑模式。
按 `Esc` 可以退出编辑模式，回到普通模式。编辑模式中可以使用 `Backspace` 或 `Del`
删除字符，使用光标键移动光标。

在普通模式下，输入 `:` 即可执行 vim 指令。输入的指令会显示在屏幕底部。

输入 `:q` 退出 vim。输入 `:q!` 强行退出 vim 不保存。输入 `:wq` 保存并退出 vim。

如果您通过配置文件开启了 autoindent，复制一段文字时出现了缩进不对的情况，
可以输入 `:set paste` 开启拷贝模式。

在普通模式下输入 `/<单词>` 即可在整个文件中搜索单词。

    /next

接着就可以按 `n` 正序搜索其他的 `next`

## 配置

vim 的配置储存在用户目录下的 `.vimrc` 文件中。

    $ vim ~/.vimrc

即可使用 vim 编辑 vim 配置文件。

以下是 SkyZH 的 vim 配置。

    set nu ru incsearch hlsearch cindent autoindent sw=4 ts=4 sts=4
    set expandtab
    set nobk

以下是 czr大爷 的 vim 配置

    set nu ru sw=4 sts=4 ts=4 cindent autoindent mouse=a incsearch hlsearch fdm=marker
    set expandtab

    syntax on

    filetype plugin indent on

    map <F2> : w <CR>
    map <F9> : call Compile() <CR>
    map <F7> : call Run() <CR>
    map <F8> : call RunFile() <CR>
    map <F5> : call Gdb() <CR>

    func Compile()
     exec "w"
     if &filetype=='cpp'
      exec "!g++ -g % -o %< -Wall -Wextra && size %<"
     elseif &filetype=='tex'
      exec "!xelatex %"
     endif
    endfunc

    func Run()
     if &filetype=='tex'
      exec "!open %<.pdf"
     else
      exec "!time ./%<"
     endif
    endfunc

    func RunFile()
     exec "!time ./%< < %<.in > %<.out"
    endfunc

    func Gdb()
     exec "!gdb %<"
    endfunc
