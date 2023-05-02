Download Link: https://assignmentchef.com/product/solved-col226-assignment-3-parser-for-spreadsheet-language
<br>
Read the description file common to assignments 2-4

In Assignment 3: you need to specify the structure of formulas as a yacc grammar, and call the appropriate operations that will be provided to you as a module. Your implementation will be modular, in that you should be able to define your parser and create the interpreter framework irrespective of the actual implementation of the backend functions. You may assume the types of the backend functions.

Informal Syntax

<table>

 <tbody>

  <tr>

   <td width="115"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

Informally the grammar of our spreadsheet formula language is:

<ul>

 <li>An instruction has a head and a body. The head consists of a cell indexing the output destination of the formula, and the body consists of an expression being evaluated with respect to the spreadsheet. The head and the body are separated by an assignment sign (:=) A formula ends with a semicolon (;)</li>

 <li>The arguments of a function are either indices, ranges, constants or expressions using mathematical operations</li>

 <li>An index is a pair of integers. General format for an index l of a cell is [i, J] Examples are [0,0], [3,4],</li>

 <li>A range consists of two indices standing for the top left index and the right bottom index. General format for an range R of cells is ( I : I ) with an example being ( [ 5, 6] : [100, 6] )</li>

</ul>

The formulas provided to you are one on each line. The general format of a formula is given below:

Type 1 formula (unary operations on a range of cells)

Type 2 formula (binary operations on ranges)

FUNC R R ;

1 :- FUNC c R ;

FUNC R c ;

I FUNC I R ;

FUNC R I ;

Backend

You may assume there exists a module in OCamI with the following functions.

<ul>

 <li>full_count: sheet -&gt; range -&gt; index -&gt; sheet : Fills count of valid entries in the given range into the specified cell</li>

 <li>row_count: sheet -&gt; range -&gt; index -&gt; sheet : Fills count of valid entries per row in the given range into the column starting from the specified cell col_count: sheet -&gt; range -&gt; index -&gt; sheet : Fills count of valid entries per column in the given range into the row starting from the specified cell.</li>

 <li>full sum: sheet -&gt; range -&gt; index -&gt; sheet : Fills the sum of entries of cells in the given range into the specified cell</li>

 <li>row sum: sheet -&gt; range -&gt; index -&gt; sheet : Fills the sum of entries of cells per row in the given range into the column starting from the specified cell</li>

</ul>




<ul>

 <li>col sum: sheet range    index -&gt; sheet : Fills the sum of entries of cells per column in the given range into the row starting from the specified cell</li>

 <li>full avg: sheet range    index -&gt; sheet Fills the average of entries of cells in the given range into the specified cell</li>

 <li>row avg: sheet range    index -&gt; sheet : Fills the average of entries of cells per row in the given range into the column starting from the specified cell  col avg: sheet range    index -&gt; sheet Fills the sum of entries of cells per column in the given range into the row starting from the specified cell</li>

 <li>full min: sheet -&gt; range -&gt; index -&gt; sheet : Fills the min of entries of cells in the given range into the specified cell</li>

 <li>row min: sheet -&gt; range -&gt; index -&gt; sheet : Fills the min of entries of cells per row in the given range into the column starting from the specified cell col min: sheet -&gt; range -&gt; index -&gt; sheet : Fills the min of entries of cells per column in the given range into the row starting from the specified cell</li>

 <li>full max: sheet -&gt; range -&gt; index -&gt; sheet : Fills the max of entries of cells in the given range into the specified cell</li>

 <li>row max: sheet -&gt; range -&gt; index -&gt; sheet : Fills the max of entries of cells per row in the given range into the column starting from the specified cell col max: sheet -&gt; range -&gt; index -&gt; sheet : Fills the max of entries of cells per column in the given range into the row starting from the specified cell</li>

 <li>add const: sheet -&gt; range -&gt; float -&gt; index -&gt; sheet : adds a constant to the contents of each cell in the selected cell range</li>

 <li>subt const: sheet -&gt; range -&gt; float -&gt; index -&gt; sheet : subtracts a constant from the contents of each cell in the selected cell range mult const: sheet -&gt; range -&gt; float -&gt; index -&gt; sheet : multiplies the contents of each cell in the selected cell range by a constant.</li>

 <li>div const: sheet -&gt; range -&gt; float -&gt; index -&gt; sheet : divides the contents of each cell in the selected cell range by a constant.</li>

 <li>add range: sheet -&gt; range -&gt; range -&gt; index -&gt; sheet : adds the cell contents for each corresponding pair of cells in two selected cell ranges</li>

 <li>subt range: sheet -&gt; range -&gt; range -&gt; index -&gt; sheet : performs a subtraction on the cell contents for each corresponding pair if cells in two selected cell ranges mult range: sheet -&gt; range -&gt; range -&gt; index -&gt; sheet : multiplies the cell contents for each corresponding pair of cells in two selected cell ranges</li>

 <li>div range: sheet -&gt; range -&gt; range -&gt; index -&gt; sheet : performs a division on the cell contents for each corresponding pair of cells in two selected cell ranges</li>

</ul>