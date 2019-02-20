#include <stdlib.h>
#include <iostream>
#include <fstream>
#include <unistd.h>
#include <conio.h>
using namespace std;

void llamada(char d[11]);
void consulta();
char usuarios[3][11]{{"8346678889"},
                     {"8347554443"},
					 {"8345653357"}};
int saldo[3]={5,5,5};
char numero[11];
char destino[11];
char numaux[11];
int monto=0;
int mint=0;
int aux=1;
int seg=0;
int total=0;
int saldom=0;;
int i;
char linea[50];
char salida;
char colgar='a';
int main()

{
	int des;
	do{
    cout << "Seleccione un opcion" << endl;
    cout << "1.- Realizar llamada" << endl;
    cout << "2.- Realizar una recarga" << endl;
    cout << "3.- Ver registro de llamadas" << endl;
    cin >> des;
    switch(des){
    			case 1: 
    			do{
					 	  cout << "ingrese su numero" << endl;
					 	  scanf(" %[^\n]s",&numero);
					 	  for(i=0;i<=2;i++){
    				 	
    				 	if(strcmp(numero,usuarios[i])==0)
    				 		aux=0;
    				 		break;
    				 		}
    				 		if(aux==0)
    				 				  break;
    				 }while(aux!=0);
    				 if(saldo[i]<1){
    				 	cout << "saldo insuficiente" << endl;
    				 }
    				 else{
    				 cout << "Ingrese el numero destino\n" << endl;
    				 scanf(" %[^\n]s",&destino);
    				 saldom=saldo[0];
    				 fflush(stdin);
    				 mint =0;
    				 seg =0;
    				 total=0;
    				 saldom=saldo[i];
    				 do{
    				 	system("cls");
    				 	cout << "llamada en curso (precione 'c' para colgar) " << endl;
    				 	cout <<mint<<":"<<seg<<endl; 
    				 				  
    				 				  		
    				 				  sleep(1);
    				 				  			  if(seg==60){
    				 				  			  	seg=0;
    				 				  			  	mint++;
    				 				  			  	total++;
				  			  		}
				  			  		 colgar = getch();
				  			  		if(colgar=='c')
				  			  					   break;
	  			  		seg+=10;
    				 }while(total<saldom);
    				 				  cout << "llamada finalizada" << endl; 
    				 				  saldo[i]-=total;
    				 				  cout << "saldo restante $" << saldo[i]<< endl;
    				 				  llamada(destino);
    				 			}
    				 				  
					 break;	
					
					 case 2:
					 	aux=1;
					 	i=0;
					 	
					 	do{
					 	  cout << "ingrese su numero" << endl;
					 	  scanf(" %[^\n]s",&numero);
					 	  for(i=0;i<=2;i++){
    				 	
    				 	if(strcmp(numero,usuarios[i])==0)
    				 		aux=0;
    				 		break;
    				 		}
    				 		if(aux==0)
    				 				  break;
    				 }while(aux!=0);
	 				      cout << i << endl;
	 				      system("pause");
	 				      cout << "ingrese el monto a recargar" << endl;
	 				      cin >> monto;
	 				      cout << "saldo anterior " << saldo[i]<< endl;
	 				      saldo[i]+=monto;
	 				      cout << "nuevo saldo " << saldo[i]<< endl;
					 	break;
					 	case 3:
					 		cout <<" Ingrese el número que quiere consultar" << endl;
					 		cin >> numero;
					 		consulta();
					 		
					 		break;
					 	default:
					 		cout << "opcion incorrecta" << endl;
					 		system("pause");
							 system("cls");
					 		break;
    	
    	
		}
                                      
		cout << "desea realizar otra accion? (s/n)"<< endl;
    	cin >> salida;
	}while(salida!='n');
    return 0;
}

void llamada(char d[11]){
	strcat(numero,".txt");
	ofstream archivo;
	
     archivo.open(numero,ios::app);
     fflush(stdin);
     system("pause");
 	 archivo << "llamada a: " << d << " duracion: " <<mint<<":"<<seg << endl;
 	 archivo.close();
   	}
	
void consulta(){
	strcat(numero,".txt");
	ifstream leer;
	leer.open(numero);
	
	while(!leer.eof())
{
                  leer.getline(linea,50);
                  cout<<linea<<endl;
}
	
}
