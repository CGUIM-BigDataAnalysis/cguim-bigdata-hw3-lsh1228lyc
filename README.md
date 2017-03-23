長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
##install.packages("rvest")
library(rvest) 
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
for (n in 2001:2005){
PttTechJob<-paste0("https://www.ptt.cc/bbs/Tech_Job/index",n,".html")
PttContent<-read_html(PttTechJob)
post_Title <- PttContent %>% html_nodes(".title") %>% html_text()
post_PushNum<-PttContent %>% html_nodes(".nrec") %>% html_text()
post_Author<-PttContent %>% html_nodes(".author") %>% html_text()


if(n==2001){
  PttTechJob_posts1 <- data.frame(Title = post_Title,PushNum = post_PushNum,Author=post_Author)
}else if(n==2002){
  PttTechJob_posts2 <- data.frame(Title = post_Title,PushNum = post_PushNum,Author=post_Author)
}else if(n==2003){
  PttTechJob_posts3 <- data.frame(Title = post_Title,PushNum = post_PushNum,Author=post_Author)
}else if(n==2004){
  PttTechJob_posts4 <- data.frame(Title = post_Title,PushNum = post_PushNum,Author=post_Author)
}else if(n==2005){
  PttTechJob_posts5 <- data.frame(Title = post_Title,PushNum = post_PushNum,Author=post_Author)
   PttTechJob_posts <- rbind(PttTechJob_posts1,PttTechJob_posts2,PttTechJob_posts3,PttTechJob_posts4,PttTechJob_posts5)
}
}
```

爬蟲結果呈現
------------

``` r
knitr::kable(
    PttTechJob_posts[1:100,c("Title","PushNum","Author")])
```

| Title                                                 | PushNum | Author       |
|:------------------------------------------------------|:--------|:-------------|
| \[請益\] 穩懋蝕刻薄膜工程師                           | 10      | pp700124     |
| \[請益〕RMA助理工程師-美國 薪資                       |         | hashbrown    |
| \[請益\] offer選擇(外商DXXX / 群暉)                   | 8       | tallBuilding |
| \[請益\] 兆利科技CAE工程師                            | 13      | m7773988     |
| \[請益\] 大選後 勞工權益會更加受到照顧嗎              | 3       | jo5566       |
| \[心得\] 新鮮人面試 景碩/亞太優勢/新泰/美光           | 10      | rbrbrb       |
| \[請益\] 南科弓銓企業                                 | 2       | cyhoza       |
| \[討論\] 台中 鴻海 作業員分紅40萬?                    | 24      | Qoofate      |
| \[請益\] 想請問最近U公司有在徵人嗎?(非研替)           | 15      | ukiller      |
| \[討論\] 為何LED在台灣不會倒                          | 7       | mcm0120      |
| \[請益\] 高科磁技                                     | 4       | bla790395    |
| Re: \[請益\] 年後想換跑道，前景和薪水?                | 8       | tde          |
| \[請益\] 台灣應材約聘公司差異？                       | 2       | jimmyrex     |
| \[徵才\] 電動車環台Party隨行工程師                    | 1       | rafael789    |
| \[徵才\] 台大李致毅實驗室誠徵研究助理/工程師1名       | 10      | e0204558     |
| \[討論\] 關於全國公證檢驗這家公司                     | 4       | jarvispeng   |
| \[請益\] 台灣半導體研發製程工程師                     | 1       | bru          |
| Re: \[討論\] 選後 可以轉職 國防及生技產業了嗎？？     | 4       | piggg        |
| \[請益\] 研替問題請益                                 | 1       | swift2       |
| Re: \[討論\] 為何LED在台灣不會倒                      | 13      | m971f8012    |
| Re: \[請益\] 想去SpaceX工作需要加強哪方面能力?        | 15      | mounan       |
| \[新聞\] 無薪假人數大減 本期少3576人                  | 4       | wyskagirl    |
| \[討論\] 關於FAE工程師之技能?                         | 12      | ken258321    |
| \[請益\] 力億企業                                     |         | poiipkimo    |
| \[新聞\] 培養科技接班人 工研院高階主管班夯            |         | lvprada      |
| \[請益\] 年末到職或繼續找                             | 2       | kentinglover |
| \[請益\] 想請問南科的外商公司                         | 7       | superlover   |
| \[面試\] 中石化頭份 筆試                              | 1       | shuan0831    |
| \[請益\] 網通研替offer (居易/達創)                    | 5       | yorkeram     |
| \[請益\] 聯電和鉅晶設備                               | 3       | Apon777      |
| \[請益\] A公司與B公司抉擇                             | 3       | remix8145    |
| \[討論\]現在竹科塞到爆                                | 53      | murray5566   |
| \[討論\] 穎台科技                                     | 4       | q521q522     |
| \[徵才\] 中研院陳文村實驗室誠徵研究助理及博士後       |         | zerocaster   |
| \[討論\] 有沒有GG要開始夜班變6天的八卦?               | 14      | kay1561      |
| \[徵才\] 台大李致毅實驗室誠徵藍芽系統開發工程師       | 2       | e0204558     |
| \[徵才\] KitCut徵Sr. Software Developer               |         | aloha2       |
| \[請益\] GG 菜鳥中科 JOS 請益!!                       | 16      | petergod     |
| \[請益\] 轉往中科台G工作的家庭規劃                    | 45      | LesMiz       |
| \[新聞\] 年終6個月 王文淵：不滿意就過份了             | 28      | f204137      |
| \[新聞\] 台積電發威！外媒估：蘋果 A10、A11 處理       |         | FK56         |
| \[請益\] 鉅城資訊 設備工程師                          |         | vatfg2005    |
| Re: \[新聞\] 年終6個月 王文淵：不滿意就過份了         | 26      | jeromeshih   |
| \[新聞\] 加班費哪去？北市公布違反勞基法名單           | 39      | david810205  |
| \[討論\] 有關捷普綠點                                 | 1       | lude71       |
| \[新聞\] 小米聯發科分手？小米全系產品採用高通晶片     | 56      | wahaha23     |
| \[徵才\] 聯合線上udn.com 網頁設計師                   |         | opachicken   |
| 請協助刪除                                            | 1       | xubb72       |
| \[請益\] 湖口工業區的弘潔科技                         | 2       | f860260      |
| \[新聞\] 尾牙典範！滿1年拿iPad 10年有勞力士           | 13      | lvprada      |
| \[請益\] 新日光研替選擇                               | 6       | readyset     |
| \[面試\] 台GG新竹面試OP                               | 8       | midnight0611 |
| \[請益\] offer請益(南茂 群創 艾克爾)                  | 8       | john80325    |
| \[請益\] offer選擇 (威盛/致茂)                        | 6       | luke71631    |
| \[請益\] 資工學士的起薪                               | 11      | sam1011      |
| \[請益\] 研替offer選擇請益                            | 1       | yangchenyue  |
| \[請益\] 該不該透露目前公司                           | 18      | BulletPeanut |
| \[請益\] 桃園楊梅的耐落                               | 18      | engineerr    |
| \[新聞\] 台積登陸案 農曆年前可望過關                  | 2       | DickMartin   |
| \[請益\]請問"研華"的"產品應用工程師"這職位~           | 13      | rick030215   |
| Re: \[新聞\] 韓政府今年擬實現無人機配送快遞，為自     |         | nihaotw      |
| \[新聞\] 聯發科要市場又要做高端 魅族回應：做夢        | 31      | double21     |
| \[討論\] 出國受訓                                     | 12      | BLF          |
| \[討論\] 尾牙抽獎資格需年資滿一年合理嗎??             |         | jordanaa     |
| \[請益\] 億光（智權）                                 | 4       | lazyalu      |
| \[請益\] 有關智成電子                                 | 5       | chaobin0930  |
| \[請益\] 東雅電子面試請益                             | 2       | aabbkk       |
| \[討論\] bios工程師的薪水                             | 13      | jordan0740   |
| \[請益\] 業務拓展供應商的激勵制度                     | 2       | Taoder       |
| \[討論\] 某面板廠年終開獎?                            | 41      | z888         |
| \[請益\] 研替offer請益 ASUS, QNAP                     | 6       | peoplewc     |
| 某板廠強迫員工買麵包                                  | 32      | Lbj2266      |
| \[請益\] 機械式鍵盤代工                               | 5       | jojisan      |
| \[新聞\] 帶薪休假無上限 遊戲橘子好福利                | 2       | lvprada      |
| \[請益\] 桃園平鎮 健鼎 研發工程師                     | 1       | FATYAHE      |
| \[請益\] 聯電 or 美光                                 | 7       | ch1473       |
| \[請益\] 國立科大化材系未來方向                       | 22      | qazasd118    |
| \[徵才\] 徵C\#\_WebForm工程師                         |         | sakura725    |
| Re: \[請益\] 有關智成電子                             | 1       | taiger1986   |
| \[討論\] 親戚公司vs台積電offer                        | 25      | hsueh        |
| \[請益\] 研替上了該不該去？                           | 28      | jeff811121   |
| \[請益\] 該誠實說現在在當警衛嗎？                     | 30      | spiderman134 |
| \[心得\] (上)研替面試心得 旺宏/旭德/群創              | 3       | curtis327    |
| Re: \[討論\] 親戚公司vs台積電offer                    | 5       | xiah41       |
| \[請益\] 離職前該注意什麼                             | 16      | accommodate  |
| \[情報\] 1/26創業講座                                 |         | dio13        |
| Re: \[討論\] 親戚公司vs台積電offer                    | 13      | yamakazi     |
| Re: \[請益\] 離職前該注意什麼                         | 5       | hidog        |
| Re: \[新聞\] 科技人悲歌！「為什麼八點之後叫正常？」   | 8       | CGDGAD       |
| \[請益\] 竹科附近租屋                                 | 4       | zxciop       |
| \[請益\] 土城桓達科技                                 | 1       | title0308    |
| \[心得\] (中)研替面試心得 緯創/欣興/矽品/超豐         | 7       | curtis327    |
| Re: \[新聞\] 科技人悲歌！「為什麼八點之後叫正常？」   | 26      | zsyian       |
| \[請益\] 聽說欣興準備裁員了?                          | 28      | number89757  |
| \[請益\] 艾克爾湖口廠問題                             | 15      | ryan800130   |
| \[請益\] 關於台南全一電子?                            | 4       | BobX         |
| \[新聞\] 【寫個慘字】電子大廠員工生日禮金變麵包兌換券 | 7       | bearian      |
| Re: \[請益\] 機械式鍵盤代工                           | 3       | hidog        |
| \[新聞\] 失業勞工上課有好康？每月給你12K              |         | wyskagirl    |
| \[請益\] 對未來感到迷茫                               | 35      | Nunewinterer |

解釋爬蟲結果
------------

``` r
str(PttTechJob_posts)
```

    ## 'data.frame':    100 obs. of  3 variables:
    ##  $ Title  : Factor w/ 98 levels "\n\t\t\t\n\t\t\t\t[心得] 新鮮人面試 景碩/亞太優勢/新泰/美光\n\t\t\t\n\t\t\t",..: 16 17 7 11 8 1 12 2 15 3 ...
    ##  $ PushNum: Factor w/ 31 levels "","1","10","13",..: 3 1 11 4 8 3 6 7 5 10 ...
    ##  $ Author : Factor w/ 94 levels "bla790395","bru",..: 13 5 18 9 8 16 3 14 20 11 ...

可透過str(PttTechJob)的結果中「100 obs. of 3 variables」可得知總共爬出100篇文章之標題。

``` r
table(PttTechJob_posts$Author)
```

    ## 
    ##    bla790395          bru       cyhoza     e0204558    hashbrown 
    ##            1            1            1            2            1 
    ##   jarvispeng     jimmyrex       jo5566     m7773988    m971f8012 
    ##            1            1            1            1            1 
    ##      mcm0120        piggg     pp700124      Qoofate    rafael789 
    ##            1            1            1            1            1 
    ##       rbrbrb       swift2 tallBuilding          tde      ukiller 
    ##            1            1            1            1            1 
    ##       aloha2      Apon777      f204137      kay1561    ken258321 
    ##            1            1            1            1            1 
    ## kentinglover       LesMiz      lvprada       mounan   murray5566 
    ##            1            1            3            1            1 
    ##     petergod    poiipkimo     q521q522    remix8145    shuan0831 
    ##            1            1            1            1            1 
    ##   superlover    wyskagirl     yorkeram   zerocaster BulletPeanut 
    ##            1            2            1            1            1 
    ##  david810205   DickMartin    engineerr      f860260         FK56 
    ##            1            1            1            1            1 
    ##   jeromeshih    john80325       lude71    luke71631 midnight0611 
    ##            1            1            1            1            1 
    ##   opachicken     readyset   rick030215      sam1011    vatfg2005 
    ##            1            1            1            1            1 
    ##     wahaha23       xubb72  yangchenyue       aabbkk          BLF 
    ##            1            1            1            1            1 
    ##       ch1473  chaobin0930     double21      FATYAHE        hsueh 
    ##            1            1            1            1            1 
    ##      jojisan   jordan0740     jordanaa      lazyalu      Lbj2266 
    ##            1            1            1            1            1 
    ##      nihaotw     peoplewc    qazasd118    sakura725   taiger1986 
    ##            1            1            1            1            1 
    ##       Taoder         z888  accommodate      bearian         BobX 
    ##            1            1            1            1            1 
    ##       CGDGAD    curtis327        dio13        hidog   jeff811121 
    ##            1            2            1            2            1 
    ##  number89757 Nunewinterer   ryan800130 spiderman134    title0308 
    ##            1            1            1            1            1 
    ##       xiah41     yamakazi       zsyian       zxciop 
    ##            1            1            1            1

可透過table(PttTechJob\_posts$Author)的結果中可看出每個作者的文章數，其中「lvprada」為三篇，是本爬蟲結果中最多者。

從爬蟲網頁後這一百個標題中，可以看出有七成是【請益】，可以看出科技業的人們喜歡在板上尋求公司的資訊，尋求到最好的待遇，而剩下的三成中，可分成三類：【討論】、【徵才】、【新聞】，讓板上使用者可以吸收一些新知及即時訊息！
