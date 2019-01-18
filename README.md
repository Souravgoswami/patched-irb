# patched-irb
This is a patched irb (for Linux).

![alt screenshot](https://raw.githubusercontent.com/Souravgoswami/patched-irb/master/screenshots/Screenshot%20from%202019-01-18%2000-19-13.png)

The idea is When you run this, you are launched in the irb shell. But you can pass multiple gem names as argument. A common  function that irb lacks in loading history:

*Load history:* Press the up arrow key and down arrow key to browse previous histories (as you would do in your BASH/ZSH/etc.  shell)!

You have some methods like (note this are not a Ruby feature, you just get it with patched-irb):

*clear* : Right, `clear` clears the screen just like just like the linux command! The method clr is aliased with clr.

*history* : Show the histories from the .irb_history file. irb_history is also an alias for history method.

*hist!n* : Shows you the history in the nth line. Example: hist!5 will show you the history that's in the line 5 in .irb_history file.

*write_history* : Writes history to .irb_history file. The history comes from Readline::HISTORY. save_history is an alias for write_history.

*delete_history* : Warning! It will delete the .irb_history file. You will clear everything.

*printenv* : Just to test stuffs out... You will see some system details and Ruby interpreter details. The details comes from ENV object.

*config* : A bigger test! The details comes from RbConfig::CONFIG.

**How to use patched-irb:**

You need to download the file, and run the irb. Use it in the way you feel comfortable.
You may rename this and move that to /bin/ or /usr/share/bin/ or /opt/ directory.

We would like to rename it and hide it by adding a `.` in front. And alias it with irb.

Example:

    `alias irb=./irb`
    
    `irb securerandom time ruby2d json net/http socket open-uri`
    
This loads irb with securerandom time ruby2d json net/http socket open-uri gems!
    
We used an ARGV.each {} loop to require the gems, also the outputs are colourized.

The file has `#!/usr/bin/ruby -w`, which will turn on all the warnings. So you can learn ruby efficiently. You can edit it and remove the `-w` option if you like it that way...


A bit more details about the methods. More or less they are aliased so that if another gem uses the variable, you will still be able to use the alias:

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

*The history method also yields if a block is given:*.

    `history { |c| puts c }`
    
   
**We also have a method call colourize on String objects:**

  `puts 'hello'.colourize`
  
  `print 'hi'.colourize`
  
  `printf 'hello'.colourize`
  
  `warn 'hello'.colourize`
  
And so on...

Here we go:
![alt screenshot2](https://raw.githubusercontent.com/Souravgoswami/patched-irb/master/screenshots/Screenshot%20from%202019-01-18%2000-14-14.png)

*This file requires `io/console`, `irb`*
