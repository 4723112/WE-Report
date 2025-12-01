# 第9回 Webエンジニアリング演習 レポート
## 学籍番号（名前は書かなくてよい）
4723112
## frontend/calculator.tsのプログラム
// 名前付きエクスポート
export function add(a: number, b: number): number {
    return a + b;
}

export function multiply(a: number, b: number): number {
    return a * b;
}

// デフォルトエクスポート
export default class Calculator {
    public static add(a: number, b: number): number {
        return a + b;
    }
}
## 動作確認結果
@4723112 ➜ /workspaces/WE-TypeScript/frontend (main) $ node main.js
5 + 3 = 8
5 * 3 = 15