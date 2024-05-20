# Registration-and-log
#include<iostream>
#include<fstream>
#include<windows.h>
#include<sstream>
using namespace std;

class Login{
	private:
		string LoginID,Password;
    public:
	    Login():LoginID(""),Password(""){}

void setID(string id){
LoginID = id;
}	    
void setPW(string pw){
Password = pw;	
}
string getID(){
	return LoginID;
}
string getPw(){
	return Password;
}
};
registration(Login log){
	system("cls");
string id,pw;	
cout<<"\tEnter login ID:";
cin>>id;
log.setID(id);

start:
cout<<"\tEnter A strong password:";
cin>>pw;
if(pw.length() >=8){
log.setPW(pw);
}	
else{
cout<<"\tenter minimum 8 characters!"<<endl;
goto start;	
}
ofstream outfile("C:\login sheet.txt",ios::app);
if(!outfile){
	cout<<"\tError: File can't open!"<<endl;
}
else{
outfile<<"\t"<<log.getID()<<" : "<<log.getPw()<<endl<<endl;
cout<<"\tUser Registered successfully!"<<endl;	
}
outfile.close();
Sleep(3000);
}	
login(){
system("cls");
string id, pw;
cout<<"\tEnter Login ID:";
cin>>id;

cout<<"\tEnter Password:";
cin>>pw;

ifstream infile("C:/Login.txt");
if(!infile){
cout<<"\tError: File can't oprn!"<<endl;	
}	
else{
string line;
bool found = false;
while(getline(infile,line)){
stringstream ss;
ss<<line;
string userID,userPW;
char delimiter;
ss>>userID>>delimiter>>userPW;	
if(id==userID && pw==userPW){
found = true;
cout<<"\tplease Wait";
for(int i =0;i<3;i++){
	cout<<".";
Sleep(800);
	
}
system("cls");
cout<<"\twelcome to this page!"<<endl;	
}
}	
if(!found){
	cout<<"\tError: incorrect login ID or password!"<<endl;
}
}
}
int main(){
Login log;	
bool exit = false;
while(!exit){
system("cls");
int val;
cout<<"\tWelcome To Registration & login form"<<endl;
cout<<"\t*************************************"<<endl;
cout<<"\t1.Register."<<endl;
cout<<"\t2.Login."<<endl;
cout<<"\t3. Exist."<<endl;
cout<<"\tEnter choice:";
cin>>val;


if(val==1){
registration(log);	
}
else if(val==2){
	login();
}
else if(val==3){
	system("cls");
	exit = true;
	cout<<"\tGood luck!"<<endl;
}
Sleep(3000);
}
}	    
	    
				
