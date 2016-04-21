2016 四月微軟在台北舉辦了一項叫做 DevDays Asia 2016 的活動： https://www.microsoft.com/taiwan/events/devdays/agenda.htm
介紹了些去年陸續放出、跟今年 Build conf. 提到的新技術，主要是 Azure Machine Learning, Microsoft Cognitive Services, 等等。
並且附帶舉辦了 Hackathon 活動，鼓勵參加者使用這些新技術做些新功能。

由於我(patrick)不確定是否 kkbox 產品方便參與這種 Hackathon 活動，工作上也沒有那麼多時間。
所以昨天活動結束後自己試驗了一下 Face API, 由於花的時間還不多，這份 demo 目前還很粗糙。
這個 demo 它做的事情是：「依照用戶目前臉部的情緒，播放一首 kkbox 歌曲給用戶」。

它的工作原理是，「讀取一張照片」，呼叫 microsoft Face API 來「判斷這張照片的情緒」，然後「要 kkbox 播放一首符合目前情緒的歌曲」。
目前 Face API example 定義的 emotions 有這八種：Anger Contempt Disgust Fear Happiness Neutral Sadness Surprise ,
現在我只有對其中三種  Anger Happiness Sadness 做判斷，利用 kkbox:// 開啟 firefox, 要 kkbox 播放「許如芸 生氣」、「Happy Birthday	寶兒 (BoA)」、「陳珊妮 如同悲傷被下載了兩次」 這三首歌曲。

如果 firefox 安裝目錄與程式預設不同，要修改此：
{{{
        private async void LoadImageButton_Click(object sender, RoutedEventArgs e)
        {
		...
            var uri = "D:\\Program Files (x86)\\Mozilla Firefox\\firefox.exe";
            System.Diagnostics.Process.Start(uri, sSongURL);
}}}


同樣由於時間不多，我是直接使用整個 SDK & sample 來修改，還沒有排除掉不需要的部分。
以下是原本 SDK readme:


Microsoft Cognitive Services client SDK and samples
====================================

This repo contains the client libraries and samples that demonstrate the [Microsoft Cognitive Services](<https://www.microsoft.com/cognitive-services>), which includes the former Project Oxford APIs.
This is an evolving portfolio of REST APIs that enable developers to leverage the power of Microsoft's natural data
understanding and easily add intelligent services into their solutions. The repo contains client SDK for the following areas:  

##### Vision
-  **[Computer Vision APIs](<https://www.microsoft.com/cognitive-services/en-us/computer-vision-api>) (Preview):** Distill actionable information from images
-  **[Emotion APIs](<https://www.microsoft.com/cognitive-services/en-us/emotion-api>) (Preview):** Personalize experiences with emotion recognition
-  **[Face APIs](<https://www.microsoft.com/cognitive-services/en-us/face-api>) (Preview):** Detect, identify, analyze, organize, and tag faces in photos
-  **[Video APIs](<https://www.microsoft.com/cognitive-services/en-us/video-api>) (Preview):** Analyze, edit, and process videos within your app

##### Speech
-  **[Speaker Recognition APIs](<https://www.microsoft.com/cognitive-services/en-us/speaker-recognition-api>) (Preview):** Give your app the ability to know who's talking
-  **[Speech APIs](<https://www.microsoft.com/cognitive-services/en-us/speech-api>) (Preview):** Convert speech to text and back again, and understand its intent


##### Language
-  **[LUIS, Language Understanding Intelligent Services](<https://www.microsoft.com/cognitive-services/en-us/language-understanding-intelligent-service-luis>) (Preview):** Teach your apps to understand commands from your users
-  **[Linguistic Analysis APIs](<https://www.microsoft.com/cognitive-services/en-us/linguistic-analysis-api>) (Preview):** Easily parse complex text with language analysis
-  **[Web Language Model APIs](<https://www.microsoft.com/cognitive-services/en-us/web-language-model-api>) (Preview):** Leverage the power of language models trained on web-scale data

##### Knowledge
-  **[Entity Linking APIS](<https://www.microsoft.com/cognitive-services/en-us/entity-linking-intelligence-service>) (Preview):** Contextually extend knowledge of people, locations, and events

To see the full list of APIs, please visit [Microsoft Cognitive Service APIs](<https://www.microsoft.com/cognitive-services/en-us/apis>).

To learn more and sign-up for Microsoft Cognitive Services, [visit our
website](<https://www.microsoft.com/cognitive-services>). You must obtain subscription
keys for different services and will need a Microsoft account.

#### For information about our latest release, check out the [Release Page](<https://github.com/Microsoft/ProjectOxford-ClientSDK/releases>)

Getting started
===============
This repo contains a suite of SDKs that includes REST wrappers and samples to
develop using the Microsoft Cognitive Services APIs. Each SDK includes a guide for
installation and use. To begin, select an API and pick the platform of
your choice:

-   [Computer Vision](</Vision/>)

-   [Emotion](</Emotion/>)

-   [Entity Linking](</EntityLinking/>)

-   [Face](</Face/>)

-   [Linguistic Analysis](</LinguisticAnalysis/>)

-   [Speech](</Speech/>)

-   [Speaker Recognition](</SpeakerRecognition/>)

-   [Video](</Video/>)

-   [Web Language Model](</WebLM/>)

**Don't see what you're looking for?** We're working on expanding our offerings and would love to hear from you what SDKs you want to see next. Let us know on the [Cognitive Services UserVoice Forum](<https://cognitive.uservoice.com>).


Contributing
============
We welcome contributions and are always looking for new SDKs, input, and
suggestions. Feel free to file issues on the repo and we'll address them as we can. You can also learn more about how you can help on the [Contribution
Rules & Guidelines](</CONTRIBUTING.md>).

For questions, feedback, or suggestions about Microsoft Cognitive Services, reach out to us directly on our [Cognitive Services UserVoice Forum](<https://cognitive.uservoice.com>).



License
=======

All Microsoft Cognitive Services SDKs and samples are licensed with the MIT License. For more details, see
[LICENSE](</LICENSE.md>).

Sample images are licensed separately, please refer to [LICENSE-IMAGE](</LICENSE-IMAGE.md>).
