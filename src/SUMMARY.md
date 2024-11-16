# Summary

[mincaml-rsについて](./introduction.md)
[このドキュメントについて](./about-this-guide.md)

# コンパイラの処理

- [コンパイルの流れ](./compilation.md)
- [字句解析・構文解析](./compilation/parsing.md)
- [名前解決と型推論](./compilation/typing.md)
- [クロージャ変換](./compilation/closure.md)
- [仮想アセンブリ](./compilation/asm_virtual.md)
- [コード生成](./compilation/codegen_wasm.md)

# コンパイラを改造する

- [ライブラリ関数](./lib_interface.md)
- [レジスタ割り当て](./regalloc.md)
- [最適化の余地](./optimization.md)
  - [グローバル変数の導入](./optimization/global_variable.md)

- [オリジナルとの対応](./correspondence.md)
- [初期の更新履歴](./changelog_v0.md)
