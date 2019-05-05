# patched-irb
This is a Patched IRB for Linux :penguin:
![screenshot](https://raw.githubusercontent.com/Souravgoswami/patched-irb/master/screenshots/sc2.jpg)

## What is Patched IRB❓
The idea is When you run this, you are launched in the irb shell :heart:. In patched IRB you can pass multiple gem names as argument, you can load up histories, clear the terminal, colourize strings, use QuickTools for some calculations! Also, just like regular IRB you can pass Patched IRB a file.

## Usage 💎
### Load history:
Press the up arrow key and down arrow key to browse previous histories (as you would do in your BASH/ZSH/etc. shell)!

### Methods:
+ clear: Right, `clear` clears the screen just like just like the Linux command! `clear` will also reset escape characters.  The method clr is aliased with `clear!`.


+ erase: It will erase the terminal except for the line you are in. It's aliased with `erase!`.

+ history: Show the histories from the .irb_history file. `history!` is also an alias for history method.

+ eval_hist!n : Evaulates the code in the nth line of the .irb_hist file. For example: `eval_hist!5` will run this code: `eval(hist!(n, true).to_s.strip)`. Thus it will evaluate whatever it gets from the file. Use it with caution, so you don't accidently do stuffs that you don't like to. Make sure what you type in the place of `n` is correct. It will not confirm of any mistakes. Its alias is simply `eval_hist n`

+ hist!n : Shows you the history in the nth line. Example: hist!5 will show you the history that's in line 5 in the .irb_history file. It's aliasesd with hist. You run `hist(5)` or `hist 5` for the same job that `hist!5` will do!

+ write_history: Writes history to .irb_history file. The history comes from Readline::HISTORY. `write_history!` is an alias for `write_history`.

+ delete_history: Warning! It will delete the .irb_history file. You will clear everything. It's not aliased with anything...

+ printenv: Just to test stuff out... You will see some system details and Ruby interpreter details. The detail comes from ENV object. It doesn't have any alias method.

+ config: A bigger test! The details come from RbConfig::CONFIG. it's not aliased either...

+ get_history_size: Another test. It will print the bytes (to standard output) that .irb_history occupies. It doesn't have any alias.

+ get_history_lines: Yet another test. It will print the total number of lines (to standard output) that .irb_history has. It has no alias.

**Note: You can easily override the above methods. You can do `clear = 5` and you can't use clear(). It will return 5. But We have aliased most of the methods so you can use them alternatively.**

## Patched String 🔡
Yes, we have the String class monkey patched so you can use `colourize` method on every String object. `colourize` is aliased with `to_colour`.

## Module
There's a module called QuickTools. You have various methods there:
+ colourize(string): Colourize string.
+ sort_word(string): Sort every character of string.
+ reverse_sort_word(string): Sort every character of string, and reverse it.
+ camelize(string): Camelize a String.
+ factorial(number): Calculate the factorial of number.
+ permutation(string): Split every character of string, return the possible ways of arranging the word.
+ prime(n): Return an Array of prime numbers upto n (n has to be an Integer).
+ prime?(n): Calculate if n is a prime of not (again, n should be an Integer).
+ benchmark(methods): Benchmark methods (require benchmark gem).
+ pi(n): Calculate Pi upto n decimal places and return a String (n is default to 1000).

## Running 🎽
You need to download the file, and run the irb. Use it in the way you feel comfortable.
You may rename this and move that to /bin/ or /usr/share/bin/ or /opt/ directory.

We would like to rename it and hide it by adding a `.` in front. And alias it with irb.

Example:

    `alias irb=$HOME/.irb`
    
So that we can run it in the following way:
    
    `irb securerandom time ruby2d json net/http socket open-uri`
    
This loads irb with securerandom time ruby2d json net/http socket open-uri gems!
    
We used an ARGV.each {} loop to require the gems, also the outputs are colourized.

The file has `#!/usr/bin/ruby -w`, which will turn on all the warnings. So you can learn ruby efficiently. You can edit it and remove the `-w` option if you like it that way...

## Screenshots 📸
![alt screenshot](https://raw.githubusercontent.com/Souravgoswami/patched-irb/master/screenshots/sc1.jpg)

*This file requires `io/console`, `irb`*

*Please give us more ideas about what to add and inform us about bugs!
