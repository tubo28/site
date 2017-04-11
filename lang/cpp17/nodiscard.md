# [[nodiscard]]属性
* cpp17[meta cpp]

## 概要

`[[nodiscard]]`属性は関数の戻り値を破棄してはならないことをコンパイラに伝え、破棄した場合に警告するための属性である。

例えばエラーを無視して処理を続行してはならない関数があったとき、プログラマが間違えてエラーを無視してしまった場合に、コンパイル時に警告を発生させることができる。

従来は警告を発生させる標準的な方法が無かったが、`[[nodiscard]]`属性により戻り値を破棄してはならないことをコンパイラに伝えることができる。

## 仕様

`[[nodiscard]]`属性は、以下の要素に対して指定できる。

* 関数宣言
* クラスもしくは列挙型の宣言

## 例
```cpp
//無視してはいけないデータ型
struct [[nodiscard]] error_info { /*...*/ };

error_info safety_mode();
void launch();

//関数の戻り値を必ず使用すること
[[nodiscard]] int check_mode();

void test_missiles() {
  safety_mode(); //無視してはいけない型を無視したため、警告が発生するだろう
  launch();

  check_mode(); //戻り値を無視しているため、警告が発生するだろう
}
```

### 出力
```
(対応コンパイラがあれば、コンパイル結果を後ほど記述)
```

## 関連項目
- [C++11 属性構文](/lang/cpp11/attributes.md)

## 参照
- [P0068R0 Proposal of [[unused]], [[nodiscard]] and [[fallthrough]] attributes.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf)
- [P0189R1 Wording for [[nodiscard]] attribute.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)