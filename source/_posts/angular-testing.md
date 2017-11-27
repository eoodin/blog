---
title: Angular测试
date: 2017-10-27 22:40:00
categories:
- web
---
# Angular测试四大件

今年以来Angular变化很多，比较大的一个变化就是文档的质量相比去年有了很大的提高，因此如果是需要系统地学习Angular测试，看官网的帮助是一个最好的选择，它还在不断地更新。这里主要是为了记录一下在为Shelf添加测试的过程和遇到的问题，以备参考。

这里说的是测试，官方文档就是说的测试，包含了单元测试和端到端测试，其中单元测试需要用到的东西有：

- Karma 这是JavaScript项目常用的单元测试的运行器

- Jasmine 这是JavaScript项目广泛采用的单元测试框架，它是一个BDD的框架

- Angular测试工具集　这是真正Angular提供用于帮助测试的东西


# 准备

Angular 今年在 @angular/cli　上投入很多，现在官网很多教程都已经采用cli来说明，Shelf也在很早以前就使用cli来管理代码，淌过不少坑。
基于CLI的测试准备也相当简单，如果是ng new出来的项目，自动就设置好了，只需要在app/src下写*.spec.ts就可以跑了。

# 测试类型

Angular 把测试分为两类，一类是跟Angular机制无关的，比如Service, Pipe，这类被测对象应该是简单的TypeScript的对象，我们只需按照一般的测试写就行了不需要用到上面列出的Angular测试工具集。另一类就比较麻烦了，比如Directive, Component这类，因为它们的测试点往往依赖Angular的Change Detection，HTML渲染等。

## Angular测试工具集

测试工具集提供这些功能

**TestBed**

用于创建一个用于测试的NgModule环境

**ComponentFixture**

使用TestBed创建出来的被测对象的封装
- .componentInstance即被测对象，　
- .debugElement提供一个操作被测对象的接口，比如检查元素状态
- .debugElement.injector.get(UserService)获取injector
- .detectChanges可以手动检测变动，如果不调用变动不会有效果
- .compileCompoennts　配合async可以正常处理外部template和style的component


**ComponentFixtureAutoDetect**

配置TestBed时将之放入provider里，除直接修改component field不生效外，可以实现自动Change Detection（因为它hook timer等async调用）

**async** 把传beforeEach setup包上async，框架会把它测试放入一个zone，异步执行后续的boforeEach和测试


# Angular模块测试

## 处理依赖

<pre>
 TestBed.configureTestingModule({
    declarations: [ WelcomeComponent ],
 // providers:    [ UserService ]  // NO! Don't provide the real service!
                                   // Provide a test-double instead
    providers:    [ {provide: UserService, useValue: userServiceStub } ]
 });
</pre>

## 访问依赖

被注入的依赖是一个clone，访问useValue的直接引用没有效果


TBC..




