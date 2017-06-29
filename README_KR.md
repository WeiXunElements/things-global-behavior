# things-global-behavior

## 이는 Elements를 통하여 전역변수의 Set/Get을 접속 가능하게 하는 Behavior이다.

아래 샘플 중, test-2에서 수정했지만 test-1에서도 감지되어 콘솔에 프린팅된다.

Example:
```html
<test-1></test-1>
<test-2></test-2>

<dom-module id="test-1">
  <template>
    <style>
      :host {
        display: block;
      }
    </style>

  </template>
  <script>
    Polymer({
      is: 'test-1',
      behavior:[
        Things.GlobalBehavior
      ],
      observers:[
        'onGlobalsChange(globals.*)'
      ],
      onGlobalsChange: function(a,b,c){
        console.log(a,b,c)
      }
    });
  </script>
</dom-module>

<dom-module id="test-2">
  <template>
    <style>
      :host {
        display: block;
      }
    </style>

  </template>
  <script>
    Polymer({
      is: 'test-2',
      behavior:[
        Things.GlobalBehavior
      ],
      observers:[
        'onGlobalsChange(globals.*)'
      ],
      onGlobalsChange: function(a,b,c){
        console.log(a,b,c)
      },
      attached: function(){
        this.set('globals.a','ABC')
      }
    });
  </script>
</dom-module>
```

## Dependencies

element의 종속성은 [Bower](http://bower.io/)를 통해 관리되며, 아래의 방법을 통해 설치할 수 있다.

    npm install -g bower

다음, element의 종속성을 다운로드한다.

    bower install


## Playing With Your Element

element를 독립적으로 처리하려면 [Polyserve](https://github.com/PolymerLabs/polyserve)를 사용하여 element의 bower 의존성을 유지하도록 하며, 이는 아래의 방법을 통해 설치할 수 있다.

    npm install -g polymer-cli

그리고, 아래의 방법을 통해 실행할 수 있다.

    polymer serve

element를 실행한 경우, `things-global-behavior`가 디렉토리 이름으로 포함되어 있는 `http://localhost:8080/components/things-global-behavior/`를 통해 이를 미리 확인할 수 있다.
