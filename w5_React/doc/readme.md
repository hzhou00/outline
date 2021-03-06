# React

## day6-1

### 面试题
* hash路由的原理
    * hashchange
* 如何路由懒加载
    * 用于优化，可以减少打包文件大小，提升首次加载速度
    * 原理：组件动态加载（也叫按需加载）
* 常用的http状态码
    * 200+
        * 200   成功
    * 300+
        * 301   永久重定向
        * 302   临时重定向
        * 304   缓存
    * 400+
        * 401   无权限，需要登录才可访问
        * 402   未支付无权限
        * 403   禁止访问，无权限
        * 404   找不到资源
    * 500+
        * 500   服务器错误

### 知识点

* 前端三大框架
    * Angular
    * React
    * Vue
        * 指令
        * 组件

* 版本概念
    * cjs   commonJS
    * umd   Universal Module Definition， commonJS/amd/cmd/全局引入
    * es    esModule

* 创建虚拟节点：React.createElement(type,prop,children)
* 渲染虚拟DOM：ReactDOM.render(VirtualDOM,target)
* JSX
    * 浏览器不支持，需要使用babel工具进行编译成浏览器支持的代码
    * babel的作用：JSX -> React.createElement()
    * JSX规范
        * js关键字不能使用：
            * class -> className
            * for   -> htmlFor
        * 属性使用驼峰写法
            * autofous  -> autoFocus
            * tabindex  -> tabIndex
            * onkeyup   -> onKeyUp
        * 必须结束标签
        * 在JSX中使用js代码，必须写到花括号中{}
        * style 属性的值接收一个对象，css 的属性必须为驼峰写法

* 组件化开发
    > 简单理解为：创建了一个html标签
    * 解决的问题
        * 复用
        * 维护
    * 定义组件
        * 函数组件
            必须有返回值
        * 类组件
            必须包含render方法，且render方法必须有返回值
    * 使用组件

* Webpack
    * gulp: 基于任务的构建工具
        * 创建gulpfile.js文件
        * 创建任务
            * 在任务中逐步编写规则实现不同的功能
        * 运行任务
    * webpack: 基于配置的构建工具
        * 在项目跟目录下创建一个`webpack.config.js`，所有的配置规则都写到该文件中，文件内部返回一个commonJS模块

## day6-2

### 面试题
* webpack常用配置
* 局部样式的原理
    > 添加scoped
    1. 给当前组件的元素添加data-v-[hash]
    2. css属性选择器: .el-button[data-v-xxxx]{}

    * 在局部样式中修改第三方组件样式
        * /deep/
        * >>>
        * 添加一个不带scoped的style
* 单页面应用的原理
    * hash
    * history
        * state
        * pushState()
        * replaceState()
* 有两条分布不均匀的绳子，每条烧完需要1个小时，如何确定15分钟

### 复习
* webpack与gulp的区别
    * gulp：基于任务的构建工具
    * webpack：基于配置的构建工具
* webpack的常用配置
    > 手动搭建基于webpack的React开发环境
    * entry     入口
    * devServer 开发服务器
        > webpack-dev-server
    * loader    加载器
        > module.rules
        * test  匹配规则（正则）
        * use   使用加载器
    * plugins   插件
        * html-webpack-plugin
* webpack的工作原理
    > 从入口开始，分析整个项目依赖，并使用加载器/插件编译相应的代码，并构建出一个或多个文件

* React
    * 特点
    * JSX
        * JSX -> React.createElement()
    * 组件
        * 定义
            * 函数组件
            * 类组件
                * 继承自React.Component
                * render
        * 使用
### 知识点
* 函数组件（无状态组件、UI组件） 推荐使用
* 类组件（状态组件、容器组件）
* 数据渲染
    * 显示数据：{}
    * 列表循环
        * map
        * filter
        * ...
    * 事件绑定
        * 改变this指向
            * bind: bind改变函数this指向只在第一次生效
            * 传参
        * event对象
            > 事件处理函数最后一个参数
    * 组件状态：state
        * 修改状态: this.setState()
            > 规则：创建新的数据并覆盖
    * refs
        > ref属性用在html元素上，得到元素节点；ref属性用在组件上，得到组件实例
        * 回调函数（推荐）
        * React.createRef()
            > 获取方式: xxx.current
        * 受控组件与非受控组件
            * 受控组件：把组件的状态与表单元素进行绑定
            * 非受控组件：不使用组件的状态操作表单元素

* 状态提升
    > 把数据提升到多个组件共同的父级

* 组件通讯
    * 父->子：props
        * 父组件操作：定义属性并传递数据
        * 子组件
            * 函数组件：函数的第一个参数为props对象
            * 类组件：this.props

## day6-3

### 面试题
* 移动端适配
    * 自适应布局
        * 百分比布局
        * 弹性盒布局
        * rem布局
        * vw/vh/vmin/vmax
        * ...
    * 响应式布局
        * media query 媒体查询
* arguments
    * callee    在严格模式下无法使用
    ```js
        function show(){
            // arguments.callee()
            // show()
        }
        setTimeout(function get(){
            // 这里的代码执行超过1s
            // setTimeout(arguments.callee,1000)
            setTimeout(get,1000)
        },1000)

        setInterval(function(){
            // 这里的代码执行超过1s
        },1000);

        //get()
    ```

### 复习
* 组件的使用
    * 什么时候用函数组件，什么时候用类组件
        * 函数组件（无状态组件, UI组件）
        * 类组件（状态组件，容器组件）
            * state
    * todolist
* 数据的挂载方式
    * 数据绑定：
        * 单向：{}
        * 双向：
            * value
            * onChange事件
    * 列表循环
        * map()
        * filter()
        * key
    * 事件绑定
        * event: 事件处理函数的最后一个参数
        * this指向：
            * bind(target,...args): 只在第一次生效
        * 传参
    * refs
        * 回调函数
        * React.createRef()
        ```js
            // 字符串
            // 获取：this.refs.xxx（不推荐）
            <input ref="xxx"> 

            // 回调函数（推荐）
            const callback = function(el){
                this.keyword = el
            }
            <input ref={callback} /> 
            
            // React.createRef()
            // 获取：myref.current
            const myref = React.createRef()
            <input ref={myref} /> 
        ```
* 受控组件与非受控组件
    * 受控组件：把state绑定到表单元素的value属性，并绑定onChange事件
    * 非受控组件：表单元素不受state/props控制，通过节点方式获取
        * 原生
        * refs
* state
    > 组件的状态
    * 读取：this.state.xxx
    * 修改：this.setState()
        > 原则：创建新数据并覆盖
* props

### 知识点

* 组件通讯
    * 父子通讯：props
        * 父组件操作：定义属性并传递数据
        * 子组件操作
            * 函数组件：函数的第一个参数
            * 类组件：this.props
    * 子父通讯：把父组件的方法传到子组件去执行并传递参数
        * 父组件操作：定义方法并通过props传入子组件
            > 数据在哪里，就把方法定义在哪里
        * 子组件操作：执行方法并传递参数
    * 多层次组件通讯
        * 逐层传递
        * Context
            1. 创建Contenxt
            2. 父组件操作：Provider共享数据
                * value
            3. 子组件操作：接收数据
                * 函数组件：Consumer
                * 类组件：
                    * Consumer
                    * this.context
    * 组件内容通讯: props.children
        
* 自定义方法使用箭头函数
    > @babel/plugin-proposal-class-properties

* render props
    > 使用一个值为函数的 prop 共享代码的简单技术（类似于 Vue 中的作用域插槽）
* props类型校验：propTypes
    > 一般用于组件编写

    ```js
        {
            <mycomponent :index="10" age="" />
            props:{
                // index:Number,
                // index: [String, Number],
                index:{
                    type:[String, Number],
                    // default:0,
                    required: true
                }
            }
        }
    ```
* props默认值：defaultProps
    > 一般用于组件编写

## day6-4

### 面试题
* 节流与防抖的理解
    * 节流：执行第一次，忽略后面所有操作
    * 防抖：执行最后一次，忽略前面所有操作
* 如何进行项目自测
    * 测试用例
    ```js
        function sum(a,b){
            return a+b;
        }
    ```
* 如何修复紧急线上bug
    * hotfix  
    * release
        * 封版
    * bug修复流程
        * 需求文档（产品经理）
        * 项目管理系统
            * bug管理
                * 添加bug
                    * 截图/视频
                    * 文字说明：如何重现bug
                * 取消bug
                * 修改bug状态
                    * new
                    * open
                    * fixed
                    * close
                    * reopen
                * 指派（分配）
* json数据格式的规范
    * 规范
        * 属性名必须使用双引号
        * 字符串必须使用双引号
        * 最后不允许多余逗号
        * 不允许有注释
        * 属性值值允许为以下类型
            * Number
            * String
            * Boolean
            * null
            * Array
            * Object
    * json对象
    * json字符串
    * 转换
        * JSON.stringify()  返回json字符串
        * JSON.parse()      返回json对象
    ```js
        let user1 = {name:'jingjign',password:1234} // js对象
        let user2 = {
            "username":"jingjing", // 用户名
            "password":1234
        } 
        let user3 = "{\"username\":\"jingjing\",\"password\":1234,}" // json字符串
    ```
* html语义化标签的理解
    * div+css（table）
    * 合适的位置使用合适标签
    * SEO
* 组件化化与模块化
    * AMD/CMD   requre.js/sea.js
    * CommonJS  nodejs
    * ES Module  ECMAScript
    * jquery如何实现模块化
        * umd 

### 复习
* 组件通讯
    * 父->子：props
        * props类型校验: prop-types
            * 必填参数
            * 数据类型
        * 默认值：defaultProps静态属性
    * 子->父：props
        > 把父组件的方法通过props传到自组件中执行
        * 规则：谁的数据谁修改
    * 兄弟->兄弟
        > 状态提升：把数据提升到他们共同的父级
    * 多层次组件通讯
        * 逐层转递
        * context（配合模块化实现）
            1. 创建context：
                > const MyContext = React.createContext(defaultValue)
            2. 父组件在context上共享数据
                > <MyContext.Provider value={共享数据}>子组件</MyContext.Provider>
            3. 子组件获取数据
                * 函数组件
                    * <MyContext.Consumer>{(value)=>{}}</MyContext.Consumer>
                * 类组件
                    * this.context
                        > 设置静态属性：contextType
                    * <MyContext.Consumer>{(value)=>{}}</MyContext.Consumer>

### 知识点

* 组件生命周（只适用于类组件）
    > 组件的生命周期分成四个状态：
    * Initial: 初始化阶段
        * constructor
            * 初始化state
    * Mounting：挂载阶段
        * componentWillMount
        * componentDidMount
    * Updating：更新阶段
        * componentWillUpdate
        * componentDidUpdate
        > 所谓的更新视图就是重新执行一次render方法
    * Unmounting：卸载阶段
        * componentWillUnmount
    
    * 特殊生命周期函数
        * componentWillReceiveProps
        * shouldComponentUpdate
            * React.PureComponent：实现了shouldComponentUpdate的React.Component
* 组件的自动刷新条件
    * state有修改
    * props有修改
    * 父组件刷新
* 强制刷新（不推荐）：this.forceUpdate()

#### React-Router
> 万物皆组件
* 路由类型
    * HashRouter
    * BrowserRouter
* 路由渲染
    * Switch
    * Route
    * Redirect

* css加载器
    * css-loader
    * style-loader

## day6-5

### 项目介绍
* 项目是做什么的
* 项目有什么特点
* 你负责的部分
* 遇到的问题及解决方案
    * 技术
    * 团队协作

### 面试题
* 前端如何做信息攻防
    * xss: Cross Site Scripting
        * 利用服务器对客户端的信任进行攻击
        * 防守：
            * 对用户输入进行过滤
            * 对输出进行处理
                * v-html
                * v-text
    * csrf: Cross-site request forgery
        * 利用用户对服务器的信任进行攻击
        * icbc.com -> lcbc.com
    * 接口权限管理
    * 防爬

### 复习
* 生命周期与钩子函数
    * 初始化阶段
        * constructor
            * state
            * propTypes
            * defaultProps
    * 挂载阶段
        * componentWillMount（不推荐）
        * compoonetDidMount
    * 更新阶段
        * componentWillUpdate(nextProps,nextState) 不推荐
        * componentDidUpdate(prevProp,prevState)
            * 当前值：this.props/this.state
    * 卸载阶段
        * componentWillUnmount
            * 取消ajax请求
            * 清除定时器
            * ...
    * 特殊钩子函数
        * componentWillReceiveProps(nextProps) 不推荐
        * shouldComponentUpdate(nextProps, nextState)
            * 必须要返回boolean
                * true 允许组件更新
                * false 不允许组件更新
* React性能优化
    * 组件刷新条件
        * state有修改
        * props有修改
        * 父组件刷新
        * 强制刷新：this.forceUpdate
    * 优化方案
        * shouldComponentUpdate
        * PureComponent
* React路由
    > 一切皆组件
    * 路由类型
        > 使用react路由一定要先指定路由类型
        * HashRouter
        * BrowserRouter
    * 路由渲染
        * Route
            * path
            * component
            * exact
            * render
        * Redirect
            * from
            * to
            * exact
        * Switch
    * 路由导航
        * 声明式导航
            * Link
                * to
            * NavLink
                * activeStyle
                * activeClassName
                * to
        * 编程式导航
### 知识点
* 编程式导航
    > 利用js实现跳转，编程式导航的三大对象：history,location,match
    ```js
        //this.$router.push()/this.$router.replace
    ```
    * history.push()
    * history.replace()
* 获取history对象
    * 利用<Route/>渲染的组件
        > 组件只要是通过`<Route component={组件}/>`方式渲染的组件，history对象自动传入组件的props（this.props.history访问）
    * withRouter高阶组件（推荐）
        > 高阶组件不是一个React组件，而是一个函数，包装函数

* 高阶组件HOC
    * 特点
        * 高阶组件是一个**纯函数**
            > 纯函数：不对传入的参数进行修改，固定的输入有固定的输出
            ```js
                // 纯函数
                function sum(a,b){
                    return a+b;
                }
                sum(1,2);//3 
                sum(1,2);//3 

                // 非纯函数
                function randomNumber(min,max){
                    return parseInt(Math.random()*(max-min+1)) + min
                }

                // 纯函数
                const arr = [10,11,20,21,30,31]
                function filter(arr){
                    return arr.filter(item=>item%5===0);
                }

                filter(arr);// [10,20,30]
                filter(arr);// [10,20,30]
            ```
        * 高阶组件的参数为组件，返回值为新组件
        * 高阶组件是一种设计模式，类似于装饰器模式
    * 应用场景
        * 提取公共部分
        * 为组件传递参数：向下传输 props
        * 拦截生命周期、state、渲染过程等
    * 自定义高阶组件
        > 遵循官方命名规范：with+名字
        * 获取用户信息

## day7-1

### 复习

* 高阶组件
    * 定义
        * 不是一个React组件，而是一个纯函数
        * 传入一个组件，返回一个新的React组件
    * 应用
        * props代理
            > 用新组件包装传入的组件，并传递需要的props
        * 反向继承
            > 创建的新组件继承传入的React组件
            * PS：同名函数需要通过`super`手动调用

### 知识点
* 动态路由
* 嵌套路由
    > Route组件的嵌套


## day7-2

### 面试题
* webpack如何配置多页面
    * 在plugins中利用HtmlWebpackPlugin输出多个页面
    * 配置多入口:entry采用对象方式

### 知识点
* webpack配置路径别名

* 加密解密
    * 单向加密
        * md5
        * sha256
        * ...
    * 双向加密
        * 对称加密
            > 加密端与解密端使用同一把钥匙
        * 非对称加密
            * 公钥
            * 私钥
            > 原理：
                * 加密：公钥加密的数据只有私钥才能解密
                * 签名：使用私钥加密，公钥解密
        * 应用
            * git: 配置公钥
                * push: 
                    1. 本地利用私钥对数据签名
                    2. github利用公钥进行解密
                * pull:
                    1. github利用公钥加密
                    2. 本地利用私钥进行解密
            * https
                > 原理：公钥+私钥
                1. 第一次访问https服务器时，证书会自动下载到本地
                2. 利用整数进行加密数据
                3. 在服务器对密文进行解密


## day7-3

### 知识点

#### redux
* redux使用步骤
    1. 引入redux
    ```js
        import {createStore} from 'redux';
    ```
    2. 创建一个仓库
    ```js
        const store = createStore(Reducer);
    ```
    3. 使用
        * 获取state
            * store.getState()
        * 修改state：唯一修改state的方式就是reducer
            * store.dispath(action)
        * 监听state
            * store.subscribe(fn)

* redux核心
    * reducer
        * Reducer 必须是一个**纯函数**，
        * 用于指定state修改逻辑，
        * 它接受当前 state 和 action 作为参数，并根据state和action的值返回新的state
    * store
        * 常用方法
            * store.getState()  获取仓库最新state状态    `Vue: this.$store.state`
            * store.dispatch()  触发reducer，并修改state
            * store.subscribe() 监听state修改
    * action
        > 格式：{type:'xxx',}
    * state: 状态，存放数据的地方
        * store.getState() 获取**最新**状态

* 搞懂概念与操作流程

* react-redux
    > 连接react组件与redux状态
    
    * 原理：利用context+高阶组件实现
        1. 通过Provider组件共享store状态
            
        2. 利用connect()高阶组件接收store数据
            > 通过props把需要的数据传入目标组件
    * 使用
        ```js
                <Provider store={store}></Provider>

                // App.js
                // mapStateToProps: 映射redux上的state到组件的props
                App = connect(mapStateToProps,mapDispatchToProps)(App);
        ```


## day7-4

### 复习
* redux
    * 核心
        * store
        * reducer
        * state
        * action
            > 格式：{type}
    * 操作
        * 获取：store.getState()
        * 修改: store.dispatch(action)
        * 监听: store.subscribe(fn)

    ```js
        import {createStore} from 'redux'

        const initState = {

        }

        const reducer = function(state=initState,action){
            // reducer有redux内部执行，并传递state与action作为参数
            // 返回一个新的state

            // 定义如何修改state
            // 修改规则：创建新的数据去覆盖旧的数据


        }

        const store = createStore(reducer)

    ```

* react-redux
    > 一个辅助工具，利用Context+高阶组件的方式实现状态的共享

    * 在React中实现数据共享需要解决的问题
        * 如何在多个组件中共享数据: Context
        * 组件如何刷新: 高阶组件传递props
    * Provider
        ```js

            <Provider store={store}></Provider> // <MyContext.Provider value={}></MyContext.Provider>
        ```
    * connect()
        ```js
            App = connect(mapStateToProps,mapDispatchToProps)(App)
        ```

### 知识点
* 编写简化版redux

* redux模块化(reducer模块化)
    > 为什么要模块化
    ```js
        // VueX
        new VueX.Store({
            modules:{}
        })

        // Redux

    ```

* <div dangerouslySetInnerHTML={{ __html: htmlString}}></div>

* actionCreator
    > 为了简化代码操作
    * action Creator: 一个用于创建action的函数
    * bindActionCreators()

* redux
    * store
    * state
    * reducer
    * 中间件middleware
* redux-saga
    * Generator 生成器
        > 生成器函数，返回一个迭代器
        * yield     暂停
        * return    结束
    * Iterator  迭代器(遍历)
        * next()    返回格式为：{value,done}的对象
            * value: 迭代到当前位置的值
            * done： 迭代器是否迭代完毕
        * for...of  能遍历具有迭代器特性的数据
            > 内部会自动调用迭代器的next方法
    ```js
        function* show(){
            console.log('start')
            yield 10
            console.log(1)
            yield 20
            console.log(2)
            return 100
            console.log('end')
        }

    ```

    * sagaAction
        > sagaAction = reducerAction + '_async'
    * reducerAction


## day7-5

### 复习
* redux模块化（reducer模块化）
    * 分离：把不同的模块分离到多个reducer中
    * 合并：combineReducers
* action creator
    > 封装生成action的方法，可以简化我们的代码
    * bindActionCreators
* 简化版的redux

* redux中间件
    * redux-saga
    * Generator
        > 返回一个迭代器
        * yield     暂停
        * return    结束
    * Iterator
        * next() 返回格式为：{value,done} 的对象
        * for...of

    ```js
        let obj = {a:10,b:20,c:30}
        //for(let val of obj){
            // 报错
        //}

        function* create(o){
            let idx = 0;
            let length = Object.keys(o).length
            for(var key in o){
                idx++
                yield {value:o[key],done:idx===length}
            }
        }

        Object.defineProperty(obj,Symbol.iterator,{
            value(){
                return create(obj)
            }
        })
    ```


## day8-1

### 知识点
* HOOK
    * 注意事项
        * 只能在函数组件或自定义Hook中使用
        * 不要在循环语句，条件或嵌套函数中调用 Hook， 确保总是在你的 React 函数的最顶层调用他们
        * 函数组件每次更新都会从上往下执行完内部所有的代码
    * useState
        > 用法：`const [value,changeValue] = useState(initValue)`
    * useEffect
        > 用来实现类组件中生命周期函数的功能
        * 用法：
            1. useEffect(function(){})
            2. useEffect(function(){},[qty])
            3. useEffect(function(){},[])
            4. 
            ```js
                useEffect(function(){ 
                    return function(){
                        // 这里的代码在组件被销毁时执行
                    }
                },[])
            ```
    * useMemo
        > 返回值：依赖改变返回新的值，否则返回缓存值
    * useCallback
    * useContext


## day8-2

### 复习
* useState
* useEffect
* useCallback
* useMemo
* useContext
* useReducer

### 知识点
* useRef
* useLayoutEffect   useEffect的同步版本
* useImperativeHandle
* useDebugValue

* 自定义hook
    * 需求驱动开发
