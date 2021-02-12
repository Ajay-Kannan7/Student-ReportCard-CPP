#include<iostream>
#include<fstream>
#include<conio.h>
#include<stdio.h>
#include<string.h>
#include<process.h>
#include<iomanip>
using namespace std;
class student
{
    int marks;
    int roll;
    char name[50];
    int english;
    int hindi;
    int maths;
    int social;
    int cs;
public:
    void enter();
    void display();
    void modify();
    int getroll();
    void report_tab();
    int total();
};
    void student :: enter()
    {
        cout<<"\nenter the name=";
        cin>>name;
        cout<<"\nenter the roll number=";
        cin>>roll;
        cout<<"\nenter the marks for english=";
        cin>>english;
        cout<<"\nenter the marks for hindi=";
        cin>>hindi;
        cout<<"\nenter the marks for maths=";
        cin>>maths;
        cout<<"\nenter the marks for social science=";
        cin>>social;
        cout<<"\nenter the marks for computer science=";
        cin>>cs;
    }
    void student :: display()
    {
        cout<<"\nNAME="<<name;
        cout<<"\nROLL-NO="<<roll;
        cout<<"\nENGLISH="<<english;
        cout<<"\nHINDI="<<hindi;
        cout<<"\nMATHS="<<maths;
        cout<<"\nSOCIAL SCIENCE="<<social;
        cout<<"\nCOMPUTER SCIENCE="<<cs;
        cout<<"\n*************************";
    }
    void student :: modify()
    {
        char nname[50];
        int r,e,h,m,s,c;
        cout<<"\nThe old details are:-";
        cout<<"\nNAME="<<name;
        cout<<"\nROLL-NO="<<roll;
        cout<<"\nENGLISH="<<english;
        cout<<"\nHINDI="<<hindi;
        cout<<"\nMATHS="<<maths;
        cout<<"\nSOCIAL SCIENCE="<<social;
        cout<<"\nCOMPUTER SCIENCE="<<cs;
        cout<<"\n*************************";
        cout<<"\nEnter new details=";
        cout<<"\nNAME:-";
        cin>>nname;
        cout<<"\nROLL-NO:-";
        cin>>r;
        cout<<"\nENGLISH=";
        cin>>e;
        cout<<"\nHINDI=";
        cin>>h;
        cout<<"\nMATHS=";
        cin>>m;
        cout<<"\nSOCIAL SCIENCE=";
        cin>>s;
        cout<<"\nCOMPUTER SCIENCE=";
        cin>>c;
        strcpy(name,nname);
        roll=r;
        english=e;
        hindi=h;
        maths=m;
        social=s;
        cs=c;
    }
    int student :: getroll()
    {
        return roll;
    }
    int student :: total()
    {
        int t=0;
        t=english+hindi+social+maths+cs;
        return t;
    }
    void student :: report_tab()
    {
        cout<<"\n\t\t\t\t\t\tREPORT CARD";
        cout<<"\n\t\tNAME:-"<<name;
        cout<<"\n\t\tENGLISH"<<setw(10)<<"MATHS"<<setw(10)<<"HINDI"<<setw(10)<<"SOCIAL"<<"\t"<<"COMPUTER SCIENCE"<<"   MAX TOTAL";
        cout<<"\n\t\t "<<english<<setw(13)<<maths<<setw(10)<<hindi<<"\t"<<social<<"\t       "<<cs<<"\t\t"<<total();
        getch();
    }
void enter_data();
void display_d();
void remove_data();
void display_sp();
void modify_s();
int main()
{
    int i,n;
    student s;
    do
    {
        cout<<"\nSTUDENT PERFORMANCE DATA";
        cout<<"\n1.ENTER NEW STUDENT DATA";
        cout<<"\n2.DISPLAY THE STUDENTS' DATA";
        cout<<"\n3.REMOVE STUDENT DATA";
        cout<<"\n4.DISPLAY SPECIFIC DATA AND FOR REPORT CARD";
        cout<<"\n5.MODIFY THE DATA=";
        cout<<"\nENTER ANY OTHER KEY OUT OF 1 TO 5 TO EXIT!";
        cout<<"\nEnter your choice=";
        cin>>i;
        switch(i)
        {
            case 1:enter_data();
            break;
            case 2:display_d();
            break;
            case 3:remove_data();
            break;
            case 4:display_sp();
            break;
            case 5:modify_s();
            break;
            default:exit(0);
        }
    }while(i>=0||i<=5);
    return 0;
}
void enter_data()
{
    student s;
    ofstream fout;
    fout.open("Student.dat",ios::out|ios::binary|ios::app);
    if(!fout)
    {
        cout<<"\file is not open!";
        cin.ignore();
        cin.get();
        return;
    }
    cout<<"\nEnter the student data";
    s.enter();
    fout.write((char*)&s,sizeof(s));
    fout.close();
    cout<<"\nStudent record added!";
    cin.ignore();
    cin.get();
}
void display_d()
{
    student s;
    ifstream fin;
    fin.open("Student.dat",ios::in|ios::binary);
    cout<<"\nDisplaying all of the records";
    if(!fin)
    {
        cout<<"\nfile is not open!";
        cin.ignore();
        cin.get();
        return;
    }
    while(fin.read((char*)&s,sizeof(s)))
    {
        s.display();
    }
    fin.close();
    cin.ignore();
    cin.get();
}
void remove_data()
{
    student s;
    int n;
    cout<<"\nEnter the roll number of the record to be deleted=";
    cin>>n;
    ifstream fin;
    ofstream fout;
    fin.open("Student.dat",ios::in|ios::binary);
    fout.open("S",ios::out);
    if(!fin)
    {
        cout<<"\nfile not open";
        cin.ignore();
        cin.get();
        return;
    }
    fin.seekg(0,ios::beg);
    while(fin.read((char*)&s,sizeof(s)))
        {
            if(s.getroll()!=n)
            {
                fout.write((char*)&s,sizeof(s));
            }
        }
    fin.close();
    fout.close();
    remove("Student.dat");
    rename("S","Student.dat");
    cout<<"\nRecord deleted!";
    cin.ignore();
    cin.get();
}
void display_sp()
{
    student s;
    int i,flag=0;
    ifstream fin;
    fin.open("Student.dat",ios::in|ios::binary);
    if(!fin)
    {
        cout<<"\nFile isn't open!";
        cin.ignore();
        cin.get();
        return;
    }
    cout<<"\nEnter the roll no of the record to be displayed=";
    cin>>i;
    while(fin.read((char*)&s,sizeof(s)))
          {
              if(s.getroll()==i)
              {
                s.report_tab();
                flag=1;
              }
          }
    fin.close();
    if(flag==0)
     cout<<"\nRecord doesn't exist!";
     cin.ignore();
     cin.get();
}
void modify_s()
{
    student s;
    int n,flag=0;
    long long unsigned pos=0;
    fstream fio;
    fio.open("Student.dat",ios::out|ios::in|ios::binary);
    cout<<"\nEnter the roll no. of the record to be modified=";
    cin>>n;
    if(!fio)
    {
        cout<<"\nFile isn't open!";
        cin.ignore();
        cin.get();
        return;
    }
    while(fio.read((char*)&s,sizeof(s))&&flag==0)
    {
        if(s.getroll()==n)
        {
            s.modify();
            pos=(-1)*sizeof(s);
            fio.seekp(pos,ios::cur);
            fio.write((char*)&s,sizeof(s));
            cout<<"\nRecord modified!";
            flag=1;
        }
    }
    fio.close();
    if(flag==0)
        cout<<"\nRecord doesn't exist!";
    cin.ignore();
    cin.get();
}
