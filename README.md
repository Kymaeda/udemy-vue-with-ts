# udemy-vue-with-ts

## JS復習
- `addEventListner`
  - 引数には、関数そのものを渡す
  - （寄り道）関数に引数を渡したいとき
    - [nameプロパティを使う](https://note.com/yamanoborer/n/n2e4cc40328b7)
    - [.bindを使う](https://devsakaso.com/javascript-passing-arguments-to-event-handlers/)
    - データ属性を使うようにする
    - removeEventできるように、addEventListnerの中で関数を呼び出すのはやめた方がいいらしい
    ```js
    const sampleFunction = (e) => console.log(`do something: ${e}`);

    // NG
    elem.addEventListner('click', function(e){
      sampleFunction(e)
    })

    // OK
    elem.addEventListner('click', sampleFunction.bind(e));
    ```
