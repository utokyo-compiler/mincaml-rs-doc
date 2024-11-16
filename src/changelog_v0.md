# 初期の更新履歴

プロセッサ・コンパイラ実験両方に関係する更新履歴をまとめています．

## 0.2.0 - 0.2.1

- [#15](https://github.com/utokyo-compiler/mincaml-rs/pull/15)

  - (codegen_wasm) float型関係のコード生成部分を修正しました．ローカル変数の宣言が誤って引数を含んでいるのを修正しました．
  - (codegen_wasm) 自己参照するクロージャが自身をクロージャ経由で呼び出すことができなかったのを修正しました．
  - (ir_closure::lowering) 直接呼べることがわかっている関数が他の関数内で自由変数とみなされる問題を修正しました．
  - (ir_closure::lowering) 引数を持たないが値として使用されるためにクロージャを生成する必要がある関数を，自身の定義内部ではクロージャを経由せず呼び出すようにしました．
  - (runtime) `miniMLRuntime.mli`の実装に必要なランタイム実装を追加しました．

  cpuex-v1.4 のファイルはこの時点でおおよそ正常に動作することを確認しました．最適化はすべて無効化されているので，画像サイズは 64 × 64 程度にすることを推奨します．

  ```
  cargo run -- -i ./globals.ml -i ./minrt.ml -i ./miniMLRuntime.mli -o ./out.wasm
  cargo run -p runtime ./out.wasm < ./contest.sld > ./contest_64_p6.ppm
  ```

- [#14](https://github.com/utokyo-compiler/mincaml-rs/pull/14)

  - `;`に関する優先順位の問題を修正しました．
  - コメントの字句解析時点で`str::trim_start_matches`ではなく誤って`str::trim_matches`を使用していたのを修正しました．
  - 型推論のパターンマッチの順序の誤りを修正しました．

- [#12](https://github.com/utokyo-compiler/mincaml-rs/pull/12)

  パーサーにより`minrt.ml`が受理できるようにしましたが，この時点では生成される構文木に誤りがありました．[#14](https://github.com/utokyo-compiler/mincaml-rs/pull/14) で修正されます．

- [#10](https://github.com/utokyo-compiler/mincaml-rs/pull/10)

  `00`のようなリテラルを無効化したり，`-`が int と float の両方を受けつけることに対応したりしました．

  仮想アセンブリへの変換で，関数の戻り値を直接 return する式が入力された場合の処理で代入が行われていなかった問題を修正しました．仮想アセンブリへの変換には他の致命的なバグがあり，それはここでは修正されていません．

- [#7](https://github.com/utokyo-compiler/mincaml-rs/pull/7)

  WebAssembly のコード生成におけるクロージャの扱いをまともにしました．この変更前はクロージャを含むコードが実行できませんでした．

- [#6](https://github.com/utokyo-compiler/mincaml-rs/pull/6)

  `.mli`ファイルに関する機能を実装しました．インターフェースの型付けを実装する過程で`let`の型付けのバグに気づいたため修正しています．この変更前まではスコープの扱いが間違っていたようです．
  特に，クロージャ変換で`analyze_let_rec`が続く式を処理していなかった問題を修正しました．
  ランタイムの実装を追加してテストした結果に基づき WebAssembly のコード生成の大部分も修正されましたが，クロージャに関してはこの時点で修正されませんでした．

- [#4](https://github.com/utokyo-compiler/mincaml-rs/pull/4)

  仮想アセンブリのデバッグ出力をデバッグし，人間向きになりました．この修正は第 1 回の課題に影響します．
  型推論における unify し忘れに対応しました．

- [#3](https://github.com/utokyo-compiler/mincaml-rs/pull/3)

  `cargo run`により`main`が選ばれるようにし，`main`では WebAssembly のバイナリ形式を出力するようにしました．
  WebAssembly のランタイムをワークスペースに追加しました．

## 0.1.0 - 0.2.0

2024 年度の講義が開始した時点で 0.2.0 に上げたため，それ以前の歴史はここには書かないでおきます．
