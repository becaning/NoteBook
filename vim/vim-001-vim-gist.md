vim神器插件[gist-vim](https://github.com/mattn/gist-vim), 这个插件可以在vim中完成Github gist的增删改查。
------------------

## 安装
```
Bundle 'mattn/webapi-vim'
Bundle 'mattn/gist-vim'
```
## 配置:

首先你需要配置你的git config

    $ git config --global github.user <username>

这个插件支持github的基本账户认证和二次认证，第一次使用需要你输入密码，如果你开启了二次验证，就会有`OTP`其实你输入二次验证码，通过验证后会获取到一个`token`,这个`token`会保存到`~/.gist-vim`中。


## 使用

最简单用法，直接vim命令模式`:Gist`,当前打开文件的内容已经推到gist上了。
以下是一些参数:
- 推送选择的内容 

        :'<,'>Gist

- Create a private gist.

        :Gist -p

- Create a public gist.
  (Only relevant if you've set gists to be private by default.)

        :Gist -P

>  This is only relevant if you've set gists to be private by default;
> if you get an empty gist list, try ":Gist --abandon".

- Create a gist anonymously.

        :Gist -a

> 匿名创建的gist是不能在你的github找到的，只能通过`URL`才能找到

- Create a gist with all open buffers.

        :Gist -m

- Edit the gist (you need to have opened the gist buffer first).
  You can update the gist with the ":w" command within the gist buffer.

        :Gist -e

- Edit the gist with name 'foo.js' (you need to have opened the gist buffer
  first).

        :Gist -e foo.js

- Post/Edit with the description " (you need to have opened the gist buffer
  first). >

        :Gist -s something
        :Gist -e -s something

- Delete the gist (you need to have opened the gist buffer first).
  Password authentication is needed.

        :Gist -d

- Fork the gist (you need to have opened the gist buffer first).
  Password authentication is needed.

        :Gist -f

- Star the gist (you need to have opened the gist buffer first).
  Password authentication is needed.

        :Gist +1

- Unstar the gist (you need to have opened the gist buffer first).
  Password authentication is needed.

        :Gist -1

- Get gist XXXXX.

        :Gist XXXXX

- Get gist XXXXX and add to clipboard.

        :Gist -c XXXXX

- List your public gists.

        :Gist -l

- List gists from user "mattn".

        :Gist -l mattn

- List everyone's gists.

        :Gist -la

- List gists from your starred gists.

        :Gist -ls

- Open the gist on browser after you post or update it.

        :Gist -b

## Tips:

If you set g:gist_clip_command, gist.vim will copy the gist code with option
'-c'.

- Mac:

        let g:gist_clip_command = 'pbcopy'

- Linux:

        let g:gist_clip_command = 'xclip -selection clipboard'

- Others (cygwin?):

        let g:gist_clip_command = 'putclip'

If you want to detect filetype from the filename:

    let g:gist_detect_filetype = 1

If you want to open browser after the post:

    let g:gist_open_browser_after_post = 1

If you want to change the browser:

    let g:gist_browser_command = 'w3m %URL%'

or:

    let g:gist_browser_command = 'opera %URL% &'

On windows, this should work with your user settings.

If you want to show your private gists with ":Gist -l":

    let g:gist_show_privates = 1

If you want your gist to be private by default:

    let g:gist_post_private = 1

If you want your gist to be anonymous by default:

    let g:gist_post_anonymous = 1

If you want to manipulate multiple files in a gist:

    let g:gist_get_multiplefile = 1

If you want to use on GitHub Enterprise:

    let g:gist_api_url = 'http://your-github-enterprise-domain/api/v3'

You need to either set global git config:

    $ git config --global github.user Username

