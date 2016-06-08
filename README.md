# Java_CloseableHttpResponse

post:
HttpPost post = new HttpPost(url);
org.apache.http.client.methods.HttpPost

get:
HttpGet get = acceptHtml ? prepareHttpGet(url) : new HttpGet(url);
org.apache.http.client.methods.HttpGet

CloseableHttpClient client = buildHttpClient();
CloseableHttpResponse response = null;
import org.apache.http.client.methods.CloseableHttpResponse;
response = client.execute(get);

	/**
	 * 准备一个{@link HttpGet}实例
	 */
	public static HttpGet prepareHttpGet(String url) {
		HttpGet get = new HttpGet(url);
		get.addHeader("Connection", "keep-alive");
		get.addHeader("Accept", "text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8");
		get.addHeader("User-Agent", "Mozilla/5.0 (Windows NT 6.3; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/42.0.2311.90 Safari/537.36");
		get.addHeader("Accept-Encoding", "gzip, deflate, sdch");
		get.addHeader("Accept-Language", "en-US,en;q=0.8");
		get.addHeader("Cache-Control", "max-age=0");
		try {
			URL _url = new URL(url);
			get.addHeader("Host", _url.getHost());
		} catch (MalformedURLException ex) {
			logger.error("访问url获取对应HTML代码时出错。原因：非法url:{}", url);
			throw Lang.wrapThrow(ex);
		}
		return get;
	}

参见：
httpclient4.4中文教程
https://www.ibm.com/developerworks/cn/opensource/os-httpclient/


