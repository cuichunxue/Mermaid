# シーケンス図テストコード

このファイルには、`<br/>`タグを含むシーケンス図のテストコードが含まれています。
エディタに貼り付けると、自動的に正しい形式に変換されます。

## テスト1: 基本的なNote with <br/>

```mermaid
sequenceDiagram
    participant A
    participant B

    A->>B: Request
    Note over A,B: This is a multi-line note<br/>Line 2<br/>Line 3
    B-->>A: Response
```

**自動変換後:**
```mermaid
sequenceDiagram
    participant A
    participant B

    A->>B: Request
    Note over A,B: This is a multi-line note
    Note over A,B: Line 2
    Note over A,B: Line 3
    B-->>A: Response
```

## テスト2: Note left of / right of

```mermaid
sequenceDiagram
    participant User
    participant System

    User->>System: Login
    Note left of User: User enters<br/>username and<br/>password
    Note right of System: System validates<br/>credentials<br/>in database
    System-->>User: Success
```

**自動変換後:**
```mermaid
sequenceDiagram
    participant User
    participant System

    User->>System: Login
    Note left of User: User enters
    Note left of User: username and
    Note left of User: password
    Note right of System: System validates
    Note right of System: credentials
    Note right of System: in database
    System-->>User: Success
```

## テスト3: 複雑なシーケンス図（元のコード）

以下は、ユーザーが提供した元のコードです。このまま貼り付けても動作します：

```mermaid
sequenceDiagram
    participant User
    participant Main as plot_datapy.py (main)
    participant Plot as PlotClusterData()
    participant PLT as matplotlib

    User->>Main: Execute script
    activate Main

    Main->>Plot: PlotClusterData(train_data, test_data, 0, 100)
    activate Plot
    Plot->>PLT: Create 2x3 subplot figure
    activate PLT

    Note over Plot,PLT: Create 6 scatter plots:<br/>1. Speed vs Current<br/>2. Speed vs CAA<br/>3. Current vs CAA<br/>4. Speed vs Mode<br/>5. Current vs Mode<br/>6. CAA vs Mode

    loop For each subplot
        Plot->>PLT: scatter() for test_data
        PLT-->>Plot: Scatter plot created
        Plot->>PLT: scatter() for train_data
        PLT-->>Plot: Scatter plot created
    end

    Plot->>PLT: plt.show()
    PLT-->>Plot: Display figure
    deactivate PLT
    Plot-->>Main: Plots displayed
    deactivate Plot

    Main-->>User: Script completed
    deactivate Main
```

## テスト4: 日本語コンテンツ

```mermaid
sequenceDiagram
    participant ユーザー
    participant システム
    participant データベース

    ユーザー->>システム: ログイン要求
    Note over ユーザー,システム: 認証処理開始<br/>ユーザー名とパスワードを確認<br/>セッショントークンを生成

    システム->>データベース: ユーザー情報取得
    activate データベース
    Note right of データベース: データベース検索<br/>ユーザーテーブルから<br/>該当レコードを取得
    データベース-->>システム: ユーザー情報
    deactivate データベース

    システム-->>ユーザー: ログイン成功
    Note left of ユーザー: セッション開始<br/>ダッシュボードに<br/>リダイレクト
```

## 使い方

1. 上記のいずれかのコードブロックをコピー
2. Mermaidエディタに貼り付け
3. 「実行」ボタンをクリック
4. 自動的に`<br/>`タグが複数のNote行に分割されます
5. エディタのコードも自動更新されます

## 確認ポイント

- ✅ `<br/>`タグが自動的に削除される
- ✅ 1つのNoteが複数のNote行に分割される
- ✅ Note over/left of/right of の位置が保持される
- ✅ エラーなく図が表示される
- ✅ SVG/PNG保存が正常に動作する
