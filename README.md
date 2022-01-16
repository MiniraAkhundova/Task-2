# Task-2
A rectangular map consisting of N rows and M columns of square areas is given. Each area is painted with a certain color.
 Two areas on the map belong to the same county if the following conditions are met:
- they have the same color;
 -it is possible to travel from one area to the other west or east) without moving over areas of a different color.
 
The map can be described by a zero-indexed matrix A consisting of N rows and M columns of integers. The color of each area is
described by the corresponding element of the matrix. Two areas have the same color if and only their corresponding matrix elements have the same value.
For example, consider the following matrix A consisting of seven
 rows and three columns:
А [0] [0] = 5 А [0] [1] = 4 А [0] [2] = 4
А [1] [0] = 4 А [1] [1] = 3 А [1] [2] = 4
А [2] [0] = 3 А [2] [1] = 2 А [2] [2] = 4
А [3] [0] = 2 А [3] [1] = 2 А [3] [2] = 2
А [4] [0] = 3 А [4] [1] = 3 А [4] [2] = 4
А [5] [0] = 1 А [5] [1] = 4 А [5] [2] = 4
А [6] [0] = 4 А [6] [1] = 1 А [6] [2] = 1

Answer+Explanation:

I have to created function Solution(In my code numberOfIslands) with one paramethr,namely Jagged Array A: public int solution(int[ ] [ ] A) ,using Java Script;
We get here a zero-indexed matrix A consisting of N rows and M columns of integers and it will return the number of different countries to
which the areas of the map described by matrix A belong
In our example is given matrix A consisting of seven rows and three columns corresponding to the example above, the function should return 11.

We want get our answer in console ,so that we write such code:
1.We will have two arrow functions checkNeighbourIsland with pharametres (A, B, i, j, N, M)
A-jagged array
B-arrays into jagged array
i-index of element by row
j-index of element by column
N-length of rows
M-length of columns

and second numberOfIsland function with pharametr A-jagged array

2.Initially when wanna get answer we path the pharametr(jaggedArray which we took as an example) to numberOfIslands function:
console.log('The number of different countries is: ', numberOfIslands([
            [5, 4, 4],
            [4, 3, 4],
            [3, 2, 4],
            [2, 2, 2],
            [3, 3, 4],
            [1, 4, 4],
            [4, 1, 1]
        ]));
3.Theese pharametr goes to function      
        const numberOfIslands = (A) => {
        
        //here we will count the count of countries
            let sum = 0;
            const N = A.length;
            const M = A[0].length;
            
            // N and M legth of row and column of jagged array
            
            if (N === 0 || M === 0) return 0;
            
            //we use here map function which consits values and indexes of values and after we iterate our array in this way
            const B = A.map(inner => inner.slice());
            for (let i = 0; i < N; i++) {
                for (let j = 0; j < M; j++) {
                    if (B[i][j] >= 0) {
                    
                    // if element is B[i][j] >= 0 then we will use following function where we check the 
                    // Neighbour Islands and if it relates to condition we make sum += 1 and return  the result
                    
                        checkNeighbourIsland(A, B, i, j, N, M);
                        sum += 1;
                    }
                }
            }
            return sum;
        }

4.We check here 
  const checkNeighbourIsland = (A, B, i, j, N, M) => {
            if (B[i][j] === -1) return;
           //it means that this element does not exsists
            B[i][j] = -1;
            
            //but if position i(by row to right ) + 1 < N we check theese neighbours A[i + 1][j] === A[i][j]
            if (i + 1 < N) {
                if (A[i + 1][j] === A[i][j]) {
                //we paste this element in array
                    checkNeighbourIsland(A, B, i + 1, j, N, M);
                }
            }
             //but if position i(by row to left ) - 1 >= 0 we check theese neighbours A[i - 1][j] === A[i][j]
            if (i - 1 >= 0) {
                if (A[i - 1][j] === A[i][j]) {
                        //we paste this element in array
                    checkNeighbourIsland(A, B, i - 1, j, N, M);
                }
            }
               //but if position i(by column to right ) + 1 < M we check theese neighbours A[i][j + 1] === A[i][j]
            if (j + 1 < M) {
                if (A[i][j + 1] === A[i][j]) {
                        //we paste this element in array
                    checkNeighbourIsland(A, B, i, j + 1, N, M);
                }
            }
               //but if position i(by column to right ) - 1 >= 0  we check theese neighbours A[i][j - 1] === A[i][j]
            if (j - 1 >= 0) {
                if (A[i][j - 1] === A[i][j]) {
                        //we paste this element in array
                    checkNeighbourIsland(A, B, i, j - 1, N, M);
                }
            }
        }
And this  jagged array gather all countries in function numberOfIslands where we get our answer
