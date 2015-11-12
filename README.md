# Dynamic-Matrix

//****************************************************************************
//
//Daniel Augustine
//Period 5
//CompSci II AP
//In this lab I will demonstrate my understanding of Arrays, ArrayLists, Matrix
//*****************************************************************************
import java.util.ArrayList;


public class Matrices
{
	public static void main(String args[])
	{
		System.out.println("\nDaniel Augustine\n");
		
		Matrix m1 = new Matrix();
		m1.displayMatrix("Matrix m1 Default Display");
		System.out.println();
		
		Matrix m2 = new Matrix(3,5);
		int count = 100;
		for(int r = 0; r < m2.getRows(); r++)
		{
			for(int c = 0; c < m2.getCols(); c++)
			{
				m2.setValue(r,c,count);
				count++;
			}
		}
		m2.displayMatrix("Matrix m2 3 X 5 Consecutive Integers Display");
		
		
		
		m2.resize(4,4);
		System.out.println();
		m2.displayMatrix("Matrix m2 After 4 X 4 Resizing Display");
		
		int cnt = 0;
		for(int d = 0; d < m2.getCols(); d++)
		{
			System.out.print(cnt + " ");
		}
		System.out.println();
		
		Matrix m3 = new Matrix(3,3,100);
		System.out.println();
		m3.displayMatrix("Matrix m3 3 X 3 Initialized to 100 Display");
	}
}


class Matrix
{
	
	private ArrayList list;	//one-dimensional arrays stores matrix values
	private int listSize;	//total number of elements in the Matrix
	private int numRows;	//number of rows in the Matrix
	private int numCols;	//numbers of cols in the Matrix
	
	public Matrix()
	{
		numRows = 0;
		numCols = 0;
		list = new ArrayList();
		listSize = 0;  
	}
	
	public Matrix(int r, int c)
	{
		list = new ArrayList();
		numRows = r;
		numCols = c;
		list = new ArrayList();
		listSize = c * r;
		
		for(int k = 0; k<listSize; k++)
			list.add(new Integer(0));
	}
	
	public Matrix(int r, int c, int value)
	{
		numRows = r;
		numCols = c;
		listSize = c * r;
		list = new ArrayList();
		
		for(int k = 0; k<listSize; k++)
			list.add(value);	
	} 
			
		
		public int getRows()
		{
			return numRows;
		}
		
		public int getCols()
		{
			return numCols;
		}
		
		public int getSize()
		{
			return listSize;
		}
		
		public int getValue(int r, int c)
		{
			int a = (Integer)list.get(c+numCols*r);
			return a;	
		}
		
		public void setValue(int r, int c, int value)
		{
			list.set(c+numCols*r,value);
		}
	
		public void displayMatrix(String str)
		{
			System.out.println(str);
			if(list.isEmpty())
				System.out.println("Matrix has no elements");
			else{
				int count = 0;
				for(int i = 0; i < getRows(); i++)
				{
					for(int z = 0; z < getCols(); z++)
					{
						System.out.print(getValue(i,z) + " ");
						
					}
					System.out.println();
				}
			}
				
		}
		
		public void resize(int rows, int cols)
		{			
		
			int count = 0;
			for(int r = 0; r < getRows(); r++)
			{
				for(int c = 0; c < getCols(); c++)
				{
					setValue(r,c,getValue(r,c));
							
				}
						
			}	
		}	
	}









