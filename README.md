# Good-text-Share
These share data are from my usual work and learning，hoping to help you，If you like you can star

最近在公司使用angular写后台系统的时候时不时的总会发现一些坑，在此分享一些关于数据传递会碰到的一些小问题，不定时更新。

在使用自定义指令directive的时候，当所请求的数据是通过后台传输过来的话，在指令调用出来对象的值是空的。
所以针对这种情况的话，我的建议是在调用函数当中写一个监听，以下是案例代码。

  directive.link = function ($scope, element, attributes) {
            var typeName = "";
            $scope.$watch('obj', function (newVale, oldVale) {
                if (newVale) {
                    switch ($scope.obj) {
                        //系统设置
                        case 10001: typeName = "邮件模板缩略图"; break;
                            //会员管理模块
                        case 22002: typeName = "会员头像"; break;
                        case 22003: typeName = "公司Logo缩略图"; break;
                        case 22004: typeName = "企业证书缩略图"; break;
                        case 22005: typeName = "角色缩略图"; break;
                        case 22006: typeName = "营业执照缩略图"; break;
                        case 22001: typeName = "会员等级图标"; break;
                            //资讯信息模块
                        case 23001: typeName = "资讯信息缩略图"; break;
                        case 23003: typeName = "资讯分类缩略图"; break;
                        case 23006: typeName = "资讯子信息缩略图"; break;
                        case 23008: typeName = "展会基本分类"; break;
                        case 23009: typeName = "资讯信息图片缩略图"; break;
                            //论坛管理模块
                        case 24001: typeName = "论坛信息缩略图"; break;
                        case 24002: typeName = "论坛版块缩略图"; break;
                            //商业信息管理模块
                        case 27001: typeName = "商业信息缩略图"; break;
                            //站中站
                        case 28001: typeName = "站中站模板缩略图"; break;
                        case 28003: typeName = "站中站友情链接缩略图"; break;
                        case 28004: typeName = "站中站导航菜单缩略图"; break;
                            //下载信息管理模块
                        case 30001: typeName = "下载信息缩略图"; break;
                        case 30002: typeName = "下载分类缩略图"; break;
                        case 30003: typeName = "下载信息标签图"; break;
                            //产品信息管理模块
                        case 32001: typeName = "产品分类缩略图"; break;
                        case 32002: typeName = "产品缩略图"; break;
                        case 32004: typeName = "子产品缩略图"; break;
                    }
                    $scope.values = typeName;
                }
            })           
        };
        directive.template = "{{values}}";
