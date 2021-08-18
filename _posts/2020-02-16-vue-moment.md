---
lang: ko-KR
title: 'vue-moment 적용 및 사용 방법'
date: 2020-02-16
update: 2020-02-16
tags:
  - vuejs
  - vue-moment
author: k1005
---

## {{ $frontmatter.title }}

```ssh
$ npm install vue-moment
```

그리고 require를 사용한다면 이렇게 쉽게 적용할 수가 있다.

```javascript
Vue.use(require('vue-moment'));
```

require를 사용하지 않는다면 이렇게 적용하자.

```javascript
import VueMoment from 'vue-moment'
Vue.use(VueMoment);
```

---

## vue-moment를 사용해 보자

위와 같이 적용을 했다면 vue에서는 `Vue.$moment` 로 호출하여 사용할 수 있다. 스크립트에서는 `this.$moment` 를 사용하고 template 에서는 `{{$moment}}`를 사용하면 된다.

혹시 안된다면 moment를 호출해 보자.

가장 기본적인 사용방법은 아래와 같다.

```html
<!-- 현재시간 표현 -->
<span>{{$moment().format('YYYY-MM-DD')}}</span>

<!-- 데이터 시간 표현 -->
<span>{{$moment(item.dateTime).format('YYYY-MM-DD')}}</span>
```

위와 같은 방법으로 Long, Date 혹은 String 타입의 데이터를 활용할 수 있다.

### String 데이터를 파싱하기

String 현태의 데이터를 파싱할 때는 다음과 같은 형식을 사용할 수 있다.

```
## An ISO 8601 string requires a date part.
2013-02-08  # A calendar date part
2013-W06-5  # A week date part
2013-039    # An ordinal date part

20130208    # Basic (short) full date
2013W065    # Basic (short) week, weekday
2013W06     # Basic (short) week only
2013050     # Basic (short) ordinal date

## A time part can also be included,
## separated from the date part by a space or an uppercase T.
2013-02-08T09            # An hour time part separated by a T
2013-02-08 09            # An hour time part separated by a space
2013-02-08 09:30         # An hour and minute time part
2013-02-08 09:30:26      # An hour, minute, and second time part
2013-02-08 09:30:26.123  # An hour, minute, second, and millisecond time part
2013-02-08 24:00:00.000  # hour 24, minute, second, millisecond equal 0 means next day at midnight

20130208T080910,123      # Short date and time up to ms, separated by comma
20130208T080910.123      # Short date and time up to ms
20130208T080910          # Short date and time up to seconds
20130208T0809            # Short date and time up to minutes
20130208T08              # Short date and time, hours only

## Any of the date parts can have a time part.
2013-02-08 09  # A calendar date part and hour time part
2013-W06-5 09  # A week date part and hour time part
2013-039 09    # An ordinal date part and hour time part

## If a time part is included,
## an offset from UTC can also be included as +-HH:mm, +-HHmm, +-HH or Z.
2013-02-08 09+07:00            # +-HH:mm
2013-02-08 09-0100             # +-HHmm
2013-02-08 09Z                 # Z
2013-02-08 09:30:26.123+07:00  # +-HH:mm
2013-02-08 09:30:26.123+07     # +-HH

## The RFC 2822 date time format
6 Mar 17 21:22 UT
6 Mar 17 21:22:23 UT
6 Mar 2017 21:22:23 GMT
06 Mar 2017 21:22:23 Z
Mon 06 Mar 2017 21:22:23 z
Mon, 06 Mar 2017 21:22:23 +0000
```

### format (포멧하기)

데이터를 표현할 때 인자를 어떻게 주느냐에 따라 내가 원하는 형태로 만들 수 있다.

```javascript
$moment("12-25-1995", "MM-DD-YYYY");
```

InputExampleDescription
<table style="border-collapse: collapse; width: 100%;" border="1">
<tbody>
<tr>
<td>YYYY</td>
<td>2014</td>
<td>4 자릿수 연도</td>
</tr>
<tr>
<td>YY</td>
<td>14</td>
<td>2 자릿수 연도</td>
</tr>
<tr>
<td>Y</td>
<td>-25</td>
<td>Year with any number of digits and sign</td>
</tr>
<tr>
<td>Q</td>
<td>1..4</td>
<td>연도를 쿼터로 나누어 표현</td>
</tr>
<tr>
<td>M MM</td>
<td>1..12</td>
<td>1, 2 자릿수 월</td>
</tr>
<tr>
<td>MMM MMMM</td>
<td>Jan..December</td>
<td>3글자 월 이름, 월의 전체 이름</td>
</tr>
<tr>
<td>D DD</td>
<td>1..31</td>
<td>Day of month</td>
</tr>
<tr>
<td>Do</td>
<td>1st..31st</td>
<td>Day of month with ordinal</td>
</tr>
<tr>
<td>DDD DDDD</td>
<td>1..365</td>
<td>Day of year</td>
</tr>
<tr>
<td>X</td>
<td>1410715640.579</td>
<td>Unix timestamp</td>
</tr>
<tr>
<td>x</td>
<td>1410715640579</td>
<td>Unix ms timestamp</td>
</tr>
</tbody>
</table>

---
## 더 깊이 들어가기

위와 같은 방식으로 대부분 원하는 대로 사용 가능 할 것이다. 하지만 이외의 더욱 깊이 알고 싶거나 자신이 원하는 방식이 아닐 경우 필요할 때마다 아래의 사이트를 이용하여 정보를 찾아 보고 적용할 수 있다.

굳이 다 알아 두겠다면 뭐.. 말리지는 않겠다.

https://momentjs.com/docs/


