we'll show a few more advanced simplifications:
First of all, some simple one to make the eyes fill more comfortable with our expressions:
1)	Nums come before vars in multifaction >> x*4 ----> 4*x
This is implemented using  Mult numBefore() method.
2)	If a Log’s base is e we change it to Ln >> log(e,5) ----> ln(5)
This is implemented with a BinaryExpressions.Ln class that extends the Log class.
3)	We print e and π as symbols instead of numbers.
This is implemented with a Const class that extends the Num class.
Second, we cancel out (and add up also) expressions even if they don’t have similar strings:
1)	(5-x) – (x-5) ----> 0
2)	17x + 17x ----> 34x
3)	(5+(2x))/((3+x)+(2+x)) ----> 1
All of the above are implemented using the boolean areSame(Expression other)  method which is part of the expression interface.
The method operates with the following steps:
a)	For Var types – checks their strings match.
b)	For Num types – checks their value is the same.
c)	For BaseExpressions types – gets a set of all Vars in this and another set for other.
checks both sets are the same and if so creates a map holding a value for each Var. if the evaluate(map) for both expressions is the exact same returns true, else return false.
Also a few simple ones are:
1)	0/exp ----> 0
2)	Log (x, y) + log(x,4) ----> log (x, 4y)
3)	x*x ----> x^2
I also implemented the power rules:
1)	(x^y)^z ----> x^(y*z)
2)	x^y * x^z ----> x^(y+z)
finally I’ve implemented the associative and commutative properties:
1)	((2x+7y)+(2y+5x)) ----> (7x + 9y)
It works even as for entire expressions:
1)	(Ln(x^2) + y)+((2*y) + (3*Ln(x^2))) ----> ((4*Ln(x^2)) + (3*y))
