# オリジナルとの対応

## コマンドライン引数

| オリジナル           | dune 対応版                    | mincaml-rs                                   |
| -------------------- | ------------------------------ | -------------------------------------------- |
| `./min-caml ./adder` | `dune exec mincaml -- ./adder` | `cargo run -- -i ./adder.ml -o ./adder.wasm` |

## モジュール

| オリジナル        | mincaml-rs                                   |              概要              |
| ----------------- | -------------------------------------------- | :----------------------------: |
| `syntax.ml`       | `syntax`                                     |            構文定義            |
| `lexer.mll`       | `parser::lexer`                              |           字句解析器           |
| `parser.mly`      | `parser::parser`                             |           構文解析器           |
| `type.ml`         | `ty`                                         |      構文木のための型定義      |
| `typing.ml`       | `typing`                                     |             型推論             |
| -                 | `ir_typed_ast`                               |        型推論後の構文木        |
| `kNormal.ml`      | `ir_knorm::{syntax, lowering}`               |            K 正規化            |
| `alpha.ml`        | `typing::name_res`, `ir_knorm::alpha_rename` |       名前解決 (α 変換)        |
| `beta.ml`         | `ir_knorm_passes::beta_convert`              |             β 簡約             |
| `assoc.ml`        | `ir_knorm_passes::let_flatten`               |            A 正規化            |
| `inline.ml`       | `ir_knorm_passes::inlining`                  |          インライン化          |
| `constFold.ml`    | `ir_knorm_passes::constant_fold`             |          定数畳み込み          |
| `elim.ml`         | `ir_knorm_passes::eliminate_unused`          |        不要な束縛の除去        |
| `closure.ml`      | `ir_closure::{syntax, lowering}`             |         クロージャ変換         |
| `main.ml`         | `main`                                       |           main 関数            |
| `x86/emit.ml`, .. | `codegen_wasm`                               | アーキテクチャ固有のコード生成 |

## データ型の要素

| オリジナル                  | mincaml-rs       |
| --------------------------- | ---------------- |
| `Unit`, `Int`,..            | `Const(LitKind)` |
| `Neg`, `FNeg`               | `Unary`          |
| `Add`, ..                   | `Binary`         |
| `Put`                       | `Set`            |
| `ExtArray`,`ExtFunApp`      | -                |
| `Let`, `LetTuple`, `LetRec` | `Let`            |
