## 模块开发流程

目录

- 创建/维护
- 权限
- 继承的基类说明
- 开发

### 创建/维护

进入后台 - 系统管理 - 系统功能 - 应用管理 - 设计新插件

> 创建成功后会在 根目录的 addons 目录下生成插件文件

### 权限

权限请在创建的模块下的 AddonConfig 文件内手动填写，安装后会自动注册进系统权限管理

例如：

```
    /**
     * 可授权权限
     *
     * 例子：
     *  array(
     *      'index/index' => '首页',
     *      'index/edit' => '首页编辑',
     *  )
     * @var array
     */
    public $authItem = [
        'curd/index' => 'Curd首页',
        'curd/edit' => 'Curd编辑',
    ];
```

查看设置权限：系统管理->用户权限->角色管理->创建/编辑

### 继承的基类说明

##### api

> 注意：开发Api的时候能使用RESTful的基类，但是不受路由规则管辖

- 无需登录的控制器请全部继承 `api\controllers\OffAuthController`,注意Curd是改过的，不想用系统的Curd可直接继承 `yii\rest\ActiveController`
- 需登录的控制器请全部继承 `api\controllers\OnAuthController`,注意Curd是改过的，不想用系统的Curd可直接继承 `api\controllers\ActiveController`

##### 其他(wechat/backend/frontend)

控制器需统一继承 `common\components\AddonsBaseController`  

### 开发

完全可以根据Yii2正常的开发流程去开发对应的控制器、视图、插件内的应用
