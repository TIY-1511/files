# files

#### Writing to a file

Using the File class:

```ruby
file_name = "example.txt"
file = File.open(file_name, "w")
file.puts "This is text"
file.close
```

### Excercises

Use exception handling to make sure that code above always closes the file

### Writing to a file - cont.

Using block notation:

```ruby
file_name = "example.txt"
File.open(file_name, "w"){ |file| file.puts "Contents of the file"}
```
The file is automatically closed when the block ends


### Reading a file

There are a few options to read a file:

```ruby 
file = File.open("example.txt", "r")
contents = file.read
puts contents   
file.close
```

and

```ruby
f = File.open("my/file/path", "r") 
f.each_line do |line| 
  puts line 
end 
f.close
```

Using a block:

```ruby
contents = File.open("sample.txt", "r"){ |file| file.read }
puts contents
```

The file is automatically closed when the block ends

### readlines and readline

A very common approach to reading files:

```ruby
File.open("example.txt").readlines.each do |line|
   puts line
end
```

This is referred when dealing with large files:

```ruby
file = File.open("example.txt", 'r')
while !file.eof?
   line = file.readline
   puts line
end
file.close
```
Note: don't forget to use exception handling in this example

Readline loads the entire file at once into memory. While this is fine for most applications, this is not good practice if the file is very large, especially if it is running on a server that is serving multiple users. - Ref http://ruby.bastardsbook.com/chapters/io/

##### Exercises
Create an audit log for the Bank class
* Each time a transfer happens, write the details to a comma seperated file (csv). 
* Name the file: audit_log.csv
* each row should contain a time stamp, the two account numbers and the value that was transferred
