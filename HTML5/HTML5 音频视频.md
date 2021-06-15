#  HTML 音频/视频 DOM 参考手册

HTML5 DOM 为 <audio> 和 <video> 元素提供了方法、属性和事件。

这些方法、属性和事件允许您使用 JavaScript 来操作 `<audio>` 和 `<video>` 元素。

```html
<audio src="./audio/刚好遇见你 - 李玉刚.mp3"></audio>
```

<audio src="./audio/刚好遇见你 - 李玉刚.mp3"></audio>

```html
<video controls="controls">
    <source src="./video/mov_ppp.mp4" type="video/mp4">
</video>
```

<video controls="controls">
    <source src="./video/mov_ppp.mp4" type="video/mp4">
</video>
## HTML 音频/视频 方法

###  canPlayType()

canPlayType() 方法检测浏览器是否能播放指定的音频/视频类型。

canPlayType() 方法可返回下列值之一：

- "probably" - 浏览器最可能支持该音频/视频类型
- "maybe" - 浏览器也许支持该音频/视频类型
- "" - （空字符串）浏览器不支持该音频/视频类型

####  语法

```javascript
audio|video.canPlayType(type));
```

####  参数值：type

规定要检测的音频/视频类型（和可选的编解码器）。

常用值：

- video/ogg
- video/mp4
- video/webm
- audio/mpeg
- audio/ogg
- audio/mp4

常用值，包括编解码器：

- video/ogg; codecs="theora, vorbis"
- video/mp4; codecs="avc1.4D401E, mp4a.40.2"
- video/webm; codecs="vp8.0, vorbis"
- audio/ogg; codecs="vorbis"
- audio/mp4; codecs="mp4a.40.5"

**注意：**如果包含编解码器，则该方法只能返回 "probably"。

####  返回值

返回一个字符串。

表示支持的级别。可能的返回值：

- "probably" - 最有可能支持
- "maybe" - 可能支持
- "" - （空字符串）不支持

###  load()

load() 方法重新加载音频/视频（audio/video）元素。

load() 方法用于在更改来源或其他设置后对音频/视频（audio/video）元素进行更新。

####  语法

```javascript
audio|video.load();
```

###  play()

play() 方法开始播放当前的音频或视频。

####  语法

```javascript
audio|video.play();
```

###  pause()

pause() 方法停止（暂停）当前播放的音频或视频。

####  语法

```javascript
audio|video.pause();
```

## HTML 音频/视频属性

###  autoplay

autoplay 属性设置或返回音频/视频是否在加载后立即开始播放。

####  语法

设置 autoplay 属性：

```javascript
audio|video.autoplay=true|false;
```

返回 autoplay 属性：

```javascript
audio|video.autoplay;
```

#### 属性值

| 值    | 描述                                          |
| :---- | :-------------------------------------------- |
| true  | 指示音频/视频应在加载后立即开始播放。         |
| false | 默认。指示音频/视频不应在加载后立即开始播放。 |

**默认值为false**

###  buffered

buffered 属性返回 TimeRanges 对象。

TimeRanges 对象表示用户的音频/视频缓冲范围。

缓冲范围指的是已缓冲音频/视频的时间范围。如果用户在音频/视频中跳跃播放，会得到多个缓冲范围。

####  语法

```javascript
audio|video.buffered;
```

####  返回值

| 类型            | 描述                                                         |
| :-------------- | :----------------------------------------------------------- |
| TimeRanges 对象 | 表示音频/视频的已缓冲部分。TimeRanges 对象的属性：           length - 获得音频/视频中已缓冲范围的数量                          start(*index*) - 获得某个已缓冲范围的开始位置                         end(*index*) - 获得某个已缓冲范围的结束位置                                 **注释：**第一个缓冲范围的*下标*是 0。 |

###  controls

controls 属性设置或返回浏览器应当显示标准的音频/视频控件。

标准的音频/视频控件包括：

- 播放
- 暂停
- 进度条
- 音量
- 全屏切换（供视频）
- 字幕（当可用时）
- 轨道（当可用时）

#### 语法

设置 controls 属性：

```javascript
audio|video.controls=true|false;
```

返回 controls 属性：

```javascript
audio|video.controls;
```

#### 属性值

| 值    | 描述                   |
| :---- | :--------------------- |
| true  | 指示显示控件。         |
| false | 默认。指示不显示控件。 |

#### 技术细节

| 返回值： | 布尔值，true\|false |
| :------- | ------------------- |
| 默认值： | false               |

###  currentSrc

currentSrc 属性返回当前音频/视频的 URL。

如果未设置音频/视频，则返回空字符串。

#### 语法

```javascript
audio|video.currentSrc;
```

###  currentTime

currentTime 属性设置或返回音频/视频播放的当前位置（以秒计）。

当设置该属性时，播放会跳跃到指定的位置。

####  语法

设置 currentTime 属性：

```javascript
audio|video.currentTime="seconds";
```

返回 currentTime 属性：

```javascript
audio|video.currentTime;
```

#### 属性值

| 值        | 描述                                  |
| :-------- | :------------------------------------ |
| *seconds* | 指示音频/视频播放的当前位置，以秒计。 |

###  defaultMuted

defaultMuted 属性设置或返回音频/视频是否默认静音。

设置该属性仅会改变默认的静音状态，而不是当前的。要改变当前的静音状态，请使用 [muted](#muted) 属性。

####  语法

设置 defaultMuted属性：

```javascript
audio|video.defaultMuted = true|false;
```

返回 defaultMuted属性：

```javascript
audio|video.defaultMuted;
```

#### 属性值

| 值    | 描述                                |
| :---- | :---------------------------------- |
| true  | 指示音频/视频默认是静音的。         |
| false | 默认。指示音频/视频默认不是静音的。 |

#### 技术细节

| 返回值： | 布尔值，true\|false |
| :------- | ------------------- |
| 默认值： | false               |

###  defaultPlaybackRate

defaultPlaybackRate 属性设置或返回音频/视频的默认播放速度。

设置该属性仅会改变默认的播放速度，而不是当前的。要改变当前的播放速度，请使用 [playbackRate](#playbackRate) 属性。

####  语法

设置 defaultPlaybackRate属性：

```javascript
audio|video.defaultPlaybackRate = playbackspeed;
```

返回 defaultPlaybackRate属性：

```javascript
audio|video.defaultPlaybackRate;
```

#### 属性值

| 值              | 描述                                                         |
| :-------------- | :----------------------------------------------------------- |
| *playbackspeed* | 指示音频/视频的默认播放速度。 例值：                                                 1.0 正常速度                                                                                               0.5 半速（更慢）                                                                                       2.0 倍速（更快）                                                                                        -1.0 向后，正常速度                                                                                  -0.5 向后，半速 |

默认值  1.0

###  duration

duration 属性返回当前音频/视频的长度，以秒计。

如果未设置音频/视频，则返回 NaN (Not-a-Number)。

####  语法

```javascript
audio|video.duration;
```

####  返回值

数字值，表示音频/视频的长度，以秒计。

###  ended

ended 属性返回音频/视频的播放是否已结束。

如果播放位置位于音频/视频的结尾时，则音频/视频已结束。

####  语法

```javascript
audio|video.ended;
```

####  返回值

布尔值，true|false。如果播放已结束，则返回 true，否则返回 false。

###  loop

#### 语法

设置 loop 属性：

```javascript
audio|video.loop=true|false;
```

返回 loop 属性：

```javascript
audio|video.loop;
```

#### 属性值

| 值    | 描述                                        |
| :---- | :------------------------------------------ |
| true  | 指示音频/视频应该在结束时重新播放。         |
| false | 默认。指示音频/视频不应该在结束时重新播放。 |

#### 技术细节

| 返回值： | 布尔值，true\|false |
| :------- | ------------------- |
| 默认值： | false               |

###  mediaGroup

mediaGroup 属性设置或返回音频/视频所属的媒体组合的名称。

媒体组合允许两个或更多音频/视频（audio/video）元素保持同步。

#### 语法

设置 mediaGroup 属性：

```javascript
audio|video.mediaGroup="group";
```

返回 mediaGroup 属性：

```javascript
audio|video.mediaGroup;
```

#### 属性值

| 值      | 描述                      |
| :------ | :------------------------ |
| *group* | 规定音频/视频的媒体组合。 |

####  返回值

字符串值，指示音频/视频的媒体组合。

###  muted

muted 属性设置或返回音频/视频是否应该被静音（关闭声音）。

#### 语法

设置 muted 属性：

```javascript
audio|video.muted=true|false;
```

返回 muted 属性：

```javascript
audio|video.muted;
```

#### 属性值

| 值    | 描述                                |
| :---- | :---------------------------------- |
| true  | 指示应该关闭音频/视频的声音。       |
| false | 默认。指示应该打开音频/视频的声音。 |

#### 技术细节

| 返回值： | 布尔值，true\|false |
| :------- | ------------------- |
| 默认值： | false               |

###  networkState

networkState 属性返回音频/视频的当前网络状态（activity）。

####  语法

```javascript
audio|video.networkState;
```

#### 返回值

| 类型   | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| Number | 表示音频/视频元素的当前网络状态：                                                                                                                                                                                                                0 = NETWORK_EMPTY - 音频/视频尚未初始化                                                                                                                                                                                    1 = NETWORK_IDLE - 音频/视频是活动的且已选取资源，但并未使用网络                                                                                                                                      2 = NETWORK_LOADING - 浏览器正在下载数据                                                                                                                                                                                3 = NETWORK_NO_SOURCE - 未找到音频/视频来源 |

###  paused

设置或返回音频/视频是否暂停。

####  语法

```javascript
audio|video.paused = true|false;//设置paused
audio|video.paused;//返回paused
```

###  playbackRate

playbackRate 属性设置或返回音频/视频的当前播放速度。

####  语法

```javascript
audio|video.playbackRate=playbackspeed;//设置 plarbackRate
audio|video.playbackRate;//返回 plarbackRate
```

#### 属性值

| 值              | 描述                                                         |
| :-------------- | :----------------------------------------------------------- |
| *playbackspeed* | 指示音频/视频的当前播放速度。 例值：                                                 1.0 正常速度                                                                                               0.5 半速（更慢）                                                                                       2.0 倍速（更快）                                                                                        -1.0 向后，正常速度                                                                                  -0.5 向后，半速 |

###  played

played 属性返回 TimeRanges 对象。

TimeRanges 对象表示用户已经播放或看到的音频/视频范围。

已播范围指的是被播放音频/视频的时间范围。如果用户在音频/视频中跳跃，则会获得多个播放范围。

####  语法

```javascript
audio|video.played;
```

#### 返回值

| 类型            | 描述                                                         |
| :-------------- | :----------------------------------------------------------- |
| TimeRanges 对象 | 表示音频/视频的已播范围。TimeRanges 对象的属性：                                                                                                                                                                                              length - 获得音频/视频中已播范围的数量                                                                                                                                                                          start(*index*) - 获得某个已播范围的开始位置                                                                                                                                                                     end(*index*) - 获得某个已播范围的结束位置                                                                                                                                                                                 **注释：**第一段已播范围的下标 *index* 是 0。 |

###  preload

preload 属性设置或返回是否在页面加载后立即加载音频/视频。

preload 属性允许作者向浏览器提供有关他/她认为会带来最佳用户体验的暗示。该属性在某些情况下被忽略。

####  语法

```javascript
audio|video.preload="auto|metadata|none";
```

#### 属性值

| 值       | 描述                                      |
| :------- | :---------------------------------------- |
| auto     | 指示一旦页面加载，则开始加载音频/视频。   |
| metadata | 指示当页面加载后仅加载音频/视频的元数据。 |
| none     | 指示页面加载后不应加载音频/视频。         |

###  readyState

readyState 属性返回音频/视频的当前就绪状态。

就绪状态指示音频/视频是否已准备好播放。

####  语法

```javascript
audio|video.readyState;
```

#### 返回值

| 类型   | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| Number | 表示音频/视频（audio/video）元素的就绪状态：                                                                                                                                                                                 0 = HAVE_NOTHING - 没有关于音频/视频是否就绪的信息                                                                                                                                                             1 = HAVE_METADATA - 关于音频/视频就绪的元数据                                                                                                                                                                                 2 = HAVE_CURRENT_DATA - 关于当前播放位置的数据是可用的，但没有足够的数据来播放下一帧/毫秒                                                                                     3 = HAVE_FUTURE_DATA - 当前及至少下一帧的数据是可用的                                                                                                                                                                          4 = HAVE_ENOUGH_DATA - 可用数据足以开始播放 |

###  seekable

seekable 属性返回 TimeRanges 对象。

TimeRanges 对象表示音频/视频中用户可寻址的范围。

可寻址范围指的是用户在音频/视频中可寻址（移动播放位置）的时间范围。

对于非流视频，通常可以寻址到视频中的任何位置，即使其尚未完成缓冲。

####  语法

```javascript
audio|video.seekable;
```

#### 返回值

| 类型              | 描述                                                         |
| :---------------- | :----------------------------------------------------------- |
| TimeRanges Object | 表示音频/视频中的可寻址部分。TimeRanges 对象的属性：                                                                                                                                                   length - 获得音频/视频中可寻址范围的数量                                                                                                                                                                        start(*index*) - 获得可寻址范围的开始位置                                                                                                                                                                           end(*index*) - 获得可寻址范围的结束位置                                                                                                                                                                                              **注释：**第一个可寻址范围的下标 *index* 是 0。 |

###  src

src 属性设置或返回音频/视频的当前来源。

####  语法

```javascript
audio|video.src = URL;
audio|video.src;
```

#### 属性值

| 值    | 描述                                                         |
| :---- | :----------------------------------------------------------- |
| *URL* | 规定音频/视频来源的 URL。可能的值：绝对 URL - 指向另一个网站（比如 src="http://www.example.com/movie.ogg"）相对 URL - 指向网站内的一个文件（比如 src="movie.ogg） |

###  volume

volume 属性设置或返回音频/视频的当前音量。

####  语法

```javascript
audio|video.volume = volumevalue;
audio|video.volume;
```

## 属性值

| 值            | 描述                                                         |
| :------------ | :----------------------------------------------------------- |
| *volumevalue* | 规定音频/视频的当前音量。必须是介于 0.0 与 1.0 之间的数字。 例值：1.0 最高音量（默认）0.5 一半音量 （50%）0.0 静音 |

