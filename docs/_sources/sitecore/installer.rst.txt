.. Sitecore のインストーラーを使用したインストール手順の記載

.. リンク定義

.. _Developer Portal: https://dev.sitecore.net/

========================================================
インストーラーを使ったSitecoreのインストール
========================================================

.. contents:: このページのトピックス
   :local:

このページでは、Sitecore 8.2 をインストーラーを使用してインストールする方法を記載します。
SIMを使ったインストール方法に関しては :doc:`sim` をご参照ください。

Sitecore のダウンロード
========================================================

`Developer Portal`_ からSitecoreの本体および、オフィシャルにサポートされるアドオンモジュールをダウンロードできます。`Developer Portal`_ のトップにあるリンクから最新バージョンをダウンロードできます。 `このページ <https://dev.sitecore.net/Downloads/Sitecore_Experience_Platform.aspx>`_ から、自分がインストールしたい任意のSitecoreのバージョンのダウンロードページに移動することができます。

Sitecoreのダウンロードページに移動したら、 *Download options* セクションの、 *Sitecore web application installer* をクリックしてダウンロードします。このドキュメントでは、下図のように Sitecore 8.2 update-5をインストールします。 Sitecore 8のほかのバージョンでもインストール手順に大きな違いはありません。

.. figure:: /images/sitecore/sc8install01.png

.. note:: Sitecore本体およびアドオンモジュールをダウンロードするには、Sitecoreの開発者向けの認定試験に合格している必要があります。

ダウンロードした zip ファイルを右クリック > プロパティ　をクリックしてプロパティーダイアログを表示します。**ブロックの解除** をクリックしてOKをクリックしてください。

Sitecore のインストール
========================================================
zip ファイルを展開して、インストーラーをダブルクリックします。 Sitecore 8.2 update-5の場合のファイル名は、``Sitecore 8.2 rev. 170728.exe`` です。

.. figure:: /images/sitecore/sc8install02.png

次の図のようなインストーラーが起動するので、**次へ**　をクリックします。

.. figure:: /images/sitecore/sc8install03.png

使用許諾画面で、 **完全** を選択して、**次へ** をクリック。

インストールの種類の選択画面で **完全** を選択して **次へ** をクリック。 

.. figure:: /images/sitecore/sc8install10.png

インスタンス名の画面で、インスタンス名を入力して次へをクリック。今回は sc8u5 という名前でインストールを実施する前提とします。

.. figure:: /images/sitecore/sc8install04.png

ライセンス ファイル 画面で、ライセンスファイルを選択して、 **次へ** をクリックします。

データベースサーバーの画面で、SQL Serverへの接続情報を入力して次へをクリックします。SQL　Server に接続するユーザーは sa などの管理者ユーザーか、sys_adminロールのユーザーを指定してください。

.. figure:: /images/sitecore/sc8install05.png

インストール先のフォルダー画面はデフォルトのまま、**次へ** をクリックします。

.. figure:: /images/sitecore/sc8install06.png

.. note:: デフォルトでは C:\inetpub\wwwroot 配下にSitecoreインスタンス名のフォルダーを作成してその配下に必要なファイルがインストールされます。

インストール内容のサマリー画面が表示されたら **インストール** をクリックします。

.. figure:: /images/sitecore/sc8install07.png

しばらくするとインストールが完了して、次の図が表示されます。完了をクリックして続いて、SitecoreクライアントインタフェースのUIおよび編集言語をデフォルトで日本語にしたい場合は、**Sitecore を起動します** を選択して、画面を閉じます。

.. figure:: /images/sitecore/sc8install08.png

.. seealso:: 日本語をデフォルトに設定する方法に関しては :doc:`setup-japanese` を参照して下さい。

Sitecore クライアントインタフェースにログイン
========================================================
インストールが終わったら、編集環境にログインして動作確認をします。ブラウザーを起動して、サイトコアをインストールしたサイト名を使用してログイン画面にアクセスします。このドキュメントでは sc8u5 というサイト名を使ってインストールしていますので、 ``http://sc8u5/sitecore`` になります。

.. figure:: /images/sitecore/sc8install09.png

デフォルトの管理者アカウント admin/b でログインできたら完了です。

.. note:: 本番で使う環境の場合はパスワードはすみやかに変更するか、別の管理者ユーザーを作成してadminユーザーを無効化します。