## urls
```py
from urllib.parse import quote
import numpy as np
import pandas as pd
import requests
import json
header={
    'Content-Type': 'application/x-www-form-urlencoded; charset=utf-8',
"Origin":"https://search.5sing.kugou.com",
"User-Agent":"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.82 Safari/537.36",
"Referer":"http://search.5sing.kugou.com/home/index?keyword=小酒窝",
"Cookie":''
}
header={
    'Content-Type': 'application/x-www-form-urlencoded; charset=utf-8',
"Origin":"https://space.bilibili.com",
"User-Agent":"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.82 Safari/537.36",
"Referer":"https://space.bilibili.com/38407276/video?tid=3&page=2&keyword=&order=pubdate",
}

ar=[]
for i in range(1,7):
    res = requests.request("get",url="https://api.bilibili.com/x/space/arc/search?mid=38407276&ps=30&tid=3&pn=1&keyword=&order=pubdate&jsonp=jsonp", 
                   headers=header)
    ar.append(pd.DataFrame(json.loads(res.text)['data']['list']['vlist'])['bvid'])
df=pd.concat(ar).reset_index(drop=True)
df='you-get https://www.bilibili.com/video/'+df

df.to_csv('df.csv',index=False,header=False)

for d in dd.iloc[0]:
    ar=[]
    for i in range(1,11):
        d=quote(d.encode('utf-8'))
        url="http://search.5sing.kugou.com/home/json?keyword={0}&sort=1&page={1}&filter=0&type=0".format(d,i)
        res = requests.request("get",url, headers=header)
        ar.append(pd.DataFrame(json.loads(res.text)['list']))
    pd.concat(ar).to_csv(d+'.csv')
```
## list
```pl
while(<DATA>){chomp;
for $i(1..10){s/ /%20/;
print "curl 'http://search.5sing.kugou.com/home/json?keyword=$_&sort=1&page=$i&filter=0&type=0'\nsleep 1\n"
}
}
__DATA__
```
## parse
```pl
#!/usr/bin/perl

use strict;
use warnings;

binmode(STDOUT, ':utf8');

while (<>) {
    s/\\u([0-9a-fA-F]{4})/chr(hex($1))/eg;
    print;
}
```
## list
```pl
while(<>){chomp;
$k=$1 if /"keyword\\">(\S+?)</;
while(/"songId":(\d+)/g){
print "$1\t$k\n"
}
}
```
## js
```js
let xhr = new XMLHttpRequest();
xhr.onreadystatechange = function(){
    if (this.readyState == 4 && this.status == 200) {
        console.log(this.responseText);
    }
};
xhr.open("POST", url, true);
xhr.setRequestHeader("Content-type", "application/json");
xhr.send(JSON.stringify(d));

function sleep(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

$(".download.action_down").each(async function(){
$(this).click()
await new Promise(r => setTimeout(r, 2000));
})

ar=[]
$("a.btn").not('.qq, .wechat, .weibo, .kugou').each(function(){
   ar.push($(this).attr("href"));
})
await new Promise(r => setTimeout(r, 2000));
ar = ar.filter((x, i, a) => a.indexOf(x) == i)
```
## aichagu/gongshi
```sh
for f in *;do perl -ne '$b=1 if /<h1>/;$b=0 if /^\r\n/;if ($b){s/<.*?>//g;s/&gt;/>/g;s/&lt;/</g;s/&nbsp;/ /g;s/&amp;/&/g;print}' $f > $f.txt;done
perl -ne 's/\r\n//;next if /^2020/ or /^{.*}\s*$/;$s.="$_ ";if (/^\s+/ or /;\s*$/){print $s,"\n";$s=""}' all > all.1
perl -ne 'next unless /:/ or /^\s+/;s/,\s*\w*(STICK|POINT|LINE|COLOR|NODRAW)\w*//g;print' all.1 > all.txt
sed -i 's/  \+/ /g;s/; *$/;/' all.txt
perl -ne 'chomp;next if /^2020\/\d/ or /^\s+$/;if(/^\t+(\S+)/){$k=$1;if ($i%50==0){$d++;close O;open(O,">d$d.txt")}print O $s,"ENTERLONG: ;\r\nEXITLONG: ;\r\n" unless $s=~/zig/i or /peak/i or /trough/i;$i++;$s="{$k}\r\n";next}$s.="$_\r\n"' all.txt
```
