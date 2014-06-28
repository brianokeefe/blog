I recently released my second gem, Lunartic. It allows you to easily calculate the phase of the moon on a given date. Check it out!

	$ gem install lunartic
	$ irb
	irb(main):001:0> require 'lunartic'
    	=> true

	# get moon data for today
	irb(main):002:0> moon = Lunartic.today
    	=> #<Lunartic::Moon:0x007fa5028e4dc0 @date=#<Date: 2014-06-25 ((2456834j,0s,0n),+0s,2299161j)>>
	irb(main):003:0> moon.day
    	=> 27
	irb(main):004:0> moon.phase
    	=> :waning_crescent
	irb(main):005:0> moon.percent_full
    	=> 0.17138763236974325

	# or, get moon data for a given Date
	irb(main):006:0> Lunartic.on_date(Date.new(1989, 12, 28)).phase
    	=> :new

Source code and more available on [Github](https://github.com/brianokeefe/lunartic).