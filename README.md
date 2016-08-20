# Simple Logger #
A simple yet powerful Ruby logger

## What is Simple Logger? ##
This is a single module that you can drop into any Ruby application to give yourself a more powerful **and simple** API for logging.

## Why? Doesn't Ruby already have a Logger class?
Yes, but I don't like using it as much. Here's some reasons:

1. It requires you to create a Logger instance and use that, passing that around. I'd like some "magic" so I can just have a logging method.
2. It has lots of logging levels: DEBUG, INFO, WARN, ERROR, FATAL.  Personally, I've only ever needed two: INFO and DEBUG. INFO for normal messages, DEBUG for, well, debugging messages.
3. It is missing some things, that seem to go with logging:
  - logging the class (And optionally even the method/line) or module being used
  - logging the memory consumption of the application
  - others?

Over time I found that I preferred a single module to include that had all the logging functionality I needed and none that I didn't. I also love the simpler DSL this affords.

## Install the gem ##

Install it with [RubyGems](https://rubygems.org/)

```ruby
gem install simplelogger
```

or add this to your Gemfile if you use [Bundler](http://gembundler.com/):

```ruby
gem "simplelogger"
```

## Usage ##

To use Simple Logger, make sure to `require` it and then `include` it in your app:

```ruby
require 'simplelogger'

class MyApp
  include SimpleLogger

  def some_method
    log "here is a log message"
    debug { "Repeated message!" * 4 }
  end

  def self.class_method
    log "logging in a class method"
    self.log "this also works"
    MyApp.log "So does this"
    SimpleLogger.log "and this too!"
  end
end
```
