# :) My custom terminal 

### :D Ở bài viết này mình sẽ hướng dẫn các bạn xem cách mình custom terminal của mình 

### :D Mình custom terminal của mình theo video của một anh người Nhật tên là  [Takuya Matsuyama](https://www.craftz.dog), một Fullstack developer người Nhật

## :D Đây là video của anh người nhật mình đã làm theo và custom terminal của mình theo, hệ điều hành hiện tại mình đang sử dụng là hệ điều hành [Windows 11](https://www.microsoft.com/vi-vn/windows/windows-11?r=1)

[![How to set up PowerShell prompt with Oh My Posh on Windows 11](https://img.youtube.com/vi/5-aK2_WwrmM/0.jpg)](https://www.youtube.com/watch?v=5-aK2_WwrmM)

### Các bạn có thể làm theo hướng dẫn của anh ấy, nếu các bạn gặp khó khăn trong việc custom terminal thì mình sẽ chỉ cho các bạn ở bài viết dưới đây nhé 

# :D :D :D :D :D :D :D :D :D :D :D :D :D 

## 1. Tải Font có tên là Hack Nerd Font

- Truy cập vào [link](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/Hack/Bold/complete) này để đến trang Github của [Ryan Oasis](https://github.com/ryanoasis) và tải file .ttf có tên là Hack Bold Nerd Font Complete.ttf

![hack font](./images/hackNF.png)

- Sau đó bạn mở file font ra, ấn vào nút install

- Bạn có thể xem video hướng dẫn tại [link](https://www.youtube.com/watch?v=5-aK2_WwrmM&t=84s)

## 2. Thiết lập window terminal và cài đặt powershell

- Đầu tiên, bạn lên Microsoft store và tải app powershell về

![powershell](/images/pow-store.png)

- Tiếp theo, bạn vào Window Terminal và cài đặt 

![powershell](/images/pow-setting.png)

- Chọn Powershell là startup và nhấn save

![powershell](/images/pow-startup.png)

## 2.1. Chỉnh font cho window terminal

- Vào setting, chọn vào default, chọn tab appearance, chọn font là Hack Nerd Font đã cài trước đó và bấm save

![powershell](/images/pow-setfont.png)

## 2.2. Modded Text (không cần làm cũng được)

- Bạn có thể tham khảo tại [link](https://youtu.be/5-aK2_WwrmM?t=160)

## 2.3. Transparent Background (không cần làm cũng được)

- Bạn có thể tham khảo tại [link](https://youtu.be/5-aK2_WwrmM?t=175)

## 3. Cài đặt [Scoop.sh](https://scoop.sh)

![scoop.sh](./images/Scoop-sh.png)

- Vào window terminal và gõ lệnh sau

``` powershell
useb get.scoop.sh | iex
```

## 3.1. Cài đặt Curl và JQuery

- Vào window terminal và gõ lệnh sau
``` powershell
scoop install curl sudo jq
```

### Note: Hoàn thành bước 3 mới có thể sang bước 4

## 4. Cài đặt [Git](https://git-scm.com/downloads)

![git](/images/git-dowload.png)

- Cài đặt git cho các hệ điều hành ở [link](https://git-scm.com/downloads)

- Hoặc có thể cài bằng dòng lênh cmd này
``` powershell
winget install -e -id Git.Git
```
### Note: Hoàn thành bước 4 mới có thể sang bước 5

## 5. Cài đặt NeoVim

- Vào Window Terminal và gõ lệnh sau, lệnh này sẽ giúp bạn cài NeoVim và gcc về máy

``` powershell
scoop install neovim gcc
```

- Cài đặt môi trường cho NeoVim

![powershell](/images/env-start.png)

- Vào thư mục chứa neovim, vào thư mục bin và copy đường dẫn và copy vào PATH phía dưới của environment variables

![powershell](/images/env-neovim-editpath.png)

- Chọn OK

- Kiểm tra neovim

![powershell](/images/nvim-checkver.png)

- Nếu kết quả như hình trên là bạn đã hoàn thành bước 5

### Note: Hoàn thành bước 5 mới có thể sang bước 6

## 6. Cài đặt thư viện [Oh My Posh](https://ohmyposh.dev)

![oh my posh](/images/ohmyposh.png)

- Click vào get started, chọn window

![oh my posh](/images/omp-gets.png)

- Trong page này, sẽ có các themes custom terminal dành cho window

- Cài đặt Oh My Posh, ta gõ 2 lệnh sau trên terminal

``` powershell
Install-Module posh-git -Scope CurrentUser -Force

Install-Module oh-my-posh -Scope CurrentUser -Force
```
### Note: Hoàn thành bước 6 mới có thể sang bước 7

## 7. Tạo file user_profile.ps1 (Dành cho account admin)
- Tạo thư mục [.config]()
``` powershell
cd user/administrator/

mkdir .config
```

- Tạo file user_profile.ps1 bằng cách gõ lệnh sau trên terminal

``` powershell
nvim user_profile.ps1
```

- Copy và paste các lệnh sau vào file user_profile.ps1

``` ps1
Import-Module posh-git
Import-Module oh-my-posh
$omp_config = Join-Path $PSScriptRoot ".\huyhoan.omp.json"
oh-my-posh --init --shell pwsh --config $omp_config | Invoke-Expression

Import-Module -Name Terminal-Icons

Set-PoshPrompt night-owl

# PSReadLine
Set-PSReadLineOption -EditMode Emacs
Set-PSReadLineOption -BellStyle None
Set-PSReadLineKeyHandler -Chord 'Ctrl+d' -Function DeleteChar
Set-PSReadLineOption -PredictionSource History

# Fzf
Import-Module PSFzf
Set-PsFzfOption -PSReadlineChordProvider 'Ctrl+f' -PSReadlineChordReverseHistory 'Ctrl+r'

# Env
$env:GIT_SSH = "C:\Windows\system32\OpenSSH\ssh.exe"

# Alias
Set-Alias vim nvim
Set-Alias ll ls
```

### Note: Hoàn thành bước 7 mới có thể sang bước 8

## 8. Tạo file config cho user_profile.ps1

- Tạo file config bằng cách gõ lệnh sau trên terminal

``` powershell
nvim $PROFILE.CurrentUserAllHosts
```

- Copy dòng sau vào file config

``` ps1
. $env:C:\Users\Administrator\.config\powershell\user_profile.ps1
```
### Note: Hoàn thành bước 8 mới có thể sang bước 9

## 9. Cài đặt nodeJS

- Gõ lệnh sau để cài đặt [nvm]()

``` powershell
scoop install nvm
```

- Kiểm tra phiên bản của nvm

![nvm](/images/nvm-ver.png)

- Gõ lệnh sau để cài đặt nodeJS

``` powershell
nvm install 14.16.0

nvm use 14.16.0
```
- Kiểm tra phiên bản của nodeJS

![node](/images/node-ver.png)

## 10. Cài đặt thư viện Terminal-Icons

- Gõ câu lệnh sau để cài đặt thư viện terminal-Icons

``` powershell
Install-Module -Name Terminal-Icons -Repository PSGallery -Force

Import-Module Terminal-Icons
```

## 11. Cài đặt phần mềm [z]()
- Gõ câu lệnh sau để cài đặt phần mềm z

``` powershell
Install-Module -Name z -Force
```

## 12. Cài đặt thư viện PSReadLine

- Gõ câu lệnh sau để cài đặt thư viện PSReadLine
``` powershell
Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
```

## 13. Cài đặt thư viện Fzf

- Gõ câu lệnh sau để cài đặt thư viện Fzf

``` powershell
Install-Module -Name PSFzf -Scope CurrentUser -Force
```

## 14. Chọn chủ đề cho terminal

- Công thức
``` powershell
Set-PoshPrompt <theme>
```

![night-owl](/images/night-owl.png)

- Ở đây mình sẽ chọn theme night owl
``` powershell
Set-PoshPrompt night-owl
```

- Mở file config để thay đổi theme

``` powershell
nvim user_profile.ps1
```

![night](/images/add-finally.png)


- Tắt terminal và mở lại và chờ kết quả nhé :)


## Vậy là xong rồi, chúc bạn thành công :D

# :D :D :D :D :D :D :D :D :D :D :D :D 