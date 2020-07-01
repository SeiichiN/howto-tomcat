# howto-tomcat
Install and management of Tomcat 9  
Tomcat9を単独でインストールする場合

## Tomcatのダウンロード
Tomcatのトップページ http://tomcat.apache.org/  
Tomcatのダウンロード https://tomcat.apache.org/download-90.cgi  

「Core」の「64-bit Windows zip」 をダウンロードする。

## Tomcatのインストール
ダウンロード・フォルダに「apache-tomcat-9.0.36-windows-x64.zip」がダウンロードされるので、
7-Zipで、「ここに解凍」。  
「apache-tomcat-9.0.36」フォルダができるので、そのフォルダを c:\ に移動する。

## 環境変数の登録
「スタート」を右クリック － 「システム」－ 「システム情報」 － 「システムの詳細設定」
ー 「環境変数」  
下の「システムの環境変数」に以下を確認あるいて登録する。  
```
「JAVA_HOME」... C:\Program Files\Java\jdk1.8.0_251         // Java8の場合  
「CATALINE_HOME」... C:\apache-tomcat-9.0.36  
「CLASSPATH」 ... C:\apache-tomcat-9.0.36\lib\jsp-api.jar  
                 C:\apache-tomcat-9.0.36\lib\servlet-api.jar
                 C:\apache-tomcat-9.0.36\lib               // これは不要
```

## Tomcatの起動
「C:\apache-tomcat-9.0.36\bin」フォルダの中の 「startup.bat」をダブルクリックで起動。
コマンドプロンプトの画面がでてきて、文字化けした文字列が表示される。  
「http://localhost:8080/」でTomcatの画面が表示される。  
画面をｘで閉じたら、終了できる。  

## Tomcatのサービスへの登録
「C:\apache-tomcat-9.0.36\bin」フォルダをコマンドプロンプトで開く。  
（アドレス欄に cmd と入力して Enter でＯＫ）  
`> service.bat install Tomcat9`  
と入力して Enter  
環境変数の状態を表示されて、サービスが登録されたことが表示される。  

サービスからの削除  
`> service.bat uninstall Tomcat9`

### サービスの確認
「スタート」を右クリック － 「コンピュータの管理」 － 「サービスとアプリケーション」の
副項目に「サービス」がある。  
クリックすると「サービス」の一覧が開く。  
「Apache Tomcat 9.0 Tomcat9」がある。  
「サービスの起動」をクリックすると、起動する。  

## ローカルの任意のフォルダをドキュメントルートに設定する
「C:\apache-tomcat-9.0.36\conf」フォルダの中に「Catalina」フォルダを作成し、さらに「localhost」フォルダを作成する。これで中に、ローカルの任意のフォルダをドキュメントルートに設定できる。  
たとえば、http://localhost:8080/example で、"C:\Users\user\Documents\example"のフォルダの中を見せたいときは、以下の内容でexample.xmlというファイルを作成する。  


```example.xml
<?xml version='1.0' encoding='utf-8'?>
<Context path="/example" docBase="C:\Users\user\Documents\example" />
```
---
# howto-tomcat with preiades
preiadesのフルセットをインストールしてある場合は、以下のようにする。

preiadesが「C:\preiades」にインストールされてあるとする。


