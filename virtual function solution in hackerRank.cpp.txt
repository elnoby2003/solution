#include <iostream>
#include <cmath>
#include <cstdlib>
#include <string>
#include <cstdint>
#include <array>
#include <algorithm>
#include <fstream>
#include <bitset>
using namespace std;
class Person {//main Class

	string Name;
	int Age;
public:
	void setName(string name) {
		Name = name;
	}
	string getName() {
		return Name;
	}
	void setAge(int age) {
		Age = age;
	}
	int getAge() {
		return Age;
	}
	virtual void getdata() = 0;
	virtual void putdata() = 0;
	
};  
class Prefosser : public Person
{
	int Publications;
	static int Cur_id ;
public:
	
	void getdata() {
		string name;
		int Age;
		cin >> name >> Age >> Publications;
		setName(name);
		setAge(Age);
	}
	Prefosser() {
		Cur_id++;
	}
	void putdata() {
		cout << getName() << " " << getAge() << " " << Publications << " " << Cur_id<<endl;
	}
};
int Prefosser::Cur_id = 0;

class Student : public Person {
	int marks[6];
	static int Cur_id;
	
public:
	void getdata() {
		string name;
		int Age;
		cin >> name >> Age;
		setName(name);
		setAge(Age);
		for (int i = 0; i < 6; i++)
		{
			cin >> marks[i];
		}
	}
	int SumMarks(int arr[6]) {
		int sumMarks = 0;
		for (int i = 0; i < 6; i++)
		{
			sumMarks += arr[i];
		}
		return sumMarks;
	}
	void putdata() {
		cout << getName() << " " << getAge() << " " << SumMarks(marks) << " " << Cur_id<<endl;
	}
	Student() {
		Cur_id++;
	}
};
int Student::Cur_id = 0;

int main() {
	int ObjNumbers;
	cin >> ObjNumbers;
	Person* Obj{};
	int Choice;
	for (int i = 0; i < ObjNumbers; i++)
	{
	cin >> Choice;
		if (Choice==1)
			Obj = new Prefosser;
		else if (Choice == 2)
			Obj = new Student;
		Obj->getdata();
		Obj->putdata();	
	}
}


	