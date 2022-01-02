# Secret_Key_Encryption
  #instructional pdf
  
  
        https://www.cs.dartmouth.edu/~ccpalmer/teaching/cs55/Assignments/Lab%201/Crypto_Encryption.pdf
# Task 1: Frequency Analysis 

  touch article.txt

      echo "This Is task and plain text" > alert.txt
![task1](https://github.com/ghulammohiodin/Secret_Key_Encryption/blob/7f54337ca89577c4781918807f8fdafff983f1c2/task_1.0SKE.png)

# Step 1: We convert all upper case characters to lower case, and then remove all punctuation and
numbers. We keep the spaces between words, so you can still see the boundaries of the words in the
ciphertext. In an actual use of a monoalphabetic cipher, spaces are removed. We keep the spaces to
simplify the task.

                 tr [:upper:] [:lower:] < alert.txt > lowercase.txt
                 tr -cd '[a-z][\n][:space:]' < lowercase.txt > plaintext.txt
  ![tr comands](https://github.com/ghulammohiodin/Secret_Key_Encryption/blob/7f54337ca89577c4781918807f8fdafff983f1c2/task_1.2SKE.png)
             
Here are the commands we used to do this step:
# Step 2: Next we generate the encryption key, i.e., the substitution table. We will permute the
alphabet from a to z using Python, and use the permuted alphabet as the key. See the following
program.


   # python
      >>> import random
     >>> s = "abcdefghijklmnopqrstuvwxyz"
     >>> list = random.sample(s, len(s))
    >>> ''.join(list)
    'sxtrwinqbedpvgkfmalhyuojzc'
 ![python](https://github.com/ghulammohiodin/Secret_Key_Encryption/blob/7f54337ca89577c4781918807f8fdafff983f1c2/task_1.1SKE.png)
        
# Task 2: Encryption using Different Ciphers and Modes 
 In this task, we will explore various encryption algorithms and modes. You can use the following
openssl enc command to encrypt/decrypt a file. Type man openssl and man enc for details

  # encrypt
  
      openssl enc  -aes-128-cbc  -e -in plaintext.txt -out cbc_cipher.bin \
      -K 00112233445566778889aabbccddeeff \
      -iv 0102030405060708
   # decrypt
        
        openssl enc  -aes-128-cbc  -d -in cbc_cipher.bin -out cbc_plain.txt \
      -K 00112233445566778889aabbccddeeff \
      -iv 0102030405060708

![task2](https://github.com/ghulammohiodin/Secret_Key_Encryption/blob/7f54337ca89577c4781918807f8fdafff983f1c2/task_2.0CBC.png)
![CFB](https://github.com/ghulammohiodin/Secret_Key_Encryption/blob/7f54337ca89577c4781918807f8fdafff983f1c2/task_2.1CFB.png)


# Explanning opensll 
    -in <file>                   input file
    -out <file>    output file
    -e              encrypt
    -d              decrypt
    -K/-iv          key/iv in hex is the next argument
    -[pP]           print the iv/key (then exit if -P)
        
# Task 3: Encryption Mode – ECB vs. CBC
        openssl enc  -aes-128-ecb  -e -in pic_original.bmp -out cipher_pic.bmp \
      -K 00112233445566778889aabbccddeeff
  Reset the header of the encrypted picture to make it openable by picture viewer:

      head -c 54 pic_original.bmp > header
      tail -c +55 cipher_pic.bmp > body
      cat header body > full_cipher_pic.bmp 
      
 ![task3](https://github.com/ghulammohiodin/Secret_Key_Encryption/blob/7f54337ca89577c4781918807f8fdafff983f1c2/task_3cipherpic.png)
 
 
#Task 4: Padding

#Commands 

         echo -n "123456" > test.txt 
         ls -ld test.txt
         openssl enc -aes-128-ecb -e -in test.txt -out ecb_out.bin
          -K 00112233445566778889aabbccddeeff ls -ld ecb_out.bin
  ![task4](https://github.com/ghulammohiodin/Secret_Key_Encryption/blob/7f54337ca89577c4781918807f8fdafff983f1c2/task_4.1CBC.png)
  
 #CBC
 
 
            openssl enc -aes-128-cbc -e -in test.txt -out cbc_out.bin
            -K 00112233445566778889aabbccddeeff
            -iv 0102030405060708 
#CFB

      openssl enc -aes-128-cfb -e -in test.txt -out cfb_out.bin
     -K 00112233445566778889aabbccddeeff
      -iv 0102030405060708 ls 
# BLESS 
      
      python -c "print '1234567890'*100" > big_file.txt
      -ld big_file.txt
      
 ![task4](https://github.com/ghulammohiodin/Secret_Key_Encryption/blob/7f54337ca89577c4781918807f8fdafff983f1c2/task_4bless%20big_file.png)
 ![task4](https://github.com/ghulammohiodin/Secret_Key_Encryption/blob/7f54337ca89577c4781918807f8fdafff983f1c2/task_4bless%20big_out.png)
 
 
       xxd big_file.txt
       
 ![xxd](https://github.com/ghulammohiodin/Secret_Key_Encryption/blob/7f54337ca89577c4781918807f8fdafff983f1c2/task_4xxd%20gih.png)






       

       

