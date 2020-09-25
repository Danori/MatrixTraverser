# MatrixTraverser

The algorithm utilized in this program was written to solve the problem described below:

---

In this problem, you are given a matrix of positive integers, and your goal is to maximize a sum by selecting one element from every column in the matrix, moving left-to-right.  As you move through the matrix column-by-column, though, there may be a penalty to your sum depending on how you move relative to your previous two positions.  If the next row you select is between the previous two selected rows, there is no penalty; however, there is a penalty of 2 to your sum for every row above the maximum of the previous two or below the minimum of the previous two.  You always start in the first column of the matrix and your previous two rows are considered to be the top row.

If you start with row 3 in column 1 of the matrix, there will be a penalty of 4, because 3 is two more than max(1, 1). If you then move to row 2 in column 2, there would be no penalty becuase 2 is between 1 and 3. If you then moved to row 7, there would be a penalty of 8 because 7 is 4 more than max(2, 3).

The total "score" of the elements you select from the matrix will be the sum of the elements you selected, minus any penalties you accrued, and your algorithm should find the maximum possible score for the given matrix.

---

Consider the 3 x 4 matrix below:

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\begin{bmatrix}&space;2&space;&&space;3&space;&&space;4&space;&&space;1\\&space;5&space;&&space;1&space;&&space;2&space;&&space;4\\&space;4&space;&&space;5&space;&&space;3&space;&&space;4&space;\end{bmatrix}" title="\begin{bmatrix} 2 & 3 & 4 & 1\\ 5 & 1 & 2 & 4\\ 4 & 5 & 3 & 4 \end{bmatrix}"/>
</p>

The best score we can make for this matrix is 13 by choosing rows 2, 3, 3, 3 (3 + 3 + 3 + 4) from left-to-right.

---

This problem / project was given at the University of South Florida College of Engineering COT4400 Analysis of Algorithms course. It is an exercise in the use of dynamic programming. For a matrix <img src="https://latex.codecogs.com/svg.latex?A" title="A"/> with <img src="https://latex.codecogs.com/svg.latex?n" title="n"/> rows and <img src="https://latex.codecogs.com/svg.latex?m" title="m"/> columns, where your previously selected rows are <img src="https://latex.codecogs.com/svg.latex?r_{old}" title="r_{old}"/> and <img src="https://latex.codecogs.com/svg.latex?r_{new}" title="r_{new}"/>, you can break down a problem instance recursively by finding the maximum traversal of sub matrices with fewer columns. For every column, consider the maximum sums you can accumulate for a matrix only consisting of the next <img src="https://latex.codecogs.com/svg.latex?m-1" title="m-1"/> columns, based on all the possible row choices for the current column, and the previous column. Continue this process until there is simply one column remaining, at which point you can simply find how much score each row choice will contribute based on the penalties, and for each <img src="https://latex.codecogs.com/svg.latex?r_{old}" title="r_{old}"/> and <img src="https://latex.codecogs.com/svg.latex?r_{new}" title="r_{new}"/> permutation, choose the row which will contribute the most and store that result, because that choice will always be the best choice for the prior <img src="https://latex.codecogs.com/svg.latex?r_{old}" title="r_{old}"/> and <img src="https://latex.codecogs.com/svg.latex?r_{new}" title="r_{new}"/>. Then, work backwards for each column choosing the best possible row choice for every column, back to the original matrix, at which that point the best choice in this final column will be the maximum score possible. This process can be described mathematically in the recurrence below, where <img src="https://latex.codecogs.com/svg.latex?p"/> is a function to calculate the penalty for each row choice:

<p>
<img src="http://www.sciweavers.org/tex2img.php?eq=M%28j%2Cr_%7Bold%7D%2C%20r_%7Bnew%7D%29%3D%5Cleft%5C%7B%5Cbegin%7Bmatrix%7D%20max%20%5Cleft%5C%7B%5Cbegin%7Bmatrix%7D%20A%5B1%5D%5Bj%5D-p%281%2Cr_%7Bold%7D%2C%20r_%7Bnew%7D%29%2BM%28j%2B1%2Cr_%7Bnew%7D%2C1%29%20%5C%5C%20A%5B2%5D%5Bj%5D-p%282%2Cr_%7Bold%7D%2C%20r_%7Bnew%7D%29%2BM%28j%2B1%2Cr_%7Bnew%7D%2C2%29%20%5C%5C%20%5Cvdots%20%5C%5C%20A%5Bn%5D%5Bj%5D-p%28n%2Cr_%7Bold%7D%2C%20r_%7Bnew%7D%29%2BM%28j%2B1%2Cr_%7Bnew%7D%2Cn%29%20%5Cend%7Bmatrix%7D%5Cright%20%26%20j%5Cleq%20m%20%5C%5C%20%5C%5C%200%20%26%20otherwise%20%5Cend%7Bmatrix%7D%5Cright.&bc=White&fc=Black&im=png&fs=18&ff=modern&edit=0" align="center" border="0" alt="M(j,r_{old}, r_{new})=\left\{\begin{matrix} max \left\{\begin{matrix} A[1][j]-p(1,r_{old}, r_{new})+M(j+1,r_{new},1) \\ A[2][j]-p(2,r_{old}, r_{new})+M(j+1,r_{new},2) \\ \vdots \\ A[n][j]-p(n,r_{old}, r_{new})+M(j+1,r_{new},n) \end{matrix}\right & j\leq m \\ \\ 0 & otherwise \end{matrix}\right." width="879" height="198" />
</p>

---

The program contains code for both a memoized solution and an iterative solution, and randomly calls one to find the maximum sum. The program will output both the maximum score as well as the rows chosen to reach the necessary maximum sum to an "output.txt" file. The input format is simply a text document ("input.txt") containing a line of two integers n and m, representing the number of rows and columns, respectively. Then, the following n lines contain m integers, representing the matrix as you would expect to see in the typical representation. Feel free to create your own input.txt files to test out the program. It should be noted however that input validation was not considered for this program, as it was to simply develop a dynamic programming algorithm.

---

The original recursion without the use of dynamic program results in an <img src="https://latex.codecogs.com/svg.latex?\Theta&space;(n^m)" title="\Theta (n^m)" /> algorithm, however saving sub results actually reduces the algorithm to a poly-time complexity of <img src="https://latex.codecogs.com/svg.latex?\Theta&space;(n^3m)" title="\Theta (n^3m)"/>. Feel free to message me on how these complexities are derived.
