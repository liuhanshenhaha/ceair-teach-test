<template>
  <div id="examination">
    <h1>前端培训结果测试</h1>
    <form id="examination-form">
      <Radio v-for="(examinationData, index) in examinationDatas" :key="index" :idx="index" :data="examinationData" @updateValue="updateValue"/>
      <Input :data="{label:'你的名字',name:'username',value:''}" @updateValue="updateValue"/>
      <div style="text-align:center">
        <button @click.prevent="submitForm">提交</button>
      </div>
    </form>
  </div>
</template>

<script>
import Radio from './form/form.radio.vue'
import Input from './form/form.input.vue'
const examinationDatas = [{
  label:'HTML 指的是？',
  name:'q1',
  value:"",
  list:[{
    text: "超文本标记语言（Hyper Text Markup Language）",
    value: 0
  }, {
    text: "家庭工具标记语言（Home Tool Markup Language）",
    value: 1
  }, {
    text: "超链接和文本标记语言（Hyperlinks and Text Markup Language）",
    value: 2
  }]
}, {
  label:'HTML5 的正确 doctype 是？',
  name:'q2',
  value:"",
  list:[{
    text: "<!DOCTYPE html>",
    value: 0
  }, {
    text: "<!DOCTYPE HTML5>",
    value: 1
  }, {
    text: "<!DOCTYPE HTML PUBLIC \"-//W3C//DTD HTML 5.0//EN\" \"http://www.w3.org/TR/html5/strict.dtd\">",
    value: 2
  }]
}, {
  label:'在下列的 HTML 中，哪个可以产生超链接？',
  name:'q3',
  value:"",
  list:[{
    text: "<a url=\"http://www.ceair.com\">www.ceair.com</a>",
    value: 0
  }, {
    text: "<a href=\"http://www.ceair.com\">www.ceair.com</a>",
    value: 1
  }, {
    text: "<a>http://www.ceair.com</a>",
    value: 2
  }, {
    text: "<a name=\"http://www.ceair.com\">www.ceair.com</a>",
    value: 3
  }]
}, {
  label:'如何制作电子邮件链接？',
  name:'q4',
  value:"",
  list:[{
    text: "<a href=\"xxx@yyy\">",
    value: 0
  }, {
    text: "<mail href=\"xxx@yyy\">",
    value: 1
  }, {
    text: "<a href=\"mailto:xxx@yyy\">",
    value: 2
  }, {
    text: "<mail>xxx@yyy</mail>",
    value: 3
  }]
}, {
  label:'如何在新窗口打开链接？',
  name:'q5',
  value:"",
  list:[{
    text: "<a href=\"ur\" new>",
    value: 0
  }, {
    text: "<a href=\"url\" target=\"_blank\">",
    value: 1
  }, {
    text: "<a href=\"url\" target=\"new\">",
    value: 2
  }]
}, {
  label:'如何产生带有数字列表符号的列表？',
  name:'q6',
  value:"",
  list:[{
    text: "<ul>",
    value: 0
  }, {
    text: "<dl>",
    value: 1
  }, {
    text: "<ol>",
    value: 2
  }, {
    text: "<list>",
    value: 3
  }]
}, {
  label:'在下列的 HTML 中，哪个可以产生复选框？',
  name:'q7',
  value:"",
  list:[{
    text: "<input type=\"check\">",
    value: 0
  }, {
    text: "<checkbox>",
    value: 1
  }, {
    text: "<input type=\"checkbox\">",
    value: 2
  }, {
    text: "<check>",
    value: 3
  }]
}, {
  label:'关于javascript语言说法错误的是？',
  name:'q8',
  value:"",
  list:[{
    text: "JavaScript是目前Web应用程序开发者使用最为广泛的客户端脚本编程语言。",
    value: 0
  }, {
    text: "javaScript是网景公司专为Navigator浏览器开发、实现网页内容交互的功能。",
    value: 1
  }, {
    text: "javascript是由SUN公司开发的。",
    value: 2
  }, {
    text: "ECMAScript是一个为了规范Javascript语言而产生的国际标准。",
    value: 3
  }]
}, {
  label:'在下列的 HTML 中，哪个可以产生下拉列表？',
  name:'q9',
  value:"",
  list:[{
    text: "<list>",
    value: 0
  }, {
    text: "<input type=\"list\">",
    value: 1
  }, {
    text: "<input type=\"dropdown\">",
    value: 2
  }, {
    text: "<select>",
    value: 3
  }]
}, {
  label:'CSS 指的是？',
  name:'q10',
  value:"",
  list:[{
    text: "Computer Style Sheets",
    value: 0
  }, {
    text: "Cascading Style Sheets",
    value: 1
  }, {
    text: "Creative Style Sheets",
    value: 2
  }, {
    text: "Colorful Style Sheets",
    value: 3
  }]
}, {
  label:'在以下的 HTML 中，哪个是正确引用外部样式表的方法？',
  name:'q11',
  value:"",
  list:[{
    text: "<style src=\"mystyle.css\">",
    value: 0
  }, {
    text: "<link rel=\"stylesheet\" type=\"text/css\" href=\"mystyle.css\">",
    value: 1
  }, {
    text: "<stylesheet>mystyle.css</stylesheet>",
    value: 2
  }]
}, {
  label:'在 HTML 文档中，引用外部样式表的正确位置是？',
  name:'q12',
  value:"",
  list:[{
    text: "文档的末尾",
    value: 0
  }, {
    text: "文档的顶部",
    value: 1
  }, {
    text: "<body> 部分",
    value: 2
  }, {
    text: "<head> 部分",
    value: 3
  }]
}, {
  label:'哪个 HTML 属性可用来定义内联样式？',
  name:'q13',
  value:"",
  list:[{
    text: "font",
    value: 0
  }, {
    text: "class",
    value: 1
  }, {
    text: "styles",
    value: 2
  }, {
    text: "style",
    value: 3
  }]
}, {
  label:'下列哪个选项的 CSS 语法是正确的？',
  name:'q14',
  value:"",
  list:[{
    text: "body:color=black",
    value: 0
  }, {
    text: "{body:color=black(body}",
    value: 1
  }, {
    text: "body {color: black}",
    value: 2
  }, {
    text: "{body;color:black}",
    value: 3
  }]
}, {
  label:'如何为所有的 h1 元素添加背景颜色？',
  name:'q15',
  value:"",
  list:[{
    text: "h1.all {background-color:#FFFFFF}",
    value: 0
  }, {
    text: "h1 {background-color:#FFFFFF}",
    value: 1
  }, {
    text: "all.h1 {background-color:#FFFFFF}",
    value: 2
  }]
}, {
  label:'如何显示这样一个边框：上边框 10 像素、下边框 5 像素、左边框 20 像素、右边框 1 像素？',
  name:'q16',
  value:"",
  list:[{
    text: "border-width:10px 5px 20px 1px",
    value: 0
  }, {
    text: "border-width:10px 20px 5px 1px",
    value: 1
  }, {
    text: "border-width:5px 20px 10px 1px",
    value: 2
  }, {
    text: "border-width:10px 1px 5px 20px",
    value: 3
  }]
}, {
  label:'我们可以在下列哪个 HTML 元素中放置 Javascript 代码？',
  name:'q17',
  value:"",
  list:[{
    text: "<script>",
    value: 0
  }, {
    text: "<javascript>",
    value: 1
  }, {
    text: "<js>",
    value: 2
  }, {
    text: "<scripting>",
    value: 3
  }]
}, {
  label:'引用名为 "xxx.js" 的外部脚本的正确语法是？',
  name:'q18',
  value:"",
  list:[{
    text: "<script src=\"xxx.js\">",
    value: 0
  }, {
    text: "<script href=\"xxx.js\">",
    value: 1
  }, {
    text: "<script name=\"xxx.js\">",
    value: 2
  }]
}, {
  label:'外部脚本必须包含 <script> 标签吗？',
  name:'q19',
  value:"",
  list:[{
    text: "是",
    value: 0
  }, {
    text: "否",
    value: 1
  }]
}, {
  label:'如何创建方法？',
  name:'q20',
  value:"",
  list:[{
    text: "function:myFunction()",
    value: 0
  }, {
    text: "function myFunction()",
    value: 1
  }, {
    text: "function=myFunction()",
    value: 2
  }]
}, {
  label:'如何调用名为 "myFunction" 的方法？',
  name:'q21',
  value:"",
  list:[{
    text: "call function myFunction",
    value: 0
  }, {
    text: "call myFunction()",
    value: 1
  }, {
    text: "myFunction()",
    value: 2
  }]
}, {
  label:'for 循环如何开始？',
  name:'q22',
  value:"",
  list:[{
    text: "for (i <= 5; i++)",
    value: 0
  }, {
    text: "for (i = 0; i <= 5; i++)",
    value: 1
  }, {
    text: "for (i = 0; i <= 5)",
    value: 2
  }, {
    text: "for i = 1 to 5",
    value: 3
  }]
}, {
  label:'请选择下列选择器中权重最高的一项',
  name:'q23',
  value:"",
  list:[{
    text: "#baba div",
    value: 0
  }, {
    text: "div.baba div",
    value: 1
  }, {
    text: "div#baba div",
    value: 2
  }, {
    text: "div.baba div.erzi",
    value: 3
  }]
}, {
  label:'下列哪个选项是正确的html id命名',
  name:'q24',
  value:"",
  list:[{
    text: "123",
    value: 0
  }, {
    text: "a~bc",
    value: 1
  }, {
    text: "a123cb",
    value: 2
  }]
}, {
  label:'下列元素中，为行内元素的是',
  name:'q25',
  value:"",
  list:[{
    text: "div",
    value: 0
  }, {
    text: "span",
    value: 1
  }, {
    text: "p",
    value: 2
  }, {
    text: "h3",
    value: 3
  }]
}, {
  label:'下列选择器中，能选择到网页中第5个div的是',
  name:'q26',
  value:"",
  list:[{
    text: "div:4th-child",
    value: 0
  }, {
    text: "div:5th-child",
    value: 1
  }, {
    text: "div:nth-child(4)",
    value: 2
  }, {
    text: "div:nth-child(5)",
    value: 3
  }]
}, {
  label:'现有如下样式定义，<br/>&nbsp;&nbsp;&nbsp;&nbsp;<i style="font-weight:normal;color:red;">.A .B { font-weight:bold;}</i><br/>&nbsp;&nbsp;&nbsp;&nbsp;下列选项中，文本加粗显示的是',
  name:'q27',
  value:"",
  list:[{
    text: "<a class=\"A\">文本A</a> ",
    value: 0
  }, {
    text: "<a class=\"B\">文本B</a>",
    value: 1
  }, {
    text: "<p class=\"A\"><a class=\"B\">文本C</a></p>",
    value: 2
  }, {
    text: "<p class=\"B\"><a class=\"A\">文本C</a></p>",
    value: 3
  }]
}, {
  label:'查看如下 JavaScript 代码：<br/>&nbsp;&nbsp;&nbsp;&nbsp;<i style="font-weight:normal;color:red;"> var a = "10";</i><br/>&nbsp;&nbsp;&nbsp;&nbsp;<i style="font-weight:normal;color:red;"> var b = 10;</i><br/>&nbsp;&nbsp;&nbsp;&nbsp;<i style="font-weight:normal;color:red;"> if (a == b)</i><br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i style="font-weight:normal;color:red;"> alert("equal");</i><br/>&nbsp;&nbsp;&nbsp;&nbsp;<i style="font-weight:normal;color:red;"> if (a === b)</i><br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i style="font-weight:normal;color:red;"> alert("same");</i><br/>&nbsp;&nbsp;&nbsp;&nbsp;此代码运行后，效果为',
  name:'q28',
  value:"",
  list:[{
    text: "只弹出”equal“ ",
    value: 0
  }, {
    text: "只弹出”same“ ",
    value: 1
  }, {
    text: "先弹出”equal“，再弹出”same“ ",
    value: 2
  }, {
    text: "没有弹出显示",
    value: 3
  }]
}, {
  label:'HTML 页面上有一个超链接，要实现当鼠标移入该超级链接时，超级链接的文本背景色变为灰色。下列选项中，能实现此功能的是',
  name:'q29',
  value:"",
  list:[{
    text: "<a href=\"#\" onmouseover=\"this.style.background.color='gray';\">注册</a> ",
    value: 0
  }, {
    text: "<a href=\"#\" onmouseout=\"this.style.background-color='gray';\">注册</a>",
    value: 1
  }, {
    text: "<a href=\"#\" onmouseover=\"this.style.backgroundColor=gray;\">注册</a>",
    value: 2
  }, {
    text: "<a href=\"#\" onmouseover=\"this.style.backgroundColor='gray';\">注册</a>",
    value: 3
  }]
}, {
  label:'下列哪个样式定义后,行级(非块状)元素可以定义宽度和高度',
  name:'q30',
  value:"",
  list:[{
    text: "display:inline",
    value: 0
  }, {
    text: "display:none",
    value: 1
  }, {
    text: "display:block",
    value: 2
  }, {
    text: "display:inheric",
    value: 3
  }]
}, {
  label:'background-color属性可以给外边距设置背景色？',
  name:'q31',
  value:"",
  list:[{
    text: "√",
    value: 0
  }, {
    text: "×",
    value: 1
  }]
}, {
  label:'表达式5+22/2%2的计算结果是',
  name:'q32',
  value:"",
  list:[{
    text: "5",
    value: 0
  }, {
    text: "6",
    value: 1
  },{
    text: "7",
    value: 2
  }, {
    text: "8",
    value: 3
  }]
}]
export default {
  name: 'Examination',
  data: function(){
    return {
      values: this.makeValue(examinationDatas),
      examinationDatas: examinationDatas
    }
  },
  components: {
    Radio,
    Input
  },
  methods: {
    makeValue: function(datas){
      let tempValues = {};
      datas.map(function(item,index){
        tempValues[item.name] = "";
      })
      tempValues.username = "";
      return tempValues;
    },
    updateValue: function(name,value){
      this.values[name] = value
    },
    submitForm: function(){
      console.log(this.values)
    }
  }
}
</script>