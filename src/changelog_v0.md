# 初期の更新履歴

## 0.2.0 - latest

- [#7](https://github.com/utokyo-compiler/mincaml-rs/pull/7)

  WebAssemblyのコード生成におけるクロージャの扱いをまともにしました．この変更前はクロージャを含むコードが実行できませんでした．

- [#6](https://github.com/utokyo-compiler/mincaml-rs/pull/6)

  `.mli`ファイルに関する機能を実装しました．インターフェースの型付けを実装する過程で`let`の型付けのバグに気づいたため修正しています．この変更前まではスコープの扱いが間違っていたようです．
  特に，クロージャ変換で`analyze_let_rec`が続く式を処理していなかった問題を修正しました．
  ランタイムの実装を追加してテストした結果に基づきWebAssemblyのコード生成の大部分も修正されましたが，クロージャに関してはこの時点で修正されませんでした．

- [#4](https://github.com/utokyo-compiler/mincaml-rs/pull/4)

  仮想アセンブリのデバッグ出力をデバッグし，人間向きになりました．この修正は第1回の課題に影響します．
  型推論におけるunifyし忘れに対応しました．

- [#3](https://github.com/utokyo-compiler/mincaml-rs/pull/3)

  `cargo run`により`main`が選ばれるようにし，`main`ではWebAssemblyのバイナリ形式を出力するようにしました．
  WebAssemblyのランタイムをワークスペースに追加しました．

## 0.1.0 - 0.2.0

2024年度の講義が開始した時点で0.2.0に上げたため，それ以前の歴史はここには書かないでおきます．
