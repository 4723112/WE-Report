# 第8回 Webエンジニアリング演習 レポート
## 学籍番号（名前は書かなくてよい）
4723112
## 実装した内容
@app.put("/todos/{todo_id}", response_model=TodoItem_Pydantic)
async def update_todo(todo_id: int, req: TodoItemUpdate_Pydantic):
    todo = await TodoItem.get(id=todo_id)
    if not todo:
        raise HTTPException(status_code=404, detail=f"ID {todo_id} のTODOが見つかりません")

    todo.title = req.title if req.title is not None else todo.title
    todo.description = req.description if req.description is not None else todo.description
    todo.completed = req.completed if req.completed is not None else todo.completed
    await todo.save()
    return todo
## 動作確認結果
get/todos (Get All Todos)
[
  {
    "id": 1,
    "title": "いいいいい",
    "description": "変更後",
    "completed": true
  },
  {
    "id": 2,
    "title": "01",
    "description": "first",
    "completed": false
  }
]

put/todos/{todo_id}
{
  "id": 2,
  "title": "02.1",
  "description": "second",
  "completed": true
}

get/todos (Get All Todos)
[
  {
    "id": 1,
    "title": "いいいいい",
    "description": "変更後",
    "completed": true
  },
  {
    "id": 2,
    "title": "02.1",
    "description": "second",
    "completed": true
  }
]

put/todos/{todo_id}
{
  "detail": "Object \"TodoItem\" does not exist"
}