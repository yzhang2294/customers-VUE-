# customers

> 使用 Vue 框架搭建的用户管理系统。

```bash
 1.使用 json-server，连接本地接口读取 json 格式的用户数据。
2.可以对数据进行增删查改。
3.不同的操作界面封装成不同 vue 组件，通过 vue-router 进行跳转
4.界面之间可以进行通信：如删除用户后会跳转到主页并显示\*\*用户已被删除
```

> 主页
> ![image](https://github.com/yzhang2294/customers-VUE-/raw/master/gitImage/mian.png)

> 搜索用户
> ![image](https://github.com/yzhang2294/customers-VUE-/raw/master/gitImage/search.png)

> 点击右上角添加用户，路由跳转到添加用户界面
> ![image](https://github.com/yzhang2294/customers-VUE-/raw/master/gitImage/add.png)

> 点击详情按钮，路由跳转到对应的用户详情界面，可以删除和修改
> ![image](https://github.com/yzhang2294/customers-VUE-/raw/master/gitImage/info.png)

> 信息提示：删除、新增、修改用户完成后，由路由跳转回首页并显示操作信息
> ![image](https://github.com/yzhang2294/customers-VUE-/raw/master/gitImage/alert.png)

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
