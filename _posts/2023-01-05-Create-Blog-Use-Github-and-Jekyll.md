---
title: Create Blog use Github and Jekyll on MacOS
published: true
---

# [](#header-1) Mục lục

1. Mục tiêu
2. Step need to do
  - `Step 01` - Upgrade ruby 3.1.3
  - `Step 02` - gem install jekyll
  - `Step 03` - create first project từ jekyll
  - `Step 04` - add SSH and pull project by SSH : https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/GitHub-SSH-Key-Setup-Config-Ubuntu-Linux
  - `Step 05` - setup public Page in github: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
  - `Step 06` - remove repository name in github link: https://stackoverflow.com/questions/44531269/is-there-a-way-to-remove-repository-name-from-github-page-link
  - `Step 07` - pick a theme in: https://jamstackthemes.dev/ssg/jekyll/page/4/

## [](#header-2) Mục tiêu
Gần cuối năm, mình có khá nhiều thời gian để đọc và tìm hiểu. Nhưng vấn đề nảy sinh là
:
1. Mình đọc khá nhiều nhưng cũng quên khá nhiều
2. Cần một nơi tổng hợp lại những thứ mình đã bỏ công để tìm hiểu, tiết kiệm thời gian tìm tòi và vọc 
3. Một vài người thân cũng cần nền tảng nào đó để viết blog cho chính họ

> A há, mình có ý tưởng này. Github hỗ trợ blog cá nhân khá ngon thấy nhiều người cũng dùng.
> Thử tìm hiểu và bắt tay vào xây dựng trang cá nhân thử xem
>

## [](#header-2) What do we need to do ?
Sau một hồi đọc vs nghịch thì mình đã đưa blog lên được. Và các step như dưới đây.

#### [](#header-4) `Step 0` - Prerequisites 
- github account
- MacOS (Vì mình dùng Mac nên mình tổng hợp các step trên Mac, còn các OS khác như Linux, Win,.. thì về cơ bản cũng na ná. Bạn đọc tự tìm hiểu)
- Đã cài Homebrew 

#### [](#header-4) `Step 1` - Upgrade ruby 3.1.3
Source: https://mac.install.guide/ruby/13.html

##### [](#header-5)Check Ruby version
Run this shell 
```shell
$ which ruby
/usr/bin/ruby
$ ruby -v
ruby 2.6.3p62 (2019-04-16 revision 67580) [....]
```


##### [](#header-5) Install Ruby
```shell
$ brew install ruby
```

##### [](#header-5) Config the shell environment
Edit the `~/.zshrc` file in your text editor.
```shell
$ vim ~/.zshrc
```

Setup in the end of file

On Mac Intel
```
# Setup $PATH for ruby
if [ -d "/usr/local/opt/ruby/bin" ]; then
  export PATH=/usr/local/opt/ruby/bin:$PATH
  export PATH=`gem environment gemdir`/bin:$PATH
fi
```

on Mac Silicon:
```
# Setup $PATH for ruby
if [ -d "/opt/homebrew/opt/ruby/bin" ]; then
  export PATH=/opt/homebrew/opt/ruby/bin:$PATH
  export PATH=`gem environment gemdir`/bin:$PATH
fi
```
Save file.

🚩 **Note**: Close and reopen the Terminal window for the changes to the `~/.zshrc` file to be recognized

##### [](#header-5) Confirm Ruby installation

```shell
$ ruby -v
ruby 3.1.3p185 (2022-11-24 revision 1a6b16756e) [arm64-darwin20]

$ echo $PATH
/opt/homebrew/lib/ruby/gems/3.1.0/bin:/opt/homebrew/opt/ruby/bin:/Users/anryseig/opt/anaconda3/bin:/Users/anryseig/opt/anaconda3/condabin:/opt/homebrew/bin:/opt/homebrew/sbin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

