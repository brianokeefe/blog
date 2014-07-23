I was working on a basic static site (more on that to come in a later post), and I wanted to streamline my development workflow with some automation of repetitive development tasks. Specifically, I wanted to be able to:

* Launch a local development server with livereload
* Automatically compile SASS and Coffeescript
* Use templates and partials for DRYer HTML
* Easily build the site into a production-ready version

I've had [Grunt](http://gruntjs.com) on the brain lately and there are plugins available to accomplish all of those tasks, so I sat down and started writing a really fleshed out Gruntfile to do what I wanted. I realized it was generic enough that I would be able to use it for other projects, so I decided to make it easy to scaffold new projects using that toolchain.

###Starch: the meat and potatoes of a basic static site

I wrote a Ruby gem, Starch, to act as a command line tool for scaffolding new projects. Ruby was maybe a questionable choice since the toolchain itself depends on NodeJS, but I didn't feel too bad about it since OSX ships with Ruby anyway. Plus, [Thor](http://whatisthor.com) made development trivial, and [Aruba](https://github.com/cucumber/aruba) was perfectly suited for [writing the style of tests I needed](https://github.com/brianokeefe/starch/blob/master/features/new.feature).

Starch is opinionated to help you get going on new projects quickly. What it generates is more of a skeleton than a framework, so you can easily add, remove, or change whatever you need for a given project without any guilt or fear of jankiness.

Using Starch is simple:

	$ gem install starch
    $ starch new mysite
    
That's it! Interacting with the toolchain is very easy as well:

	$ grunt serve   # start the development server
    $ grunt build   # build your site for production
    
All of the automation happens within those two meta-tasks. No need to think about it!

More detailed documentation and the source code is available [on Github](https://github.com/brianokeefe/starch)!

Credit goes to my buddy [Stan](http://www.schwertly.com) for the awesome name!