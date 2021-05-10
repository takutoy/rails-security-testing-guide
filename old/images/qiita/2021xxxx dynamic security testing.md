# Ruby on Rails 製 Web アプリケーションのセキュリティテストガイド (動的テスト：DAST)

## これなに？

Ruby on Rails 製 Webアプリケーションのセキュリティテストをするためのガイドです。本ガイドは脆弱なRailsアプリである [RailsGoat](https://github.com/OWASP/railsgoat) を題材にセキュリティテストの手法を解説します。

本記事では稼働しているWebアプリケーションに対して疑似攻撃をすることで脆弱性を発見する手法である __動的アプリケーションセキュリティテスト(DAST)__ を扱います。

### 対象読者

Ruby on Rails でプロダクト開発している組織の**セキュリティチーム**を想定していますが、セキュリティに関心がある**開発者**や**テスター**にとっても役立つしれません。

前提知識・スキル

- 情報セキュリティに関する基本的な用語を知ってること
- 基本的なWebアプリケーションの脆弱性について知ってること
- Ruby on Rails のコードが読めること
- Linux のコマンドを叩けること

### 目次

1. 動的アプリケーションセキュリティテストの準備
2. アクセス制御をテストする
3. 静的テストで見つけた脆弱性を精査する
4. Active Scan と Fuzzing 
5. HTTP通信ログから問題を発見する

## 静的アプリケーションセキュリティテストの準備

静的アプリケーションセキュリティテストはソースコードをツールで解析したり、目視でレビューしたりすることにより脆弱性を発見します。

テストを始める前に、Rails アプリによくあるプログラミングミスを把握しておいたり、コードを読みやすい環境を整えておいたりしておくと効率よくテストを進められます。