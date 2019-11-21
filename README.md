#include <iostream>
#include <conio.h>
#include <math.h>
#include <stdio.h>

using namespace std;

void RDatos();
void Rcalcular();


float mantenimiento, tiempo, preparar,cant;
float calculo[30], calr[30];



int main(){
	int resp=0;
	
	
	do{
			
	cout << "\n\t MODELO DE REVISION PERIODICA";
		
	        RDatos();	    
			Rcalcular();		
	
}while(resp!=1);
    	
	return 0;
	
}

void RDatos(){
	
	
	for(int l=0;l<20;l++){
		calculo[l]=0;
		calr[l]=0;
	}
	int r=0, suma=0;
	
	cout << "\n\n(k): ";
	cin >> preparar;
	cout << "\n(h): ";
	cin >> mantenimiento;
	cout << "\nperidos: ";
	cin >> tiempo;
	cout << "\nIngrese cantidad de distribucion: ";
	cin >> cant;
	cout << "\n\n\t\t\t\t" << endl;
	
		system("cls");
	do{
		if(suma < cant || suma > cant  ){
	     suma=0;
    	for(int i=1; i<=tiempo; i++){
	    	cout << "\nCantidad de perdiodo " << i << " : ";
		    cin >> calr[i];
			suma+=calr[i];
		}
	
	    }
	    
		if(suma==cant || suma<cant){
		        cout << "\ncorrecto ";
		        cout << "\nmostrar iteraciones[1]: ";
		        cin >> r;
	     }
	   
	     else {
			cout << "\nincorrecto";
			cout << "\ncorregir [0] o seguir [1]: ";
			cin >> r;
		    }	  
    	}
    while(r!=1);
    
    
    for(int j=1; j<=tiempo+1; j++)
    	  calculo[j]=0;
        
		
	for(int i=1; i<=tiempo; i++){
	

		
		cout <<"\nproducto:" << i << " es: " << calr[i] <<endl;
		
	}
	
		system("cls");
}
	


void Rcalcular(){
	int cont=0;
	float aux;
	float min=0;
	int costo[20];
	for(int x=tiempo; x>=1; x--){
		cout<<"       "<<endl;
		cout << "\nITERACIONES PARA EL PERIODO: " << x ;
    	cont=0;
		for(int i=x; i<=tiempo;i++ ){
			aux=0;
			for(int k=1;k<cont+1;k++){
				aux+=k*calr[x+k];
				
			}
			if(i==x){
				calculo[x]=calculo[i+1]+preparar+(mantenimiento*aux);
				min=calculo[x];
				cout <<"\nPeriodo " << x << " a " << i+1 <<" Iteracion= "<<calculo[i+1]<<"+"<<preparar<<"="<<calculo[x]<< endl;
			}else{
				calculo[x]=calculo[i+1]+preparar+(mantenimiento*aux);
					cout <<"\nPeriodo " << x << " a " << i+1 <<" Iteracion= "<<calculo[i+1]<<"+"<<preparar<<"+("<<mantenimiento<<"*"<<aux<<")"<<"="<<calculo[x]<< endl;
			}
		  	if(min<calculo[x]){
    			calculo[x]=min;
			}else{
				min=calculo[x];
			}
			cont++;
		} 
		cout <<"\n\nEl costo minimo para  "<<"C"<<x<< " es: " << min << endl<<endl;
		min=0;
		cout<<"__________________________________________________________________"<<endl;
	}}
	


