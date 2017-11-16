#include<iostream>
using namespace std;

class cmatrix{

public:
	int r,c;
	double **matrix;
	void  createInitializedMatrix ();
	cmatrix  createMatrix(int r , int c);
	void fillMatrix();
	void  printMatrix( );
	cmatrix add (cmatrix B);
	cmatrix subtract (cmatrix B);
	cmatrix transpose ();
	cmatrix InverseMatrix();
	cmatrix MultiplyMatrixBy(cmatrix B);
	cmatrix DevideMatrixBy(cmatrix B);
	cmatrix GetCofactor(int x, int y);
	double getDeterminant();
	cmatrix adjMatrix();


};

  cmatrix cmatrix:: createMatrix (int rows,int columns)
{   cmatrix h;
     h.matrix =  new double * [rows];
	 for(int i=0;i<rows;i++)
	 {
		 h.matrix[i] = new double [columns];

	 }

	 for(int i=0;i<rows;i++)
		 { for (int j = 0; j < columns; j++)
		 {
			 h.matrix[i][j]=0;
		 }
	 }

return h;
}
    void cmatrix:: createInitializedMatrix ()
{
      matrix =  new double * [r];
	 for(int i=0;i<r;i++)
	 {
		 matrix[i] = new double [c];

	 }

	 for(int i=0;i<r;i++)
		 { for (int j = 0; j < c; j++)
		 {
			 matrix[i][j]=0;
		 }
	 }

}

  void cmatrix:: fillMatrix(){
  cout<<"enter the matrix elements  of rows "<<" "<<r<<" "<<"and columns"<<" "<<c<<endl;
	for(int i=0;i<r;i++)
	{
		for(int j=0;j<c;j++)
		{
			cin>>matrix[i][j];
		}
	}

  }
  void cmatrix:: printMatrix( )
  {
	  for(int i=0;i<r;i++)
		{
			for(int j=0;j<c;j++)
		 {
			 cout<<matrix[i][j]<<" ";
		 }
			cout<<endl;
	  }
	  getchar();
  }
   	cmatrix cmatrix:: add (cmatrix B){
		cmatrix newMatrix ;
		newMatrix.r=r;
		newMatrix.c=c;
		newMatrix.createInitializedMatrix();
		for(int i=0;i<r;i++)
		{
			for(int j=0;j<c;j++)
			{
				newMatrix.matrix[i][j]=matrix[i][j]+B.matrix[i][j];
			}
		}
		return newMatrix;
	}
	 	cmatrix cmatrix:: subtract (cmatrix B){
		cmatrix newMatrix ;
		newMatrix.r=r;
		newMatrix.c=c;
		newMatrix.createInitializedMatrix();
		for(int i=0;i<r;i++)
		{
			for(int j=0;j<c;j++)
			{
				newMatrix.matrix[i][j]=matrix[i][j]-B.matrix[i][j];
			}
		}
		return newMatrix;
	}
		cmatrix cmatrix::transpose ()
		{ cmatrix newMatrix;
		 newMatrix.r=c;
		 newMatrix.c=r;
		 newMatrix.createInitializedMatrix();
		 for(int i=0;i<newMatrix.r;i++)
		 {
			 for(int j=0;j<newMatrix.c;j++)
			 {
				 newMatrix.matrix[i][j]=matrix[j][i];
			 }
	   	}
		   return newMatrix;
		}

cmatrix cmatrix:: MultiplyMatrixBy(cmatrix B)
{
	cmatrix newMatrix;
	newMatrix.r=r;
	newMatrix.c = B.c;
	newMatrix.createInitializedMatrix();

	for(int i=0;i<r;i++)
	{
		for(int j=0;j<B.c;j++)
		{
			for(int k=0;k<c;k++)
			{
               newMatrix.matrix[i][j] += matrix[i][k]*B.matrix[k][j];
			}
		}
	}
	return newMatrix;
}
// Get Cofactor of certain element
cmatrix cmatrix::GetCofactor(int x, int y)
{  // e is matrix to store the cofactor
   cmatrix e;
   e.r=r-1;
   e.c=c-1;
   e.createInitializedMatrix();

     int i=0,j=0;
     for(int iR=0;iR<r;iR++)
    {
        for(int iC=0;iC<c;iC++)
         {
              //  Copying into temporary matrix only those element
                //  which are not in given row and column
                if (iR != x && iC != y)
                {
                    e.matrix[i][j++] = matrix[iR][iC];

                    // Row is filled, so increase row index and
                    // reset col index
                    if (j == c - 1)
                    {
                        j = 0;
                        i++;
                    }
                }
         }
    }
     return e;
 }

//Function To get determinant of matrix using Cofactor

double cmatrix::getDeterminant()
{
    double value = 0; // Initialize result
	if( c !=r)
		throw("Invalid matrix dimension");
   //  Base case : if matrix contains single element
    if (r == 1 && c==1)
        return matrix[0][0];
    // Matrix to store result
    cmatrix temp;
    // To store sign multiplier
    int sign = 1;
    // Iterate for each element of first row
	for(int iR=0;iR<r;iR++)
	{   temp=GetCofactor(0,iR);
		value+= sign * matrix[0][iR] * GetCofactor(0, iR).getDeterminant();
		sign*=-1;
	}
	return value;
}

// To find Adjoint of Matrix
cmatrix cmatrix:: adjMatrix()
{
        cmatrix adj;
        adj.r=r;
        adj.c=c;
        adj.createInitializedMatrix();
        if (r == 1 && c==1)
        {
            adj.matrix[0][0] = 1;
            return adj;
        }
         int sign = 1;
         //cmatrix temp;
         //temp.createInitializedMatrix();

        for (int i=0; i<r; i++)
        {
            for (int j=0; j<c; j++)
            {
                // Get cofactor of A[i][j]
             // temp=GetCofactor(i,j);

                // sign of adj[j][i] positive if sum of row
                // and column indexes is even.
                sign = ((i+j)%2==0)? 1: -1;

                // Interchanging rows and columns to get the
                // transpose of the cofactor matrix
                adj.matrix[j][i] = (sign)*GetCofactor(i,j).getDeterminant();
            }
        }

       return adj;

}

// Function To find The Inverse Of Matrix
cmatrix cmatrix::InverseMatrix(){
    double resultDeterminant=getDeterminant();
    if (resultDeterminant == 0)
    {
        cout << "Singular matrix, can't find its inverse";
    }

	cmatrix newMatrix;
	newMatrix.r=r;
	newMatrix.c =c;
	newMatrix.createInitializedMatrix();
    cmatrix D=adjMatrix();

	for(int i=0;i<r;i++)
	{
		for(int j=0;j<c;j++)
		{

               newMatrix.matrix[i][j] += D.matrix[i][j]*double(1/resultDeterminant);

		}
	}
	return newMatrix;


}

// Function To devide Matrix By another Matrix
cmatrix cmatrix:: DevideMatrixBy(cmatrix B)
{
	cmatrix newMatrix;
	newMatrix.r=r;
	newMatrix.c = B.c;
	newMatrix.createInitializedMatrix();
	cmatrix D=B.InverseMatrix();
	for(int i=0;i<r;i++)
	{
		for(int j=0;j<B.c;j++)
		{
			for(int k=0;k<c;k++)
			{
               newMatrix.matrix[i][j] += matrix[i][k]*D.matrix[k][j];
			}
		}
	}
	return newMatrix;
}



#define n 2

int main()
{
	cmatrix A,B;

	A.r=n;A.c=n;B.r=n;B.c=n;
	A.createInitializedMatrix();
	B.createInitializedMatrix();
	A.fillMatrix();
	B.fillMatrix();
	cmatrix C;
	//cmatrix E;
	//double D;
	//C=A.MultiplyMatrixBy(B);
	//C.printMatrix();
	//C=A.transpose();
	//C.printMatrix();
	//getchar();
    //C=A.adjMatrix();
	 //C.printMatrix();
    //E=A.InverseMatrix();
    //E.printMatrix();
	//D=A.getDeterminant();
	//cout<<"Deter="<<D;
	C=A.DevideMatrixBy(B);
	C.printMatrix();
	getchar();
}
