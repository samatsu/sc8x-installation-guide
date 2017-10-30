.. SIMを使用したインストール手順の記載

.. リンク定義

.. _Developer Portal: https://dev.sitecore.net/

========================================================
SIMを使ったSitecoreのインストール
========================================================

.. contents:: このページのトピックス
   :local:

このページでは、SIM(Sitecore Instance Manager)を使った、Sitecoreのインストール方法をご紹介します。  
インストーラーを使用した方法に関しては、 :doc:`installer` をご参照ください。

SIMのダウンロードとインストール
========================================================
SIMはMarket Place からインストールページにアクセスできます。`Sitecore Instance Manager <https://marketplace.sitecore.net/Modules/S/Sitecore_Instance_Manager.aspx?sc_lang=en>`__ にアクセスします。

**DOWNLOAD** ボタンをクリックします。使用許諾の画面が表示されたら **I AGREE** をクリックします。

.. figure:: /images/sitecore/sc-sim01.png

ダイアログの中の **Link** をクリックします。

.. figure:: /images/sitecore/sc-sim02.png

SIMをインストールするページが表示されます。**Install and Launch** をクリックして、インストーラーうダウンロードします。

.. figure:: /images/sitecore/sc-sim03.png

.. note:: SIMはClick Once アプリケーションです

ダウンロードが完了すると、自動的に構成ウィザードが始まります。

SIMのコンフィグレーション
========================================================
ダウンロードが完了すると、Configuration Wizard が開始されます。ここで、初期設定を行います。ここで設定した内容はあとから変更できます。**Next** をクリックします。

.. figure:: /images/sitecore/sc-sim04.png

ライセンスアグリーメント画面が表示されたら **Next** をクリックして、インストーラーうダウンロードします。

Instances Root Folderという画面が表示されたら、Sitecore のインストールフォルダーを指定します。デフォルトでは、 ``C:\inetpub\wwwroot`` です。 **Next** をクリックします。

.. figure:: /images/sitecore/sc-sim06.png

次に、 Local Repository and Sitecore License という画面が表示されます。ここで、Sitecore の zip形式のインストールファイルを配置するリポジトリフォルダーとインストール時に使用するライセンスファイルを指定します。*LOCLA REPOSITORY* の [...] ボタンをクリックして、Sitecoreインストール用のzipファイルを保存するフォルダーを指定します。 *SITECORE LICENSE* の [...] ボタンをクリックして、使用するライセンスファイルを選択します。**次へ** をクリックします。

.. figure:: /images/sitecore/sc-sim07.png

SQL Serverへの接続文字列の設定をします。 sa ユーザー化 sys_admin ロールのユーザーを指定して、SQL Server に接続を行うように構成します。**次へ** をクリックします。

.. figure:: /images/sitecore/sc-sim08.png

File System Permissions 画面が表示されます。 **Grant** ボタンをクリックして、 Network Service ユーザーに Sitecoreをインストールするフォルダー配下に適切な権限を付与します。この例では、デフォルトの ``C:\inetpub\wwwrooot`` が対象になります。

.. figure:: /images/sitecore/sc-sim09.png

権限の割り当てに成功すると、 次のダイアログが表示されます。

.. figure:: /images/sitecore/sc-sim10.png

.. warning:: 権限の割り当てに失敗する場合は、 SQL Server のサービスアカウントが、 Network Service で実行されているか確認して下さい。

Grant ボタンの処理に成功したら、 **Next** をクリックします。

Completed 画面が表示されたら **Finish** ボタンをクリックして、構成ウィザードを終了します。

.. figure:: /images/sitecore/sc-sim11.png

Sitecoreのインストール
========================================================
SIMの構成が終わったら、インストールをおこないます。まず最初に SIMでインストール時に使用するSitecore の zipファイルを取得します。
`Developer Portal <https://dev.sitecore.net/Downloads/Sitecore_Experience_Platform.aspx>`__ から利用するSitecore 8.x の zip 形式のファイルをダウンロードします。

今回は、 `Sitecore 8.2 update 5 のページ <https://dev.sitecore.net/Downloads/Sitecore_Experience_Platform/82/Sitecore_Experience_Platform_82_Update5.aspx>`__ からファイルをダウンロードします。

ページ内の、*Download options* セクションから、 `Zip archive of the Sitecore site root folder` をクリックして zip ファイルをダウンロードします。 

.. figure:: /images/sitecore/sc-sim12.png

.. note:: Sitecore の本体及びモジュールをダウンロードするには、Sitecoreの開発者向けの試験に合格している必要があります。

ダウンロードしたファイルを SIMのリポジトリフォルダーに配置します。今回は、SIMの構成時に、`C:\SIM\Repos` をリポジトリフォルダーとして設定した前提で進めます。

.. figure:: /images/sitecore/sc-sim13.png

SIMを起動します。`Win + Q` で検索チャームを起動して `SIM` と入力すれば見つかるはずです。ホームタブの **Install Instance** をクリックします。
 
.. figure:: /images/sitecore/sc-sim14.png

Installing new instance ダイアログが起動します。 ドロップダウンリストで、インストールするSitecoreのバージョンを選択できます。ここで選べるバージョンは、 SIMのリポジトリフォルダーに配置した zip ファイルにより変わります。

Site Name などに、パラメーターを設定したら、 **Next** をクリックします。

.. figure:: /images/sitecore/sc-sim15.png

残りの部分は、デフォルトのまま進めることができます。

Instance details という画面が表示されたら **Next** をクリックします。

Modules list という画面が表示されたら **Next** をクリックします。

Custom Packages という画面が表示されたら **Next** をクリックします。

インストールするモジュールとパッケージの順番を変更する画面が表示されたら **Next** をクリックします。手順通り進めた場合は、モジュールおよびパッケージはインストールに含まれないので ``No modules or pakcages selected`` が薄く表示されているはずです。 

インストールが完了すると、Complted 画面が表示されます。 Sitecore の編集画面にアクセスできることを確認するために **Open in Browwser(Sitecore Client)** にチェックしてから **Finish** ボタンをクリックします。使用許諾の画面が表示されたら

.. figure:: /images/sitecore/sc-sim16.png

ブラウザーが起動して、ラウンチパッドへのログイン画面が表示されたらインストール成功です。

.. figure:: /images/sitecore/sc-sim17.png

.. note:: インストール完了画面で、チェックボックスを選択せずに閉じた場合は、ブラウザーを起動して、インストールしたサイトにアクセスしてください。今回の例では `http://v82u5/sitecore` です。

日本語環境をセットアップする場合は :doc:`setup-japanese` を参照してください。