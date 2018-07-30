# agrep-sample

agrepというあいまい検索ができるコマンドがあるらしいので試してみる。

## インストール

```sh
❯ wget ftp://ftp.cs.arizona.edu/agrep/agrep-2.04.tar
❯ tar -xf agrep-2.04.tar
❯ cd agrep-2.04
```

TODO: `make`できない。。。

### TRE

[TRE](https://github.com/laurikari/tre/)というものでもできるらしい。

```sh
❯ brew install tre
```

agrepの実装している[repoのissue](https://github.com/Wikinaut/agrep/issues/2)見ると以下のように述べられている。。。

> TRE ( https://github.com/laurikari/tre/ ) is not agrep...

[Agrep - Wikipedia](https://ja.wikipedia.org/wiki/Agrep)を読む限り、実態としてはTREが使われているようにも読み取れる。

実際TREをインストールすると`agrep`コマンドが使えるようになる。


## 試してみる

以下の`txt`から`Charlie`を探す。

```txt
Alice
Bob
Charlie
Dave
Ellen
Frank
```

`-#`で許容するエラーを指定しながら以下のように使える。これはノーミスパターン。

```sh
❯ agrep -1 Charlie sample.txt
Charlie
```

先頭小文字、`i`と`e`入れ替え。

```sh
❯ agrep -1 charlei sample.txt
```

`-2`にするといける。

```sh
❯ agrep -2 charlei sample.txt
Charlie
```

先頭を大文字にしてもOK

```sh
❯ agrep -1 Charlei sample.txt
Charlie
```

ちなみに、helpを見ると文字の欠けや余剰のコストは設定できるみたい。

```sh
Approximate matching settings:
  -D, --delete-cost=NUM	    set cost of missing characters
  -I, --insert-cost=NUM	    set cost of extra characters
  -S, --substitute-cost=NUM set cost of wrong characters
  -E, --max-errors=NUM	    select records that have at most NUM errors
  -#			    select records that have at most # errors (# is a
			    digit between 0 and 9)
```


## References
* [agrep(tre-agrep)コマンドであいまい検索を行う - 俺的備忘録 〜なんかいろいろ〜](https://orebibou.com/2016/07/agrep%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%A7%E3%81%82%E3%81%84%E3%81%BE%E3%81%84%E6%A4%9C%E7%B4%A2%E3%82%92%E8%A1%8C%E3%81%86/)
* [Agrep - Wikipedia](https://ja.wikipedia.org/wiki/Agrep)
* [TRE](https://github.com/laurikari/tre/)