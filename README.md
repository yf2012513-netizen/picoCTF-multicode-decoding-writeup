# picoCTF MultiCode General Skills Writeup  
多層エンコードを段階的に解除する問題の解法（日本語＋英語）

This repository contains my writeup for the picoCTF challenge  
**“MultiCode General Skills (Easy, 200 pts)”**, which involves decoding multiple layers of encoding  
(Base64 → Hex → ROT13 → URL).  
All commands were executed in a WSL (Ubuntu) environment.

本リポジトリは、picoCTF のチャレンジ  
**「MultiCode General Skills（Easy, 200 pts）」** の解法をまとめたものです。  
Base64 → Hex → ROT13 → URL といった複数のエンコードを順番に解除していきます。  
ここでは、WSL（Ubuntu）で実際に入力したコマンド履歴をそのまま掲載しています。

---

## 🔽 Challenge File Download  
チャレンジファイルのダウンロード

```bash
wget https://challenge-files.picoctf.net/c_plain_mesa/67ac0960ab56cd43a4566c1425e713ab6b422eec4f822b3c3e6c1dff07557524/message.txt
cat message.txt
