# 1. Introduction
http://learnyouahaskell.com/introduction#about-this-tutorial

Don't tell the computer what to do, but what things are. As functions.  
No side effects, referential transparency, series of transformations.  
Lazy.  
Statically typed => catch errors. Type inference.  
GHC compiler, or Haskell Platform.  
`ghci` repl, `:l myfunction`, `:r`.  

# 2. Starting out
http://learnyouahaskell.com/starting-out

`/=`  
infix functions: +, *  
prefix functions: `succ 8`  
prefix evaluated before infix  
prefix => infix with backticks  
Never use paranthesis to indicate param, only order  
This is a very simple example of a common pattern you will see throughout Haskell. Making basic functions that are obviously correct and then combining them into more complex functions.  
Order of programs doesn't matter  
if then else - else is mandatory, always returns something, = expression  
Functions can contain ', but never start with upper case  
Function without params = definition  

__Lists__  
Homogenous  
(let to define stuff in ghci)  
[a,b,c]  
"hej" = ['h','e','j']  
++ to concat lists (has to walk through left)  
1:[2,3] to prepend item.  
!! to retrieve by index  
Lists in lists can be different length, but not type  
comparisons are lexiographical (funky! think dictionary)  
head vs tail, last vs init  
length, null (if empty), reverse
take 2 [list], drop
maximum, minimum, sum, product
elem 4 [list] - if the list contains

__Ranges__  
[1..20]  
[1, 3 .. 19]  
combine unlimited with take
cycle cycles list infinitely  
repeat repeats element  
replicate 3 10 => [10,10,10]

__List comprehensions__, similar to set comprehensions in math  
[x*2 | x <- [1..10], x*2 >= 12]  
length' xs = sum [1 | _ <- xs]   

__Tuples__  
Predefined length
Can contain different types
No singletons
fst and snd work on pairs
zip combines lists into list of pairs (different lengths ok)

# 3. Types and Typeclasses
http://learnyouahaskell.com/types-and-typeclasses

Static type system = known at compile time
Type inference
Type is a label for each expression, `:t` in ghci  
`::` = "has type of"

```
functionName :: param -> param -> output
functionName x y = x + y
```
Common types: Int, Integer (larger), Float, Fouble, Bool, Char.  
Type variable a, undefined type, polymorphic function  

__Typeclasses__  
Interface that implements behavior.  
```
ghci> :t (==)  
(==) :: (Eq a) => a -> a -> Bool
```
(Eq a) is the _class constraint_
Any type where equality makes sense should be a member of the Eq class.  

- Eq
- Ord(ering)
- Show (has string representation)
- Read (opposite, needs to know type)
- Enum (sequentially ordered, can be used in ranges and with succ/pred)
- Bounded
- Num (Int, Integer, Float, Double)
- Integral (Int, Integer)
- Floating (Float, Double)

# 4. Syntax in Functions
http://learnyouahaskell.com/syntax-in-functions

__Pattern matching__
Separate bodies for different patterns.  
Top to bottom.  
If nothing matches the program crashes.  
(x:xs) is common in recursion.  
error "Message" generates runtime error.  
@patterns are handy to keep a handle on the whole before splitting.  

__Guards (where bindingd)__  
A more readable if statement.  
Pipe and statement.  
end with `otherwise`  
add a `where` in the end for binding (consts or functions)  
```
bmiTell weight height
    | bmi <= skinny = "You're underweight, you emo, you!"  
    | bmi <= normal = "You're supposedly normal. Pffft, I bet you're ugly!"  
    | bmi <= fat = "You're fat! Lose some weight, fatty!"  
    | otherwise   = "You're a whale, congratulations!"
    where bmi = weight / height ^ 2
          skinny = 18.5
          normal = 25.0
          fat = 30.0
```

__Let bindings__  
let <bindings> in <expression>  
Very local.  
Separate with newline + indent or with semi colon.  
Can be used in list comprehensions (no _in_).  

__Case expressions__  
Just like pattern matching in function definitions.  
```
case expression of pattern -> result  
                   pattern -> result  
                   pattern -> result  
                   ...  
```

# 5. Recursion
http://learnyouahaskell.com/recursion  
No loops in haskell.  
Find edge condition/case.  
Num is not a subclass of Ord. That means that what constitutes for a number doesn't really have to adhere to an ordering. So that's why we have to specify both the Num and Ord class constraints when doing addition or subtraction and also comparison.  
Mostly examples. 

# 6. Higher Order Functions
http://learnyouahaskell.com/higher-order-functions  
Functions as parameters or return values.  

__Curried functions__  
"Functions actually only take one parameter, multiple params is actually currying."  
"Putting a space between two things is simply function application. The space is sort of like an operator and it has the highest precedence."  
`max 4 5 is equivalent to (max 4) 5`  
`max :: (Ord a) => a -> a -> a is equivalent to max :: (Ord a) => a -> (a -> a)`  
Calling with too few params returns a _partially applied function_.  
`compareWithHundred x = compare 100 x` is equivalent to `compareWithHundred = compare 100`  
"Sections" can create partials from infix `(/10)`.  
(Except `-`, use `subtract` instead).  

```
flip' :: (a -> b -> c) -> b -> a -> c  
flip' f y x = f x y
```

__Maps and filters__  



# 7. Modules
# 8. Making Our Own Types and Typeclasses
# 9. Input and Output
# 10. Functionally Solving Problems
# 12. A Fistful of Monads
# 13. For a Few Monads More
# 14. Zippers
