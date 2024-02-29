# Cryptography---19CS412-classical-techqniques


# Caeser Cipher
Caeser Cipher using with different key values

# AIM:

To develop a simple C program to implement Caeser Cipher.

## DESIGN STEPS:

### Step 1:

Design of Caeser Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
#include <stdio.h>
#include <string.h>
#include <conio.h>
#include <ctype.h>

int main() {
    char plain[10], cipher[10];
    int key, i, length;
    int result;

    printf("\n Enter the plain text:");
    scanf("%s", plain);

    printf("\n Enter the key value:");
    scanf("%d", &key);

    printf("\n \n \t PLAIN TEXT: %s", plain);
    printf("\n \n \t ENCRYPTED TEXT: ");

    for (i = 0, length = strlen(plain); i < length; i++) {
        cipher[i] = plain[i] + key;

        if (isupper(plain[i]) && (cipher[i] > 'Z'))
            cipher[i] = cipher[i] - 26;

        if (islower(plain[i]) && (cipher[i] > 'z'))
            cipher[i] = cipher[i] - 26;

        printf("%c", cipher[i]);
    }

    printf("\n \n \t AFTER DECRYPTION : ");

    for (i = 0; i < length; i++) {
        plain[i] = cipher[i] - key;

        if (isupper(cipher[i]) && (plain[i] < 'A'))
            plain[i] = plain[i] + 26;

        if (islower(cipher[i]) && (plain[i] < 'a'))
            plain[i] = plain[i] + 26;

        printf("%c", plain[i]);
    }

    return 0;
}

## OUTPUT:
![1a](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/119393279/270a1cd2-32b8-4cef-b2ae-1a9757a128db)

## RESULT:
The program is executed successfully

---------------------------------

# PlayFair Cipher
Playfair Cipher using with different key values

# AIM:

To develop a simple C program to implement PlayFair Cipher.

## DESIGN STEPS:

### Step 1:

Design of PlayFair Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
#include<stdio.h>
#include<conio.h>
#include<string.h>
#include<ctype.h>
#define MX 5

void playfair(char ch1, char ch2, char key[MX][MX]) {
    int i, j, w, x, y, z;
    FILE *out;
    if ((out = fopen("cipher.txt", "a+")) == NULL) {
        printf("File Corrupted.");
    }
    for (i = 0; i < MX; i++) {
        for (j = 0; j < MX; j++) {
            if (ch1 == key[i][j]) {
                w = i;
                x = j;
            } else if (ch2 == key[i][j]) {
                y = i;
                z = j;
            }
        }
    }
    if (w == y) {
        x = (x + 1) % 5;
        z = (z + 1) % 5;
        printf("%c%c", key[w][x], key[y][z]);
        fprintf(out, "%c%c", key[w][x], key[y][z]);
    } else if (x == z) {
        w = (w + 1) % 5;
        y = (y + 1) % 5;
        printf("%c%c", key[w][x], key[y][z]);
        fprintf(out, "%c%c", key[w][x], key[y][z]);
    } else {
        printf("%c%c", key[w][z], key[y][x]);
        fprintf(out, "%c%c", key[w][z], key[y][x]);
    }
    fclose(out);
}

int main() {
    int i, j, k = 0, l, m = 0, n;
    char key[MX][MX], keyminus[25], keystr[10], str[25] = {0};
    char alpa[26] = {'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'};
    printf("\nEnter key:");
    gets(keystr);
    printf("\nEnter the plain text:");
    gets(str);
    n = strlen(keystr);
    for (i = 0; i < n; i++) {
        if (keystr[i] == 'j') keystr[i] = 'i';
        else if (keystr[i] == 'J') keystr[i] = 'I';
        keystr[i] = toupper(keystr[i]);
    }
    for (i = 0; i < strlen(str); i++) {
        if (str[i] == 'j') str[i] = 'i';
        else if (str[i] == 'J') str[i] = 'I';
        str[i] = toupper(str[i]);
    }
    j = 0;
    for (i = 0; i < 26; i++) {
        for (k = 0; k < n; k++) {
            if (keystr[k] == alpa[i]) break;
            else if (alpa[i] == 'J') break;
        }
        if (k == n) {
            keyminus[j] = alpa[i];
            j++;
        }
    }
    k = 0;
    for (i = 0; i < MX; i++) {
        for (j = 0; j < MX; j++) {
            if (k < n) {
                key[i][j] = keystr[k];
                k++;
            } else {
                key[i][j] = keyminus[m];
                m++;
            }
            printf("%c ", key[i][j]);
        }
        printf("\n");
    }
    printf("\n\nEntered text :%s\nCipher Text :", str);
    for (i = 0; i < strlen(str); i++) {
        if (str[i] == 'J') str[i] = 'I';
        if (str[i + 1] == '\0') playfair(str[i], 'X', key);
        else {
            if (str[i + 1] == 'J') str[i + 1] = 'I';
            if (str[i] == str[i + 1]) playfair(str[i], 'X', key);
            else {
                playfair(str[i], str[i + 1], key);
                i++;
            }
        }
    }
    return 0;
}

## OUTPUT:
![Screenshot 2024-02-29 135801](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/119393279/624dad52-2835-492e-9c0c-2e1b4b1ba171)


## RESULT:
The program is executed successfully


---------------------------

# Hill Cipher
Hill Cipher using with different key values

# AIM:

To develop a simple C program to implement Hill Cipher.

## DESIGN STEPS:

### Step 1:

Design of Hill Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
#include<stdio.h>
#include<conio.h>
#include<string.h>

int main(){
    unsigned int a[5][5] = {{6, 24, 1}, {13, 16, 10}, {20, 17, 15},{13,45,63},{7,3,5,}};
    unsigned int b[5][5] = {{8, 5, 10}, {21, 8, 21}, {21, 12, 8},{5,7,3},{5,87,15}};
    int i, j, t = 0;
    unsigned int c[20], d[20];
    char msg[20];

    printf("Enter plain text: ");
    scanf("%s", msg);

    for (i = 0; i < strlen(msg); i++){
        c[i] = msg[i] - 65;
        printf("%d ", c[i]);
    }

    for (i = 0; i < 5; i++){
        t = 0;
        for (j = 0; j < 5; j++){
            t = t + (a[i][j] * c[j]);
        }
        d[i] = t % 26;
    }

    printf("\nEncrypted Cipher Text :");
    for (i = 0; i < 5; i++)
        printf(" %c", d[i] + 65);

    for (i = 0; i < 5; i++){
        t = 0;
        for (j = 0; j < 5; j++){
            t = t + (b[i][j] * d[j]);
        }
        c[i] = t % 26;
    }

    printf("\nDecrypted Cipher Text :");
    for (i = 0; i < 5; i++)
        printf(" %c", c[i] + 65);

    getch();
    return 0;
}

## OUTPUT:
![Screenshot 2024-02-29 143232](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/119393279/eb3617d9-c6a3-41b7-b88d-c4fa92ad4c2c)
![Screenshot 2024-02-29 143232](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/119393279/27c9c925-97cf-444b-b7cf-412035ab5eb2)



## RESULT:
The program is executed successfully

-------------------------------------------------

# Vigenere Cipher
Vigenere Cipher using with different key values

# AIM:

To develop a simple C program to implement Vigenere Cipher.

## DESIGN STEPS:

### Step 1:

Design of Vigenere Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:


## OUTPUT:


## RESULT:
The program is executed successfully

-----------------------------------------------------------------------

# Rail Fence Cipher
Rail Fence Cipher using with different key values

# AIM:

To develop a simple C program to implement Rail Fence Cipher.

## DESIGN STEPS:

### Step 1:

Design of Rail Fence Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:

## OUTPUT:

## RESULT:
The program is executed successfully
