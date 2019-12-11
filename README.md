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

The best score we can make for this matrix is 13 by choosing rows 2, 3, 3, 3 (3 + 3 + 4 + 3)from left-to-right.

---

This problem / project was given at the University of South Florida College of Engineering COT4400 Analysis of Algorithms course. It is an exercise in the use of dynamic programming. A problem instance of this problem can be broken up into smaller sub matrices. For a matrix <img src="https://latex.codecogs.com/svg.latex?A" title="A"/> with <img src="https://latex.codecogs.com/svg.latex?n" title="n" /> rows and <img src="https://latex.codecogs.com/svg.latex?m" title="m" /> columns, where your previously selected rows are <img src="https://latex.codecogs.com/svg.latex?r_{old}" title="r_{old}"/> and <img src="https://latex.codecogs.com/svg.latex?r_{new}" title="r_{new}"/>

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?M(j,r_{old},&space;r_{new})=\left\{\begin{matrix}&space;max&space;\left\{\begin{matrix}&space;A[1][j]-p(1,r_{old},&space;r_{new})&plus;M(j&plus;1,r_{new},1)&space;\\&space;A[2][j]-p(2,r_{old},&space;r_{new})&plus;M(j&plus;1,r_{new},2)&space;\\&space;\vdots&space;\\&space;A[n][j]-p(n,r_{old},&space;r_{new})&plus;M(j&plus;1,r_{new},n)&space;\end{matrix}\right&space;&&space;j\leq&space;m&space;\\&space;\\&space;0&space;&&space;otherwise&space;\end{matrix}\right." title="M(j,r_{old}, r_{new})=\left\{\begin{matrix} max \left\{\begin{matrix} A[1][j]-p(1,r_{old}, r_{new})+M(j+1,r_{new},1) \\ A[1][j]-p(1,r_{old}, r_{new})+M(j+1,r_{new},1) \\ \vdots \\ A[2][j]-p(2,r_{old}, r_{new})+M(j+1,r_{new},2) \end{matrix}\right & j\leq m \\ \\ 0 & otherwise \end{matrix}\right."/>
</p>
