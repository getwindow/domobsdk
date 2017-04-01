## domob 积分墙对开发者的激活反馈接口技术说明书

Version:3.0.0

更新时间: 2014-09-12

### 一 说明

- 接口统一使用的编码为：<b style='color:red'>UTF-8</b>

- 适合于开发者使用自己的服务器来托管积分的情况

- 当我们收到广告主反馈的积分时，我们会实时反馈给开发者服务器

- 需要开发者提供一个自己应用的积分反馈地址，接口接收数据的方式:GET

- <b style='color:red'>注:若开发者在使用积分墙 SDK 的应用中绑定 userid(SDK2.0.3 的最新功能)，或
  对于没有升级到嵌入了 iOS SDK 2.0.3 以上版本 SDK 的用户，则积分反馈信息中的账
  户 ID(下文中的 UserID)为经过 md5 加密的 MAC 地址</b>

### 二 解决方案

1 开发者联系多盟的商务或技术接口人，设置自己应用的<b style='color:red'>积分反馈地址</b>，并获取多盟为开发者分配的<b style='color:red'>密钥</b>(下文中的 private_key)

2 当多盟的服务器接收到一个有效的激活记录时，就会按开发者提供的积分反馈地址，加 上相关的参数(具体参数见下面的表格)，一起反馈给开发者的服务器(HTTP GET 的方式）

|     参数名     | 类型           | 说明                                       |
| :---------: | :----------- | :--------------------------------------- |
|   orderid   | 字符串          | 订单 ID。该值是唯一的，如果开发者接收到相同的订单号，那说 明该订单已经存在  |
|    pubid    | 字符串          | Publisher ID，即开发者的积分墙应用 ID               |
|     ad      | 字符串          | 广告名称                                     |
|    adid     | 整型           | 广告 ID，即 offer ID                         |
|    user     | 字符串          | UserID <b style='color:red'>iOS 平台</b>，若开发者没有在积分墙 iOS SDK 中绑定 userid，或对 于没有升级到嵌入了 SDK 2.0.3 以上版本 SDK 的用户，则 user 为经过 md5 加密的用户设备的带冒号的大写的 MAC 地址。例 子:md5('24:AB:81:5E:F6:1E')= 13A81BB8DCA00BE81794E246C8429C0E <b style='color:red'>android 平台</b>，如果开发者没有在积分墙 android SDK 中绑定 userid，则 user 为设备的 imei |
|   device    | 字符串          | 设备号。<b style='color:red'>iOS:设备号优先级为 mac 地址 > IDFA > OpenUDID</b> 如果 mac 地址为有效值(iOS 7 将获取不到有效的 MAC 地 址)，则为大写的原始 mac 地址;否则如果多盟的 SDK 能够获 取到设备的 IDFA(iOS 6 才能获取)，则为设备的IDFA;如果 mac 地址无效且获取不到设备的 IDFA，则为设备的 OpenUDID <b style='color:red'>android:统一返回设备的 imei</b> |
|   channel   | 整型           | 渠道号。预留给 android 的推广，对于 iOS 来说该值为 0       |
|    price    | 浮点型， 保留两位 小数 | 开发者获得的收入                                 |
|    point    | 整型           | 用户可获得的积分                                 |
|     ts      | 整型           | 成功结算的时间戳，精确到秒                            |
|    sign     | 字符串          | 签名。根据 private_key 与所有参数共同计算得出。           |
|     pkg     | 字符串          | 被激活的广告的包名，例如 cn.domob.demo               |
|   action    | 整型           | 动作编号，从 0 开始。通常 0 表示激活，从 1 开始表示签到         |
| action_name | 字符串          | 动作名称，例如“激活”，“签到-1”，“签到-2”等               |

3 返回值

- 多盟会根据开发者服务器返回的 HTTP 状态码(http code)来判断进行什么样的操作
- 如果是 200，表示开发者服务器正常接收到消息并且正常处理了
- 如果是 403，则多盟会不再重发这个请求
- 如果是超时、或收到的不是 200 和 403，多盟会在下一次循环请求开发者服务器。下一次请求会有一定的延迟，延迟分别为:5s、10s、60s、300s、600s、3600s(距 离上次发送)。即在最差情况下，多盟最多将发送 7 次请求

4 签名算法(即 sign 的计算方法)

将【参数】列表中所有参数作为 key 求 MD5 值:

假设参与参数签名计算的请求参数分别是“k1”、“k2”、“k3”，它们的值 分别是“v1”、“v2”、“v3”，则参数签名计算方法如下:

- 将请求的非 binary 类型的参数格式化为“key=value”格式，即 k1=v1”、“k2=v2”、“k3=v3”
- 将参数的键值以字典序升序排列后，拼接在一起，及“k1=v1k2=v2k3=v3”
- 在拼接好的字符串末尾追加上 private_key
- 上述字符串的 MD5 值即为签名的值

**注意：**

- 签名过程中的各个参数并未经过 urlencode 处理

```
sign=md5(“action={$action}action_name={$action_name}ad={$ad}adid={$adid}c hannel={ $channel }device={$ device }orderid={$ orderid }pkg={$pkg}point={$ poi nt }price={$ price } pubid={$pubid }ts={$ts}user={$user}{$private_key}");
```


**示例：**

```
原URL:
http://www.example.com/cb.php?orderid=113208719&ad=%E6%80%A A%E5%85%BD%E5%90%88%E5%94%B1%E5%9B%A2&point=2800&pri ce=10.00&pubid=96ZJ0zfgzes8rwQ25L&ts=1410504843&action_name =%E6%BF%80%E6%B4%BB&action=0&adid=10385&user=BB48B510- 2A45-4CF6-B06B-2A0D146BC2CE&device=- 1&channel=0&pkg=com.yodo1.mysingingmonsters
private_key:940db0e6
```

**经计算后：**

```
sign=a59b6dfb4349299fcc6e89e37b99c976
http://www.example.com/cb.php?orderid=113208719&ad=%E6%80%AA%E5%85%BD%E5%90%88%E5%94%B1%E5%9B%A2&point=2800&price=10.00&pubid=96ZJ0zfgzes8rwQ25L&ts=1410504843&action_name=%E6%BF%80%E6%B4%BB&action=0&adid=10385&user=BB48B510- 2A45-4CF6-B06B-2A0D146BC2CE&device=-1&channel=0&pkg=com.yodo1.mysingingmonsters&sign=a59b6dfb4349299fcc6e89e37b99c976
```

```php
// php实现
<?php
$url = 'http://www.example.com/cb.php?orderid=113208719&ad=%E6%80%AA%E5%85%BD%E5%90%88%E5%94%B1%E5%9B%A2&point= 2800&price=10.00&pubid=96ZJ0zfgzes8rwQ25L&ts=1410504843&acti on_name=%E6%BF%80%E6%B4%BB&action=0&adid=10385&user=BB 48B510-2A45-4CF6-B06B-2A0D146BC2CE&device=- 1&channel=0&pkg=com.yodo1.mysingingmonsters';
$private_key = '940db0e6';
$url .= '&sign=' . getUrlSignature($url, $private_key);
echo $url, "\n";
function getUrlSignature($url, $private_key) {
	$params = array();
	$url_parse = parse_url($url);
	if (isset($url_parse['query'])) {
		$query_arr = explode('&', $url_parse['query']);
		if (!empty($query_arr)) {
			foreach ($query_arr as $p) {
				if (strpos($p, '=') !== false) {
					list($k, $v) = explode('=', $p);
					$params[$k] = urldecode($v);
				}
			}
		}
	}
	return getSignature($params, $private_key);
}

function getSignature($params, $private_key) {
	$signStr = '';
	ksort($params);
	foreach ($params as $k => $v) {
		$signStr .= "{$k}={$v}";
	}
	$signStr .= $private_key;
	return md5($signStr);
}
```

```python
# python实现
import md5
import urlparse
import urllib

def getUrlSignature(url, private_key):
    params = {}
    url_parse = urlparse.urlparse(url)
    if url_parse.query != None:
        query_arr = url_parse.query.split('&')
        if len(query_arr) != 0:
            for para in query_arr:
                if '=' in para:
                    key, value = para.split('=')
                    params[key] = urllib.unquote(value)
        return getSignature(params, private_key)

def getSignature(params, private_key):
    sortedForm = sorted(params.items(), key=lambda param: param[0])
    signStr = ''
    for param in sortedForm:
        signStr += (str(param[0]) + '=' + str(param[1]))
    signStr += str(private_key)
    return md5.new(signStr).hexdigest()

if __name__ == '__main__':
    url = "http://www.example.com/cb.php?orderid=113208719&ad=%E6%80%AA%E5%85%BD%E5%90%88%E5%94%B1%E5%9B%A2&point=2800&price=10.00&pubid=96ZJ0zfgzes8rwQ25L&ts=1410504843&action_name=%E6%BF%80%E6%B4%BB&action=0&adid=10385&user=BB48B510-2A45-4CF6-B06B-2A0D146BC2CE&device=-1&channel=0&pkg=com.yodo1.mysingingmonsters"
    private_key = '940db0e6'
    url += '&sign=' + getUrlSignature(url, private_key)
    print url
```

```java
# java实现

import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;
import java.util.ArrayList;
import java.util.Collection;
import java.util.Collections;
import java.util.HashMap;
import java.util.List;
public class Domb {
	public static String getMD5(String msg) {
		MessageDigest md = null;
		try {
			md = MessageDigest.getInstance("MD5");
		} catch (NoSuchAlgorithmException e) {
			e.printStackTrace();
		}
		md.reset();
		md.update(msg.getBytes());
		byte[] bytes = md.digest();
		String result = "";
		for (byte b : bytes) {
			// byte转换成16进制
			result += String.format("%02x", b);
		}
		return result;
	}
	public static String getParam(String url) {
		int start = url.indexOf("?") + 1;
		String params = url.substring(start);
		return params;
	}
	public static void main(String[] args) {
		String private_key = "940db0e6";
		String url = "http://www.example.com/cb.php?orderid=113208719&ad=%E6%80%AA%E5%85%BD%E5%90%88%E5%94%B1%E5%9B%A2&point=2800"+"&price=10.00&pubid=96ZJ0zfgzes8rwQ25L&ts=1410504843&action_name=%E6%BF%80%E6%B4%BB&action=0&adid=10385"+ "&user=BB48B510-2A45-4CF6-B06B-2A0D146BC2CE&device=-1&channel=0&pkg=com.yodo1.mysingingmonsters";
		String params = getParam(url);
		String[] strs = params.split("&");
		HashMap<String, String> map = new HashMap<String, String>();
		for (String str : strs) {
			String[] param =str.split("=");
			map.put(param[0], param[1]);
		}
		Collection<String> keyset = map.keySet();
		List<String> list = new ArrayList<String>(keyset);
		// 对key键值按字典升序排序
		Collections.sort(list);
		// 排序后的参数 sb
		StringBuilder sb = new StringBuilder();
		for (int i = 0; i < list.size(); i++) {
			sb.append(list.get(i) + "={" + map.get(list.get(i))+"}");
		}
		sb.append("{"+private_key+"}");
		System.err.println(sb.toString());		System.err.println(getMD5(sb.toString()))
	}
}

```




