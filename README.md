# MatrixTraverser

This program was written to solve the problem described below:

In this problem, you are given a matrix of positive integers, and your goal is to maximize a sum by selecting one element from every column in the matrix, moving left-to-right.  As you move through the matrix column-by-column, though, there may be a penalty to your sum depending on how you move relative to your previous two positions.  If the next row you select is between the previous two selected rows, there is no penalty; however, there is a penalty of 2 to your sum for every row above the maximum of the previous two or below the minimum of the previous two.  You always start in the first column of the matrix and your previous two rows are considered to be the top row.

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?M(j,r_{old},&space;r_{new})=\left\{\begin{matrix}&space;max&space;\left\{\begin{matrix}&space;A[1][j]-p(1,r_{old},&space;r_{new})&plus;M(j&plus;1,r_{new},1)&space;\\&space;A[2][j]-p(2,r_{old},&space;r_{new})&plus;M(j&plus;1,r_{new},2)&space;\\&space;\vdots&space;\\&space;A[n][j]-p(n,r_{old},&space;r_{new})&plus;M(j&plus;1,r_{new},n)&space;\end{matrix}\right&space;&&space;j\leq&space;m&space;\\&space;\\&space;0&space;&&space;otherwise&space;\end{matrix}\right." title="M(j,r_{old}, r_{new})=\left\{\begin{matrix} max \left\{\begin{matrix} A[1][j]-p(1,r_{old}, r_{new})+M(j+1,r_{new},1) \\ A[1][j]-p(1,r_{old}, r_{new})+M(j+1,r_{new},1) \\ \vdots \\ A[2][j]-p(2,r_{old}, r_{new})+M(j+1,r_{new},2) \end{matrix}\right & j\leq m \\ \\ 0 & otherwise \end{matrix}\right."/>
</p>
