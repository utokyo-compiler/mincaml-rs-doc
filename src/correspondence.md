# オリジナルとの対応

## モジュール

| オリジナル        | mincaml-rs                                               |           概要           |
| ----------------- | -------------------------------------------------------- | :----------------------: |
| `syntax.ml`       | `syntax/src/lib.rs`                                      |         構文定義         |
| `lexer.mll`       | `parser/src/lexer`                                       |        字句解析器        |
| `parser.mly`      | `parser/src/parser`                                      |        構文解析器        |
| `type.ml`         | `ty/src/lib.rs`                                          |   構文木のための型定義   |
| `typing.ml`       | `typing/src/lib.rs`                                      |          型推論          |
| -                 | `ir_typed_ast`                                           |     型推論後の構文木     |
| `kNormal.ml`      | `ir_knorm/src/{syntax, lowering}.rs`                     |         K 正規化         |
| `alpha.ml`        | `typing/src/name_res.rs`, `ir_knorm/src/alpha_rename.rs` |    名前解決 (α 変換)     |
| `beta.ml`         | `ir_knorm_passes/src/beta_convert.rs`                    |          β 簡約          |
| `assoc.ml`        | `ir_knorm_passes/src/let_flatten.rs`                     |         A 正規化         |
| `inline.ml`       | `ir_knorm_passes/src/inlining.rs`                        |       インライン化       |
| `constFold.ml`    | `ir_knorm_passes/src/constant_fold.rs`                   |       定数畳み込み       |
| `elim.ml`         | `ir_knorm_passes/src/eliminate_unused.rs`                |     不要な束縛の除去     |
| `closure.ml`      | `ir_closure/src/{syntax, lowering}.rs`                   |      クロージャ変換      |
| `main.ml`         | `main/src/main.rs`                                       |        main 関数         |
| `x86`, ..         | -                                                        | アーキテクチャ固有の実装 |
| `x86/emit.ml`, .. | `codegen_wasm`                                           |        コード生成        |

## データ型の要素

| オリジナル                  | mincaml-rs       |
| --------------------------- | ---------------- |
| `Unit`, `Int`,..            | `Const(LitKind)` |
| `Neg`, `FNeg`               | `Unary`          |
| `Add`, ..                   | `Binary`         |
| `Put`                       | `Set`            |
| `ExtArray`,`ExtFunApp`      | -                |
| `Let`, `LetTuple`, `LetRec` | `Let`            |
