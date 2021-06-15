#  Geolocation(地理定位)

HTML5 Geolocation（地理定位）用于定位用户的位置。

##  定位用户的位置

HTML5 Geolocation API 用于获得用户的地理位置。

鉴于该特性可能侵犯用户的隐私，除非用户同意，否则用户位置信息是不可用的。

## HTML5 - 使用地理定位

使用 getCurrentPosition() 方法来获得用户的位置。

## getCurrentPosition() 方法 - 返回数据

T若成功，则 getCurrentPosition() 方法返回对象。始终会返回 latitude、longitude 以及 accuracy 属性。如果可用，则会返回其他下面的属性。

| 属性                    | 描述                   |
| :---------------------- | :--------------------- |
| coords.latitude         | 十进制数的纬度         |
| coords.longitude        | 十进制数的经度         |
| coords.accuracy         | 位置精度               |
| coords.altitude         | 海拔，海平面以上以米计 |
| coords.altitudeAccuracy | 位置的海拔精度         |
| coords.heading          | 方向，从正北开始以度计 |
| coords.speed            | 速度，以米/每秒计      |
| timestamp               | 响应的日期/时间        |