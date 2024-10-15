```C
matrix* create_matrix(int rows, int cols) {
	matrix mat = malloc(sizeof(matrix));
	mat.rows = rows
	mat.cols = cols
	int** data = malloc(rows*sizeof(int*));
	for (int i = 0; i < rows; i++) {
		int *row = malloc(cols * sizeof(int));
		for (int j = 0; j < cols; j++) {
			row[j] = 0;
		}
		data[i] = row;
	}
	return &mat;
}
```

Correct solution:
```C
matrix* create_matrix(int rows, int cols) {
	matrix *mat = malloc(sizeof(matrix));
	mat->rows = rows
	mat->cols = cols
	int** data = malloc(rows*sizeof(int*));
	for (int i = 0; i < rows; i++) {
		mat->data[i] = malloc(cols * sizeof(int));
		for (int j = 0; j < cols; j++) {
			mat->data[i][j] = 0;
		}
	}
	return mat;
}
