Description
---
Ngify is a Browserify transform for converting Angular templates to javascript
using $templateCache.

Usage
---
Install ngify locally:


    npm install ngify --save-dev


Configure browserify to use this transform in package.json:


      "browserify": {
        "transform": [
          "ngify"
        ]
      }

When you require html files, they will processesed by ngify:


    require('angularTemplate.html')

The output bundle will contain the following:


    angular.module("{{moduleName}}")
        .run([
            "$templateCache",
            function($templateCache){
                $templateCache.put("{{templateName}}","{{html}}")
            }
         ])


Where the following values are filled in:

* {{moduleName}}
    1. The name defined in package.json
    2. If there is no package.json but there is an index.js file, this value
    will be the name of the containing folder

* {{templateName}}
    1. The file name with extension

* {{html}}
    1. The contents of the file minimized using html-minifier


        {
            collapseWhitespace: true,
            conservativeCollapse: true
        }

Execute Tests
---
For a single run:


    npm test

For continuous testing with changes:


    npm run-script autotest

License
---
The MIT License (MIT)

Copyright (c) 2014 Michael A. Jackson

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.