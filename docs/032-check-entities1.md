# 3. 探索結果の確認

## Entities の確認１

続いて、ASMが発見した Entities (= 外部露出している IT 資産）を確認します。

１．画面上部の **Entities** タブをクリックすると、下記画面が表示されます。

![image-20240418111539824](images/image-20240418111539824.png)



２．左ペインのFiltersを選択することで、表示する Entities をフィルタすることができます。試しに**DNSRecord** を選択して、DNSレコードのみを表示します。デモ環境のドメイン(acme.com)に関連するDNSレコードが確認できます。

![image-20240418111750387](images/image-20240418111750387.png)



３．次に、デモ組織に関連する Web サイトを確認してみます。左ペインのFiltersから、<u>DNSRecord の選択を解除し</u>、**URI** を選択します。デモ組織に関連する Web サイトのURLが500件程度表示されます。

![image-20240418111917603](images/image-20240418111917603.png)



!!! warning
    Filters で新しく条件を設定する時は、すでに選択している Filter をクリックし解除するのを忘れないでください。



４．Webサイトの数が多いのでテーブルビューに表示を変更します。画面右上の **Switch To Table View** をクリックすると表示が切り替わり、名前(Name)のほかに Web ページのタイトル(Title)や HTTPレスポンスのコード(Code)なども確認できます。また、**Name** をクリックすることでソートができ、ドメインベースのURLをリスト上部に表示させることもできます。

![image-20240418112109476](images/image-20240418112109476.png)



５．ここから、先ほどダッシュボードで確認した「ヨーロッパのIT資産」を確認していきます。<u>URIの選択を解除し</u>、画面右側の `Search Summary` を確認します。このサマリーペインでは Entityの種別や、リスク重大度、位置情報などの統計情報が確認できます。`LOCATION`の **Show More** をクリックし、**Germany** をクリックします。

![image-20240418112220551](images/image-20240418112220551.png)



６．７つの Entity が表示されました。この IT 資産がドイツに存在しているようです。root.acme.com というWebサイトがあるので、**hxxps://root.acme.com:443**  の Entity をクリックして詳細を確認します。

![image-20240418112304728](images/image-20240418112304728.png)



!!! note
    WebサイトのEntity(URL)はドメインベースのURLから確認すると効率的です。これは、ドメインベースURLがサイトの内容を確認しやすい一方、IPアドレスベースのURLはCDN等によって動的に変化したもので、調査するとドメインベースURLと同一サイトであるケースが多いためです。



８．`Network Name` を確認すると ドイツの企業にホスティングされており、 Acme-profileというタイトル(Title)のサイトで、HTTPレスポンスコード(Code)200を返していることから現在稼働しているようです。

![image-20240418112517858](images/image-20240418112517858.png)



９．また、画面右下のScreenShotをクリックすると、このWebサイトのページの画像も確認できます。

![image-20240418112555675](images/image-20240418112555675.png)


１０．Webサーバのコンテンツの情報に加えて、その他の情報も確認していきます。**Technologies** タブを選択すると、このWebサイトが利用しているソフトウェアなどがcpe形式で表示されます。このサイトでは apacheとbootstrapなどが使われているようです。

![image-20240418112642010](images/image-20240418112642010.png)


１１.  また**Checks** タブを選択すると、この Entity に対して実施したセキュリティチェックも確認できます。リンク切れのチェックといった簡単なものから、Heartbleed の脆弱性チェックまで行われています。

![image-20240418112656345](images/image-20240418112656345.png)

!!! info
    このセキュリティチェックで問題があった場合は Issue が作成されます。Issue が作成されなかった場合は、チェックの結果問題がなかったことを意味します。



１２. このサイトは把握しているサイトで、（リンク切れはあるものの）特にセキュリティ上のリスクはなので問題ないと判断しました。
    
    ![image-20240418113008622](images/image-20240418113008622.png)
    
    

  [次のステップ](../033-check-entities2) で、Webサイト以外の Entitlesについて、もう少し確認していきます。
