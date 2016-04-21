# 人臉情緒播歌 POC

### Demo 簡介
2016 四月微軟在台北舉辦了一項叫做 DevDays Asia 2016 的活動： https://www.microsoft.com/taiwan/events/devdays/agenda.htm
介紹了些 2015 陸續放出、跟 2016 Build conf. 提到的新技術，主要是 Azure Machine Learning, Microsoft Cognitive Services, 等等。
並且附帶舉辦了 Hackathon 活動，鼓勵參加者使用這些新技術做些新功能。

由於我(patrick)不確定是否 kkbox 產品適合參與這種 Hackathon 活動，工作上也沒有那麼多時間。<br>
所以昨天演講結束後就沒參加 Hackathon, 自己玩了 Face API, 由於花的時間還不多，這份 demo 目前還很粗糙。<br>
這個 demo 它做的事情是：「依照用戶目前臉部的情緒，播放一首 kkbox 歌曲給用戶」。

它的工作原理是，「讀取一張照片」，呼叫 microsoft Face API 來「判斷這張照片的情緒」，然後「要 kkbox 播放一首符合目前情緒的歌曲」。
目前 Face API example 定義的 emotions 有這八種：Anger Contempt Disgust Fear Happiness Neutral Sadness Surprise ,
現在我只有對其中三種  Anger Happiness Sadness 做判斷，利用 Custom URL Scheme `kkbox://` 開啟 firefox, 要 kkbox 播放「許如芸 生氣」、「Happy Birthday	寶兒 (BoA)」、「陳珊妮 如同悲傷被下載了兩次」 這三首歌曲。


### 使用方法
下載安裝免費使用的 visual studio 2015 community 版本，然後開啟：
`ProjectOxford-clientsdk\Emotion\Windows\Sample-WPF\EmotionAPI-WPF-Samples.sln` 
F5 執行 `EmotionAPI-WPF-Samples` project, 就會看到 Face API example dialog.

Emotion API dialog 會先要求我們填入 key, 要在這邊申請自己的 Face API subscription key:
https://www.microsoft.com/cognitive-services/en-us/face-api
https://www.microsoft.com/cognitive-services/en-us/subscriptions

填完 key 之後，選 Detect emotion using a stream, `Load Image` button, 然後選 `emotionFaces` folder 下的任何一張照片。
經過大概三秒鐘的分析之後，會出現分析結果，顯示這張照片主要是 Anger, Happiness, or Sadness, 並且呼叫 `kkbox://` 播放對應的歌曲。

如果 firefox 安裝目錄與程式預設不同，要修改此：<br>
```
        private async void LoadImageButton_Click(object sender, RoutedEventArgs e)
        {
		...
            var uri = "D:\\Program Files (x86)\\Mozilla Firefox\\firefox.exe";
            System.Diagnostics.Process.Start(uri, sSongURL);
```

由於投入的開發時間不多，我是直接使用整個 SDK & sample 來修改，還沒有排除掉不需要的部分，檔案數量有點大。



