# lab-4 
#include <iostream>
#include <iomanip>
#include <math.h>
using namespace std;


class Matrix{
    //закриті змінні-члени класу
private:
    int M[5][5] = {6, 34, 12, 70, -1,
                    -7, 97, 80, 99, -99,
                    1, 6,  -3, 2, -8,
                    3, 33, -1, 0, -78,
                    -3, -5, -8, -56, -23};
public:
    //відкриті функції-члени класу
    void InputMatrix();
    void OutputMatrix();
    void Sort();
    void Sum();
    void GeometricMean(double arr_of_sum[]);
};

void Matrix::InputMatrix(){
    for (int i=0;i<5;i++)
        for (int j=0;j<5;j++)
        {
            cout<<"["<<i+1<<"]["<<j+1<<"] = ";
            cin>>M[i][j];
        }
}
void Matrix::OutputMatrix(){
    for (int i=0;i<5;i++)
    {
        for (int j=0;j<5;j++)
            cout<< setw(7)<<M[i][j]<<"    ";
        cout<<endl;
    }
}
void Matrix::Sort(){
    //Алгоритм сортування вибором
    for(int j = 0;j<5;j++) {
        for (int i = 0; i < 5; i++) {
            int min = M[i][j];
            int k, *tmp;
            for(k = i + 1; k < 5; k++){
                if(M[k][j] < min){
                    min = M[k][j];
                    tmp = &M[k][j];
                }
            }
            if (M[i][j] != min){
                *tmp = M[i][j];
                M[i][j] = min;
            }
        }
    }
}


void Matrix::Sum() {
    double arr_of_sum [5];
    for (int i = 0; i < 5; ++i) {
        int sum = 0;
        for (int j = 0; j < 5; ++j) {
            sum += M[i][j];
        }
        arr_of_sum[i] = sum;
        cout << "sum of elements in row N" << i+1 << " = "<< sum << endl;
    }

    GeometricMean(arr_of_sum);
}

void Matrix::GeometricMean(double arr_of_sum[]){
    double temp = 1.0;
    for (int k = 0; k < 5; ++k) {
        temp *= arr_of_sum[k];
    }

    double geometric_mean = pow(temp, 1.0/5);
    cout << "geometric mean = " << geometric_mean << endl;
}

int main()
{
    Matrix A;
    cout<<"Input elements of matrix A"<<endl;
    A.InputMatrix();
  //  cout<<"\nInput Matrix A "<<endl;
    A.OutputMatrix();
    A.Sort();
    cout<<"\nSorted Matrix A "<<endl;
    A.OutputMatrix();
    cout<<endl;
    A.Sum();
    system("pause");
}


