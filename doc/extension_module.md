# -- Extension modules --

An extension module allows you to script your box through the veewee box API.

From within an extension module:

* you have access all box instance variables
* you can use all box methods (up, halt, console_type ...)


## -- Implementation --

The module file name must follow the rails `lowercase and underscore`convention.
E.g  an extension module named `MyModule` must be defined in a file named `my_module.rb`

Because the extension module is injected into a box
all methods from it are added to the box instance.
After injecting the extension module the `run_extension` is called.

## -- Example --

file `my_module.rb`
<pre>
module PostModule

  def self.extended(clazz)
    puts "The box #{clazz} has extended me!"
  end

  def run_extension
    up()
    sleep(10)
    console_type("Hello World")
  end
end
</pre>

Run the extension module:
<pre>
veewee vbox extension mybox ~/path/to/my_module.rb
</pre>