---
slug: ruby
title: Ruby
layout: page.jade
---

#### → __[Ruby-Gem](/wiki/ruby-gem/)__


## リファレンス

#### [逆引きRuby](http://www.namaraii.com/rubytips/)

逆引きRubyはRubyを使ってやりたい事から、その方法を調べられる逆引きのリファレンスです。

- [逆引きRuby - ディレクトリ](http://www.namaraii.com/rubytips/?%A5%C7%A5%A3%A5%EC%A5%AF%A5%C8%A5%EA=)  
Dirクラスによりディレクトリの作成、削除、ファイル一覧取得などを行うことができます。
- [逆引きRuby - 例外](http://www.namaraii.com/rubytips/?%E4%BE%8B%E5%A4%96)
- [Ruby Error Handling, Beyond the Basics](http://www.sitepoint.com/ruby-error-handling-beyond-basics/)

#### [Ruby · Styleguide](https://github.com/styleguide/ruby)
GitHubのRubyコーディング規約

#### [Awesome Ruby](https://github.com/Sdogruyol/awesome-ruby)
Ruby関連の厳選リンク集


### 本
- [Amazon.co.jp： Effective Ruby あなたのRubyをより輝かせる48の特別な方法: Peter J. Jones, arton, 長尾 高弘: 本](http://www.amazon.co.jp/dp/4798139823)
- [これからRubyを勉強する人が絶対読んでおきたい書籍9冊＋α | Find Job ! Startup](http://www.find-job.net/startup/ruby-books)
- [Rails で "とりあえず動くコード" を書けるようになった人が次に遭遇する問題とそれを解決してくれる本まとめ - 彼女からは、おいちゃんと呼ばれています](http://blog.inouetakuya.info/entry/2014/06/08/194015)


## まとめ

- [2013年新学期にRubyを始めるエンジニアが読むべきサイトまとめ - satooshi@blog](http://blog.satooshi.jp/blog/2013/04/08/before-you-get-started-ruby-programming/)

### 記法

- [知って得する！５５のRubyのトリビアな記法](http://melborne.github.io/2013/03/04/ruby-trivias-you-should-know-4/)
- [Rubyで使われる記号の意味（正規表現の複雑な記号は除く）](http://docs.ruby-lang.org/ja/1.8.7/doc/symref.html)
- [Rubyでrbファイルをrequireするときはドットを打つと良さそう - アインシュタインの電話番号](http://blog.ruedap.com/2011/05/31/ruby-require-load-path)  
※Ruby 1.9.2ではロードパスにカレントディレクトリが含まれなくなった  
`require './hoge.rb'`
    - [Ruby1.9.2以降でrequireする際の注意点 - Qiita](http://qiita.com/nekogeruge_987/items/2d18f388219597c75e05)  
      `require_relative 'app.rb'`
- [Ruby/演算子 - BugbearR's Wiki](http://www.bugbearr.jp/?Ruby%2F%E6%BC%94%E7%AE%97%E5%AD%90)
- [ビット反転演算子（~）でindexOfの判定 - hokaccha.hamalog v2](http://d.hatena.ne.jp/hokaccha/20110718/1310941427)  
チルダはビット反転演算子で、整数をビット反転させると符号を反転させて1引いた数になる。  
つまり-1のときだけ0になるので、indexOfと組み合わせて使うことができる。
- [RubyのFile.expand_path('相対パス', __FILE__)の意味 - maeharinの日記](http://d.hatena.ne.jp/maeharin/20130104/p1)
- [Procを制する者がRubyを制す（嘘）](http://melborne.github.io/2014/04/28/proc-is-the-path-to-understand-ruby/)  
  `Method#call`, `& + call == yield`, `Proc, lambda, ->`
- [Rubyにおけるスコープのおはなし](http://melborne.github.io/2013/09/24/rubys-scope/)  
  インスタンス変数(`@`)、クラス変数(`@@`)、グローバル変数(`$`)
- [Rubyのモジュールメソッドの作り方 - Qiita](http://qiita.com/ionis_h/items/5f26248ea4e154cce424)


### よく使う

#### Encoding

    # coding: utf-8

#### 正規表現

- [正規表現](http://docs.ruby-lang.org/ja/2.2.0/doc/spec=2fregexp.html)

```ruby
# 抽出
"Hello, World".slice /W.+$/  #=> "World"
"Hello, World".slice /w.+$/i #=> "World"

# マッチ＆抽出
"Hello, World. Hey, John.".match(%r{Hey, (.*).})[1] #=> "John"
"/path/to/article?q=hello".match(%r{.*/article\?q=(.*)})[1] #=> "hello"

# 含む
"Hello, World" =~ /Hello/  #=> 0
"Hello, World" =~ /hello/  #=> nil
"Hello, World" =~ /hello/i #=> 0
"Hello, World".include? "Hello" #=> true
["dog", "cat", "mouse"].include? "cat" #=> true

# 完全一致
"Hello, World" =~ /^Hello$/        #=> nil
"Hello, World" =~ /^Hello, World$/ #=> 0
```

#### String

- [Rubyで%記法（パーセント記法）を使う - Qiita](http://qiita.com/mogulla3/items/46bb876391be07921743)
- [Rubyでクオート、ダブルクオート以外でのStringの書き方 - Qiita](http://qiita.com/tsugi2009/items/dc974669e55a2cbe2809)

```ruby
str = %(Programming language "Ruby")
puts str
# => Programming language "Ruby"

ruby = "Ruby"
str2 = %(Programming language "#{ruby}")
puts str2
# => Programming language "Ruby"
```

| %  | desc |
|----|----------------------------------------|
| %  | ダブルクオートで囲う場合と同等。式展開される。 |
| %q | シングルクオートで囲う場合と同等。式展開されない。 |
| %W | スペース区切りで配列定義。式展開される。 |
| %w | スペース区切りで配列定義。式展開されない。 |
| %I | 要素がシンボルの配列を作る。式展開される。 |
| %i | 要素がシンボルの配列を作る。式展開されない。 |
| %x | コマンド出力を行う。バッククオートで囲った場合と同等。 |
| %s | シンボル。式展開されない。 |

#### true / false

```ruby
!!(1)   #=> true
!!(0)   #=> true
!!(-1)  #=> true
!!(nil) #=> false
!!([])  #=> true
!!({})  #=> true
```

#### オブジェクトを JSON に変換
```ruby
JSON.generate(obj)
JSON.pretty_generate(obj) # 整形
```

#### 日付・時刻の計算
```ruby
require 'active_support/time'

Time.now           #=> 2014-10-24 20:50:15 +0900
Time.now + 3.hours #=> 2014-10-24 23:50:15 +0900
```
via - [Rubyで日付の計算するならactive_support使っとけって世間で言われてるけどマジだわ - yachibit.log](http://yachibit.hatenablog.jp/entry/2013/06/08/030926)

### Books

- [Rails で "とりあえず動くコード" を書けるようになった人が次に遭遇する問題とそれを解決してくれる本まとめ - 彼女からは、おいちゃんと呼ばれています](http://blog.inouetakuya.info/entry/2014/06/08/194015)


## Install Ruby

### Install rbenv on Mac

- [Ruby - Homebrewのインストールとrbenvのインストール Mac編 - Qiita](http://qiita.com/issobero/items/e0443b79da117ed48294)  
  `$ rbenv init`も必要 https://github.com/sstephenson/rbenv#how-rbenv-hooks-into-your-shell

### Install uru on Windows

- [pikの替わりにuru～windowsで複数バージョンのrubyを切り替える～ - Qiita](http://qiita.com/tikkss@github/items/a70af204d5fb3612bb39)

### Install rbenv on Ubuntu

```bash
$ sudo apt-get update
$ sudo apt-get dist-upgrade
$ sudo apt-get install ssh git build-essential libssl-dev

$ git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshrc
$ echo 'eval "$(rbenv init -)"' >> ~/.zshrc

$ git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build

$ rbenv install 2.0.0-p353
$ rbenv global 2.0.0-p353
$ rbenv rehash
```
- https://github.com/sstephenson/rbenv#installation
    - `rbenv install` needs [ruby-build](https://github.com/sstephenson/ruby-build#readme)

#### Ruby 1.9.3 のインストールでエラー発生

```bash
checking for gcc... /usr/bin/gcc-4.2
checking whether the C compiler works... no
configure: error: in `/tmp/ruby-build.20140417163730.6400/yaml-0.1.6':
configure: error: C compiler cannot create executables
```

`gcc-4.2`が見つからないのが原因。`$ gcc -v`を見ると 4.6.3 となっていた。 4.2 のインストール方法を探しても見つからないのでシンボリックリンクを張って対処。

```bash
$ sudo ln -sf /usr/bin/gcc /usr/bin/gcc-4.2
```

### Update rbenv

```bash
$ cd ~/.rbenv
$ git pull origin master
$ cd ~/.rbenv/plugins/ruby-build
$ git pull origin master
```
via - [rbenvとruby-buildでRuby環境を最新に保つ](https://gist.github.com/mochiz/4736183)

### 新規プロジェクト作成時

- [bundlerでgemをプロジェクトごとに管理する ｜ Developers.IO](http://dev.classmethod.jp/server-side/language/bundler-gem-management/)
    - [Windows Proxy環境でbundle installでのエラー回避 ? Ryu's Blog](http://www.ryuslab.com/archives/179)

<pre>
$ cd %ProjectDir%
$ bundle init
Gemfileに追記 gem 'gemname'
$ set http_proxy=http://localhost:8080
$ bundle install --path vendor/bundle
$ bundle exec ruby sample.rb
</pre>

- [Proxy経由のgem install - 京の路](http://blog.matake.jp/archives/proxygem_install)


## 開発環境
- [Rubyプログラミングが快適になるVim環境を0から構築する - Qiita](http://qiita.com/mogulla3/items/42a7f6c73fa4a90b1df3)

#### 環境変数

- [Ruby - Dotenv使ってみた - Qiita](http://qiita.com/ogawatti/items/e1e612b793a3d51978cc)


## Rake
- [ファイルを扱う作業をRakeで便利にしよう！（パート1：概要編） - るびくる＆RBのRubyプログラミング大作戦！ - rubicle.net](http://rubicle.net/rubicle_talk_1-1.html)
- [ファイルを扱う作業をRakeで便利にしよう！（パート2：実践編1） - るびくる＆RBのRubyプログラミング大作戦！ - rubicle.net](http://rubicle.net/rubicle_talk_1-2.html)


## irb

"Interactive Ruby" ― 対話型 Ruby 処理系

```bash
$ irb
```

exit で終了

- [configuration - IRb: how to start an interactive ruby session with pre-loaded classes - Stack Overflow](http://stackoverflow.com/questions/2652514/irb-how-to-start-an-interactive-ruby-session-with-pre-loaded-classes)  
  ライブラリを自動読み込みする
```bash
$ irb -r 'myclass.rb'
```

- [irb を快適に使うための Tips - すがブロ](http://sugamasao.hatenablog.com/entry/20091207/1260143043)
- [configuration - IRb: how to start an interactive ruby session with pre-loaded classes - Stack Overflow](http://stackoverflow.com/questions/2652514/irb-how-to-start-an-interactive-ruby-session-with-pre-loaded-classes)

### Pry
#### [Pry - an IRB alternative and runtime developer console](http://pryrepl.org/)

- [Rubyistよ、irbを捨ててPryを使おう - TIM Labs](http://labs.timedia.co.jp/2011/12/rubyist-should-use-pry.html)
- [Ruby - Pryコンソールのプロンプトをカラフルかつ便利にする - Qiita](http://qiita.com/okuramasafumi/items/900286cd4f07c1bbbb5d)
- [Ruby - awesome_print を pry の表示のデフォルトに使う - Qiita](http://qiita.com/Linda_pp/items/d75d7c3953faa34a1f0e)


## TIPS

#### コマンドライン引数

*[Rubyメモ - コマンドライン引数](http://www2.atwiki.jp/kmo2/pages/16.html)

<pre>
puts ARGV[0]
</pre>

### 例外
- [Ruby - Railsアプリケーションにおけるエラー処理（例外設計）の考え方 - Qiita](http://qiita.com/jnchito/items/3ef95ea144ed15df3637)

### File

#### 出力
```ruby
# r:読込 w:上書 a:追記
open("log.txt", "a"){|f| f.write("文字列")}
```

#### Path
- [Get Filename without extension from file path in Ruby - Stack Overflow](http://stackoverflow.com/questions/374326/get-filename-without-extension-from-file-path-in-ruby)

```ruby
File.basename("/home/gumby/work/ruby.rb")          #=> "ruby.rb"
File.basename("/home/gumby/work/ruby.rb", ".rb")   #=> "ruby"
```

### Debug
#### メソッド一覧

<pre>
require 'pp'
pp [].methods.sort
</pre>

##### pry
- [Ruby - ググるよりもまずはpry - Qiita](http://qiita.com/Kokudori/items/2b36068cdf2e40e75c2d)

#### ブロックコメント

<pre>
=begin
  :
  :
=end
</pre>

#### CSV
- [Ruby標準添付ライブラリcsvのCSV.tableメソッドが最強な件について](http://melborne.github.io/2013/01/24/csv-table-method-is-awesome/)
    - [Ruby 2.1.0 リファレンスマニュアル class CSV::Table](http://docs.ruby-lang.org/ja/2.1.0/class/CSV=3a=3aTable.html)

```ruby
CSV.table("data.tsv", { :col_sep => "\t", :quote_char => "\"" }) # needs header row
```

#### Array

要素数を指定して取得
```ruby
[1,2,3,4,5].take(3)  #=> [1, 2, 3]
[1,2,3,4,5].first(3) #=> [1, 2, 3]
```

- [rubyの配列からnilと空文字を取り除く - Qiita](http://qiita.com/ta1kt0me@github/items/33c4d37a65b69b75ee40)

### Time

#### ActiveSupport による日時演算
```ruby
gem 'activesupport'
require 'active_support/all'

Time.now                #=> 2014-10-06 21:39:10 +0900
Time.now.since(3.hours) #=> 2014-10-07 00:39:10 +0900
```

#### ActiveSupport による UTC(String) → JST(String) 変換
9時間進めて JST 表記にする
```ruby
gem 'activesupport'
require 'active_support/all'

Time.strptime("2014-10-06 12:39:10 UTC", "%F %T UTC").since(9.hours).strftime("%F %T JST")
#=> "2014-10-06 21:39:10 JST"
```

### rails/blank.rb
- [rails/blank.rb at master · rails/rails](https://github.com/rails/rails/blob/master/activesupport/lib/active_support/core_ext/object/blank.rb)
- [Rails以外の環境でblank?メソッドを使うときの注意 - (ﾟ∀ﾟ)o彡 sasata299's blog](http://blog.livedoor.jp/sasata299/archives/51495666.html)


## Rubyワンライナー

- [Rubyワンライナー入門 - maeharinの日記](http://d.hatena.ne.jp/maeharin/20130113/ruby_oneliner)

### ワンライナー基礎

"-e": 一番基本的なオプション。スクリプトを実行する。（ちなみに他のオプションと組み合わせる時は必ず最後に記載する）

<pre>
$ ruby -e 'puts "hoge"'
</pre>

#### Windowsの環境変数Pathを改行して表示

<pre>
echo %path% | ruby -F; -ane 'puts $F'
</pre>

`echo %path%`で出力される内容を、rubyコマンドの引数として渡し、`-n`オプションによって行ごとに処理をループする。ループは Kernel.#gets により組込変数`$_`に格納される。`echo %path%`の場合は`;`区切りの1行文字列のため、ループは1回となる。次に、`-a`オプションによってループの先頭で自動的に $F = $_.split が実行され、結果の格納された`$F`を puts で出力している。splitの区切り文字はデフォルトで半角スペースのようだが、オプション`-F;`で`;`を区切り文字に指定している。

### [rubyを使って簡易webサーバー構築](https://gist.github.com/manji6/5056073)


## Ruby技術者認定試験
### [Rubyアソシエーション: Ruby技術者認定試験制度](http://www.ruby.or.jp/ja/certification/examination/)
- [Ruby技術者認定試験Silverに卒業単位やばい学生だけど合格できたお話【試験合格記】 | メモ帳代わりのブログ](http://www.absolute-keitarou.net/blog/?p=785)
- [Rubyアソシエーション: Ruby技術者認定試験再受験無料キャンペーン](http://www.ruby.or.jp/ja/news/20141105.html)