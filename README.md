# ng2-touying
ng2投影，父组件模板中的代码投影到子组件中


描述，组件复用，在父组件中，使用标签，引入子组件，一般情况，不会再标签之中，书写代码，或者书写“加载中..."，当子组件代码渲染完毕以后就会替换掉这些代码，但是，如果想把父组件中的代码片段通过这样的形式传递给子组件，然后根据子组件的布局显示到界面上，就要使用到投影了，具体步骤如下：

1、定义子组件模板 child.component.html

<h4>子组件</h4>
<!-- 使用ng-content标记子组件位置，使用select区分不同的ng-conent -->
<!-- 使用标签形式 -->
<ng-content select="header"></ng-content>
<ng-content select="content"></ng-content>
<ng-content select="footer"></ng-content>
<!-- 使用class形式 -->
<ng-conent select=".class-select"></ng-content>
2、定义子组件 child.component.ts

import {Component} from "@angular/core";
@Component({
  selector: "child",
  templateUrl: "../templates/child.component.html"
})
export class AboutComponent {
  constructor() {
    console.log("child");
  }
}
3、定义父组件 home.component.ts

import {Component} from "@angular/core";
@Component({
  selector: "my-home",
  templateUrl: "../templates/home.component.html"
})
export class HomeComponent {
  name: string = "zxc";
  constructor() {
    console.log("home");
  }
}
4、定义组件模板 home.component.html

<my-contact>
  <!--这是传递给子组件的内容-->
  <header><h4>传递过来的内容,ng-content接受, {{name}}</h4></header>
  <footer>底部</footer>
  <div class="class-select>class传递信息</div>
</my-contact>
