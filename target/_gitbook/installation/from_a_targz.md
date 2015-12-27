# tar.gz からインストール

何らかの理由で、これまで紹介した方法でインストールすることができない場合、.tar.gz ファイルをダウンロードする方法もあります。その中に、Crystal に必要なすべてのものが含まれています。

最新のファイルは [GitHub のリリースページ](https://github.com/manastech/crystal/releases)から入手することが可能です。

それぞれのプラットフォームに合わせて適切なファイルをダウンロードして展開してください。その中に、`bin/crystal` という実行ファイルが含まれています。

実行ファイルに対して、パスの通った場所のシンボリックを貼っておけば、より簡単に利用することができるでしょう。

`ln -s [full path to bin/crystal] /usr/local/bin/crystal`

こうしておけば、`crystal` と入力するだけでコンパイラを起動することができます。