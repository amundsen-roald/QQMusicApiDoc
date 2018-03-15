# QQMusicApiDoc
本文只限于学习,请勿商用,如果侵权请联系作者删除

### 主页数据接口

#### **简要描述：**

- 获取主页主要信息接口(如：轮播图,热门歌单,新歌首发,新碟首发,排行榜,MV)   
     
#### **请求URL：**  

```html
https://u.y.qq.com/cgi-bin/musicu.fcg
```
#### **请求方式：**
    
* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|comm|Object|{"ct": 24}| 
|category|Object|{"method":"get_hot_category","param":{"qq": ""},"module":"music.web_category_svr"}| 
|recomPlaylist|Object|{"method":"get_hot_recommend","param":{"async": 1,"cmd": 2},"module":"playlist.HotRecommendServer"}|
|playlist|Object|{"method":"get_playlist_by_category","param": {"id":8,"curPage": 1,"size": 40,"order": 5,"titleid": 8},"module": "playlist.PlayListPlazaServer"}|
|new_song|Object|{"module": "QQMusic.MusichallServer","method": "GetNewSong","param": {"type": 2}}|
|new_album|Object|{"module": "QQMusic.MusichallServer",	"method": "GetNewAlbum","param": {"type": 0,"category": "-1","genre": 0,"year": 1,"company": -1,"sort": 1,	"start": 0,	"end": 39}}|
|toplist|Object|{"module": "music.web_toplist_svr","method": "get_toplist_index","param": {}}|
|focus|Object|{"module": "QQMusic.MusichallServer","method": "GetFocus","param": {}}|
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0| 

#### **返回实例**

```html
__jp1(
    {
    category: {},
    focus: {},
    new_album: {},
    new_song: {},
    playlist: {},
    recomPlaylist: {},
    toplist: {},
    code: 0,
    ts: 1521016373239
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|category|Object|热门推荐|
|focus|Object|轮播图|
|new_album|Object|新碟首发|
|new_song|Object|新歌推荐|
|playlist|Object|播放列表|
|recomPlaylist|Object|推荐播放列表|
|toplist|Object|排行榜数据|  


### 获取主页精选电台导航接口

#### **简要描述：**

- 主页精选电台导航接口 
     
#### **请求URL：**  

```html
https://c.y.qq.com/v8/fcg-bin/fcg_v8_radiolist.fcg
```
#### **请求方式：** 
   
* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|hostUin|Number|0| 
|notice|Number|0| 
|needNewCode|Number|0| 
|p|Number|Math.random()| 
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|channel|String|radio| 
|page|String|index| 
|platform|String|yqq| 
|param|String|jsonpCallback| 

#### **返回实例**

```html
__jp2(
    {
        code: 0,
        subcode: 0,
        message: "",
        default: 0,
        data: {
            data: {
                gmgg: null,
                groupList: [
                    {
                        name: "热门",
                        radioList: [],
                        type: "24"
                    }
                    ........
        }
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|groupList|Object|电台分类数据|


### 主页歌单推荐刷新后的数据接口

#### **简要描述：**

- 主页歌单推荐刷新后的数据接口 
     
#### **请求URL：**   

```html
https://u.y.qq.com/cgi-bin/musicu.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|loginUin|Number|0| 
|hostUin|Number|0| 
|needNewCode|Number|0| 
|notice|Number|0| 
|param|Number|需要传入的歌单ID(data中的param就是该值)|
|data|String|{"comm": {"ct": 24 }, "playlist": {"method": "get_playlist_by_category", "param": {"id": param,"curPage": 1,"size": 7,"order": 5,"titleid": param }, "module": "playlist.PlayListPlazaServer"}} param为下面的参数| 
|platform|String|'String'| 
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 

#### **返回实例**

```html
__jp4(
    {
     playlist: {
     data: {
      total: 146,
      v_playlist: []
    },
      code: 0
    },
    code: 0,
    ts: 1521023420398
  }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|total|Number|歌单数量|
|v_playlist|Object|歌单列表|

### 普通电台歌曲接口

#### **简要描述：**    

- 普通电台歌曲接口 
     
#### **请求URL：**    

```html
https://u.y.qq.com/cgi-bin/musicu.fcg
```

#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|loginUin|Number|0| 
|hostUin|Number|0| 
|needNewCode|Number|0| 
|platform|String|yqq| 
|data|String|{'songlist':{'module':'pf.radiosvr','method':'GetRadiosonglist','param':{'id':parseInt(param),'firstplay':1,'num':10}}}| 
|param(此处参数为上面data的param)|Number|param(上面data的param为电台ID)| 

#### **返回实例**

```html
__jp6(
    {
        songlist: {
            data: {
                id: 199,
                track_list: []
            },
            code: 0
        },
        code: 0,
        ts: 1521083162685
    }
)
```  

#### **返回参数说明**  

|参数名|类型|说明|
|---------|--------|-------------|
|track_list|Object|歌曲列表|
|id|Number|电台ID|


### 个性电台歌曲接口

#### **简要描述：**   

- 个性电台歌曲接口 
     
#### **请求URL：**    

```html
https://c.y.qq.com/rcmusic2/fcgi-bin/fcg_guess_youlike_pc.fcg
```

#### **请求方式：**     

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|loginUin|Number|0| 
|hostUin|Number|0| 
|needNewCode|Number|0| 
|cid|Number|703| 
|uin|Number|0| 
|platform|String|yqq| 
|param|String|jsonpCallback| 

#### **返回实例**

```html
__jp6(
    {
        code: 0,
        id: "99",
        msg: "songvec_5songinfo_0_size_5_rc_0_norights_0_black_0",
        orderid: 99,
        ordertype: 10004,
        songlist: [],
        timeout1: 60,
        timeout2: 60,
        title: "5Liq5oCn55S15Y+w",
        type: 10004
    }
)
```  

#### **返回参数说明**   

|参数名|类型|说明|
|---------|--------|-------------|
|songlist|Object|歌曲列表|
|id|Number|电台ID|

### 分类歌单导航接口   

#### **简要描述：**   

- 分类歌单导航接口 
     
#### **请求URL：**   

```html
https://c.y.qq.com/splcloud/fcgi-bin/fcg_get_diss_tag_conf.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|loginUin|Number|0| 
|hostUin|Number|0| 
|needNewCode|Number|0| 
|notice|Number|0| 
|platform|String|yqq| 
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|param|String|jsonpCallback| 

#### **返回实例**

```html
__jp1(
    {
        code: 0,
        subcode: 0,
        message: "",
        default: 0,
        data: {
            categories: []
        }
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|categories|Object|歌单导航|

### 分类歌单接口   

#### **简要描述：**   

- 分类歌单接口(需要代理) 
     
#### **请求URL：**   

```html
https://c.y.qq.com/splcloud/fcgi-bin/fcg_get_diss_by_tag.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|loginUin|Number|0| 
|hostUin|Number|0| 
|notice|Number|0| 
|picmid|Number|1| 
|needNewCode|Number|0| 
|rnd|Number|Math.random()| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|jsonpCallback|String|getPlaylist| 
|inCharset|String|utf8| 
|platform|String|yqq| 
|categoryId|String|param(需要传入的歌单ID)| 
|sin|Number|param(需要传入的歌单数量开始位置)| 
|ein|Number|param(需要传入的歌单数量结束位置)| 

#### **返回实例**

```html
{
    code: 0,
    subcode: 0,
    message: "",
    default: 0,
    data: {
    uin: 0,
        categoryId: 10000000,
        sortId: 5,
        sum: 5865,
        sin: 0,
        ein: 29,
        list: []
    }
}
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|list|Object|歌单列表|
|sin|Number|开始位置|
|ein|Number|结束位置|

### MV列表接口   

#### **简要描述：**   

- MV列表接口
     
#### **请求URL：**   

```html
https://c.y.qq.com/v8/fcg-bin/getmv_by_tag
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|loginUin|Number|0| 
|hostUin|Number|0| 
|needNewCode|Number|0| 
|notice|Number|0| 
|lan|Number|param(MV的ID)| 
|cmd|String|shoubo| 
|platform|String|yqq| 
|outCharset|String|GB2312| 
|inCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 

#### **返回实例**

```html
__jp4(
    {
        code: 0,
        subcode: 0,
        message: "",
        default: 0,
        data: {
            lan: "all",
            mvlist: [],
            name: "",
            sum: 50
        }
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|mvlist|Object|MV数据|

### 对应MV的信息接口   

#### **简要描述：**   

- 对应MV的信息接口
     
#### **请求URL：**   

```html
https://u.y.qq.com/cgi-bin/musicu.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|uin|Number|0| 
|ct|Number|23| 
|cv|Number|0| 
|data|String|{"getMvInfo":{"module":"MvService.MvInfoProServer","method":"GetMvInfoList","param":{"vidlist": param(需要传入的MVID)}}}| 
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0| 

#### **返回实例**

```html
__jp1(
    {
        getMvInfo: {
            data: {
                mvlist: []
            },
            code: 0
        },
        code: 0,
        ts: 1521087066870
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|mvlist|Object|该MV的信息|

### MV播放地址接口   

#### **简要描述：**   

- MV播放地址接口
     
#### **请求URL：**   

```html
https://u.y.qq.com/cgi-bin/musicu.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|uin|Number|0| 
|ct|Number|23| 
|cv|Number|0| 
|data|String|{"getMvUrl":{"module":"Mv.MvDownloadUrlServer","method":"GetMvUrls","param":{"fileid": param(MV信息接口里面的fileid),"filetype":[-1]}}}| 
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0| 

#### **返回实例**

```html
__jp2(
    {
        getMvUrl: {
            data: {
                code: 0,
                data: {
                    1049_M0119900002UINXA31PdmJ1001534167: []
                }
            },
             code: 0
        },
    code: 0,
    ts: 1521087322907
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|1049...|Object|MV播放地址数据|

### 新歌速递点击导航的数据接口   

#### **简要描述：**   

- 新歌速递点击导航的数据接口
     
#### **请求URL：**   

```html
https://u.y.qq.com/cgi-bin/musicu.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|loginUin|Number|0|  
|hostUin|Number|0|  
|needNewCode|Number|0|  
|platform|String|0|  
|data|String|{'comm':{'ct':24},'new_song':{'module':'QQMusic.MusichallServer','method':'GetNewSong','param':{'type':param(导航id)}}}|  
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0|  

#### **返回实例**

```html
__jp6(
    {
        new_song: {
            data: {
                size: 100,
                song_list: [],
                type: 1,
                type_info: []
            },
            code: 0
        },
        code: 0,
        ts: 1521087547190
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|song_list|Array|歌曲信息列表|
|type_info|Array|导航标题|

### 新碟接口   

#### **简要描述：**   

- 新碟接口
     
#### **请求URL：**   

```html
https://u.y.qq.com/cgi-bin/musicu.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|loginUin|Number|0|  
|hostUin|Number|0|  
|platform|String|yqq|  
|needNewCode|Number|0|  
|data|String|{'albumlib':{'method':'get_album_by_tags','param':_param(请看下一个参数),'module':'music.web_album_library'}}|  
|_param|String|{'area':id(导航ID),'sin':页数(显示的数据页数),'company':-1,'genre':-1,'type':-1,'year':-1,'sort':2,'get_tags':1,'num':20,'click_albumid':0}|  
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0|  

#### **返回实例**

```html
__jp7(
    {
        albumlib: {
            data: {
                list: [],
                tags: {},
                total: 28,
                rec: 1,
                sort: 0
            },
            code: 0
        },
        code: 0,
        ts: 1521087939654
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|list|Array|歌曲信息列表|
|tags|Array|导航标题|
|total|Number|信息数量|

### 新碟专辑歌单列表接口   

#### **简要描述：**   

- 新碟专辑歌单列表接口
     
#### **请求URL：**   

```html
https://c.y.qq.com/v8/fcg-bin/fcg_v8_album_info_cp.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|callback|String|albuminfoCallback| 
|albummid|String|albummid(歌单专辑id)| 
|loginUin|Number|0| 
|hostUin|Number|0| 
|platform|String|yqq| 
|needNewCode|Number|0| 
|param|String|jsonpCallback| 
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0|  

#### **返回实例**

```html
__jp7(
    {
        albumlib: {
            data: {
                list: [],
                tags: {},
                total: 28,
                rec: 1,
                sort: 0
            },
            code: 0
        },
        code: 0,
        ts: 1521087939654
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|list|Array|歌曲信息列表|
|tags|Array|导航标题|
|total|Number|信息数量|

### 数字专辑数据接口   

#### **简要描述：**   

- 数字专辑数据接口(需要代理)
     
#### **请求URL：**   

```html
https://u.y.qq.com/cgi-bin/musicu.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|notice|Number|0| 
|uin|Number|0| 
|needNewCode|Number|1| 
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|platform|String|h5| 
|MusicHallDigitalAlbum|Object|{'module':'mall.AlbumPgcMgrServer','method':'GetMallIndexPage','param':{}}| 
|moreAlbum|Object|{'module':'mall.AlbumPgcMgrServer','method':'GetMoreAlbums','param':{'start':0(此处可以传入你想要的专辑页数),'count':9}}| 

#### **返回实例**

```html
MusicHallDigitalAlbum :{data: {,…}, code: 0}
code: 0
moreAlbum:{data: {start: 0, total: 47,…}, code: 0}
ts:1521090120457
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|MusicHallDigitalAlbum|Object|数字专辑轮播图|
|moreAlbum|Object|数字专辑数据|

### 数字专辑歌曲列表接口   

#### **简要描述：**   

- 数字专辑歌单列表接口
     
#### **请求URL：**   

```html
https://c.y.qq.com/v8/fcg-bin/musicmall.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|cmd|String|get_base_sale_info| 
|albumid|String|param(专辑id)| 
|platform|String|h5| 
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0| 
|uin|Number|0| 
|needNewCode|Number|1| 
|songlist|Number|1| 
|desc|Number|1| 
|singerinfo|Number|1| 
|salecount|Number|1| 

#### **返回实例**

```html
__jp3(
    {
        code: 0,
        subcode: 0,
        message: "",
        default: 0,
        data: {}
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|data|Object|数字专辑歌单数据|

### 排行榜数据接口   

#### **简要描述：**   

- 排行榜数据接口
     
#### **请求URL：**   

```html
https://c.y.qq.com/v8/fcg-bin/fcg_myqq_toplist.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|platform|String|h5| 
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0| 
|uin|Number|0| 
|needNewCode|Number|0| 

#### **返回实例**

```html
__jp1(
    {
        code: 0,
        subcode: 0,
        message: "",
        default: 0,
        data: {
            topList: []
        }
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|topList|Array|排行榜数据|

### 排行榜歌曲数据接口   

#### **简要描述：**   

- 排行榜歌曲数据接口
     
#### **请求URL：**   

```html
https://c.y.qq.com/v8/fcg-bin/fcg_v8_toplist_cp.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|platform|String|h5| 
|type|String|top| 
|page|String|detail| 
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0| 
|topid|Number|param(排行榜id)| 
|needNewCode|Number|1| 
|uin|Number|0| 
|tpl|Number|3| 

#### **返回实例**

```html
__jp2(
    {
        code:0
        color:0
        comment_num:73055
        cur_song_num:100
        date:"2018-03-14"
        day_of_year:"73"
        song_begin:0
        songlist:[]
        topinfo: {}
        total_song_num: 100
        update_time: "2018-03-14"
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|songlist|Array|排行榜歌曲列表|
|topinfo|Object|排行榜的一些信息|
|total_song_num|Number|歌曲数量|
|update_time|String|发布时间|

### 热门搜索接口   

#### **简要描述：**   

- 热门搜索接口
     
#### **请求URL：**   

```html
https://c.y.qq.com/splcloud/fcgi-bin/gethotkey.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0|
|uin|Number|0|
|needNewCode|Number|1|
|platform|String|h5|

#### **返回实例**

```html
__jp0(
    {
        code: 0,
        data: {
            hotkey: [],
            special_key: "梦想的声音第二季",
            special_url: "https://y.qq.com/m/act/voiceofdreams2/v3/index.html"
        },
        subcode: 0
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|hotkey|Array|热门搜索|

### 搜索歌曲接口   

#### **简要描述：**   

- 搜索歌曲接口
     
#### **请求URL：**   

```html
https://c.y.qq.com/soso/fcgi-bin/search_for_qq_cp
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|w|String|搜索内容| 
|ie|String|utf-8| 
|remoteplace|String|txt.mqq.all| 
|platform|String|h5| 
|notice|Number|0| 
|p|Number|页数| 
|perpage|Number|每页显示条数| 
|n|Number|每页显示条数| 
|catZhida|Number|zhida(是否直达) ? 1 : 0| 
|zhidaqu|Number|1| 
|t|Number|0| 
|flag|Number|1| 
|sem|Number|1| 
|aggr|Number|0| 
|uin|Number|0| 
|needNewCode|Number|1| 

#### **返回实例**

```html
__jp4(
    {
        code: 0,
        data: {
            keyword: "q",
            priority: 0,
            qc: [ ],
            semantic: {
                curnum: 0,
                curpage: 1,
                list: [ ],
                totalnum: 0
            },
            song: {},
            totaltime: 0,
            zhida: {
                type: 0
            }
        },
        message: "",
        notice: "",
        subcode: 0,
        time: 1521091441,
        tips: ""
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|song|Object|搜索数据|

### 歌手列表接口   

#### **简要描述：**   

- 歌手列表接口
     
#### **请求URL：**   

```html
https://c.y.qq.com/v8/fcg-bin/v8.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|channel|String|singer| 
|page|String|list| 
|key|String|all_all_all| 
|platform|String|yqq| 
|pagesize|Number|100| 
|pagenum|Number|1| 
|hostUin|Number|0| 
|needNewCode|Number|0| 
|notice|Number|0| 

#### **返回实例**

```html
__jp4(
    {
    code: 0
    data:{}
    message:"succ"
    subcode:0
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|data|Object|歌手列表数据|

### 歌手信息列表接口   

#### **简要描述：**   

- 歌手信息列表接口
     
#### **请求URL：**   

```html
https://c.y.qq.com/v8/fcg-bin/fcg_v8_singer_track_cp.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|platform|String|h5page| 
|order|String|listen| 
|from|String|h5| 
|notice|Number|0| 
|uin|Number|0| 
|needNewCode|Number|1| 
|begin|Number|0| 
|singerid|Number|param(歌手ID)| 
|num|Number|param(需要显示的歌曲条数)| 

#### **返回实例**

```html
__jp4(
    {
    code: 0
    data:{}
    message:"succ"
    subcode:0
    }
)
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|data|Object|歌手数据|

### 歌单专辑收藏量接口   

#### **简要描述：**   

- 歌单专辑收藏量接口(需要代理)
     
#### **请求URL：**   

```html
https://c.y.qq.com/3gmusic/fcgi-bin/3g_dir_order_uinlist
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|notice|Number|0| 
|disstid|Number|param(歌单ID)| 

#### **返回实例**

```html
{
    code: 0,
    msg: "",
    diruin: 0,
    dirid: 0,
    sin: 0,
    ein: -1,
    totalnum: 179,
    list: [ ]
}
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|totalnum|Number|歌单收藏量|

### 歌单专辑信息接口   

#### **简要描述：**   

- 歌单专辑信息接口(需要代理)
     
#### **请求URL：**   

```html
https://c.y.qq.com/qzone/fcg-bin/fcg_ucc_getcdinfo_byids_cp.fcg
```
#### **请求方式：**    

* GET
  
#### **参数：**       

|参数名|类型|说明|
|---------|--------|-------------|
|inCharset|String|utf-8| 
|outCharset|String|utf-8| 
|g_tk|String|5239908145| 
|format|String|jsonp| 
|platform|String|h5| 
|new_format|Number|1| 
|needNewCode|Number|1| 
|pic|Number|500| 
|notice|Number|0| 
|type|Number|1| 
|json|Number|1| 
|utf8|Number|1| 
|onlysong|Number|0| 
|nosign|Number|1| 
|song_num|Number|15| 
|disstid|Number|param(歌单ID)| 
|song_begin|Number|param(最大条数)| 
|uin|Number|0| 

#### **返回实例**

```html
{
    code: 0,
    subcode: 0,
    accessed_plaza_cache: 0,
    cdlist: [ ]
}
```  

#### **返回参数说明**

|参数名|类型|说明|
|---------|--------|-------------|
|cdlist|Array|歌单信息|

### 免责声明
本文章的所有内容，包括文字、图片、音频、视频、软件、程序、以及网页版式设计等均在网上搜集。      
本文章提供的内容仅用于个人学习、研究或欣赏。我们不保证内容的正确性。通过使用本站内容随之而来的风险与本站无关
访问者可将本网站提供的内容或服务用于个人学习、研究或欣赏，以及其他非商业性或非盈利性用途，但同时应遵守著作权法及其他相关法律的规定，不得侵犯本网站及相关权利人的合法权利。
本网站内容原作者如不愿意在本网站刊登内容，请及时通知本人，予以删除。


**链接到本站**  
任何网站都可以链接到本站的任何页面。
如果您需要在对少量内容进行引用，请务必在引用该内容的页面添加指向被引用页面的链接。

**保证**
本网站不提供任何形式的保证。所有与使用本站相关的直接风险均由用户承担。本网站提供的所有代码均为实例，并不对性能、适用性、适销性或/及其他方面提供任何保证。
菜鸟教程的内容可能包含不准确性或错误。本人不对本网站及其内容的准确性进行保证。如果您发现本站点及其内容包含错误，请联系我们以便这些错误得到及时的更正：282126990@qq.com

**您的行为**  

当您使用本站点时，说明您已经同意并接受本页面的所有信息。
