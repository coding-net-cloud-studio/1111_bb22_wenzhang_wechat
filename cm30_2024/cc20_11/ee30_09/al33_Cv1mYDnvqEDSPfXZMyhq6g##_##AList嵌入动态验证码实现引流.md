[原文地址](https://mp.weixin.qq.com/s/Cv1mYDnvqEDSPfXZMyhq6g)

# AList嵌入动态验证码实现引流

**原创** **软件接口平台** [软件接口平台](javascript:void(0);) *2024年08月23日 11:45* *广东*

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/pic9wpyIGagaBFywSec6qBca9RYoLCj8Ira9aNXIgqtMbeiaEUsJszZcAm11icIM0g7u0w43wpk6ynjSmnHibBnQxw/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=10005&wx_lazy=1&wx_co=1)

## 前言

晓杰利用ALists创建了个网盘资源站，想着如何增加个动态验证码进行验证后才能进行访问下载，刚开始利用了固定的验证码，用户可以通过JS代码中进行绕过或直接拿到验证码，经过晓杰多次优化，最终版本支持动态获取验证码，使用了禁止打开控制台校验等方式减少绕过几率，现在分享给大家。

## AList介绍

‌AList是一个支持多种存储、支持网页浏览和WebDAV的文件列表程序‌，AList的功能包括但不限于添加云盘服务，如阿里云盘，通过简单的步骤如点击服务状态按钮运行、添加驱动、获取刷新令牌等操作，实现云盘的挂载和使用。用户还可以通过AList管理自己的网盘，包括添加、删除、浏览和分享文件等。此外，AList还支持将网盘挂载到本地，通过特定的软件如RaiDrive，实现本地访问。 总的来说，AList是一个功能强大的本地网盘管理器，它提供了一个直观的用户界面和丰富的功能，使用户能够方便地管理和访问自己的云存储资源‌

## 技术栈

THINKPHP5.1+Redis+mysql

## 代码

### 前端代码

部分代码参考：[Javascript反调试实现判断用户是否打开了浏览器控制台 ](http://mp.weixin.qq.com/s?__biz=MzU5MzczNDc2Nw==&mid=2247484819&idx=1&sn=6b35222f4a6b863ae64ddc3ead069292&chksm=fe0ab893c97d3185774d1835b9982fe3e7c140b30df6e3b1c8cb232f5f56cf003e30bf7a1e28&scene=21#wechat_redirect)

嵌入位置看下图

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/pic9wpyIGagaBFywSec6qBca9RYoLCj8IdyTYQcBasqjVD2dde9DgS3gLiaicDbDwxvz0Y06IO26sa6ibcicBo1tAibA/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=10005&wx_lazy=1&wx_co=1 "null")

```
<script disable-devtool-auto src='https://cdn.jsdelivr.net/npm/disable-devtool'></script>
<script >
if (checkPwd(localStorage.getItem('pan_password'))) {

} else {
    checkPassword("success", "输入密码进入")
}
function checkPwd(password) {
    if (password === "" || password === null) {
        return false;
    }
    const xhr = new XMLHttpRequest();
    xhr.open("POST", "https://自己的域名/code", false); // 注意这里的第三个参数为 false
    xhr.setRequestHeader("Content-Type", "application/json");
    xhr.onreadystatechange = function () {
        if (xhr.readyState === 4 && xhr.status === 200) {
            const data = JSON.parse(xhr.responseText);
            if (data.code === 200) {
                localStorage.setItem("pan_password", password);
                return true;
            }
        }
        return false;
    };
    xhr.send(JSON.stringify({ "password": password }));
    return xhr.onreadystatechange();
}
function checkPassword(ic, ti) {
    swal({
        title: "免责申明",
        text: "\n本站所展示内容均收集于网络\n仅供本人学习研究及收藏存档\n如有侵犯权益，敬请联系删除\n\n公众号：软件接口平台\n回复【密码】获取密码",
        closeOnConfirm: false,
        closeOnClickOutside: false,
        icon: ic,
        buttons: {
            confirm: {
                text: "确认访问",
                value: "confirm",
                className: "custom-swal-button swal-button--confirm"
            },
            viewAnnouncement: {
                text: "获取密码",
                value: "view_announcement",
                className: "custom-swal-button swal-button--copy"
            },
        },
        content: {
            element: "input",
            attributes: {
                placeholder: "请输入验证码",
                type: "text",
            },
        },
    })
        .then((value) => {
            if (value == '') {
                checkPassword("warning", "请输入正确的密码");
            }else if (value === "view_announcement") {
                // 弹出显示公告内容的提示框
                showAnnouncement();
            } else if (checkPwd(value)) {
                swal("欢迎！", {
                    button: false,
                });
            } else {
                checkPassword("warning", "密码错误");
            }
        });
    function showAnnouncement() {
        swal({
            title: '软件接口平台',
            text: "扫码下面二维码或关注\n“软件接口平台”公众号\n回复“密码”获取最新验证码",
            buttons: {
                cancel: {
                    text: "关闭",
                    value: false,
                    visible: true,
                },
            },
            icon: "info",
            content: {
                element: "img",
                attributes: {
                    src: "https://zhanzhang.sogou.com/api/wxapp/file/link?uuid=07e7299ffd299325a6e383897c23eb6d.jpg", // 这里用占位图代替实际图片
                },
            },
        }).then((value) => {
            checkPassword("success", "输入密码进入");
        });
    }

}
document.addEventListener('keydown', function(event) {
    // 检查 F12 键
    if (event.key === 'F12') {
        event.preventDefault();
    }
    // 检查 Ctrl + Shift + I 组合键
    if (event.ctrlKey && event.shiftKey && event.key === 'i') {
        event.preventDefault();
    }
    // 检查 Ctrl + Shift + J 组合键
    if (event.ctrlKey && event.shiftKey && event.key === 'j') {
        event.preventDefault();
    }
    // 检查 Ctrl + Shift + C 组合键
    if (event.ctrlKey && event.shiftKey && event.key === 'c') {
        event.preventDefault();
    }
});
document.addEventListener('contextmenu', function(event) {
    event.preventDefault();
});
var ConsoleManager={
    onOpen(){
        location.href="https://www.java.pet";
    },
    onClose(){
    },
    init(){
        var self = this;
        var x = document.createElement('div');
        var isOpening = false,isOpened=false;
        Object.defineProperty(x, 'id', {
            get(){
                if(!isOpening){
                    self.onOpen();
                    isOpening=true;
                }
                isOpened=true;
            }
        });
        setInterval(function(){
            isOpened=false;
            console.info(x);
            console.clear();
            if(!isOpened && isOpening){
                self.onClose();
                isOpening=false;
            }
        },200)
    }
}

ConsoleManager.onOpen = function(){
    location.href="https://www.java.pet";
}
ConsoleManager.init();

DisableDevtool({
    ondevtoolopen: (type) => {
        const info = 'devtool opened!; type =' + type;
        },
})
</script>
```

### 后端代码

Code.php 校验 和获取 接口

```
<?php

namespace app\api\controller;

use think\cache\driver\Redis;
use tools\Tools;

class Code
{
//用于公众号或WXQQ机器人调用
 public function getCode(){
       
        $redis= new Redis();
        $yzmRedisKey ='GZHsoftwareinterface'.date("Y-m-d");
        if(!$redis->has($yzmRedisKey)){
            $times = 86400;
            $yzmCode=ToolsModel::random_str(6,1);
            $redis->set($yzmRedisKey,$yzmCode,$times);

        }
        $yzmCode = $redis->get($yzmRedisKey);
        return $yzmCode;
    }
    //用于网页调用
    public function index()
    {
        if (request()->isPost()){
            $data = json_decode(file_get_contents('php://input'),true);
            isset($data['password'])?$password = $data['password']:exit(json_encode(array('code'=>0,'msg'=>'验证码不能为空')));
            $redis = new Redis();
            $yzmRedisKey = 'GZHsoftwareinterface'.date("Y-m-d");//存储有效验证码
            $redisKey = 'GZHyzms'.Tools::GetIp().date("Y-m-d");//存储同一个获取次数 防止恶意扫描
            $sd = $redis->get($redisKey);
            if (empty($sd)){
                $sd =1;
                $redis->set($redisKey,$sd,86400);
            }else{
                $redis->inc($redisKey);
            }
            if ($sd>100){
                $data = array(
                    'code'=>0,
                    'msg'=>'今日验证码次数已超过100次',
                );
                return json_encode($data);
            }
            $yzmCode = $redis->get($yzmRedisKey);
            if(empty($yzmCode)){
                $yzmCode = Tools::random_str(6,1);
                $redis->set($yzmRedisKey,$yzmCode,86400);
            }
            if ($yzmCode==$password && !empty($password)){
                $data = array(
                    'code'=>200,
                    'msg'=>'验证码正确',
                );
                return json_encode($data);
            }else{
                $data = array(
                    'code'=>0,
                    'msg'=>'验证码错误',
                );
                return json_encode($data);
            }
        }
        header("HTTP/1.1 403 FORBIDDEN");
        header("Status: 403 FORBIDDEN");
        throw new \think\exception\HttpException(403, '~~~非法请求~~~');
        return;
    }
}
```

## 示例网址

[https://pan.metanetdisk.com/](https://pan.metanetdisk.com/)![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/pic9wpyIGagaBFywSec6qBca9RYoLCj8IIjCtE6eBFqOicuCZLg2dLHzeibfWbmsa0GdFuHN3E6vfXaDJaY4STmXw/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=10005&wx_lazy=1&wx_co=1 "null")

## 本人作者

Soujer

**置顶 软件接口平台 公众号**

**每天外卖红包领不停![图片](https://mmbiz.qpic.cn/mmbiz_png/k572XescDqrWOCXOXxSWibAjAtEdCy428fDia5wbHPDQdYZNpcONH1VAQ7ibmmTG5JM06bGgf8ic1ex0ge1BZiaEzPQ/640?wx_fmt=other&wxfrom=10005&wx_lazy=1&wx_co=1&tp=webp)**

○

**长按扫码关注**

○

![图片](https://mmbiz.qpic.cn/mmbiz_png/pic9wpyIGagbKbfdvSGyzVEbiaAoJOSicqvCKJSGeTxNtZjFfvicRrhJbicjPiannMLWewlMT21IeucfMSXKiaaGZFX1g/640?wx_fmt=other&wxfrom=10005&wx_lazy=1&wx_co=1&tp=webp "undefined")

![图片](https://mmbiz.qpic.cn/mmbiz_png/pic9wpyIGagbKbfdvSGyzVEbiaAoJOSicqvTt2tl9Le0x7PkQiaOFyQWY6EC0aIUQG6yNb2bzLLq7TM6nz8Y6XbicGg/640?wx_fmt=other&wxfrom=10005&wx_lazy=1&wx_co=1&tp=webp)

**记得这是一个有深度的公众号**

![图片](https://mmbiz.qpic.cn/mmbiz_png/pic9wpyIGagbKbfdvSGyzVEbiaAoJOSicqvt4RKvoyibVv3GdfHa3jAm9RwJBQlgicsDosWfwSmoCiblc4AcReT6h5ZA/640?wx_fmt=other&wxfrom=10005&wx_lazy=1&wx_co=1&tp=webp)
