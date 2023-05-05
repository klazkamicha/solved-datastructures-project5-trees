Download Link: https://assignmentchef.com/product/solved-datastructures-project5-trees
<br>
In this project, you will be dealing with a tree data structure that can represent <strong>mathematical expressions. </strong>Don’t worry, there’s no parsing this time, and the evaluation is far easier!

<h1>Starting point</h1>

<a href="https://jarrettbillingsley.github.io/teaching/classes/cs0445/projects/cs0445_proj5_materials.zip"><strong>Download and extract these materials.</strong></a> Contained are:

<strong>Expression.java </strong>, <strong>the file you will modify.</strong>

<strong>ExpressionError.java </strong>, just an exception type.

<strong>Driver.java </strong>, which is used to test <strong>Expression </strong>.

I’ve given you a starting point, but <strong>you should expand upon this and add more tests!</strong>

To compile and run, do:

<h1>Expression trees</h1>

Like I showed in class, trees come up a lot in representing languages, such as math and programming languages.

The <strong>Expression</strong> class represents a <strong>node</strong> in an expression tree. Each instance of <strong>Expression</strong> can be one of three things:

a <strong>Number </strong>in which case its <strong>_value</strong> is a string representation of the value.

you can use <strong>getNumberValue()</strong> to easily convert that string to a <strong>double </strong>.

a <strong>Variable</strong> name in which case its <strong>_value</strong> is the variable’s name.

an <strong>Operator </strong>in which case its <strong>_value</strong> is one of these operators: <strong>“+”, “-“, “*”, “/”,</strong> or <strong>“^” </strong>also, <strong>_left and </strong><strong>_right are its children</strong> – the operands to that operator.

There are no “bracket” nodes; order of operations is entirely determined by the tree’s structure.

Here are some examples of mathematical expressions and the trees which represent them:

Compare the last two trees. You can think of parentheses as saying, “force this part of the expression to be a sub-tree.”

<h1>Your task</h1>

Open <strong>Expression.java</strong> and look through it. There are already some methods written, but there are several stubbed-out ones with <strong>TODO</strong> inside them.

Each method gives you practice writing very common kinds of tree algorithms: <strong>visiting</strong> all the nodes in a tree; <strong>searching</strong> through a tree; creating a <strong>new tree</strong> which is a modification of an old one; and <strong>building a tree from scratch.</strong>

The next section documents some methods I wrote for you that will be helpful in writing these.

<h2>String toString()</h2>

returns a human-readable <strong>infix</strong> string representation of this expression tree. <strong>for numbers:</strong> return the string representation of its value. <strong>for variables:</strong> return the variable name (the <strong>_value</strong> member).

<strong>for operators:</strong> return a string of the form <strong>“(left op right)” </strong>, where:

<strong>left</strong> is the string representation of the <strong>_left</strong> member <strong>op</strong> is this operator (the <strong>_value</strong> member)

<strong>right</strong> is the string representation of the <strong>_right</strong> member

the result will have lots of parentheses. that’s correct &#x1f642;

<h2>String toPostfix()</h2>

returns a human-readable <strong>postfix</strong> string representation of this expression tree. this should be a very slight modification of <strong>toString() </strong>. <em>don’t forget to call </em><strong><em>toPostfix()</em></strong><em> recursively. </em>there should be no parentheses in the output.

<strong>double evaluate(Map&lt;String, Double&gt; variables) </strong>given a set of variables, evaluate the expression tree and return the result. <strong>for numbers:</strong> return the numerical value of the node ( <strong>getNumberValue() </strong>). <strong>for variables:</strong>

check             if          the       variable’s           name    ( <strong>_value </strong>)        exists    in          the       set        of         variables,           using <strong>variables.containsKey()</strong>

if not, throw an <strong>ExpressionError</strong> with a descriptive error message. if so, return the value from <strong>variables.get() </strong>.

<a href="https://docs.oracle.com/javase/8/docs/api/java/util/Map.html"><strong>Here is the documentation for </strong></a><a href="https://docs.oracle.com/javase/8/docs/api/java/util/Map.html"><strong>Map</strong></a> <a href="https://docs.oracle.com/javase/8/docs/api/java/util/Map.html">.</a> You can find the docs for <strong>containsKey()</strong> and <strong>get() </strong>there.

<strong>for operators: </strong>recursively evaluate the <strong>_left</strong> and <strong>_right</strong> children, using the same <strong>variables</strong> argument to them.

based on this operator ( <strong><sub>_value </sub></strong>), perform the right calculation on those two values and return the result.

<h2>Expression reciprocal()</h2>

returns a <strong>completely new</strong> expression tree that is the reciprocal of this one.

you will not be making recursive calls to <strong>reciprocal() </strong>, but <strong>you should use </strong><strong>clone() where appropriate.</strong>

there are 3 cases:

<strong>numbers:</strong> return a <strong>new</strong> number node whose value is the reciprocal.

<strong>division:</strong> return a <strong>new</strong> division node whose children are cloned and swapped. <strong>everything else:</strong> return a <strong>new</strong> division node whose children are 1 and a clone of this.

<h2>Set&lt;String&gt; getVariables()</h2>

returns a set containing all the unique variable names which appear in the expression tree.

the code I gave already creates the <strong>Set&lt;String&gt;</strong> for you.

it has an <strong>.add()</strong> method that you can use to add Strings to it.

you will have to write a <strong>private recursive method</strong> to actually find the variables, and have this call that one.

you will pass that <strong>variables</strong> set as an argument to it. think about how each kind of node will change the set (if at all).

<h2>static Expression geometricMean(double[] numbers)</h2>

You may not use <strong>quickParse()</strong> to implement this method. Sorry &#x1f609;

creates an <strong>Expression</strong> that represents the <a href="https://www.mathsisfun.com/numbers/geometric-mean.html"><strong>g</strong></a><a href="https://www.mathsisfun.com/numbers/geometric-mean.html"><strong>eometric mean</strong></a> of the array of numbers given as an argument. the resulting <strong>Expression</strong> should be of the form:

<strong>(numbers[0] * numbers[1] * … * numbers[n-1]) ^ (1 / n) </strong>where <strong><sub>n</sub></strong> is the length of the array.

(it’s OK to assume that the array is always at least 1 item long.) use the <strong>Number() </strong>, <strong>Operator() </strong>, and <strong>reciprocal()</strong> methods to create the expression.

making the chain of multiplications can be done iteratively or recursively.

it’s a fun little puzzle &#x1f642;

<h1>The methods I wrote for you</h1>

<strong>Number(double) </strong>makes a new <strong>Expression</strong> node containing a number. e.g. <strong>Expression e = Number(3.1415);</strong>

<strong>Variable(String)</strong>

makes a new <strong>Expression</strong> node containing a variable name. e.g. <strong>Expression e = Variable(“num_people”);</strong>

<strong>Operator(Expression, String, Expression) </strong>makes a new <strong>Expression</strong> node containing an operator, and which points to two children.

e.g. <strong>Expression e = Operator(Number(4), “/”, Number(5));</strong> for the expression <strong>4 / 5 </strong>. <strong>quickParse(String) </strong>parses a string into a tree of <strong>Expression</strong> nodes. supports <strong>+-*/^</strong> and regular parentheses <strong>() </strong>. e.g. <strong>Expression complex = Expression.quickParse(“1 / (5*x^2 + 3*x – 9)”);</strong>

<strong>quickParse</strong> has very little error checking and will likely crash or give weird results with erroneous

input. But it’s really there for testing purposes, so just give it valid expressions please &#x1f642;

<strong>isOperator() </strong>, <strong>isNumber() </strong>, <strong>isVariable() </strong>return <strong>boolean </strong>s saying what type of node this is. e.g. <strong>if(expr.isOperator()) … getNumberValue() </strong>for number nodes, parses the <strong>_value</strong> member into a <strong>double </strong>. for operator and variable nodes, will probably crash. (that’s why it’s private.)

<strong>clone() </strong>makes a complete copy of an expression, recursively. <strong>have a look at how this method is implemented!</strong>

<h1>Testing</h1>

<strong>Driver.java</strong> has a small amount of code in it to test your <strong>Expression</strong> methods. However it does pretty minimal testing. Like it tells you, <strong>TEST MORE THOROUGHLY!!!</strong> Use <strong>Expression.quickParse()</strong> to easily create test cases.

Here are the outputs I got from my implementation:

toString:        (((4.0 * x) + (y / 9.0)) + 12.0) toPostfix:       4.0 x * y 9.0 / + 12.0 + evaluate:        55.0 reciprocal:      (1.0 / (((4.0 * x) + (y / 9.0)) + 12.0)) reciprocal(num): 0.14285714285714285 reciprocal(div): (10.0 / x) getVariables:    [x, y]

geometricMean:   (((((4.0 * 9.0) * 3.0) * 7.0) * 6.0) ^ 0.2) it evalutes to:  5.3868466094227525

<h1>Extra Credit [+10]</h1>

<h2>String toNiceString()</h2>

Turns the expression into a nice string. &#x1f609;

This is like <strong>toString()</strong> but it will <strong>only put parentheses where needed. </strong>Hints:

Don’t forget to call <strong>toNiceString()</strong> recursively.

Decide whether to put parentheses around <em>each</em> of an operator’s <em>children.</em>

Think about when you, as a human, need to put parentheses in an expression. What is the rule there? What does it have to do with?


