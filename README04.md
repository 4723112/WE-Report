# 第4回 Webエンジニアリング演習 レポート
## 学籍番号（名前は書かなくてよい）
47231112
## 実装したプログラム
- `book_manager.py`の内容と処理の説明
import sys
import json

#　本データベースの初期化
books = [
    {"title": "Java基礎",
    "author": "佐藤花子",
    "year": 2023,
    "isbn": "978-4-987654-32-1",
    "price": 2800
    },
    {
    "title": "Web開発",
    "author": "山田次郎",
    "year": 2023,
    "isbn": "978-4-111111-11-1",
    "price": 3200
    }
]

#1.

#2.
new = json.loads(sys.argv[1])
books.append(new)

print()
print(books)
print()

#3.
print("本データベース:")
print("1." + books[0]["title"] + " - " + books[0]["author"] + " (" + str(books[0]["year"]) + ") " + "ISBN: " + books[0]["isbn"] + " 価格: " + str(books[0]["price"]) + "円")
print("2." + books[1]["title"] + " - " + books[1]["author"] + " (" + str(books[1]["year"]) + ") " + "ISBN: " + books[1]["isbn"] + " 価格: " + str(books[1]["price"]) + "円")
print("3." + books[2]["title"] + " - " + books[2]["author"] + " (" + str(books[2]["year"]) + ") " + "ISBN: " + books[2]["isbn"] + " 価格: " + str(books[2]["price"]) + "円")

説明：実行時引数で受け取ったjsonファイルを辞書型には変換し、bookの辞書全体を表示する。

実行結果：
@4723112 ➜ /workspaces/WE-Python (main) $ python book_manager.py "{ \"title\": \"Python入門\", \"author\": \"田中太郎\", \"year\": 2024, \"isbn\": \"978-4-123456-78-9\", \"price\": 2500 }"

[{'title': 'Java基礎', 'author': '佐藤花子', 'year': 2023, 'isbn': '978-4-987654-32-1', 'price': 2800}, {'title': 'Web開発', 'author': '山田次郎', 'year': 2023, 'isbn': '978-4-111111-11-1', 'price': 3200}, {'title': 'Python入門', 'author': '田中太郎', 'year': 2024, 'isbn': '978-4-123456-78-9', 'price': 2500}]

本データベース:
1.Java基礎 - 佐藤花子 (2023) ISBN: 978-4-987654-32-1 価格: 2800円
2.Web開発 - 山田次郎 (2023) ISBN: 978-4-111111-11-1 価格: 3200円
3.Python入門 - 田中太郎 (2024) ISBN: 978-4-123456-78-9 価格: 2500円
