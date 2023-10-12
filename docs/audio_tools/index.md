---
title: 有声书工具箱
sidebar: false
navbar: false
footer: false
prev: false
next: false
---
# 🎹 有声书工具箱
---
剪辑片头片尾，修改元数据，制作有声书、音乐播客源（宝藏App播客是时候用起来了，Apple原生应用播放 Nas 中的海量音乐），元数据 plex、Audiobookshelf 可识别。
<div class="base_img"><img src="/audio_tools/cover.png"/></div>

::: tip 主要功能说明
- 剪辑有声书片头片尾
- 本地音频生成 Apple 播客源，原理是制作 RSS 订阅链接，通过播客 App 订阅。
- iOS可自动添加到播客 App 订阅
- 修改有声书元数据
- 同步喜马拉雅音频为播客源
:::
::: info 播客源兼容安卓
例如：Antennapod，复制播客源链接到 App 中订阅即可
:::

<div class="base_img"><img src="/audio_tools/3.png"/></div>


### 使用说明
---
- 将 `audio_tools` 文件夹放到 `Plugins` 文件夹。或通过 Mbot 插件市场免费安装。
- 重启后如果日志报错：依赖库 `mutagen` `cn2an` `ffmpeg` 安装失败而导致插件载入失败，请手动进入 MR 命令行安装，安装命令：`pip install mutagen cn2an ffmpeg-python`
- 通过播客源页面将有声书播客源 URL 添加到 iOS 自带的播客 App 中。
<div class="base_img"><img src="/audio_tools/4.png"/></div>


### 插件设置
---
::: warning 注意
所有涉及到的路径均为映射到 Mbot 容器内路径
:::
<div class="base_img"><img src="/audio_tools/5.png"/></div>



### 音频剪辑
---
<div class="base_img"><img src="/audio_tools/6.png"/></div>


### 生成播客源
---
<div class="base_img"><img src="/audio_tools/7.png"/></div>

### 修改音频封面
---

::: tip 说明
- 单独提出来的修改有声书封面的快捷功能，填文件夹路径即可
- 输入路径下必须有 cover.jpg
:::
### 整理有声书
---

::: tip 说明
这是一个整理元数据的快捷功能，按要求填入相应信息即可，设置项都有详细的说明
:::
### 修改 metadata.abs
---
::: info 说明
如果你使用的是 Audiobookshelf 服务器，可能此功能在某些时候有用
:::
### 下载喜马拉雅
---
::: info 说明
用于下载喜马拉雅音频，仅用作测试，谨慎使用！仅支持免费音频，版权归喜马拉雅所有，请支持正版！
:::
### 同步播客
---
::: info 说明
- 同步喜马拉雅并更新到播客节目中，仅支持免费音频，版权归喜马拉雅所有，请支持正版！
- 在插件设置中设置好订阅信息后，可自动下载并更新，全自动。
:::
 

### 如果帮到了你可以请我喝杯咖啡
---
<div class="base_img" align=left><img src="/coffee.png" width="150" /></div>


::: details 播客源的 RSS 指南

一个RSS订阅包含了一个播客的所有元数据。这些信息决定了在苹果服务上用户看到的有关你的播客的内容，包括节目封面、是否在相关搜索中显示以及剧集标题和描述等等。
为了能够在苹果播客目录中列出你的播客，并在苹果播客应用程序中显示，需要创建相应的RSS订阅，提交到Podcasts Connect，并通过苹果的验证（有关更多信息，请参考Podcaster Support）。
RSS订阅中的所有元数据都存储在元素标签中（参考RSS Feed Sample）。每个标签都适用于节目数据（包含在 `<channel>` 标签中）或剧集数据（包含在 `<item>` 标签中）。本指南将解释应包含哪些数据以及如何进行结构化。
注意：本页面未列出所有支持的RSS标签，仅列出了最重要的。如果苹果将来废弃RSS标签，播客人士将会在Podcasts Connect和新闻通讯中收到通知。
下图显示了苹果播客应用程序中的“节目视图”，并标注了 `<channel>` 标签如何映射到节目信息。

<div class="base_img"><img src="/audio_tools/1.png"/></div>

在下表中，`必需的标签` 必须存在于你的RSS订阅中，否则将无法通过验证以在苹果播客中列出。`推荐的标签` 虽然不是必需的，但强烈建议使用，因为它们为用户提供了有用的信息。`情景标签` 在特定情况下很重要。

|  标签  |  用法  |  父标签  |
| :-----------: | ----------- | :-----------: |
|  `<title>`  |  <h4>播客标题</h4>为你的播客取一个清晰、简洁的名称非常重要。让你的标题具体明确。一个标题为《我们的社区公告》的节目太过模糊，无论内容多么引人入胜，都难以吸引许多订阅者。<br><br>请特别注意标题，因为苹果播客会使用这个字段进行搜索。<br><br>如果你试图通过包含长长的关键词列表来操控播客搜索，你的节目可能会被从苹果目录中移除。 |  `<channel>`  |
|  `<description>`  |  <h4>播客描述</h4>其中描述是包含一个或多个句子的文本，用于向潜在听众描述您的播客。此标签允许的文本最大长度为4000字节。<br><br>要在描述中包含链接或丰富的HTML，请遵循以下技术指南：将包含嵌入HTML的XML部分全部放在CDATA部分中，以防止格式问题，并确保链接功能正常。例如：<br>`<![CDATA[ <a href="http://www.apple.com">Apple</a> ]]>` |  `<channel>`  |
|  `<itunes:image>`  |  <h4>播客封面</h4>通过提供指向封面的URL来指定您的节目封面。<br><br>根据用户设备的不同，订阅者会以不同的尺寸看到您的播客封面。因此，请确保您的设计在原始尺寸和缩略图尺寸上都能有效果。您应该在播客封面中包含节目标题、品牌或来源名称作为其中的一部分。以下是额外的市场营销最佳实践。有关播客封面的示例，请参阅热门播客排行榜。为了避免在更新播客封面时出现技术问题，请确保：<br><ol><li>同时更改封面文件名和URL</li><li>验证托管封面的Web服务器是否允许HTTP head请求</li><li>验证托管封面的Web服务器是否允许HTTP head请求</li><li>封面的最小尺寸必须为1400 x 1400像素，最大尺寸为3000 x 3000像素，以JPEG或PNG格式，72 dpi，并具有适当的文件扩展名（.jpg、.png），以及RGB颜色空间。这些要求与标准的RSS图片标签规范有所不同。</li><li>确保URL中的文件类型与图像文件的实际文件类型相匹配。</li></ol>  |  `<channel>`  |
|  `<language>`  |  <h4>播客使用的语言</h4>由于 Apple Podcasts 在世界各地都可用，因此指定播客的语言非常重要。Apple Podcasts 仅支持 ISO 639 列表中的语言代码（两个字母的语言代码，可能带有一些修饰符，例如 `en-us`）。无效的语言代码将导致您的Feed未通过Apple的验证。 |  `<channel>`  |
|  `<itunes:category>`  |  <h4>播客类别信息</h4>如需完整的类别和子类别列表，请参阅 Apple Podcast 类别。<br><br>请选择最能反映您节目内容的类别。如果可用，您还可以定义一个子类别。虽然您可以在RSS源中指定多个类别和子类别，但是Apple Podcasts只会识别第一个类别和子类别。在指定类别和子类别时，请确保正确转义和符号。例如：<br>指定单个类别<br>`<itunes:category text="历史" />`<br>包含符号的类别<br>`<itunes:category text="儿童与家庭" />`<br>带有子类别的类别<br>`<itunes:category text="社会与文化">`<br>`<itunes:category text="纪录片" />`<br>`</itunes:category>`<br>多个类别<br>`<itunes:category text="社会与文化">`<br>`<itunes:category text="纪录片" />`<br>`</itunes:category>`<br>`<itunes:category text="健康">`<br>`<itunes:category text="心理健康" />`<br>`</itunes:category>` |  `<channel>`  |
|  `<itunes:explicit>`  |  <h4>播客的家长指导信息</h4>取值可以是以下之一<br><ol><li>如果指定为 `true`，表示有含有不适宜内容，Apple Podcasts 将在您的播客中显示一个明确的家长指导图标。包含明确内容的播客不在某些 Apple Podcasts 地区可用。</li><li>如果指定为 `false`，表示您的播客不包含明确语言或成人内容，Apple Podcasts 将在您的播客中显示一个干净的家长指导图标。</li></ol>  |  `<channel>`  |
|  `<itunes:author>`  |  <h4>播客的作者</h4>节目作者通常指的是播客的母公司或网络，但也可以用于标识主持人（如果没有）。<br><br>如果一个公司或组织发布多个播客，作者信息尤其有用。 |  `<channel>`  |
|  `<link>`  |  <h4>与播客相关联的网站</h4>通常是播客的主页或一个较大网站的专门部分。例如：<br>`<link> http://www.mypodcast.com </link>` 或 `<link> http://www.mediacompany.com/podcast </link>` |  `<channel>`  |
|  `<itunes:owner>`  |  <h4>播客所有者的联系信息</h4>在嵌套的 `<itunes:email>` 标签中包含所有者的电子邮件地址，并在嵌套的 `<itunes:name>` 标签中包含所有者的姓名。<br>注意： `<itunes:owner>` 标签信息是供进行有关播客的管理通讯使用的，不会在 Apple Podcasts 中显示。请确保电子邮件地址是有效的并且有人监测。 |  `<channel>`  |
|  `<itunes:title>`  |  <h4>在 Apple Podcasts 中特定的节目标题</h4>`<itunes:title>` 是一个字符串，包含了您的节目在Apple Podcasts上清晰简洁的名称。 |  `<channel>`  |
|  `<itunes:type>`  |  <h4>在 Apple Podcasts 中特定的节目标题</h4>`<itunes:title>` 是一个字符串，包含了您的节目在Apple Podcasts上清晰简洁的名称。 |  `<channel>`  |

下面的图示显示了 Apple Podcasts 应用程序中的“节目视图”，并标出了 `<item>` 标签如何映射到剧集信息。需要注意的是，上面列出的 `<itunes:type>` 节目标签会影响剧集的显示方式。请注意：Apple会显示最近的 2,000 集剧集。其中，只有有效的剧集会显示在节目页面上。

默认情况下，节目被归类为“Episodic”，这意味着最新的剧集会首先展示，并且会显示每个剧集的发布日期（`<pubDate>`）。如果您将节目的itunes:type指定为“Serial”，同时还需要为每个剧集指定itunes:episode集数，那么剧集将按照从最旧到最新的顺序列出。
<div class="base_img"><img src="/audio_tools/2.png"/></div>

在下表中，必需的标签必须存在于您的RSS订阅源中，否则无法通过验证无法在Apple Podcasts中列出。推荐的标签不是必需的，但是强烈建议使用，因为它们为用户提供了有用的信息。根据情况的不同，一些特定标签也很重要。


以下是一个RSS订阅源的示例。

提示：如果您在解决验证失败的问题时遇到困难，可以使用外部工具，如Cast Feed Validator和Podbase Podcast Validator，它们可能会提供更详细的洞察。
```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd" xmlns:content="http://purl.org/rss/1.0/modules/content/">
  <channel>
    <title>Hiking Treks</title>
    <link>https://www.apple.com/itunes/podcasts/</link>
    <language>en-us</language>
    <copyright>&#169; 2020 John Appleseed</copyright>
    <itunes:author>The Sunset Explorers</itunes:author>
    <description>
      Love to get outdoors and discover nature&apos;s treasures? Hiking Treks is the
      show for you. We review hikes and excursions, review outdoor gear and interview
      a variety of naturalists and adventurers. Look for new episodes each week.
    </description>
    <itunes:type>serial</itunes:type>
    <itunes:image
      href="https://applehosted.podcasts.apple.com/hiking_treks/artwork.png"
    />
    <itunes:category text="Sports">
      <itunes:category text="Wilderness"/>
    </itunes:category>
    <itunes:explicit>false</itunes:explicit>
    <item>
      <itunes:episodeType>trailer</itunes:episodeType>
      <itunes:title>Hiking Treks Trailer</itunes:title>
      <description>
          <![CDATA[The Sunset Explorers share tips, techniques and recommendations for
          great hikes and adventures around the United States. Listen on 
          <a href="https://www.apple.com/itunes/podcasts/">Apple Podcasts</a>.]]>
      </description>
      <enclosure 
        length="498537" 
        type="audio/mpeg" 
        url="http://example.com/podcasts/everything/AllAboutEverythingEpisode4.mp3"
      />
      <guid>D03EEC9B-B1B4-475B-92C8-54F853FA2A22</guid>
      <pubDate>Tue, 8 Jan 2019 01:15:00 GMT</pubDate>
      <itunes:duration>1079</itunes:duration>
      <itunes:explicit>false</itunes:explicit>
    </item>
    <item>
      <itunes:episodeType>full</itunes:episodeType>
      <itunes:episode>4</itunes:episode>
      <itunes:season>2</itunes:season>
      <title>S02 EP04 Mt. Hood, Oregon</title>
      <description>
        Tips for trekking around the tallest mountain in Oregon
      </description>
      <enclosure
        length="8727310" 
        type="audio/x-m4a" 
        url="http://example.com/podcasts/everything/mthood.m4a"
      />
      <guid>22BCFEBF-44FB-4A19-8229-7AC678629F57</guid>
      <pubDate>Tue, 07 May 2019 12:00:00 GMT</pubDate>
      <itunes:duration>1024</itunes:duration>
      <itunes:explicit>false</itunes:explicit>
    </item>
    <item>
      <itunes:episodeType>full</itunes:episodeType>
      <itunes:episode>3</itunes:episode>
      <itunes:season>2</itunes:season>
      <title>S02 EP03 Bouldering Around Boulder</title>
      <description>
        We explore fun walks to climbing areas about the beautiful Colorado city of Boulder.
      </description>
      <itunes:image
        href="http://example.com/podcasts/everything/AllAboutEverything/Episode2.jpg"
      />
      <link>href="http://example.com/podcasts/everything/</link>
      <enclosure 
        length="5650889" 
        type="video/mp4" 
        url="http://example.com/podcasts/boulder.mp4"
      />
      <guid>BE486CAA-B3D5-4FB0-8298-EFEBE71C5982</guid>
      <pubDate>Tue, 30 Apr 2019 13:00:00 EST</pubDate>
      <itunes:duration>3627</itunes:duration>
      <itunes:explicit>false</itunes:explicit>
    </item>
    <item>
      <itunes:episodeType>full</itunes:episodeType>
      <itunes:episode>2</itunes:episode>
      <itunes:season>2</itunes:season>
      <title>S02 EP02 Caribou Mountain, Maine</title>
      <description>
        Put your fitness to the test with this invigorating hill climb.
      </description>
      <itunes:image
        href="http://example.com/podcasts/everything/AllAboutEverything/Episode3.jpg"
      />
      <enclosure 
        length="5650889"
        type="audio/x-m4v" 
        url="http://example.com/podcasts/everything/caribou.m4v"
      />
      <guid>142FAFE9-B1DF-4F6D-BAA8-79BDBAF653A9</guid>
      <pubDate>Tue, 23 May 2019 02:00:00 -0700</pubDate>
      <itunes:duration>2434</itunes:duration>
      <itunes:explicit>false</itunes:explicit>
    </item>
    <item>
      <itunes:episodeType>full</itunes:episodeType>
      <itunes:episode>1</itunes:episode>
      <itunes:season>2</itunes:season>
      <title>S02 EP01 Stawamus Chief</title>
      <description>
        We tackle Stawamus Chief outside of Vancouver, BC and you should too!
      </description>
      <enclosure
        length="498537" 
        type="audio/mpeg" 
        url="http://example.com/podcasts/everything/AllAboutEverythingEpisode4.mp3"
      />
      <guid>5F1DBAEB-3327-49FB-ACB3-DB0158A1D0A3</guid>
      <pubDate>2019-02-16T07:00:00.000Z</pubDate>
      <itunes:duration>13:24</itunes:duration>
      <itunes:explicit>false</itunes:explicit>
    </item>
    <item>
      <itunes:episodeType>full</itunes:episodeType>
      <itunes:episode>4</itunes:episode>
      <itunes:season>1</itunes:season>
      <title>S01 EP04 Kuliouou Ridge Trail</title>
      <description>
        Oahu, Hawaii, has some picturesque hikes and this is one of the best!
      </description>
      <enclosure
        length="498537" 
        type="audio/mpeg" 
        url="http://example.com/podcasts/everything/AllAboutEverythingEpisode4.mp3"
      />
      <guid>B5FCEB80-317C-4CD0-A84B-807065B43FB9</guid>
      <pubDate>Tue, 27 Nov 2018 01:15:00 +0000</pubDate>
      <itunes:duration>929</itunes:duration>
      <itunes:explicit>false</itunes:explicit>
    </item>
    <item>
      <itunes:episodeType>full</itunes:episodeType>
      <itunes:episode>3</itunes:episode>
      <itunes:season>1</itunes:season>
      <title>S01 EP03 Blood Mountain Loop</title>
      <description>
        Hiking the Appalachian Trail and Freeman Trail in Georgia
      </description>
      <enclosure 
        length="498537" 
        type="audio/mpeg" 
        url="http://example.com/podcasts/everything/AllAboutEverythingEpisode4.mp3"
      />
      <guid>F0C5D763-ED85-4449-9C09-81FEBDF6F126</guid>
      <pubDate>Tue, 23 Oct 2018 01:15:00 +0000</pubDate>
      <itunes:duration>1440</itunes:duration>
      <itunes:explicit>false</itunes:explicit>
    </item>
    <item>
      <itunes:episodeType>full</itunes:episodeType>
      <itunes:episode>2</itunes:episode>
      <itunes:season>1</itunes:season>
      <title>S01 EP02 Garden of the Gods Wilderness</title>
      <description>
        Wilderness Area Garden of the Gods in Illinois is a delightful spot for 
        an extended hike.
      </description>
      <enclosure 
        length="498537" 
        type="audio/mpeg" 
        url="http://example.com/podcasts/everything/AllAboutEverythingEpisode4.mp3"
      />
      <guid>821DD0B2-571D-4DFD-8E11-556E8C1EFE6A</guid>
      <pubDate>Tue, 18 Sep 2018 01:15:00 +0000</pubDate>
      <itunes:duration>839</itunes:duration>
      <itunes:explicit>false</itunes:explicit>
    </item>
    <item>
      <itunes:episodeType>full</itunes:episodeType>
      <itunes:episode>1</itunes:episode>
      <itunes:season>1</itunes:season>
      <title>S01 EP01 Upper Priest Lake Trail to Continental Creek Trail</title>
      <description>
        We check out this powerfully scenic hike following the river in the Idaho
        Panhandle National Forests.
      </description>
      <enclosure 
        length="498537" 
        type="audio/mpeg" 
        url="http://example.com/podcasts/everything/AllAboutEverythingEpisode4.mp3"
      />
      <guid>EABDA7EE-1AC6-4B60-9E11-6B3F30B72F87</guid>
      <pubDate>Tue, 14 Aug 2018 01:15:00 +0000</pubDate>
      <itunes:duration>1399</itunes:duration>
      <itunes:explicit>false</itunes:explicit>
    </item>
  </channel>
</rss>
```
:::