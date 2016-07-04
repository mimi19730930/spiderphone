# -*- coding:utf-8 -*-
import urllib
import urllib2
import sys 
import json
from bs4 import BeautifulSoup
import re

'''
url='https://www.baidu.com/s?wd=13264027309'
user_agent = 'Mozilla/4.0 (compatible; MSIE 5.5; Windows NT)'# 将user_agent写入头信息
values = {'name' : 'Michael Foord',
          'location' : 'Northampton',
          'language' : 'Python' }
headers = { 'User-Agent' : user_agent }
data = urllib.urlencode(values)
req = urllib2.Request(url, data, headers)
response = urllib2.urlopen(req)
the_page = response.read()
print the_page
'''

#爬百度程序



#读文件
url='http://www.ip138.com:8080/search.asp?mobile=18187470000&action=mobile'
response=urllib2.urlopen(url)
the_page = response.read()
print the_page


pattern =re.compile(r'<TD\sclass="tdc2" align="center">.*&nbsp;.*</TD>')
result = pattern.findall(the_page)
print result

result = result.replace("\t<TD width=* align=\"center\" class=tdc2>",'')
print result


#爬apk的程序

'''

#!coding=utf-8

import codecs
import urllib
import urllib2
import sys 
import json
from bs4 import BeautifulSoup
reload(sys)
sys.setdefaultencoding('utf-8')

def parse_meizu(argv):
    parse_info = {}
    parse_info['rank'] = -1
    parse_info['list']=[]
    para =  urllib.urlencode({'keyword': argv[1]})

    
#argv[1]=手机卫士
    url= 'http://app.meizu.com/apps/public/search/page?cat_id=1&%s&start=0&max=18'% para
    hdr = {"User-Agent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Ubuntu Chromium/48.0.2564.116 Chrome/48.0.2564.116 Safari/537.36"}
    req = urllib2.Request(url,headers=hdr)
    page=urllib2.urlopen(req).readline()
    dicts=json.loads(page)
    
    for num, item in enumerate(dicts["value"]["list"]):
	count=num+1
        parse_info['list'].append(item["name"])
        if item["package_name"]=="com.qihoo360.mobilesafe":
           parse_info['rank'] = count
           break 
    print json.dumps(parse_info)
    #return json.dumps(parse_info)
    #return parse_info
    

if __name__ == '__main__':
#input is sys augments
    parse_meizu(sys.argv)
'''
#蒋涛的代码


'''
class Spider(object):
    def request(self, url):
        global QUERY_COUNT
        response = ''
        for i in range(3):
            try:
                QUERY_COUNT += 1
                response = urllib2.urlopen(url).read()
                break
            except:
                response = ''
                time.sleep(1)
        return response


        '''

#模拟浏览器
'''
import urllib
import urllib2
url = 'https://www.baidu.com/s?wd=18187470000&rsv_spt=1&rsv_iqid=0xc7fb593200052ff4&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=baiduhome_pg&rsv_enter=0&rsv_t=ef60m8KWT%2F%2Bg3Uf0B8QOp8oznWsOJs6jTwA4csaYO9HRvgxV5%2B4sMutCwv56tFVp%2BD%2BP&oq=1%26lt%3B264027%26lt%3B09&rsv_pq=ecc522560003b894&sug=urllib%20urllib2%20%E5%8C%BA%E5%88%AB&rsv_n=2&rsv_sug3=38&bs=13264027309'
print url
print '\n\n'
user_agent = 'Mozilla/4.0 (compatible; MSIE 5.5; Windows NT)'# 将user_agent写入头信息
values = {'name' : 'Michael Foord',
          'location' : 'Northampton',
          'language' : 'Python' }
headers = { 'User-Agent' : user_agent }
data = urllib.urlencode(values)
req = urllib2.Request(url, data, headers)
response = urllib2.urlopen(req)
the_page = response.read()
print the_page

'''

#百度贴吧的抓取
'''
author__ = 'CQC'
# -*- coding:utf-8 -*-
import urllib
import urllib2
import re
#百度贴吧爬虫类
class BDTB:
#初始化，传入基地址，是否只看楼主的参数
def __init__(self,baseUrl,seeLZ):
self.baseURL = baseUrl
self.seeLZ = '?see_lz='+str(seeLZ)
#传入页码，获取该页帖子的代码
def getPage(self,pageNum):
try:
url = self.baseURL+ self.seeLZ + '&pn=' + str(pageNum)
request = urllib2.Request(url)
response = urllib2.urlopen(request)
print response.read()
return response
except urllib2.URLError, e:
if hasattr(e,"reason"):
print u"连接百度贴吧失败,错误原因",e.reason
return None
baseURL = 'http://tieba.baidu.com/p/3138733512'
bdtb = BDTB(baseURL,1)
bdtb.getPage(1)
'''

#最简单的抓取程序
'''

	1. import urllib2  
	2. response = urllib2.urlopen('http://www.baidu.com/')  
	3. html = response.read()  
	4. print html 

'''


