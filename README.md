Hi! 👋

You've opened the IDE Sandbox. 🎉

The Sandbox is an environment that you can access on "readme" and "code-along" lessons in Learn. It's a great place to experiment with code when you're not working on a "lab" (labs open the IDE In Browser).

The work you do in the Sandbox will be saved from lesson to lesson, and is automatically saved on your behalf to a repository in your GitHub account called `learn-co-sandbox`.

Please DO NOT touch this repository in GitHub, as it will affect your Sandbox experience, and potentially cause your work to be out of sync.

To learn more about the Sandbox, please visit http://help.learn.co/ide-in-browser#sandbox.

//variables declared with var are only available within that function's scope
//variables declared without var attach themselves to the global object

function myFunction() {
  var y= 2;
  console.log(y);
}
//because the variable y in the myFunction function was defined with the var keyword, it is only available inside the function


var x = 1;
function myFunction(){
  y = 2;
  console.log(x);
}
myFunction(); //1
console.log(y); //2
console.log(x); //1
//because of the myFunction call, the global variable y exists, and console.log(y) will work

function outerFunction() {
  var innerVariable = "I'm sort of a secret"
  
  return function innerScope() {
    var inaccessible ='Nothing can touch me.';
    
    return innerVariable;
  }
}
var myScope = outerFunction();
myScope();  //"I'm sort of a secret."
innerScope(); //will throw an error undefined is not a function

//break loops

const array = ["dog", 1, "cat"]
for (let i=0; i < array.length; i++) {
  if (typeof array[i] !== 'string') {
    break
  }
  doSomethingToString(array[i])
}


//use break to find the first element that matches given criteria

const mostlyOne = [1, 1, 1, 1, 2, 1, 1, 3]

let notOne = null

for (let i=0; i < mostlyOne.length; i++) {
  if (mostlyOne[i] !== 1) {
    notOne = mostlyOne[i]
    break
  }
}


//we have to initalize a variable, notOne, and assign a value to it
//we can rewrite the final break by wrapping it in a function and using return to break out of the loop

function firstNotOne(array) {
  for (let i=0; i < array.length; i++) {
    if (array[i] !== 1) {
      return array[i]
    }
  }
}

const notOne = firstNotOne([1, 1, 1, 1, 1, 2, 1, 1, 1, 3])


function find(array, criteriaFunc) {
  for (let i = 0; i < array.length; i++) {
    if (criteriaFunc(array[i])) {
      return array[i]
    }
  }
}



//contine

const scores = [3, 4, 10, 5, 11, 6]
//increment all scores < 10
for (let i = 0; i < scores.length; i++) {
  if (scores[i] >= 10) {
    constinue
  }
  scores[i]++
}

//[4, 5, 10, 6, 11, 7]

//contine is helpful when we need to apply a few different operations within one loop





//Nested Objects

const person = {
  name: 'Awesome Name',
  occupation: {
    title: "Senior Manager of Awesome",
    yearsHeld: 2
  },
  pets: [{
    kind: 'dog',
    name: 'Fiona'
  }, {
    kind: 'cat',
    name: 'Ralph'
  }]
}

//to access yearsHeld use person.occupation.yearsHeld

//arrays in an array
const collections = [1, [2, [4, [5, [6]], 3]]]
//to access the number six use collections[1][1][1][1][0]


//criteria for finding an element in a nested data structure
function find(array, criteriaFn) {
  for (let i=0; i < array.length; i++) {
    if (criteriaFn(array[i])) {
      return array[i]
    }
  }
}

//find function with different data types
find( [1, 2, ["a", "b"]], function(someNumber){ return someNumber % 2 === 0} )



//arrow function syntax
find ( [1, 2, ["a", "b"]], someNumber => someNumber % 2 === 0)




//working with find but the array is like collections

function find(array, criteriaFn){
  //initalize two variables, 'current' and 'next'
  //'current' keeps track of the element that we're currently on
  //'next' is itself an array that keeps track of the elements
  let current = array
  let next = []
  //'while' loop will only trigger if 'current' is truthy
  //when we exhause 'next' and attempt to shift() 'undefined' (when next is empty)
  //onto current, we'll exit the loop
  //add || on this statement, if current is 0 it won't be run in the loop
  while (current || current === 0) {
  //if 'current' satisfies the 'criteriaFn', then return it
  //return will exit the entire function
    if (criteriaFn(current)) {
      return current
    }
  //if 'current' is an array, we want to push all of its elements onto 'next'
    if (Array.isArray(current)) {
      for (let i=0; i < current.length; i++) {
        next.push(current[i])
      }
    }
    //after pushing any children of 'current' onto 'next'
    //we wnat to take the first element of 'next' and make it the new 'current' 
    //for the next pass of the 'while' loop
    current = next.shift()
  }
  // if we haven't
  return null
}
  n => (typeOf n === 'number' && n > 5)
//implemented the first BREADTH-FIRST SEARCH
//that is one of the main algorithms used to search through nested objects







//intro to Ruby
//building a Ruby Tic Tac Toe board

//running a ruby command

/*if you type ruby -v it will print the version of ruby you are currently running. to run a ruby program, you would simply type ruby some-program.rb */

//words in a program - every word can be one of three possible things 

/*a ruby keyword, literaly data such as numbers or strings, or barewords like variables and methods */

// an error will be thrown if any of the words are not one of those three things 


//irb stands for "Interactive Ruby" - REPL read-evaluate-print-loop
//IRB is for testing code and exists temporarily, it will not get saved anywhere
/* to use, type irb in the terminal, type commands, and to leave the irb just type exit */

//ruby variables are set using the variable name followed by = and then the value
//variable names are snake_case instead of camelCase in JS 
//variables follow the value not the reference 

/*defining methods in ruby
def method_name
  method body
end */

//interpolate variables in ruby
/*to interpolate variables wrap the variable like this #{} 
puts "There are #{num_of_attendees} people coming to Beyonce's birthday party" */





CLI File structure
  typical root directory
    |-bin
    |   -tictactoe
    |-config
    |   -enviorment.rb
    |-lib
    |   -tic_tac_toe.rb
    |-spec
    |   -tic_tac_toe_spec.rb
    |   -spec_helper.rb
    |-Gemfile
    |-ttt.rb
    
    
bin/
  Code that relates to running our actual program
  executable files
  
config/ 
  code required to initalize the application's environment
  responsible for file requirements, establishing connections to database and ensuring test suite has access to the files that contain the code it is testing
  
lib/ (app/)
  Library directory
  files that define what the program can do
  all of methods and classes our program needs are defined within the files in this directory
  
spec/ (test/)
  contains all tests
    .rspec
    .learn
    Gemfile 
    Gemfile.lock
    Rakefile
      a gem is a library of code that you can include in your Ruby program to lend it the capabilities of that library


Running CLI Applications
  in order to run our program from a command line, a few things need to be set up:
    1. bin directory - "bin" is short for "binary" and is just another way to refer to executable files. (Your executable files belong in this directory)
      executable files - any file that contain instructions in a form that a computers opertating system or application can understand and follow
        any executable files we place in the bin directory need to begin with:
          #!/usr/bin/env ruby 
        this is refered to as the "shebang line" and it tells the shell which interperter to use to execute the remainder of the file
      Using the above setup, you can run your program by typing:
        ruby bin/< your file name >   in the command line
      You can also execute your program by simply typing:
        ./bin/< your file name >    in the command line 
          since the shebang line at the top of your executable file is already telling the shell to use Ruby to interpret the rest of the file
      Generally our executable file is responsible for running our program


File Permissions and chmod
  executable files are given expilcit permission to execute 
  when we execute code through the ruby interperter with the ruby command, your shell has already given the ruby command permission to execute code
  in order for your shell to execute a file via a command like ./bin/<file name>
  
  
  
Ruby boolean opertators
  boolean opertators are methods that have return values of true and false
    in ruby there are three main boolean opertators:
      ! (single bang opertator) which represents "NOT"
        reverses the logical state of its operand: if a condition is true, then ! will make it false
      && (double ampersand) which represents "AND"
        for && to evalaute to true, both values of either side of the symbol must evalaute to true
      || (double pipe) which represents "OR"
        for || to evalaute to true, only one value on either side of the symbol must evalaute to true
        
  other opertators
    != if the value of two operands are not equal, then the evaluation is true
    >,<,<=,>= greater than, less than, greater than or equal, less than or equal    
  Comparison opertators
    == (double equal sign) checks if two values are equal to return true if not false is returned
      * the comparison operator (==) is distinct from the assignment operator(=) that is used to set a variable equal to a value 
      
      
The LOOP keyword
  This is the simplest looping construct that we have in Ruby.
    It executes a block (the code between do and end keywords)
    
      ex: loop do
            puts "Hello World!"
            break
          end
          
  counter
      ex: counter = 0 
          loop do 
            counter + 1 
            puts "Iteration #{counter} of the loop"
            if counter >= 10
              break
            end
          end
          
+= for increments, we are adding a new incrememnt to a known value
  counter = 0 
  loop do 
    counter += 1 
    puts "Iteration #{counter} of the loop"
    if counter >= 10
      break
    end
  end
  
  
while loops
  The while construct will keep executing a block as long as a specific condition is true
  
  ex: num_of_laps = 0 
      while num_of_laps < 10
        num_of_laps += 1 
        puts "You have completed #{num_of_laps} lap(s)"
      end
      
      puts "You completed a total of #{num_of_laps} laps!"
      
      
until loops
  until is simply the inverse of a while loop.
  An until keyword will keep executing a block until a specific condition is true
    the block of code following until will execute while the condition is false
      think about it as to read until as "if not"
      
  ex: counter = 0 
      until counter == 20
        puts "The current number is less than 20"
        counter += 1 
      end 
      
      
Iteration vs Looping 
  Looping occurs when you tell your program to do something a certain number of times
  Iteration occurs when you have a collection of data (array) and you operate on each member of the collection
  
  ex: basket = ["apple 1","apple 2","apple 3","apple 4","apple 5","apple 6","apple 7","apple 8","apple 9","apple 10"]
      apples_in_basket = basket.size # Step 1
      apples_taken_out = 0
      basket.each do |apple|
        puts "Taking out #{apple}"
        apples_taken_out += 1
      end
      
  you can also use curly brackets to establish a code block instead of do/end
  
    ex: brothers = ["Tim", "Tom", "Jim"]
        brothers.each{|brother| puts "Stop hitting yourself #{brother}!"}
        
    it is appropriate to use the {} syntax when the code block is short and fits on one line
    
    
Nested Arrays 
  Arrays are a container for grouped data
  in ruby arrays can contain all types of data including other arrays
  
Acessing Data from a Nested Array
  To access data from a nested array, we double up on bracket notation to access the second, nested level of the array 
  
  nested_students = [
  ["Mike", "Grade 10", "A average"],
  ["Tim", "Grade 10", "C average"],
  ["Monique", "Grade 11", "B average"]
  ]
  nested_students[0][0] #=> "Mike"
  
  The first set of brackets refer to the top level of the nested array
  You can set the return value equal to a variable, and then can operate on it further 
  
  mike = nested_students[0]
  mike[0] #=> "Mike"
  
Adding Data to a Nested Array 
  To add data to a nested array, use <<, or shovel, method to add to a one-dimensional array
  
  students = ["Mike", "Tim", "Monique"]
  students << "Sarah"
  students #=> ["Mike", "Tim", "Monique", "Sarah"]
  
  To add to a nested array:
    First we have to access the data in which we want to add more data to
    Then hit it with the shovel
    
  nested_students[2] << "Class President"
  
  
Iterating Over Nested Arrays 
#each
  When working with a one-dimensional array and want to do something with every element, we iterate using methods like .each and .collection
  
  ex: students.each do |student|
        puts student
      end
      
  In order to manipulate on each element of a nested array, dig down into that level of the array
  
  nested_students = [
  ["Mike", "Grade 10", "A average"],
  ["Tim", "Grade 10", "C average"],
  ["Monique", "Grade 11", "B average", "Class President"]
  ]
  
  Access the first level of the nested array
    nested_students.each do |student_array|
      puts student_array.inspect 
    end 
    
  Access the second level of the nested array
    nested_students.each do |student_array|
      student_array.each do |student_deatil|
        puts student_deatil
      end
    end
When we are iterating over objects in a collection with each we generally don't care about the return values

#all?
  For the all? enumerator the block passed to it must return true for every iteration for the entire #all? method to return true
  
  all_odd = [1,3].all? do |number|
  number.odd? # Will evaluate to true for 1, true for 3
  end #=> true
  all_odd #=> true
  
  if any iteration returns false the entire #all? method returns false 
  
  all_odd = [1,2,3].all? do |number|
  number.odd? # Will evaluate to true for 1, false for 2, true for 3
  end #=> false
  all_odd #=> false
  
#none?
  The opposite of the #all? method 
  
  [1,3].none?{|i| i.even?} #=> true
  
  The entire #none? expression returns true because none of those numbers will produce a true expression when asked within the block if they are even
  
  if any of the elements in the collection evaluate to true when passed to the block, #none? will return false. If none of the elements evaluate to true, #none? will return true.
  
#any?
  To ensure that aleast one element in a collection will create a true expression within the block passes
  The any? enumerator will return true if atleast one iteration of the block evaluates to true, but false if none of them do
  
  [1,2,100].any?{|i| i > 99} #=> true
  
#include?
  include? will return true if the given object exists in the element. If it doesn't match it will return false
  
  the_numbers = [4,8,15,16,23,42]
  the_numbers.include?(42)   #=> true
  the_numbers.include?(6)   #=> false
  
  The #include? expression first returns true because the_numbers[5] == 42. When it is run with 6, it will evaluate to false since that item is not present in the array.
  
#select
   the return value will be a new array containing all the elements of the collection that cause the block passed to #select to return true.
    for each iteration, if the block evaluates to true, the element yielded to that iteration will be kept in the return value array.
      [1,2,3,4,5].select do |number|
       number.even?
      end #=> [2,4]
      
    Notice that if no element makes the block evaluate to true, an empty array is returned.
    
#detect or #find
  two names for the same method and can be used interchangibly
  will only return the first element that makes the block true
  
  [1,2,3].detect{|i| i.odd?} #=> 1
  
  Notice also that #detect will always return a single object where #select will always return an array.
  
#reject 
  reject will return an array with the elements for which the block is false.

  [1,2].reject{|i| i.even?} #=> [1]
  
  
  
  
Create a class in ruby
  class names are CamelCase and begin with a capital letter
  use the .new notation to add new instances to the class
  
  class Dog
  end
 
  fido = Dog.new
  fido #=> #<Dog:0x007fc52c2d7d20>
 
  snoopy = Dog.new
  snoopy #=> #<Dog:0x007fc52c2d4170>
  
Building Instance Methods

class Dog
  def bark
    puts "Woof!"
  end
end
 
fido = Dog.new
fido.bark #> "Woof!"

By defining #bark within the Dog class, bark becomes a method of all instances of Dogs. If we make more dogs, they can all bark.

class Dog
  def bark
    puts "Woof!"
  end
end
 
fido = Dog.new
fido.bark #> "Woof!"
 
snoopy = Dog.new
snoopy.bark #> "Woof!"

#initalize method
getter and setter Methods

class Person
 
  def initialize(name)
    @name = name
  end
 
  def name
    @name
  end
 
  def name=(new_name)
    @name = new_name
  end
 
end
 
kanye = Person.new("Kanye")
kanye.name #=> "Kanye"

class Person
 
  def initialize(first_name, last_name)
    @first_name = first_name
    @last_name = last_name
  end
 
  def name=(full_name)
    first_name, last_name = full_name.split
    @first_name = first_name
    @last_name = last_name
  end
 
  def name
    "#{@first_name} #{@last_name}".strip
  end
 
end

If we want each instance of our class to be created with certain attributes, we must define an #initialize method 
  this is a method that is called automatically whenever #new is used
  
class Dog
  def initialize(breed)
    @breed = breed
  end
 
  def breed=(breed)
    @breed = breed
  end
 
  def breed
    @breed
  end
end

We can call #new like this

lassie = Dog.new("Collie")
 
lassie.breed #=> "Collie"

When new is called with an argument, it will pass that argument (or arguments) to the #initializemethod and invoke that method
  the code in #initialize will then run, using an arguments from #new
It is a callback method, it is automatically invoked everytime the #new method is used to create new instances of the class 
