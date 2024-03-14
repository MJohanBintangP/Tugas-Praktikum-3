Code.C
```sh
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LENGTH 2024
#define MIN_LENGTH 1945

void lessThanRequired(int *lengthOfText) {
    printf("The length of your text is less than specified, please update your text\n");
    *lengthOfText = MIN_LENGTH;
}

void equalThanRequired() {
    printf("Thank you, Your text length is correct\n");
}

void moreThanRequired(int *lengthOfText) {
    printf("Your text is too long, please reduce the text\n");
    *lengthOfText = MIN_LENGTH;
}

int checkLengthRequirement(char* text) {
    int length = strlen(text);
    if (length < MIN_LENGTH)
        return 0;
    else if (length == MIN_LENGTH)
        return 1;
    else
        return 2;
}

int main() {
    int lengthOfText, selectOption;
    FILE *fptr = NULL;
    char text[MAX_LENGTH];

    fptr = fopen("file.txt", "r");

    if (fptr == NULL) {
        printf("Error");
        exit(1);
    }

    fgets(text, MAX_LENGTH, fptr);

    fclose(fptr);

    selectOption = checkLengthRequirement(text);
    void (*options[3])(int *) = {lessThanRequired, equalThanRequired, moreThanRequired};
    options[selectOption](&lengthOfText);

    printf("\nThe Length is updated to %d", lengthOfText);

    return 0;
}
```
Penjelasan
1. `#include <stdio.h>` header ini berfungsi untuk menggunakan printf
2. `#include <stdlib.h>` header ini berfungsi untuk mengalokasikan memori dan bisa untuk konversi
3. `#include <string.h>` header ini berfungsi untuk menyimpan fungsi-fungsi yang digunakan untuk menangani string
4. `#define MAX_LENGTH 2024` digunakan untuk mendefinisikan konstanta sampai maksimal 2024
5. `#define MIN_LENGTH 1945` digunakan untuk mendefinisikan konstanta minimal 1945
6. `void lessThanRequired(int *lengthOfText) {
    printf("The length of your text is less than specified, please update your text\n");
    *lengthOfText = MIN_LENGTH;
   }` Bagian ini merupakan prosedur yang berfungsi untuk menangani situasi ketika panjang teks yang di input kurang dari aturan yang ada
7. `void equalThanRequired() {
    printf("Thank you, Your text length is correct\n");
}` Bagian ini merupakan prosedur yang berfungsi untuk menangani kondisi ketika teks yang di masukkan sudah sesuai, maka akan terdisplay teks seperti di `printf`
8. `void moreThanRequired(int *lengthOfText) {
    printf("Your text is too long, please reduce the text\n");
    *lengthOfText = MIN_LENGTH;
}` Bagian ini merupakan prosedur yang berfungsi untuk menagani kondisi ketika panjang teks yang di input lebih dari aturan yang ada
9. `int checkLengthRequirement(char* text) {
    int length = strlen(text);
    if (length < MIN_LENGTH)
        return 0;
    else if (length == MIN_LENGTH)
        return 1;
    else
        return 2;
}` Bagian ini berfungsi untuk memeriksa apakah teks yang ada dalam file.txt panjangnya sudah sesuai, jika panjangnya kurang dari `min_length` maka program akan berhenti, jika panjangnya sama dengan `min_length` maka program akan berlanjut
9. `int main() {` ini merupakan fungsi utama dalam program
10. `   int lengthOfText, selectOption;
    FILE *fptr = NULL;
    char text[MAX_LENGTH];` bagian ini untuk mendeklarasikan variabel-variabel didalamnya
11. `fptr = fopen("file.txt", "r");` code ini akan membuka file.txt lalu membaca file tersebut
12. `if (fptr == NULL) {
        printf("Error");
        exit(1);
    }` Bagian ini berfungsi untuk jika variabel kosong (belum membuat file.txt) maka akan terdsiplay teks error
13. `fgets(text, MAX_LENGTH, fptr);` ini berfungsi untuk membaca baris teks daari file
14. `fclose(fptr);` code ini berfungsi untuk menutup text yang sebelumnya sudah dibuka oleh program
15. `selectOption = checkLengthRequirement(text);
    void (*options[3])(int *) = {lessThanRequired, equalThanRequired, moreThanRequired};
    options[selectOption](&lengthOfText);` bagian ini berfungsi untuk memanggil prosedur yang sudah dibuat diatas
16. `printf("\nThe Length is updated to %d", lengthOfText);` ini berfungsi untuk mendisplay teks yang sesuai dengan teks dalam printf
17. ` return 0;` ini akan mengembalikan program dari awal

Output
![image](https://github.com/MJohanBintangP/Tugas-Praktikum-3/assets/163379288/7291daa2-dba8-4f92-b010-e502ef973104)
