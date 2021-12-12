# PDF.js Express - Vue sample

[PDF.js Express Viewer](https://pdfjs.express/) is a powerful JavaScript-based PDF Library. It provides a slick, responsive and customizable UI that out-of-the-box interacts with the core library to view PDFs and is ready to be embedded into any web project.


This repo is specifically designed for any users interested in integrating WebViewer into Vue project.

## Initial setup

Before you begin, make sure your development environment includes [Node.js](https://nodejs.org/en/).

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

### 链接上加file=您的pdf链接 下边这段代码请放在打包后的index.html head里。
### 在把window.$$file 值确定下在不在app.js里
    https://hpread.xhwxpos.com/newpdf/index.html?file=https://hpread.xhwxpos.com/uploads/20211022/38676e9236fa6656ac59eb3cf3427862.pdf
    
    <script>
        let params = (new URL(document.location)).searchParams;
        var file = params.get('file');
        window.$$file = file
    </script>
