### **Node.js简介**

Node.js是一个基于Chrome V8 JavaScript引擎的开源、轻量级的服务器端运行环境。它允许使用JavaScript构建高性能的网络应用程序，特别适用于实时应用程序、API、后端服务等。

### **安装和环境配置**

1. **下载安装Node.js：**
   
   前往Node.js官方网站（https://nodejs.org/），根据你的操作系统下载适用于你的版本。通常情况下，你可以选择稳定版（LTS）或者最新版本。

2. **安装验证：**
   
   安装完成后，打开终端（命令行）并运行以下命令来验证Node.js和npm（Node.js包管理工具）是否已经成功安装：

   ```bash
   node -v
   npm -v
   ```

   如果你看到类似的输出，表示安装成功：

   ```
   v14.17.4  // Node.js版本号
   7.20.3   // npm版本号
   ```

3. **创建一个简单的Node.js应用：**
   
   在一个文件夹中创建一个名为`app.js`的文件

   在`app.js`中输入以下代码，用于输出"Hello, Node.js!"到终端：
   
   ```javascript
   console.log("Hello, Node.js!");
   ```

   保存文件后，回到终端，运行`node app.js`命令。你应该会看到输出："Hello, Node.js!"。
   







`fs`模块是Node.js内置的核心模块之一，它提供了文件系统操作的功能，允许你在Node.js应用程序中执行各种文件和目录相关的操作。这些操作包括读取文件内容、写入文件、创建目录、删除文件等。下面是一些`fs`模块的常见功能和用法：

### **常见的fs模块操作：**

1. **读取文件内容：**

   使用`fs.readFile`方法来读取文件的内容。这是一个异步操作，你可以传递一个回调函数来处理读取完成后的数据。

   ```javascript
   const fs = require('fs');

   fs.readFile('file.txt', 'utf8', (err, data) => {
       if (err) {
           console.error('Error reading file:', err);
           return;
       }
       console.log('File content:', data);
   });
   ```

2. **写入文件：**

   使用`fs.writeFile`方法来将数据写入文件。同样也是异步操作，需要提供回调函数来处理写入的结果。

   ```javascript
   const fs = require('fs');

   const content = 'Hello, Node.js!';
   fs.writeFile('output.txt', content, (err) => {
       if (err) {
           console.error('Error writing file:', err);
           return;
       }
       console.log('File written successfully.');
   });
   ```

3. **检查文件或目录是否存在：**

   使用`fs.existsSync`来检查指定的文件或目录是否存在。

   ```javascript
   const fs = require('fs');

   const fileExists = fs.existsSync('file.txt');
   if (fileExists) {
       console.log('File exists.');
   } else {
       console.log('File does not exist.');
   }
   ```

4. **创建目录：**

   使用`fs.mkdir`来创建新目录。

   ```javascript
   const fs = require('fs');

   fs.mkdir('new_directory', (err) => {
       if (err) {
           console.error('Error creating directory:', err);
           return;
       }
       console.log('Directory created.');
   });
   ```

5. **删除文件或目录：**

   使用`fs.unlink`删除文件，使用`fs.rmdir`删除目录。

   ```javascript
   const fs = require('fs');
   
   fs.unlink('file.txt', (err) => {
       if (err) {
           console.error('Error deleting file:', err);
           return;
       }
       console.log('File deleted.');
   });
   
   fs.rmdir('directory', (err) => {
       if (err) {
           console.error('Error deleting directory:', err);
           return;
       }
       console.log('Directory deleted.');
   });
   ```



`path`模块是Node.js内置的核心模块之一，它用于处理文件路径和目录路径的操作。`path`模块提供了一组方法，帮助你在不同操作系统上正确地操作路径，以便你的应用程序在不同环境中都能正常工作。

下面是一些`path`模块常见的功能和用法：

### **常见的path模块操作：**

1. **连接路径：**

   使用`path.join`方法来连接多个路径片段，创建一个正确格式的路径。

   ```javascript
   const path = require('path');

   const fullPath = path.join(__dirname, 'files', 'file.txt');
   console.log('Full path:', fullPath);
   ```

2. **解析路径：**

   使用`path.resolve`方法来获取绝对路径。

   ```javascript
   const path = require('path');

   const absolutePath = path.resolve('files', 'file.txt');
   console.log('Absolute path:', absolutePath);
   ```

3. **获取路径信息：**

   使用`path.parse`方法来解析路径，获取其各个组成部分。

   ```javascript
   const path = require('path');

   const parsedPath = path.parse('/path/to/file.txt');
   console.log('Parsed path:', parsedPath);
   ```

4. **获取路径的基础名或扩展名：**

   使用`path.basename`获取路径的基础名，使用`path.extname`获取路径的扩展名。

   ```javascript
   const path = require('path');

   const basename = path.basename('/path/to/file.txt');
   const extname = path.extname('/path/to/file.txt');
   console.log('Basename:', basename);
   console.log('Extension:', extname);
   ```

5. **标准化路径：**

   使用`path.normalize`方法将路径标准化，处理不同操作系统的路径格式。

   ```javascript
   const path = require('path');

   const normalizedPath = path.normalize('/path//to/file.txt');
   console.log('Normalized path:', normalizedPath);
   ```

6. **相对路径：**

   使用`path.relative`方法来获取从一个路径到另一个路径的相对路径。

   ```javascript
   const path = require('path');
   
   const relativePath = path.relative('/path/from', '/path/to');
   console.log('Relative path:', relativePath);
   ```



可以使用Node.js中的`fs`模块来读取HTML文件的内容，然后使用字符串操作来去掉空格和换行，最后将处理后的内容写入新的文件。下面是一个示例代码：

```javascript
const fs = require('fs');
const path = require('path');

// 读取原始HTML文件
fs.readFile('input.html', 'utf8', (err, data) => {
    if (err) {
        console.error('Error reading file:', err);
        return;
    }

    // 去掉空格和换行
    const cleanedContent = data.replace(/[\s\n]+/g, '');

    // 写入新文件
    fs.writeFile('output.html', cleanedContent, (err) => {
        if (err) {
            console.error('Error writing file:', err);
            return;
        }
        console.log('New file written successfully.');
    });
});
```

在这个代码示例中：

1. 使用`fs.readFile`读取原始HTML文件的内容。
2. 使用正则表达式`/[\s\n]+/g`来匹配所有的空格和换行，使用`replace`方法将其替换为空字符串，从而去掉这些空格和换行。
3. 使用`fs.writeFile`将处理后的内容写入新的HTML文件。





`http`模块是Node.js内置的核心模块之一，它提供了构建HTTP服务器和客户端的功能。使用`http`模块，你可以创建HTTP服务器以监听来自客户端的请求，也可以作为客户端发送HTTP请求到其他服务器。

以下是一些`http`模块的常见功能和用法：

### **常见的http模块操作：**

1. **创建HTTP服务器：**

   使用`http.createServer`方法创建一个HTTP服务器，监听指定的端口号，接收客户端的请求。

   ```javascript
   const http = require('http');
   
   const server = http.createServer((req, res) => {
       res.writeHead(200, {'Content-Type': 'text/plain'});
       res.end('Hello, World!\n');
   });
   
   server.listen(8080, () => {
       console.log('Server is listening on port 8080');
   });
   ```

`http.createServer`方法中，回调函数接收两个参数：`req`和`res`。它们分别是HTTP请求对象和HTTP响应对象。

1. `req`：`req`是HTTP请求对象，它代表了客户端向服务器发送的HTTP请求。通过这个对象，你可以获取有关请求的信息，如请求的URL、HTTP方法、请求头等。

2. `res`：`res`是HTTP响应对象，它代表了服务器向客户端发送的HTTP响应。通过这个对象，你可以设置响应的状态码、头部信息以及响应体等。

全称分别是：

- `req`：`request`，即HTTP请求对象。
- `res`：`response`，即HTTP响应对象。



在Node.js的HTTP模块中，`res.writeHead`和`res.end`是用于设置HTTP响应的两个重要方法。

1. **`res.writeHead(statusCode, headers)`：**

   `res.writeHead`方法用于设置HTTP响应的状态码和响应头。它的参数包括：

   - `statusCode`：HTTP响应的状态码，例如200表示成功，404表示资源未找到等。
   - `headers`：一个包含响应头的对象，用来设置HTTP响应的头部信息，如Content-Type、Cache-Control等。

   例如，`res.writeHead(200, {'Content-Type': 'text/plain'})` 将设置响应的状态码为200（成功），并设置Content-Type响应头为'text/plain'，表示响应内容为纯文本。

2. **`res.end([data[, encoding]][, callback])`：**

   `res.end`方法用于结束HTTP响应并发送响应内容给客户端。它的参数包括：

   - `data`：要发送的响应体内容。可以是字符串、Buffer对象或其他可以被转换为字符串的数据类型。
   - `encoding`：可选参数，用于指定响应体内容的编码方式。默认为'utf-8'。
   - `callback`：可选参数，一个回调函数，当响应结束时被调用。

   例如，`res.end('Hello, World!')` 将发送'Hello, World!'作为响应体内容给客户端。

这两个方法通常一起使用，`res.writeHead`用于设置响应头，然后使用`res.end`来发送响应内容给客户端。



```javascript
server.listen(8080, () => {
    console.log('Server is listening on port 8080');
});
```

`server.listen`方法来启动HTTP服务器，以监听指定的端口号（在这里是8080）。当服务器成功开始监听指定的端口后，回调函数将被调用，这里使用回调函数输出一条日志。



除了使用普通的文本形式，还可以使用其他内容类型的数据来响应客户端请求。HTTP响应的`Content-Type`头部可以设置为不同的值，以指示服务器正在返回的数据类型。以下是一些常见的数据类型和示例：

1. **HTML内容：**

   设置`Content-Type`为`text/html`，然后发送包含HTML标记的字符串。

   ```javascript
   res.writeHead(200, {'Content-Type': 'text/html'});
   res.end('<html><body><h1>Hello, World!</h1></body></html>\n');
   ```

2. **JSON数据：**

   设置`Content-Type`为`application/json`，然后发送JSON格式的数据。

   ```javascript
   const jsonData = { message: 'Hello, World!' };
   res.writeHead(200, {'Content-Type': 'application/json'});
   res.end(JSON.stringify(jsonData));
   ```

3. **图像文件：**

   设置`Content-Type`为合适的图像MIME类型，然后将图像文件的二进制数据作为响应体发送。

4. **其他数据类型**



### 时钟案例

**需求：**创建一个简单的HTTP服务器，用于提供静态HTML文件（`clock.html`），并对其他请求返回404错误。

**前情提要**

`http.createServer().on()`的使用方式是通过创建HTTP服务器对象并监听不同的事件来处理请求。在Node.js中，HTTP服务器对象使用事件驱动的方式来处理不同类型的HTTP请求事件，例如`'request'`、`'connect'`、`'upgrade'`等。

以下是`http.createServer().on()`的基本使用方式示例：

```javascript
const http = require('http');

const server = http.createServer();

server.on('request', (req, res) => {
    if (req.url === '/html') {
        // 处理/html请求
        res.writeHead(200, {'Content-Type': 'text/plain'});
        res.end('This is the HTML page.\n');
    } else {
        // 处理其他请求
        res.writeHead(404, {'Content-Type': 'text/plain'});
        res.end('Not Found\n');
    }
});

server.listen(8080, () => {
    console.log('Server is listening on port 8080');
});
```

在这个示例中，我们首先使用`http.createServer()`创建了一个HTTP服务器对象，然后使用`.on()`方法为该服务器对象注册事件处理程序。

- `'request'`事件：当客户端发送HTTP请求时，触发`'request'`事件。回调函数接收`req`（请求对象）和`res`（响应对象）作为参数，你可以在回调函数中处理请求并发送响应。





```javascript
const http = require('http');
const fs = require('fs');
const path = require('path');

const server = http.createServer().on('request', (req, res) => {
    if (req.url === '/clock.html') {
        const filePath = path.join(__dirname, 'clock.html');
        
        fs.readFile(filePath, 'utf8', (err, content) => {
            if (err) {
                res.writeHead(500, {'Content-Type': 'text/plain'});
                res.end('Internal Server Error');
                return;
            }
            
            res.writeHead(200, {'Content-Type': 'text/html'});
            res.end(content);
        });
    } else {
        res.writeHead(404, {'Content-Type': 'text/plain'});
        res.end('Not Found');
    }
});

const port = 8080;
server.listen(port, () => {
    console.log(`Server is running at http://localhost:${port}`);
});

```



**时钟模块**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Clock</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        
        #clock {
            font-size: 2em;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Current Time</h1>
    <div id="clock">Loading...</div>

    <script>
        function updateClock() {
            const now = new Date();
            const hours = formatTime(now.getHours());
            const minutes = formatTime(now.getMinutes());
            const seconds = formatTime(now.getSeconds());
            const currentTime = `${hours}:${minutes}:${seconds}`;
            document.getElementById('clock').textContent = currentTime;
        }

        function formatTime(time) {
            return time < 10 ? `0${time}` : time;
        }

        setInterval(updateClock, 1000);
    </script>
</body>
</html>
```

这个示例页面会在浏览器中显示一个实时的时钟，显示当前的小时、分钟和秒数。可以将这个代码保存为`clock.html`文件，然后使用浏览器打开，即可看到时钟在每一秒钟更新。



### 导入导出



***CommonJS***

CommonJS是一种用于在JavaScript环境中定义模块的规范。它的目标是解决JavaScript中的模块化问题，使开发者能够更好地组织代码、重用功能，并实现更好的可维护性。

主要特点和用法包括：

1. **模块导出和导入：** 在CommonJS中，每个文件被视为一个模块，模块中的函数、对象、变量等可以通过 `module.exports` 导出，其他模块可以使用 `require` 来导入这些导出的内容。

2. **`module.exports` 和 `require`：** 使用 `module.exports` 将某个值或功能暴露给其他模块，使用 `require` 来引入其他模块的导出。例如：

   ```javascript
   // 导出模块
   // utils.js
   function sum(a, b) {
       return a + b;
   }
   module.exports = { sum };

   // 引入模块
   // main.js
   const utils = require('./utils');
   console.log(utils.sum(2, 3)); // 输出 5
   ```

3. **路径解析：** 当使用 `require` 导入模块时，CommonJS使用一些规则来解析模块的路径，包括相对路径和绝对路径。

4. **同步加载：** CommonJS模块系统是同步加载模块的，这意味着当一个模块被 `require` 时，它会被立即加载并执行，然后再继续执行下面的代码。

5. **循环依赖处理：** CommonJS模块系统支持循环依赖，但需要注意适当的使用方式，避免出现无限循环。



ECMAScript（缩写为ES）是JavaScript语言的标准化规范，定义了JavaScript的基本语法、数据类型、操作、控制结构等等。其中，ES6（也称为ES2015）引入了一种新的模块化系统，支持默认导入和导出方式，以便更好地组织和管理代码。

**默认导出（Default Export）：**

默认导出允许一个模块默认导出一个值，而导入时不需要使用花括号来指定导入的成员名。一个模块只能有一个默认导出。

**示例：**

假设我们有一个模块 `math.js`，默认导出一个加法函数：

```javascript
// math.js
export default function add(a, b) {
    return a + b;
}
```

然后在另一个模块中导入这个默认导出：

```javascript
// main.js
import add from './math.js';

console.log(add(2, 3)); // 输出 5
```

**默认导入（Default Import）：**

默认导入语法使用 `import` 关键字，后跟要导入的模块的路径。导入的内容会被放在指定的变量名中。注意，变量名可以随意命名，但通常应该与默认导出的模块名一致。



以下是等价的写法：

```javascript
// math.js

// 先声明函数
function add(a, b) {
    return a + b;
}

// 导出函数
export default add;
```

这个写法将声明和导出分开，清楚地展示了模块中的功能以及默认导出的内容。在另一个模块中导入时，使用相同的 `import` 语法即可：



其他环境依赖:在 `package.json` 中添加 `"type": "module"`：

```json
{
    "type": "module",
    "dependencies": {
        // 其他依赖
    }
}
```



如果有多个函数需要导出，并且想要使用 `export default` 来进行默认导出，可以在模块底部将这些函数分别赋值给对象的属性，然后将该对象进行默认导出。

下面是一个示例，假设你有一个 `math.js` 模块，里面有两个函数需要导出：

```javascript
// math.js

function add(a, b) {
    return a + b;
}

function subtract(a, b) {
    return a - b;
}

export default {
    add,
    subtract
};
```

在这个示例中，我们将 `add` 和 `subtract` 函数分别赋值给了一个对象的属性，然后将这个对象通过 `export default` 进行了默认导出。

然后，在另一个模块中，你可以使用 `import` 来导入这些函数：

```javascript
// main.js

import mathFunctions from './math.js';

console.log(mathFunctions.add(2, 3));      // 输出 5
console.log(mathFunctions.subtract(5, 2)); // 输出 3
```

使用这种方式，你可以在一个模块中导出多个函数，并在其他模块中进行默认导入。记住，默认导出的对象会带有你在模块中定义的函数名作为属性名。



想要在一个模块中导出多个函数或变量，并且想要通过名称来明确导入它们时，你可以使用命名导出和命名导入。这使得你可以更清晰地了解导入和导出的内容。

**命名导出（Named Export）：**

在模块中，你可以使用 `export` 关键字来命名导出函数、变量等。每个导出项都需要一个独立的名称。

示例，在 `math.js` 模块中命名导出两个函数：

```javascript
// math.js

export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}
```

**命名导入（Named Import）：**

在另一个模块中，你可以使用 `import` 关键字，然后使用花括号来明确导入你需要的函数或变量。

示例，在 `main.js` 模块中使用命名导入：

```javascript
// main.js

import { add, subtract } from './math.js';

console.log(add(2, 3));      // 输出 5
console.log(subtract(5, 2)); // 输出 3
```

**同时使用默认导出和命名导出：**

你还可以在一个模块中同时使用默认导出和命名导出。示例如下：

```javascript
// math.js

export default function multiply(a, b) {
    return a * b;
}

export function divide(a, b) {
    return a / b;
}
```

在另一个模块中使用默认导入和命名导入：

```javascript
// main.js

import multiply, { divide } from './math.js';

console.log(multiply(2, 3)); // 输出 6
console.log(divide(10, 2));  // 输出 5
```

这种方式允许你在一个模块中同时使用默认导出和命名导出，以及在另一个模块中同时使用默认导入和命名导入。



**集中导出（Aggregating Exports）**

你可以使用一个 `index.js` 文件来汇总所有模块的导出，然后在其他模块中使用集中导出的内容。

希望在 `utils/lib` 文件夹中创建多个模块，并且将它们的功能集中导出，可以按照以下步骤进行操作：

1. **创建模块文件：** 在 `utils/lib` 文件夹中，创建 `num.js`、`str.js` 和 `arr.js` 三个文件，每个文件分别包含对应的函数。

   ```javascript
   // utils/lib/num.js
   function addNumbers(a, b) {
       return a + b;
   }

   module.exports = {
       addNumbers
   };
   ```

   ```javascript
   // utils/lib/str.js
   function capitalizeString(str) {
       return str.toUpperCase();
   }

   module.exports = {
       capitalizeString
   };
   ```

   ```javascript
   // utils/lib/arr.js
   function findMax(arr) {
       return Math.max(...arr);
   }

   module.exports = {
       findMax
   };
   ```

2. **创建集中导出文件：** 在 `utils` 文件夹中，创建一个 `index.js` 文件，用于集中导出 `utils/lib` 文件夹中的模块。

   ```javascript
   // utils/index.js
   const numFunctions = require('./lib/num');
   const strFunctions = require('./lib/str');
   const arrFunctions = require('./lib/arr');

   module.exports = {
       ...numFunctions,
       ...strFunctions,
       ...arrFunctions
   };
   ```

3. **导入使用：** 在其他模块中，你可以导入 `utils` 模块的内容并使用其中的函数。

   ```javascript
   // main.js
   const utils = require('./utils');
   
   console.log(utils.addNumbers(2, 3)); // 使用 num.js 中的函数
   console.log(utils.capitalizeString('hello')); // 使用 str.js 中的函数
   console.log(utils.findMax([1, 5, 3])); // 使用 arr.js 中的函数
   ```

这样，你就成功将 `num.js`、`str.js` 和 `arr.js` 中的函数集中导出，并在 `main.js` 中使用了这些功能。



如果你只想导入指定的那三个函数，你可以直接将它们导出，而不是通过展开对象来导出。以下是如何修改 `index.js` 文件的示例：

```javascript
// utils/index.js
const addNumbers = require('./lib/num').addNumbers;
const capitalizeString = require('./lib/str').capitalizeString;
const findMax = require('./lib/arr').findMax;

module.exports = {
    addNumbers,
    capitalizeString,
    findMax
};
```

在这个示例中，我们使用 `require` 来获取各个模块中的特定函数，并将它们分别赋值给一个变量。然后，我们通过 `module.exports` 分别导出这些变量。

这样，在其他模块中，你可以按照之前的方式导入和使用这些函数：

```javascript
// main.js
const utils = require('./utils');

console.log(utils.addNumbers(2, 3));
console.log(utils.capitalizeString('hello'));
console.log(utils.findMax([1, 5, 3]));
```

这样的修改将仅导出你指定的那三个函数，而不是将所有模块的内容都集中导出。



### npm

`npm`（Node Package Manager）是一个用于管理Node.js应用程序依赖的包管理器。通过npm，你可以方便地安装、更新、卸载和管理项目所需的各种包和库。以下是一些基本的关于使用npm管理项目依赖的信息：

1. **初始化项目：** 首先，在你的项目根目录中，打开命令行终端，运行以下命令来初始化一个新的npm项目。这将创建一个 `package.json` 文件，其中包含了项目的基本信息以及依赖管理的配置。

   ```sh
   npm init
   ```

2. **安装依赖：** 你可以使用 `npm install` 命令来安装项目所需的依赖包。例如，要安装 `express` 框架，可以运行以下命令：

   ```sh
   npm install express
   ```

   这会在项目的 `node_modules` 文件夹中安装 `express` 包，并将其添加到 `package.json` 中的依赖列表中。

3. **全局安装 vs 本地安装：** 默认情况下，`npm install` 命令会将包安装到项目的 `node_modules` 文件夹中。如果你希望全局安装一个包，可以使用 `-g` 标志。全局安装的包通常是用于命令行工具等，而项目内的依赖应该使用本地安装。

   ```sh
   npm install -g package-name   # 全局安装
   npm install package-name      # 本地安装
   ```

4. **保存依赖：** 通过 `npm install package-name --save` 或 `npm install package-name -S` 命令，你可以将包添加到 `package.json` 的 `dependencies` 字段中。

   ```sh
   npm install express --save    # 安装并保存到 dependencies
   ```

5. **开发依赖：** 对于只在开发过程中使用的工具或库，你可以使用 `--save-dev` 或 `-D` 标志将它们添加到 `package.json` 的 `devDependencies` 字段中。这些依赖在项目构建、测试和开发时会用到。

   ```sh
   npm install jest --save-dev   # 安装并保存到 devDependencies
   ```

6. **卸载依赖：** 如果你想卸载一个已安装的依赖，可以使用 `npm uninstall package-name` 命令。

   ```sh
   npm uninstall express
   ```

7. **更新依赖：** 使用 `npm update package-name` 命令可以更新指定的依赖包。如果不指定依赖包名称，它会更新所有依赖。

   ```sh
   npm update express          # 更新 express
   npm update                  # 更新所有依赖
   ```

8. **查看依赖：** 通过 `npm list` 命令可以查看当前项目的所有依赖，以及它们的版本。

   ```sh
   npm list
   ```

这些是一些基本的npm命令，用于管理项目依赖。npm是一个强大的工具，它使得管理和维护项目中的各种库和工具变得更加方便。



### Express

`Express` 是一个流行的 Node.js Web 应用程序框架，用于构建Web和API应用程序。它简化了处理路由、中间件、请求和响应等各种HTTP相关任务的过程，使开发者能够更轻松地构建功能丰富的Web应用程序。

以下是一些关于 Express 框架的特点和用途：

1. **简洁而灵活：** Express 提供了一组简单且灵活的API，可以用于处理HTTP请求、路由和中间件。它允许你根据项目的需求自定义应用程序结构。

2. **路由和中间件：** Express 具有强大的路由和中间件支持。你可以使用路由来定义不同URL路径的处理逻辑，而中间件可以处理请求和响应之间的各种操作，如日志记录、验证和错误处理。

3. **HTTP方法：** Express 支持常见的HTTP方法，如 GET、POST、PUT、DELETE 等，可以根据需要将请求映射到相应的处理函数。

4. **视图引擎支持：** 虽然 Express 本身不包含视图引擎，但它支持多种模板引擎，如 EJS、Pug（之前的Jade）等，用于在后端生成HTML。

5. **中间件生态系统：** Express 生态系统中有大量的第三方中间件，可以用于处理各种需求，如身份验证、会话管理、缓存、CORS 等。

6. **API 开发：** 除了传统的Web应用程序外，Express 也常用于构建API。通过简单的路由和中间件，你可以构建出RESTful API。

7. **活跃的社区：** Express 框架拥有一个活跃的社区，这意味着你可以轻松地找到教程、示例和插件来支持你的项目开发。

以下是一个简单的 Express 应用程序示例：

```javascript
const express = require('express');
const app = express();
const port = 3000;

// 处理根路径请求
app.get('/', (req, res) => {
  res.send('Hello, Express!');
});

// 启动服务器
app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

在这个示例中，我们导入 Express 模块，创建一个 Express 应用程序实例，并在根路径上定义了一个处理函数来响应请求。最后，我们通过 `app.listen` 启动了一个服务器，监听在指定的端口上。



`node_modules` 是用于存放 Node.js 项目依赖包的文件夹。当你在项目中使用第三方库、框架或工具时，这些依赖包会被下载并存放在 `node_modules` 文件夹中。



`npm i` 是 `npm install` 命令的简写形式，它是 Node.js 包管理器 npm 提供的一个命令，用于安装项目依赖包。

运行 `npm install` 或 `npm i` 会根据项目的 `package.json` 文件安装所需的依赖包，这些依赖包将会被下载并组织在 `node_modules` 文件夹中







**需求**

要通过 Express 在 `http://localhost:3000/index.html` 上显示 `index.html` 的内容，可以使用 Express 提供的静态文件服务功能来实现。这样，Express 将会自动为你提供 `index.html` 文件的内容。

以下是如何在 Express 中实现这个目标的步骤：

1. **创建项目文件结构：** 确保你的项目文件结构如下：

```
project-folder
├── app.js
├── public
│   └── index.html
```

2. **Express 服务器代码：** 在 `app.js` 中编写 Express 服务器的代码。使用 `express.static` 中间件来指定静态文件服务的根目录为 `public` 文件夹。

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.use(express.static('public')); // 静态文件服务根目录为 public 文件夹

app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

3. **index.html 文件：** 在 `public` 文件夹中创建 `index.html` 文件，添加你的 HTML 内容。

4. **运行服务器：** 在终端中运行 `node app.js` 启动 Express 服务器。

5. **访问页面：** 打开浏览器，访问 `http://localhost:3000/index.html`，你将会看到 `index.html` 文件的内容。

通过这个设置，Express 会将 `public` 文件夹中的内容作为静态文件提供给客户端。这样，你就可以通过 Express 在 `http://localhost:3000/index.html` 上显示 `index.html` 文件的内容。



**需求**

简单的前后端交互

在前端页面上使用 Axios 发送请求到 Express 服务器，并在页面上显示返回的数据



要实现这个功能，你需要做以下几个步骤：

1. **创建 HTML 文件：** 在项目文件夹中创建一个新的 HTML 文件，比如 `index.html`。在该文件中添加一个按钮或其他触发事件的元素。

2. **编写 JavaScript 代码：** 在 `index.html` 中编写 JavaScript 代码，使用 Axios 来发送请求到 `http://localhost:3000/app` 并处理返回的数据。

以下是一个简单的示例：

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Axios Example</title>
</head>
<body>
  <button id="fetchData">Fetch Data</button>
  <div id="output"></div>

  <script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
  <script>
    const fetchDataButton = document.getElementById('fetchData');
    const outputDiv = document.getElementById('output');

    fetchDataButton.addEventListener('click', async () => {
      try {
        const response = await axios.get('http://127.0.0.1:3000/app');
        outputDiv.textContent = response.data;
      } catch (error) {
        console.error('Error:', error);
      }
    });
  </script>
</body>
</html>
```

确保将上述代码保存为 `index.html` 并放置在你的项目文件夹中。

3. **更新 Express 服务器：** 在 Express 服务器的代码中，确保你已经启用静态文件服务，以便可以访问到 `index.html` 文件。同时，处理来自客户端的请求并返回一些数据。

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.use(express.static('public')); // 启用静态文件服务，将 index.html 放在 public 文件夹中

app.get('/app', (req, res) => {
  res.send('Data from server'); // 返回一些数据给客户端
});

app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

确保你在项目根目录下创建了 `public` 文件夹，并将之前的 `index.html` 文件放在其中。

4. **运行服务器：** 在终端中运行 `node app.js` 启动服务器。

5. **访问页面：** 打开浏览器，访问 `http://localhost:3000/index.html`，当你点击 "Fetch Data" 按钮时，页面会使用 Axios 发送请求到服务器并显示返回的数据。

