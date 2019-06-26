# Thinkphp 5.1 中间件最佳实践
本项目意在指导初次接触中间件的同学更加规范的去使用中间件，帮助初学者更好的理解中间件的用途
```
clone到本地后，cd到本目录，执行composer install即可在本地体验
```
### 中间件的应用场景
```
1、动态加载某些项目配置/常量
2、权限校验
3、变量前置验证
4、跨域OPTIONS请求处理
```
### 类说明
`app\http\middleware\CrossDomain::class`:
```
用于处理跨域请求中的OPTIONS类，方便前端使用ajax跨域
```
`app\http\middleware\Before::class`:
```
全局前置中间件，用于全局拦截http请求并执行相关逻辑
```
`app\common\middleware\AppConst::class`:
```
自定义业务逻辑类，用于动态加载一些项目配置或应用常量，如一些需要通过计算或判断的配置项
```
`app\common\middleware\Auth::class`:
```
自定义权限校验类，一个简单的基于module/controller/action的权限校验的实现
1、当直接访问domain.com/index.php/index/Index/hello时会抛出异常“未通过验证”
2、当访问domain.com/index.php/index/Index/hello/name/thinkphp是为正常访问结果
```
### 注意事项：
1、中间件逻辑类（application/common/middleware目录下）中，只可以通过抛出异常来跳出当前请求