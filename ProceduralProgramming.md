# Do the languages support Procedural Programming?

## C# (sharp)

* C# is not a procedural programming language according to [Wikipedia](https://en.wikipedia.org/wiki/Category:Procedural_programming_languages), and does not cleanly allow for procedural programming.  A procedural style can be mimicked, but not easily.

* The example below shows a simple program detailing how procedural programming looks in C#.
```csharp
void printNumber(int num) {
    printf("%dn", num);
}
 
int main() {
    // print '5'
    printNumber(5);
}
```

## Ruby

* [Wikipedia](https://en.wikipedia.org/wiki/Ruby_(programming_language)) states that "Ruby has been described as a multi-paradigm programming language: it allows procedural programming (defining functions/variables outside classes makes them part of the root, 'self' Object), with object orientation . . . or functional programming."

* Ruby supports procedural programming, but not purely procedural programming as would be found in true procedural languages.

* This example shows a procedural programming example in Ruby:
```ruby
board = Array.new(9, " ") # Creates an array with 9 elements filled with " "

def current_player(board)
  turn_count(board) % 2 == 0 ? "X" : "O"
end

def turn_count(board)
  board.count{|token| token == "X" || token == "O"}
end

def display_board(board)
  puts " #{board[0]} | #{board[1]} | #{board[2]} "
  puts "-----------"
  puts " #{board[3]} | #{board[4]} | #{board[5]} "
  puts "-----------"
  puts " #{board[6]} | #{board[7]} | #{board[8]} "
end
```
