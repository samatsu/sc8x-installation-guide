========================================================
日本語環境のセットアップ
========================================================

.. contents:: このページのトピックス
   :local:

Sitecoreをクリーンインストールした直後の環境で、日本語環境をセットアップする方法を記載します。この手順を実施すると次の項目の言語がデフォルトで日本語になります。

* クライアントアプリケーションのデフォルトのUIの言語
* コンテンツ編集者が編集するデフォルトの言語バージョン

日本語化の設定
========================================================
ブラウザーを起動し、adminフォルダーにあるInstallLanguage.aspx にアクセスします。sc8u5というサイトでSitecoreの編集環境をセットアップしている場合は、``http://sc8u5/sitecore/admin/InstallLanguage.aspx`` になります。

ログイン画面が表示されたら admin ユーザーでログインします。

.. figure:: /images/sitecore/sc-setupja01.png

ログイン後、install a language が表示されます。

.. figure:: /images/sitecore/sc-setupja02.png

ドロップダウンリストから Japanese を選択します(キーボードで *japanese* とタイプすると簡単に選択できます)。ドロップダウンリストで選択した言語を編集用の言語として追加できます。さらに、*Run the website and the Sitecore UI in this language* にチェックをつけます。これにより、次の言語がデフォルトで日本語になります。

* コンテンツエディターなどのクライアントインタフェースのUIの言語
* コンテンツ編集者が編集する言語バージョン
* デフォルトのライブサイト(website)で表示する言語バージョン

**Install** ボタンをクリックして日本語を追加し、デフォルトの言語を日本語バージョンに変更します。


変更された内容の確認
========================================================
ブラウザーを起動している場合は、いったんブラウザーを閉じてから、ライブサイトにアクセスします。たとえば、sc8u5という名前でSitecoreをインストールしている場合は、``http://sc8u5/`` にアクセスします。そうすると、コンテンツが日本語で表示されていることを確認できます。これでライブサイトのコンテンツのデフォルトが日本語になっていることを確認できます。

.. figure:: /images/sitecore/sc-setupja05.png

編集環境にログインすると、ラウンチパッドが日本語で表示されます。これでUIがデフォルトで日本語になっていることを確認できます。

.. figure:: /images/sitecore/sc-setupja03.png

InstallLangauge.aspxのドロップダウンリストで選択した言語アイテムが */sitecore/system/languages* 配下に作成されていることを確認します。

.. figure:: /images/sitecore/sc-setupja04.png

.. tip:: 言語アイテムを作成することで、編集者はその言語バージョンのアイテムを作成できるようになります。

InstallLangauge.aspx で *Run the website and the Sitecore UI in this language* にチェックをつけたことにより変更された *Sitecore.DefaultLanguage.aspx* の中身も確認します。
*<Sitecore instllation folder> /Website/App_Config/Include/Sitecore.DefaultLanguage.config* の中身を確認すると、次のように変更されています。*ClientLanguage* の設定により、クライアントアプリケーションのデフォルトの編集言語が日本語になります。*contentLanguage* の設定により、デフォルトの変種言語が日本語になります。languageの設定により、デフォルトのライブサイト(website)の紺天狗の言語が日本語(ja-jp)になるようパッチファイルが変更されていることを確認できます。

.. code-block:: xml

    <configuration xmlns:patch="http://www.sitecore.net/xmlconfig/">
    <sitecore>
        <sites>
        <site name="website">
            <patch:attribute name="language">ja-JP</patch:attribute>
        </site>
        <site name="login">
            <patch:attribute name="language">ja-JP</patch:attribute>
        </site>
        <site name="shell">
            <patch:attribute name="contentLanguage">ja-JP</patch:attribute>
        </site>
        </sites>
        <settings>
        <setting name="ClientLanguage">
            <patch:attribute name="value">ja-JP</patch:attribute>
        </setting>
        </settings>
    </sitecore>
    </configuration>

これでSitecore環境のデフォルトの言語を日本語にする作業は完了です。