# using-the-4-principle-in-oop-in-c++
#include <bits/stdc++.h>
using namespace std;
class Employee {
protected:
	string name;
	int id;
	double salary;
public:
	Employee() {
		name = "";
		id = 0;
		salary = 0.0;
	}
	Employee(string name, int id, double salary) {
		this->name = name;
		this->id = id;
		this->salary = salary;
	}

	void setName(string name) {
		this->name = name;
	}
	string getName() {
		return this->name;// return name;
	}
	void setId(int id) {
		this->id = id;
	}
	int getId() {
		return this->id;// return id;
	}
	void setSalary(double salary) {
		this->salary = salary;
	}
	// pure virtual function
	virtual double getTotalSalary() = 0;

	virtual void print() {
		cout << "Your Name: " << name << "\nYour Id: " << id
			<< "\nYour Salary: " << salary << endl;
	}
};

class Sales : public Employee {
private:
	float grossSales;
	float commissionRate;
public:
	Sales() {
		grossSales = 0.0;
		commissionRate = 0.0;
	}
	Sales(string name, int id, double salary, 
		float grossSales, float commissionRate): Employee(name, id, salary) {
		this->grossSales = grossSales;
		this->commissionRate = commissionRate;
	}
	void setGrossSales(float grossSales) {
		this->grossSales = grossSales;
	}
	float getGrossSales() {
		return this->grossSales;
	}
	void setCommissionRate(float commissionRate) {a
		this->commissionRate = commissionRate;
	}
	float getCommissionRate() {
		return this->commissionRate;
	}
	double getTotalSalary() {
		return salary + (grossSales * commissionRate);
	}
	void print() override {
		Employee::print();
		cout << "Your Gross Sales: " << grossSales
			<< "\nYour Commission Rate: " << commissionRate << endl;
	}
};

class Engineer : public Employee {
private:
	string specialty;
	int experience;
	int overTimeHour;
	int overTimeHourRate;
public:
	Engineer() {
		specialty = "";
		experience = 0;
		overTimeHour = 0;
		overTimeHourRate = 0;
	}
	Engineer(string name, int id, double salary, string specialty,
	int experience, int overTimeHour, int overTimeHourRate):
	Employee (name, id, salary){
		this->specialty = specialty;
		this->experience = experience;
		this->overTimeHour = overTimeHour;
		this->overTimeHourRate = overTimeHourRate;
	}
	void setSpecialty(string specialty) {
		this->specialty = specialty;
	}
	string getSpecialty() {
		return this->specialty;
	}
	void setExperience(int experience) {
		this->experience = experience;
	}
	int getExperience() {
		return this->experience;
	}
	void setOverTimeHour(int overTimeHour) {
		this->overTimeHour = overTimeHour;
	}
	int getOverTimeHour() {
		return this->overTimeHour;
	}
	void setOverTimeHourRate(int overTimeHourRate) {
		this->overTimeHourRate = overTimeHourRate;
	}
	int getOverTimeHourRate() {
		return this->overTimeHourRate;
	}

	double getTotalSalary() {
		return salary + (overTimeHour * overTimeHourRate);
	}
	
	void print() override {
		Employee::print();
		cout << "Your specialty: " << specialty
			<< "\nYour Experience: " << experience
			<< "\nYour Over Time Hour: " << overTimeHour
			<< "\nYour Over Time Hour Rate: " << overTimeHourRate
			<< endl;
	}
};

int main() {

	Employee* emp;

	Sales sal("Ahmed", 1, 5000, 15, 150);

	emp = &sal;

	emp->print();
	cout << "Total Salary: " << emp->getTotalSalary() << endl;

	cout << "\n=============================================================\n\n";

	Engineer eng("Mohamed", 1, 20000, "CS", 2, 10, 700);

	emp = &eng;
	emp->print();
	cout << "Total Salary: " << emp->getTotalSalary() << endl;
}
