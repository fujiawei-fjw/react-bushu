## react

#### react 环境搭建

使用官方提供的脚手架 create-react-app , 如果使用

1. `npx create-react-app react-hello`前提 Node >= 8.10 和 npm >= 5.6
2. 全局安装 create-react-app 包 , npm i -g create-react-app , 使用命令 `create-react-app my-react-app`

#### react 的基础知识

###### JSX 语法

在 js 文件内写 html 语法,
如何再 html 内写 js,html 内的 js 语法都使用{}套上

###### 条件渲染

直接在 html 内使用 js 做判断

###### 列表渲染

将你的列表 使用 map 方法转换成标签数组直接放到 html 内 , 自动会被渲染 注意的时 key 属性

###### 事件处理

如何绑定事件

1. 首先在组件的 class 内创建一个方法 handleClick
2. 使用标签的 onClick 属性绑定事件 例如`<span onClick={this.handleClick}></span>`

事件绑定如何传递参数

1.  事件绑定的必须是一哥函数不能是函数调用
2.  要把你定义好的 handleClick 放到一个箭头函数内去执行并传参 , 然后将该箭头函数绑定给标签的 onClick 属性 例如 `<span onClick={()=> {this.handleClick(argument)}}></span>`
    **需要额外注意的就是 事件对象 event , 这个对象必须是函数才有的**

###### state

组件的状态,react 框架要求页面的所有变化需要和 state 有直接的关系

1. 如何定义
   再 class 内
   ```js
   class Btn extends Component {
   state = {
    count: 10
   };
   ```
2. render 函数内获取 this.state
3. 修改 state 必须通过 setState 函数修改

###### props

父子组件传递数据

1. 在 父组件内直接给组件自定义一个属性把想传递的数据当做属性值传递过去 例如
   `<Btn text="父组件的数据" />`
2. 在子组件内会有一个默认的 props 属性用来存储父组件传递过来的数据
   `this.props.text`
3. 可以通过 Btn(组件名).defaultprops 设置 props 的默认值，还可以使用环境自带的 Prop-types 包对 props 进行类型检查

```js
import PropTypes from "prop-types";
// 做类型检查
Btn.propTypes = {
  text: PropTypes.string
};

// 设置默认值
Btn.defaultProps = {
  text: "默认按钮"
};
```
