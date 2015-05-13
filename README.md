grunt-manifest-generator
========================

>this tool will scan all the html files, and get all the images, css, js, html to generator the manifest file.

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-manifest-generator
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-manifest-generator');
```

You can run the testcase. change you path to ./node_modeules/grunt-manifest-generator/, and run grunt. You could see the result file ./output/test.manifest file was created! The ./Gruntfile.js has the base function of this task, so you could use it as that. If you have any question, you can contact me at sina weibo: http://weibo.com/ginano
## The "manifest-generator" task

### Overview
In your project's Gruntfile, add a section named `manifestGenerator` to the data object passed into `grunt.initConfig()`.

```js
'use strict';

module.exports = function(grunt) {
    grunt.initConfig({
        // Configuration to be run (and then tested).
        manifestGenerator:{
            test: {
                options:{

                    //Cache all html files in source files
                    //{Boolean}
                    //default:true
                    includeHTML:true,

                    //Cache all images from img tags or inline style with background-images from the source files
                    //{Boolean}
                    //default:true
                    includeHtmlImage:true,

                    //Cache all stylesheet (css) files imported by the html
                    //{Boolean}
                    //default:true
                    includeCSS:true,

                    //Cache all background-images from all css content
                    //{Boolean}
                    //default:true
                    includeCssImage:true,

                    //Cache all JavaScript (js) files imported by the html
                    //{Boolean}
                    //default:true
                    includeJS:true,

                    //all the files above but the following files.
                    //Regular expressions are allowed.
                    //{Array}
                    //default:[]
                    excludeFiles:['/\.png$/']

                    //Specify any additional static resources to include, such as '/\.json$/i', 'favicon.ico' etc.
                    //{Array}
                    //default:[]
                    extraFiles: [],

                    //In special cases (single page applications for example) some html resources in
                    //sub-folders are not pages, but templates referenced from (and resolved to) the root folder.
                    //When specified, resources than cannot be found will be referenced as if they are relative
                    //to one of the paths listed here (if found).
                    applicationRoot: [],

                    //Files listed in this section may come from the network if they aren't in the cache,
                    //otherwise the network isn't used, even if the user is online.
                    //You can white-list specific URLs here, or simply "*", which allows all URLs. Most sites need "*".
                    network: '*',

                    //An optional section specifying fallback pages if a resource is inaccessible.
                    //The first URI is the resource, the second is the fallback used if the network request fails or errors.
                    //Both URIs must from the same origin as the manifest file.
                    //You can capture specific URLs but also URL prefixes.
                    //  e.g. "images/large/" will capture failures from URLs such as "images/large/whatever/img.jpg".
                    //{String}
                    fallback: '',

                    //Additional settings to output in the final manifest file
                    //  see:
                    //{Array}
                    settings: []

                  },
                files: {
                    //the task will scan all the source files, and generate 'test.manifest' file as the cache setting.
                    'test.manifest': ['test/test.html','test/index.html']
                }
            }
        }
    });
    // Actually load this plugin's task(s).
    grunt.loadNpmTasks('grunt-manifest-generator');
    grunt.registerTask('grunt', ['manifestGenerator:test']);
};
```


## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
2013-8-23 0.1.0 create the plugin

2013-10-12 0.1.1 add the extraFiles option for add some extra files to the manifest file. optimize the rule of geting image files from htmlcontent.

2013-11-25 0.1.2-0.1.3 add some comments for the sourecode. change the usage of lib/util.
