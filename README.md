# javascript_code_style
=====================
*常用的一些javascript规范*
=====================

## <a name='variables'>变量</a>
- 总是使用 `var` 来定义变量。如果不这么做将定义一个全局变量出来。我们希望避免全局命名空间的污染。

    ```javascript
    // 不推荐
    superPower = new SuperPower();

    // 推荐
    var superPower = new SuperPower();
    ```

- 使用一个`var` 声明多个变量，并且每声明一个变量就换一行。

    ```javascript
    // 不推荐
    var items = getItems();
    var goSportsTeam = true;
    var dragonball = 'z';

    // 推荐
    var items = getItems(),
        goSportsTeam = true,
        dragonball = 'z';

    ```

- 声明多个变量时，把不赋值的变量放在后面。这样做是有好处的，如果日后你想给未赋值变量赋值的时候，可能要引用到上面已经赋值的变量。

    ```javascript
    // 不推荐
    var i, len, dragonball,
        items = getItems(),
        goSportsTeam = true;

    // 不推荐
    var i, items = getItems(),
        dragonball,
        goSportsTeam = true,
        len;

    // 推荐
    var items = getItems(),
        goSportsTeam = true,
        dragonball,
        length,
        i;

    ```

- 在一个作用域的顶部给一个变量赋值。这样有助于避开，变量声明和声明提前的分配问题。

    ```javascript
    // 不推荐
    function() {
      test();
      console.log('doing stuff..');

      //..other stuff..

      var name = getName();

      if (name === 'test') {
        return false;
      }

      return name;
    }

    // 推荐
    function() {
      var name = getName();

      test();
      console.log('doing stuff..');

      //..other stuff..

      if (name === 'test') {
        return false;
      }

      return name;
    }

    // 不推荐
    function() {
      var name = getName();

      if (!arguments.length) {
        return false;
      }

      return true;
    }

    // 推荐
    function() {
      if (!arguments.length) {
        return false;
      }

      var name = getName();

      return true;
    }
    ```


