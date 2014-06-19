I'm excited to say that I've released my first Ruby gem, `vhost_writer`! It's a command-line tool that will automatically generate virtual host configuration files based on a directory of existing websites and a given ERB template. You can give it a shot by installing it with `gem`:

	$ gem install vhost_writer
    
Then run it like this:

	$ vhost_writer /path/to/sites/ /path/to/configs/ /path/to/template.erb
    
I wrote this tool because it was something I wanted to use - I've got a lot of weird one-off sites with almost indentical vhost configs, so something like this suits my needs perfectly. Maybe you'll find it useful too!

I plan on continuing to develop some additional enhancements (the ability to take a config file, blacklist certain sites, generate sane default templates, and maybe more).

For more details as well as the source, check it out [on Github!](https://github.com/brianokeefe/vhost_writer)