# vue3study

## vue3 설치

공식 사이트 : https://v3.vuejs.org/

 get started > installation

vue.js를 설치하는 방법은 주로 CDN(Content Delivery Network), npm(Node Package Manager), CLI(Command-Line Interface), Vite(프랑스어로 'fast'를 뜻함.) 중 하나를 사용하여 설치한다.

CLI를 이용하여 설치를 진행해보자.

선행 단계로 먼저 node.js부터 설치하자.

 	1. node.js 공식 사이트 : https://nodejs.org/ko/ 에서 LTS 버젼 다운로드
 	2. 터미널에서 `node -v` 을 통해 현재 설치된 node의 버젼을 확인.
 	 * 터미널은 ctrl + ` 으로 열 수 있다.(bash 터미널로 설정하자.)
 	   * 윈도우 VSCode 터미널에서 간혹 먹지않는 명령어들이 있는데 이를 해결하기 위해서는 기본터미널을 git bash로 바꿔주면 된다.
 	   * VSCode에서 터미널을 git bash 기본으로 설정하기 : https://mishka.kr/2019/06/24/vscode-gitbash/

3. node를 설치하면 npm(node package manager)이 같이 설치가 되므로 터미널에서`npm -v`  을 통해 npm 설치여부 및 버젼 확인.

4. 터미널에서 `npm install -g @vue/cli`을 통해 vue CLI를 설치.

5. 터미널에서 `vue -V` 또는 `vue --version` 을 통해 vue CLI 설치여부 및 버젼을 확인.

   * 여기서 본인은 commend not found 에러메세지가 떴다.
   * 원인은 아마 path라는 환경변수에서 vue가 설치되어있는 경로가 없거나 잘못 지정되었기 때문이라고 생각했다.(vue 실행오류의 주범)
     * 환경변수란?
       * 프로세서가 컴퓨터에서 동작하는 방식에 영향을 미치는 동적인 값들의 모임이다.
       * 환경 변수 중 하나인 path변수는 운영체제가 어떤 프로세스를 실행시킬때, 그 경로를 찾는데 이용도니다.
       * 따라서, 환경변수설정을 제대로 해주지 않으면 프레임워크가 제대로 동작하지 않을 수 있다.
   * 일단 환경변수를 추가하기 위해서는 vue가 설치된 경로를 알아야 하는데 99%확률로 다음과 같은 경로상에 있다.
     * C:\Users\사용자이름\AppData\Roaming\npm\node_modules\@vue\cli\bin
     * 여기서 본인은 경로를 따라가다가 AppData폴더가 안보였다.
       * 숨김폴더 보기 옵션을 이용하여 AppData폴더를 드러냈다.
     * 헤당 경로에 vue 파일이 존재하는지 확인한다.
   * vue 파일이 존재하는 경우 해당 경로를 복사해놨다가 환경변수에 추가해준다.
     * win10기준으로 시작 > 시스템 환경 변수 편집 > 고급 > 환경 변수 > 시스템 변수 에서 Path 변수 클릭 후 편집 버튼 클릭 > 새로 만들기 > vue 파일이 설치되어있는 경로 붙여넣기 후 확인.
   * 여기까지 한 후 혹시 몰라 터미널에서 `npm uninstall vue-cli-g` 을 통해 vue를 삭제하고 재설치 한 후 vscode를 한번 껏다가 켜서 버젼확인을 해보니 잘 되었다.

6. 프로젝트 생성

   * 터미널에서 `vue create 프로젝트명` 을 통해 프로젝트를 생성한다.
     * 여기서 vue2로 생성할지, vue3으로 생성할 지 묻는다. -> vue3 선택

7. 확장툴(extension tool)설치

   * vue.js를 코딩할 때 도움을 주는 확장툴을 설치한다

     * 필수 확장툴 : vetur(Pine Wu가 만든 패키지)

       * vetur 공식 깃허브 프로젝트 설정 : https://vuejs.github.io/vetur/guide/setup.html#project-setup 

       * `jsconfig.json` 또는 `tsconfig.json`이 있는 폴더경로에 `jsconfig.json`파일을 만들고 그 안에 아래와 같은 내용을 붙여넣기 해준다.

       * ```json
           {
             "include": [
               "./src/**/*"
             ]
           }
         ```



### 프로젝트 둘러보기

* `package.json`

  * `dependencies`, `devDependencies`
    * 필요한 패키지들을 리스트로 저장해놓는 공간
      * 패키지란? 쉽게 말하자면 남들이 만들어 놓은 부품이다.
      * 따라서 개발을 할 때 이 패키지들을 사용하기 위해서 `dependencies`와 `devDependencies`에 리스트로 저장해놓았다.
      * `dependencies` : 개발을 할때, production에 올릴때 필요한 패키지들을 담아놓은곳
      * `devDependencies` : 개발을 하는 동안에만 유용한 패키지들을 담아놓는 곳(나중에 production에 올릴때에는 이 패키지들은 필요하지 않다.). 또한 설치를 하게 되면 `node_modules` 안에 폴더형태로 설치가 된다.
        * Q: 그러면 왜 node_modules 안에 막상 들어가보면 패키지들이 수백개가 설치되어 있나요?
        * A: 하나의 패키지 안에서 내부적으로 사용하는 패키지들까지 같이 설치가 되기 때문입니다.

* `public`

  * `index.html`

    * vue프로젝트를 웹 브라우저에서 열었을 때 처음으로 받아오는 html파일.

    * 파일을 살펴보자.

    * ```html
      <!DOCTYPE html>
      <html lang="">
        <head>
          <meta charset="utf-8">
          <meta http-equiv="X-UA-Compatible" content="IE=edge">
          <meta name="viewport" content="width=device-width,initial-scale=1.0">
          <link rel="icon" href="<%= BASE_URL %>favicon.ico">
          <title><%= htmlWebpackPlugin.options.title %></title>
        </head>
        <body>
          <noscript>
            <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled. Please enable it to continue.</strong>
          </noscript>
          <div id="app"></div>
          <!-- built files will be auto injected -->
        </body>
      </html>
      
      ```

    * 위의 코드를 보면 id="app"인 div 태그가 하나 있는데 이 태그안에서 vue application이 전부 구동이 된다.

    * 나중에 build를 하게 되면 div태그 밑줄에 자바스크립트 script가 자동으로 들어가게된다.

      * 자바스크립트 script가 들어가게 되면 src(source) 폴더 내에 있는 main.js가 가장먼저 실행된다.

      * main.js 를 살펴보면

        * ```js
          // vue에서 createApp 함수를 가져와서
          import { createApp } from 'vue'
          import App from './App.vue'
          // vue3가 되면서 기존의 Vue 생성자 함수를 사용하는 대신에, createApp() 함수를 사용한다.
          // 최상위 컴포넌트(App)를 createApp 함수에 넣어주고
          // App 컴포넌트의 컨텐츠를 id가 app인 div태그안에 넣는다.
          createApp(App).mount('#app')
          
          ```

      * 그렇다면 App.vue 컴포넌트 안에는 어떤 컨텐츠들이 있는지 살짝 살펴보자.

        ```vue
        <template>
          <!-- 이미지 태그가 있다. -->
          <img alt="Vue logo" src="./assets/logo.png">
          <!-- 3. HelloWorld 태그에서 메세지를 띄운다. -->
          <HelloWorld msg="Welcome to Your Vue.js App"/>
        </template>
        
        <script>
        // 1. HelloWorld.vue로부터 HelloWorld를 불러와서
        import HelloWorld from './components/HelloWorld.vue'
        
        export default {
          // 2. 이름이 App인 컴포넌트에 HelloWorld 컴포넌트를 등록한다.
          name: 'App',
          components: {
            HelloWorld
          }
        }
        </script>
        
        <style>
        #app {
          font-family: Avenir, Helvetica, Arial, sans-serif;
          -webkit-font-smoothing: antialiased;
          -moz-osx-font-smoothing: grayscale;
          text-align: center;
          color: #2c3e50;
          margin-top: 60px;
        }
        </style>
        ```

        * image 태그가 id가 App인 div 태그안에 잘 들어갔는지 웹 브라우저에서 확인해보자.

          * package.json파일을 살펴보면 다음과 같은 코드가 있을 것이다.

            ```json
              "scripts": {
                "serve": "vue-cli-service serve",
                // build는 production에 올리기 전에 production에 올리기에 최적화 된 파일을 만드는 과정이다.
                "build": "vue-cli-service build",
                "lint": "vue-cli-service lint"
              },
            ```

            이 말인 즉슨, 개발서버를 실행시키기 위해서는 "serve"를 사용해야 한다는 것이다.

            터미널에서 `npm run serve` 명령어로 개발서버를 실행시킬수 있다.

      * App.vue 컴포넌트 내의 코드를 다 지우고 다음과 같이 작성한 후 서버를 실행시켜보자.
      
        ```vue
        <template>
          <div>username</div>
        </template>
        ```
      
        F12를 눌러 개발자 도구를 활성화 한 다음 Elements를 보면 id가 app인 div태그 내에 내가 작성한 div태그가 들어가있는 모습을 볼 수 있다.
    
    

