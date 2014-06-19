Due to the lack of a convenient way to export the Markdown from a Ghost blog, I've written a nodejs module to do exactly that! It's called `ghost-export` and you can install it like this:

	$ npm install -g ghost-export
    
Then, you can use it like so:

	$ ghost-export /path/to/ghost/app /path/to/output
    
You'll end up with a directory full of Markdown files from your blog. Simple!

For the source and more information, check out [ghost-export on Github](https://github.com/brianokeefe/ghost-export)!