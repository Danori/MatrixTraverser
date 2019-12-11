# MatrixTraverser

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?M(j,r_{old},&space;r_{new})=\left\{\begin{matrix}&space;max&space;\left\{\begin{matrix}&space;A[1][j]-p(1,r_{old},&space;r_{new})&plus;M(j&plus;1,r_{new},1)&space;\\&space;A[1][j]-p(1,r_{old},&space;r_{new})&plus;M(j&plus;1,r_{new},1)&space;\\&space;\vdots&space;\\&space;A[2][j]-p(2,r_{old},&space;r_{new})&plus;M(j&plus;1,r_{new},2)&space;\end{matrix}\right&space;&&space;j\leq&space;m&space;\\&space;\\&space;0&space;&&space;otherwise&space;\end{matrix}\right." title="M(j,r_{old}, r_{new})=\left\{\begin{matrix} max \left\{\begin{matrix} A[1][j]-p(1,r_{old}, r_{new})+M(j+1,r_{new},1) \\ A[1][j]-p(1,r_{old}, r_{new})+M(j+1,r_{new},1) \\ \vdots \\ A[2][j]-p(2,r_{old}, r_{new})+M(j+1,r_{new},2) \end{matrix}\right & j\leq m \\ \\ 0 & otherwise \end{matrix}\right."/>
</p>
