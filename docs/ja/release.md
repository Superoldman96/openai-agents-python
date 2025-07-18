---
search:
  exclude: true
---
# リリースプロセス／変更履歴

プロジェクトでは、 `0.Y.Z` 形式を用いたセマンティックバージョニングのやや変更されたバージョンを採用しています。先頭の `0` は SDK がまだ急速に進化していることを示します。各コンポーネントの増分規則は以下のとおりです。

## マイナー ( `Y` ) バージョン

ベータでない公開インターフェースに **互換性を壊す変更 (breaking changes)** が入る場合、マイナーバージョン `Y` を増やします。たとえば `0.0.x` から `0.1.x` への更新には互換性を壊す変更が含まれることがあります。

互換性を壊す変更を避けたい場合は、プロジェクトで `0.0.x` 系にバージョンを固定することを推奨します。

## パッチ ( `Z` ) バージョン

互換性を壊さない変更では `Z` を増やします。

- バグ修正  
- 新機能  
- プライベートインターフェースの変更  
- ベータ機能の更新  

## 互換性を壊す変更の変更履歴

### 0.2.0

このバージョンでは、これまで `Agent` を引数に取っていたいくつかの箇所が、代わりに `AgentBase` を引数に取るようになりました。例としては MCP サーバーの `list_tools()` 呼び出しなどです。型に関する変更のみであり、受け取るオブジェクトは引き続き `Agent` です。更新する際は、型エラーを解消するために `Agent` を `AgentBase` に置き換えてください。

### 0.1.0

このバージョンでは、[`MCPServer.list_tools()`][agents.mcp.server.MCPServer] に新しいパラメーター `run_context` と `agent` が追加されました。`MCPServer` を継承するクラスでは、これらのパラメーターを追加する必要があります。