# patched-irb
This is a patched irb (for Linux).

![alt text](https://raw.githubusercontent.com/Souravgoswami/patched-irb/master/screenshot/a.png)

The idea is When you run this, you are launched in the irb shell. But you can pass multiple gem names as argument.

Example:
    `alias irb=./irb`
    `irb securerandom time ruby2d json net/http socket open-uri`
    
    
So this will load every gem from securerandom to open-uri in a ARGV.each loop, also the outputs are colourized.

The file has `#!/usr/bin/ruby -w`, which will turn on all the warnings. So you can learn ruby efficiently.

**We have a `clear` method** that you can use directly in irb. Type clear to `clear` the screen. Clear is also aliased with `clr`. You can also type `clr` to `clear` the screen!

**The session will be saved in a file named `.irb_history` while you exit irb. To skip this, use `exit!`**

**We have a `history` method**, which will load up the history saved at the exit time.

 *If you want to see 10 histories, type:*
      `history 10`

 *If you want to see the history in n number of line:*
      `hist!5`

 **If you want to delete all the history, type:**
      `delete_history`

**We call the `write_history` method only while exiting (exit and not exit!), or if you type** `write_history`

**For testing purpose, call `printenv` and `config` methods.**

*The history method also yields if a block is given:*
    `history { |c| puts c }`
    
   
**We also have a method call colourize on String objects:**

  `puts 'hello'.colourize`
  
  `print 'hi'.colourize`
  
  `printf 'hello'.colourize`
  
  `warn 'hello'.colourize`
  
And so on...

*This file requires `io/console`, `irb`*
