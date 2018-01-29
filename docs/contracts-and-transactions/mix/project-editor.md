# 项目编辑器

You can use projects to manage the creation and testing of a dapp. The
project will contain data related to both backend and frontend as well
as the data related to your scenarios (blockchain interaction) for
debugging and testing. The related files will be created and saved
automatically in the project directory.

## 创建一个新的

The development of a dapp start with the creation of a new project.
Create a new project in the "edit" menu. Enter the project name, e.g.
"Ratings" and select a path for the project file.

## 编辑后端合同文件

By default, a new project contains a contract "Contract" for backend development on the blockchain using the Solidity language and the "index.html" for the frontend.
Check the Solidity tutorial for references.

Edit the empty default contract "Contract", e.g.

```js
    contract Rating {
        function setRating(bytes32 _key, uint256 _value) {
            ratings[_key] = _value;
        }
        mapping (bytes32 =uint256) public ratings;
    }
```

Check the Solidity tutorial for help getting started with the solidity
programming language.

Save changes

### 编辑前端html文件

选择默认的index.html文件并输入下面的代码

```js
    ....
    <script>
    function getRating() {
        var param = document.getElementById("query").value; var res =
        contracts["Rating"].contract.ratings(param);
        document.getElementById("queryres").innerText = res;
    }
    function setRating() {
        var key = document.getElementById("key").value; var value =
        parseInt(document.getElementById("value").value); var res =
        contracts["Rating"].contract.setRating(key, value);
    }
    </script>
```

```html
    </head>
    <body bgcolor="#E6E6FA">
        <h1>Ratings</h1>
        <div>
            Store: <input type="string" id="key">
            <input type="number" id="value">
            <button onclick="setRating()">Save</button
        </div>
        <div>
            Query: <input type="string" id="query" onkeyup='getRating()'>
            <div id="queryres"></div>
        </div>
    </body>
</html>
```

然后，可以添加许多合同文件以及许多HTML，JavaScript，CSS文件
