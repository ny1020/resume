
## やったこと

### 電子書籍を販売するWebアプリケーションの運用・改修

フロントエンド・バックエンド問わず、要件定義から設計、実装、テスト、運用まで一通り経験した。
以下に具体的な実績をまとめた。

- PostgreSQL RDS のバージョンアップ(9.6.11 -> 11.1)
- ローカル開発環境のHTTPS化
  - localhostをDNSに登録し、DNS認証で証明書を発行した。
  - 本番環境と合わせるために、本番環境で使っているロードバランサーの代わりとしてnginxを使ってプロキシサーバーを立てた。
- モバイル端末からローカル環境を見られる環境を構築
  - ngrokを使って実現した。
  - ngrokを使用するとポートフォワーディングのためのURLが発行されるので、対応するために環境変数でアプリケーションのURLを変更できるように設定を追加した。
  - ビジネスメンバーがモバイル環境でデバッグしたいという要望を叶えるために実装したので、ドキュメントを用意していつでもデバッグできるようにした。
- 外部から自社サイトのポイント(サイト内で使える通貨)を使用するAPIの実装
  - 2重消費や不正な利用が起きないよう、ポイントを使用するためのトークンを生成するAPIとポイントを使用するAPIの2つを用意した。
- APIのドキュメントを作成
  - バックエンドとフロントエンドを分離する動きがあるにも関わらず、APIのドキュメントが存在していなかったので、OpenAPIを用いて、ドキュメントを作成した。
  - それに伴って、committeeを利用してAPIのレスポンスをテストできるようにした。
- 外部APIを使用した決済機能の改修
  - 運営しているサービスからアカウントを削除したユーザーの決済情報を削除できる機能を追加した。
  - 決済代行会社が保持している会員情報を削除するAPIを呼び出すことで、上記の機能を実現できた。サービスからアカウントを削除するたびにAPIを呼び出すと、処理が重くなってしまう恐れがあったので、その問題を解消するために、削除対象の情報を保存するDBを用意して、そのDBのデータを対象に先程追加した処理を走らせるバッチを実装した。
- jestの導入
  - フロントエンドのテストがまったくなかったので導入した。
  - ひとまずスナップショットテストは作ったものの、単体テスト、ユニットテストは網羅できていない。
  - モブプロの時間を設けて、メンバーに使い方を共有した。
  
### 開発以外の実績
開発業務だけではなく、スクラム改善、エンジニア組織改善、採用業務などを主体的に実践してきたので以下にまとめる。

### スクラム改善
自分自身がスクラムマスターを担当する以前は、プロダクトバックログのメンテナンス不備や、スプリントの概念も曖昧になっており、スクラムの効果を発揮できているとは言い難い状態だった。
上記のことから、ジュニアなメンバーの開発が滞っていることが多く、チームとして最善のアウトプットが出せていないと考え、スクラムの改善、浸透に尽力した。
開発チームにスクラムの解説をすることはもちろん、ビジネスメンバーへ理解してもらう努力を行うことで、プロジェクト全体にスクラムの考えを浸透させることができた。その結果、スクラムをしっかり行うことができ、開発チームとしてのパフォーマンスが向上した。

### エンジニア組織改善
業務に直接影響はしないが、どうすればよりよいエンジニア組織にできるかを考え行動した。
具体的には、エンジニアランチ、分報、輪読会などを新たに開催した。
上記のいずれも、実際に実行する前にマネージャー層を巻き込むことを意識している。
輪読会については、開催のときに読む対象の章を担当者が交代でまとめてくるようになっていたが、担当者が忙しくてまとめられないようなときでも開催できるよう、常に自分でまとめることを欠かさなかった。

### 採用業務
自ら希望してエンジニア採用にも携わった。
採用したい人材像の絞り込みや、一次面接を担当した。
