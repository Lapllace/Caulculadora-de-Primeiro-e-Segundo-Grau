# Caulculadora-de-Primeiro-e-Segundo-Grau

 
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
#include <conio.h>
#include <math.h>

void imprime_cabec(void)
{
  	printf("*************************************\n");
    printf("*** Bem vindo a minha Calculadora ***\n");
    printf("*************************************\n\n");  

  return; /* retorno de uma função void  */}

float delta(float a, float b, float c){
	float resultado = ((pow(b,2))-(4*a*c));
	return resultado;
}

float primeiro(float a, float b){
	  float x=(-b/a);
	return x;
}

float raiz(float D){
	float rD=sqrt(D);
	return rD;
}

float x1(float b, float a, float rD){
	float x1=((-b+rD)/(2*a));
	return x1;
}
float x2(float a, float b, float rD){
	float x2=((-b-rD)/(2*a));
	return x2;
}

int main(){
	setlocale(LC_ALL,"Portuguese_Brazil");
	
	float  A, B, C, resultado, D, RD, X1,X2;
	int r;
	
	imprime_cabec();
	
	while(r!=1 || r!=2){
		printf("\nPor Favor escolher qual o tipo da equação: \n");		
        printf("1-Calcular a raiz de uma equação do primeiro grau: \n");
        printf("2-Calcular a raiz de uma equação do segundo grau: \n");
        printf("\nQual deseja calcular? \n");
		scanf("%d", &r);
		
		system("cls");
		
		switch(r){
			
			//Raiz da equação do primeiro grau
			case 1:
				printf("Você escolheu a opção 1.\n");
				printf("Escolha um valor para A.\n");
				scanf("%f", &A);
				
				//enquanto não for escrito no código uma das duas alternativas ele permanecerá em loop.
				while(A==0){
					printf("Escolha um valor diferente de 0 para A.\n");
					scanf("%f", &A);
					}
				 	
				printf("Escolha um valor para B.\n");
			 	scanf("%f", &B);
			 	resultado= primeiro(A, B);         //Atribuindo e chamando a função
			 	printf("A raiz da equção é:\n%f\n", resultado);
			 	
			 	system("pause");
			 	system("cls");
			 	break;
			
			//calculos para definir Delta e o resultado das equações de 2° grau
			
			case 2:
				printf("Você escolheu a opção 2.\n");
				printf("Escolha um valor para A.\n");
				scanf("%f", &A);
				
				//Se A=0
				
				while(A==0){
			 		printf("Escolha um valor diferente de 0 para A.\n");
			 		scanf("%f", &A);
			 		}
				printf("Escolha um valor para B.\n");
				scanf("%f", &B);
				
				printf("Escolha um valor para C.\n");
				scanf("%f", &C);
				
				D=delta(A,B,C);          //Atribuindo e chamando
				
				
				if(D<0){              //Delta menor que 0
					printf("Não existe raiz no conjunto dos reais, pois delta é igual a:\n%.2f .\n", D);
				}
				
				else if (D==0){
					
					resultado= primeiro(A,B);
					printf("Ambas as raízes são iguais, assim o resultado é:\n%.2f . \n", resultado);
				}
				//aplicação de acordo com os resultados para o texto ideal e print das respostas
				else{
					D= delta(A,B,C);
					RD=raiz(D);
					X1= x1(B,A,RD);
					X2=x2(A,B,RD);
					printf("Os valores das raízes são:\nx1= %.2f\nx2= %.2f . \n", X1,X2);
				}
				
				system ("pause");
				system("cls");
				break;
				
				//Para finalizar
				
				case 3:
				printf("Saindo do programa...\n");
				exit(0);
				break;
			}
	}
	
	system("pause");
	return 0 ; 
}
	
