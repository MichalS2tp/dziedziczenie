#include <iostream>
#include <fstream>
#include <string>
#include <cstdlib>
using namespace std;


class osoba
{
	
	public:
		
		string imie,nazwisko;
		int pesel;
		string x1;
		char x2;
		
		ifstream plik1;
    		ofstream plik2;
		
		osoba();
        	~osoba();
		
		void wprowadz();
		void wypisz();
		void wprowadzPlik();
		void wypiszPlik();
};

osoba::osoba(){
    plik1.open("c:\\1.txt");
    plik2.open("c:\\2.txt");
};

void osoba::wprowadz(){
	cout<<"Podaj imie, nazwisko, pesel"<<endl;
	cin>>imie>>nazwisko>>pesel;
};

void osoba::wypisz(){
	cout<<"{\"imie"<<"\":\""<<imie<<"\",\"nazwisko\":\""<<nazwisko<<"\,\"pesel\":\""<<pesel<<"\"}";
}

void osoba::wprowadzPlik(){
	
	int i=0;
	string helped;
	
	while(!plik1.eof()){ 
		if(i<3){
	        plik1>>znak>>x1;
			
			if(i==0) imie=x2+x1;		
			if(i==1) nazwisko=x2+x1;		
			if(i==2) helped=x2+x1;
			
			pesel=atoi(helped.c_str());		
			 
			i++;
		 }else{
		 	break;					
		 }
	}
};

void osoba::wypiszPlik(){
	plik2<<"{\"imie"<<"\":\""<<imie<<"\",\"nazwisko\":\""<<nazwisko<<"\,\"pesel\":\""<<pesel<<"\"}";
}

class uczen:public osoba
{
	string klasa;
	string srednia_ocen;				
	
	public:
		void wprowadz_uczen();
		void wyprowadz_uczen();
		void wpisz_uczen_Plik();
		void wypisz_uczen_Plik();
};

void uczen::wprowadz_uczen(){
	wprowadzKonsola();
	cout<<endl<<"Klasa oraz srednia"<<endl;
	cin>>klasa>>srednia_ocen;
};

void uczen:: wypisz_uczen(){
	cout<<"{\"imie"<<"\":\""<<imie<<"\",\"nazwisko\":\""<<nazwisko<<"\,\"pesel\":\""
	<<pesel<<"\",\"klasa"<<"\":\""<<klasa<<"\",\"srednia\":\""<<srednia_ocen<<"\"}";
}

void uczen::wprowadz_uczen_Plik(){
	int i=0;
	wprowadzPlik();
	while(!plik1.eof()){ 
        plik1>>x2>>x1;   
        
        if(i==0) klasa=x2+x1;
        if(i==1) srednia_ocen=x2+x1;
		i++; 
	}
};

void uczen::wypisz_uczen_Plik(){
	plik2<<"{\"imie"<<"\":\""<<imie<<"\",\"nazwisko\":\""<<nazwisko<<"\,\"pesel\":\""
	<<pesel<<"\",\"klasa"<<"\":\""<<klasa<<"\",\"srednia\":\""<<srednia_ocen<<"\"}";
};

class nauczyciel:public osoba
{
	string przedmiot;
	
	public:
		void wprowadz_nauczyciela();
		void wprowadz_nauczyciela_Plik();
		void wypisz_nauczyciela();
		void wypisz_nauczyciela_Plik();
};

void nauczyciel::wprowadz_nauczyciela(){
	wprowadzKonsola();
	cout<<endl<<"I przedmiot"<<endl;
	cin>>przedmiot;
}

void nauczyciel:: wypisz_nauczyciela(){
	cout<<"{\"imie"<<"\":\""<<imie<<"\",\"nazwisko\":\""<<nazwisko<<"\,\"pesel\":\""
	<<pesel<<"\",\"przedmiot"<<"\":\""<<przedmiot<<"\"}";
}

void nauczyciel::wprowadz_nauczyciela_Plik(){
	wprowadzPlik();
	while(!plik1.eof()){ 
        plik1>>x2>>x1;    
	}
	cout<<x2<<x1;
}

void nauczyciel::wypisz_nauczyciela_Plik(){
	plik2<<"{\"imie"<<"\":\""<<imie<<"\",\"nazwisko\":\""<<nazwisko<<"\,\"pesel\":\""
	<<pesel<<"\",\"przedmiot"<<"\":\""<<przedmiot<<"\"}";
}

osoba::~osoba(){
    plik1.close();
    plik2.close();
}

int main(int argc, char** argv) {
	nauczyciel ;
	osoba ;
	uczen ;

	return 0;
}
