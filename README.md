# lab1-array-string-processing
#include <iostream>

using namespace std;

int main() {
    int N, M;

    cout << "Insert N: ";
    cin >> N;

    cout << "Insert M: ";
    cin >> M;

    int A[100][100];
    int B[100];

    cout << "Insert matrix:" << endl;

    for (int i = 0; i < N; i++) {
        for (int j = 0; j < M; j++) {
            cin >> A[i][j];
        }
    }

    // Tao mang B
    for (int j = 0; j < M; j++) {
        int product = 1;
        bool hasNonZero = false;

        for (int i = 0; i < N; i++) {
            if (A[i][j] != 0) {
                product = product * A[i][j];
                hasNonZero = true;
            }
        }

        if (hasNonZero) {
            B[j] = product;
        }
        else {
            B[j] = 0;
        }
    }

    // Shell Sort
    int gap = M / 2;

    while (gap > 0) {
        for (int i = gap; i < M; i++) {
            int temp = B[i];
            int j = i;

            while (j >= gap && B[j - gap] > temp) {
                B[j] = B[j - gap];
                j = j - gap;
            }

            B[j] = temp;
        }

        gap = gap / 2;
    }

    // In ket qua
    cout << "Array B after arrangement:" << endl;

    for (int i = 0; i < M; i++) {
        cout << B[i] << " ";
    }

    cout << endl;

    return 0;
}
