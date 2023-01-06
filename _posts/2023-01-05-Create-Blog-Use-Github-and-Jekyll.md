---
title: Create Blog use Github and Jekyll on MacOS
published: true
---

# [](#header-1) Mục lục

1. Mục tiêu
2. Step need to do
  - `Step 1` - Upgrade ruby 3.1.3
  - `Step 2` - gem install jekyll
  - `Step 3` - create first project từ jekyll
  - `Step 4` - pick a theme in: https://jamstackthemes.dev/ssg/jekyll/page/4/
  - `Step 5` - add SSH and pull project by SSH : https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/GitHub-SSH-Key-Setup-Config-Ubuntu-Linux
  - `Step 6` - setup public Page in github: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
  - `Step 7` - remove repository name in github link: https://stackoverflow.com/questions/44531269/is-there-a-way-to-remove-repository-name-from-github-page-link
  

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

### [](#header-3) `Step 0` - Prerequisites 
- github account
- MacOS (Vì mình dùng Mac nên mình tổng hợp các step trên Mac, còn các OS khác như Linux, Win,.. thì về cơ bản cũng na ná. Bạn đọc tự tìm hiểu)
- Đã cài Homebrew 

### [](#header-3) `Step 1` - Upgrade ruby 3.1.3
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

### [](#header-3) `Step 2` - gem install jekyll
### [](#header-3) `Step 3` - create first project từ jekyll
Về cơ bản thì `Step 2` + `Step 3`  follow DOC của [https://jekyllrb.com/docs/](https://jekyllrb.com/docs/)
để install và run thử một project tạo từ jekyll.

```shell
$ gem install jekyll
$ jekyll new myblog
$ cd myblog
$ bundle exec jekyll serve
....
    Server address: http://127.0.0.1:4000/
```

Vô link server trên và bạn đã access vào blog của bạn.
Chúc mừng, bạn đã thành công khởi tạo blog cá nhân của bạn ở môi trường local.

### [](#header-3) `Step 4` - Pick a theme
Để rút gọn thời gian và tập trung vào việc đưa trang blog cá nhân của bạn vào luồng chạy,
hãy chọn một theme thích hợp với bạn ở đây: [https://jamstackthemes.dev/ssg/jekyll/](https://jamstackthemes.dev/ssg/jekyll/)

Pull theme mà bạn chọn và đọc qua cách sử dụng theme đó.


🚩 **Note**: Tới đây thì về cơ bản bạn đã tạo được môi trường để có thể chạy jekyll project.
Vấn đề tiếp theo là triển khai project từ máy của bạn lên môi trường Internet.
Ở đây chúng ta lựa chọn nền tảng github để triển khai blog của mình.


### [](#header-3) `Step 5` - Add SSH and pull project by SSH

Github thay đổi security policy và bắt chúng ta pull/push project qua ssh.
Nên bạn cần setup SSH config và pull project với SSH key đó.

Plz follow the below link:
[GitHub-SSH-Key-Setup-Config-Ubuntu-Linux](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/GitHub-SSH-Key-Setup-Config-Ubuntu-Linux)


### [](#header-3) `Step 6` - Setup public Page in github

Tới đây thì về cơ bản bạn đã push được project lên github. Github cung cấp cho chúng ta 
một tính năng để triển khai những đoạn code kia thành trang blog của bạn.
Github lo tất, triển khai, DNS, ..... etc 

Việc của bạn là tham khảo cấu hình `Page` của github:
[https://docs.github.com/en/pages/getting-started-with-github-pages](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)


### [](#header-3) `Step 7` - Remove repository name in github link
Đến đây thì bạn sẽ thấy link blog của bạn có hơi kì kì.
Kiểu `blogcuatoi.gihub.com/myblog`, cái path trùng với repository name của project của bạn thành mặc định của path đường dẫn.
Nó hơi kì cục và để pro hơn, bạn nên cấu hình xoá path đó đi, chuyển thành đúng dạng domain `blogcuatoi.github.com` 

> To remove the repository name, you'll need to make it a User Page (or an Organization page). 
> Create a repository named myusername.github.io, and commit your content to the master branch

See [this help page](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages) for more information.

Refer: https://stackoverflow.com/questions/44531269/is-there-a-way-to-remove-repository-name-from-github-page-link
