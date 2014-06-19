My [recent adventures](https://github.com/brianokeefe/vhost_writer) have had me working with both RSpec and Thor for the first time. I had to do a little tinkering to come up with a strategy for using the two together harmoniously -- here's what I found.

## Handling Input

The cool thing about Thor is that you can call all of a Thor object's command-line methods programmatically, which makes for convenient testing.

* You can test different commands simply by calling the method on your subject (example: `$ my_gem command` becomes `subject.command`)
* Additional arguments match up with your method's parameters (`$ my_gem command foo` becomes `subject.command 'foo'`)
* You can set flags programmatically by modifying your object's `options` hash (you can simulate `$ my_gem command --foo` by setting `subject.options = {:foo => true}` before you call `subject.command`)


## Handling Output

Testing output is a little bit less straightforward. [This thread](http://stackoverflow.com/questions/12673485/how-to-test-stdin-for-a-cli-using-rspec) helpfully pointed out to me [a very convenient capture method in Thor's spec helper](https://github.com/erikhuda/thor/blob/d634d240bdc0462fe677031e1dc6ed656e54f27e/spec/helper.rb#L49):


    def capture(stream)
      begin
        stream = stream.to_s
        eval "$#{stream} = StringIO.new"
        yield
        result = eval("$#{stream}").string
      ensure
        eval("$#{stream} = #{stream.upcase}")
      end

      result
    end

You can include this method in your `spec_helper.rb` and use it like so:

	let(:output) { capture(:stdout) { subject.command 'foo' } }

This will capture the stdout you would get from running your command and store it in `output`, which you can test against. Hooray!

You might be tempted (as I was) to test all of your commands using the `capture` method, but one important caveat to remember is that `let` is always lazy-loaded. This means that if you're testing something other than stdout (which is most likely the case if you expect a command to run quietly), the method won't ever be called. In those cases, I call the method in a `before` block, which will always be evaluated.