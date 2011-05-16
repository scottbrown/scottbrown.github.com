---
layout: default
title: Getting Staticmatic To Work On EEEBuntu (Asus EEEPC 1000HE)
published: true
categories:
  - information technology
tags:
  - eeebuntu
  - eeepc
  - ruby
  - staticmatic
---

After I installed ruby and rubygems via apt-get, I installed staticmatic.

    $ sudo apt-get install ruby
    $ sudo apt-get install rubygems

    $ sudo gem install staticmatic

I received an error about "makemf", which meant that I had to install the
ruby 1.8 development code.

    $ sudo apt-get install ruby1.8-dev

After that, staticmatic was installed in my system.  No errors from gem
at all.  But lo and behold, something wasn't right.  On the command line
when I tried to execute staticmatic:

    $ staticmatic

I was greeted with...nothing.  I checked where the executable was coming
from:

    $ which staticmatic

And it found nothing.  It is normally supposed to be installed in /usr/bin,
so I checked my path and /usr/bin was in there:

    $ echo $PATH | grep /usr/bin
    /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/bin

On another system (my Ubuntu desktop system) the executable was installed
in /usr/bin correctly, so I inspected that file (which is just a plan ruby
file).  I copied the executable onto my eeepc, producing the code below:

    #!/usr/bin/ruby1.8

    require 'rubygems'
    version = ">= 0"

    if ARGV.first =~ /^_(.*)_$/ and Gem::Version.correct? $1 then
      version = $1
      ARGV.shift
    end

    gem 'staticmatic', version
    load 'staticmatic'

I saved this file in /usr/bin and changed the permissions to 755.  I then
ran the executable and the following happens:

    $ staticmatic
    /usr/lib/ruby/1.8/rubygems.rb:578:in `report_activate_error': Could not find RubyGem newgem (>= 1.1.0) (Gem::LoadError)
    from /usr/lib/ruby/1.8/rubygems.rb:134:in `activate'
    from /usr/lib/ruby/1.8/rubygems.rb:158:in `activate'
    from /usr/lib/ruby/1.8/rubygems.rb:157:in `each'
    from /usr/lib/ruby/1.8/rubygems.rb:157:in `activate'
    from /usr/lib/ruby/1.8/rubygems.rb:49:in `gem'
    from /usr/bin/staticmatic:11

It seems that staticmatic needs the newgem gem.  So I installed that:

    $ sudo gem install newgem

Which installed newgem and 5 other gems, but no errors were found.  So I again tried
to run staticmatic:

    $ staticmatic
    /usr/lib/ruby/1.8/rubygems.rb:578:in `report_activate_error': Could not find RubyGem cucumber (>= 0.1.8) (Gem::LoadError)
    from /usr/lib/ruby/1.8/rubygems.rb:134:in `activate'
    from /usr/lib/ruby/1.8/rubygems.rb:158:in `activate'
    from /usr/lib/ruby/1.8/rubygems.rb:157:in `each'
    from /usr/lib/ruby/1.8/rubygems.rb:157:in `activate'
    from /usr/lib/ruby/1.8/rubygems.rb:158:in `activate'
    from /usr/lib/ruby/1.8/rubygems.rb:157:in `each'
    from /usr/lib/ruby/1.8/rubygems.rb:157:in `activate'
    from /usr/lib/ruby/1.8/rubygems.rb:49:in `gem'
    from /usr/bin/staticmatic:11

So now it needs the cucumber gem!  Geez, you'd think that these would be listed as dependencies
when you install the staticmatic gem.  So I installed the cucumber gem, with only one error
resulting.

    $ sudo gem install cucumber
    Successfully installed term-ansicolor-1.0.3
    Successfully installed polyglot-0.2.5
    Successfully installed treetop-1.2.5
    Successfully installed diff-lcs-1.1.2
    Successfully installed builder-2.1.2
    Successfully installed cucumber-0.2.2
    6 gems installed
    Installing ri documentation for term-ansicolor-1.0.3...
    Installing ri documentation for polyglot-0.2.5...
    Installing ri documentation for diff-lcs-1.1.2...
    Installing ri documentation for builder-2.1.2...
    ERROR:  While generating documentation for builder-2.1.2
    ... MESSAGE:   Unhandled special: Special: type=17, text="<!-- HI -->"
    ... RDOC args: --ri --op /var/lib/gems/1.8/doc/builder-2.1.2/ri --title Builder -- Easy XML Building --main README --line-numbers --quiet lib CHANGES Rakefile README doc/releases/builder-1.2.4.rdoc doc/releases/builder-2.0.0.rdoc doc/releases/builder-2.1.1.rdoc
    (continuing with the rest of the installation)
    Installing ri documentation for cucumber-0.2.2...
    Installing RDoc documentation for term-ansicolor-1.0.3...
    Installing RDoc documentation for polyglot-0.2.5...
    Installing RDoc documentation for diff-lcs-1.1.2...
    Installing RDoc documentation for builder-2.1.2...
    Installing RDoc documentation for cucumber-0.2.2...

The error listed here is in the RDoc, so it doesn’t matter much (mental note, try to fix
this myself and add as a patch to repository).  I then tried to run staticmatic again, this
time crossing my fingers, toes, *and* eyes.

    $ staticmatic
    Usage: /usr/bin/staticmatic <build|setup|preview> <directory>

Huzzah!  We have lift off!

