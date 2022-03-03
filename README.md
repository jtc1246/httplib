# MyHttp

## 1. Usage

(1) http(url:str,Method:str="GET",Header:dict={},Timeout:int=None,ToJson:bool=True,Body:str="",Decode:bool=True)

    url: need to begin with 'http://' or 'https://' / 需要带有 'http://' 或 'https://'
    Timeout: unit ms, default value is 2000ms. You can also set default timeout with setDefaultTimeout() / 单位为毫秒，默认为2000毫秒。可以通过setDefaultTimeout()修改默认值。
    Return value: dict, it has four keys: status, code,header, text, extra
    
    Status:
    -1: 无网络 / No Internet Connection
    -2: 超时 / Timeout
    -3: 域名不存在 / Domian not exists
    -4: 其它问题, 主要是代理服务器设置错误 / Other problem, mainly proxy server error
    1: 不是 UTF-8 编码, text 返回空字符串 / Not UTF-8 encode, the return value of text will be empty str
    2: 不是 Json 格式(在 toJSON=True 的前提下) / Not in Json format (when toJSON=True)
    3: 对方网站不支持https, 但是却使用了https连接, 这种情况会自动切换为http连接, 若此次status不为0, 返回该status, 若为0, 返回3
    The website does not support https. It will change to http automatically in this situation. If the status this time is 0, the status will be 3. If not 0, it will return this status.
    
    Code: Http status code / Http 状态码
    
    header: response header
    
    text: response body
    
    extra: when status is 1, the binary text will be stored in extra; when status is 2, the original text will be stored in extra. In other cases, it will be ''
    status 为 1 时, 会将二进制信息储存在 extra 中, status 为 2 时, 会将原始字符串储存在 extra 中, 其它情况为空字符串。

(2) testIInternet()
    
    Return 0 when there is Internet connection; return -1 when there is no Internet connection. /
    如果有网络连接, 返回 0; 如果没有网络连接, 返回 -1
    
    Default testing url is 'https://apple.com' / 默认测试链接为 'https://apple.com'
    You can change default testing url through setDefaultTestingUrl() / 可通过 setDefaultTestingUrl() 修改默认测试链接
    

    
