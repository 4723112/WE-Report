# 第7回 Webエンジニアリング演習 レポート
## 学籍番号（名前は書かなくてよい）
4723112
## PUTリクエスト検証用のモデルとAPI部分のコード
# PUTエンドポイントの実装
@app.put("/todos/{todo_id}", response_model=TodoItem) # idはパスパラメータで取得
def update_todo(todo_id: int, req: TodoItemUpdateScheme): # リクエストボディの検証モデルを指定
    for i, todo in enumerate(todos):
        if todo.id == todo_id:
            todos[i] = TodoItem(
                id=todo_id,
                title=req.title if req.title is not None else todo.title,
                description=req.description if req.description is not None else todo.description,
                completed=req.completed if req.completed is not None else todo.completed
            )
            return todos[i]
    raise HTTPException(status_code=404, detail=f"ID {todo_id} のTODOが見つかりません")
## 動作確認結果
- Swagger UIでのPUTエンドポイントテスト結果
- 正常系：存在するタスクの更新
Request body
todo_id = 6
{
  "title": "aaaaaaaa",
  "description": "bbbbbb",
  "completed": true
}

Response body
{
  "id": 6,
  "title": "aaaaaaaa",
  "description": "bbbbbb",
  "completed": true
}
- 異常系：存在しないタスクIDでのエラー確認
Request body
todo_id = 8
{
  "title": "aaaaaaaa",
  "description": "bbbbbb",
  "completed": true
}

Response body
{
  "detail": "ID 8 のTODOが見つかりません"
}