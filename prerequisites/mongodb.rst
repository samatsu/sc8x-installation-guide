================================================================
MongoDBのセットアップ
================================================================
.. contents:: このページのトピックス
   :local:

ダウンロード
================================================================

MongoDBのインストーラーMongoDBのサイト `<https://www.mongodb.com/download-center#community>`__ からダウンロードできます。ダウンロードページで、 Community Server タブを選択して、 内側のWindows タブが選択されている状態で、 **All Version Binaries** をクリックします。

.. figure:: /images/prerequisites/pre-mongo01.png

今回は、一覧のページから、 ３.2.1の最新バージョンの ``mongodb-win32-x86_64-2008plus-ssl-3.2.17-signed.msi`` をクリックしてダウンロードしました。

.. figure:: /images/prerequisites/pre-mongo02.png

ダウロードした msi を右クリックして プロパティをクリックします。プロパティダイアログで **ブロックの解除** をクリックして **適用ボタン** をクリックします。

.. note:: Sitecoreのバージョンと互換性のあるMongoDBのバージョンは `MongoDB compatibility table <https://kb.sitecore.net/articles/633863>`__ から確認できます。


インストール
================================================================
今回は、 ``C:\mondogb\`` 配下にインストールします。コマンドプロンプトを起動して、次のコマンドを実行するか、エクスプローラーを使用して、mongodbフォルダーを作成します。

.. code-block:: bat

    cd C:\
    mkdir mongodb

次に、コマンドプロンプトを起動して、msiファイルをダウンロードしたフォルダーに移動します。

.. code-block:: bat

    msiexec.exe /q /i mongodb-win32-x86_64-2008plus-ssl-3.2.17-signed.msi  INSTALLLOCATION="C:\mongodb" ADDLOCAL="all"

インストールが成功すると、 mongodb フォルダーにファイルが作成されるはずです。

.. figure:: /images/prerequisites/pre-mongo03.png

今回は簡単なインストール方法をご紹介しましたが、詳細については下記ページも参照下さい。

    | Install MongoDB on Windows 
    | `<http://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows/>`_


Windows サービスとして登録
================================================================
MongoDB がWindowsのサービスとして動作するようにします。今回の例では、MongoDBのデータとログを ``C:\data`` フォルダー配下に作成するように構成します。コマンドプロンプトを起動して次のコマンドを実行するか、エクスプローラーで手動で ``data`` フォルダーとその配下に、``db``, ``log`` フォルダーを作成します。

.. code-block:: bat

    mkdir C:\data
    cd C:\data
    mkdir db
    mkdir log

次に、コンフィグファイルを準備します。 service.conf というファイルを次の内容で作成し、 ``C:\data`` フォルダーに保存します。

.. code-block:: sh

    # ログの出力先とポート、DBフォルダーのパスを指定 
    systemLog :  
    destination : "file" 
    path : "C:\\data\\log\\mongodb.log" 

    net: 
    port : 27017
    storage : 
    dbPath : "C:\\data\\db" 


コマンドプロンプトを起動し、MongoDBのbinフォルダーに移動します。今回の場合は ``C:\mongodb\bin`` です。

次のコマンドを実行して、 Windows サービスとして起動するようにします。

.. code-block:: bat

    mongod.exe --config C:\data\service.conf --install 

サービスを起動する場合は、次のコマンドを実行します

.. code-block:: bat

  net start MongoDB

.. figure:: /images/prerequisites/pre-mongo04.png

.. note:: 自動的にMongoDBは起動するようになっているので、次回以降 MongoDB を手動で開始する必要はありません。

コマンドプロンプト上で、 ``service.msc`` と入力すると サービス スナップイン画面を表示できます。こちらから、 MongoDB サービスが登録されていることを確認できます。

.. figure:: /images/prerequisites/pre-mongo05.png

サービスとして適切に起動していると、ログファイルが出力されていることも確認できるはずです。今回の例では、``C:\data\log`` にファイルが作成されます。

.. figure:: /images/prerequisites/pre-mongo06.png

.. note:: MongoDB のデータベースをGUIのツールで確認したい場合は、Robo 3T(Robomongo) などを利用できます。

