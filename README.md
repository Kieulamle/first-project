#include <iostream>
using namespace std;
class Casi
{
public:
	string hoten;
	int nam;
	int dia;
	int buoibieudien;
	long luong;
	virtual void Nhap()
	{
		cout << "Nhap ho va ten ca si:";
		cin >> hoten;
		cout << "Nhap so nam lam viec:";
		cin >> nam;
		cout << "Nhap so dia ban ra:";
		cin >> dia;
		cout << "Nhap so buoi bieu dien:";
		cin >> buoibieudien;
	}
	virtual void Xuat()
	{
		cout << "Ho va ten:" << hoten << endl;
		cout << "So nam lam viec:" << nam << endl;
		cout << "So dia ban ra:" << dia << endl;
		cout << "So buoi bieu dien:" << buoibieudien << endl;
	}
	virtual void Tinhluong() = 0;


};
class Casichua :public Casi
{
public:
	void Nhap()
	{
		Casi::Nhap();
	}
	void Tinhluong()
	{
		this->luong = 3000000 + 500000 * this->nam + 1000 * this->dia + 200000 * this->buoibieudien;
	}
	void Xuat()
	{
		Casi::Xuat();
	}

};
class Casinoi :public Casi
{
public:
	int gameshow;
	void Nhap()
	{
		Casi::Nhap();
		cout << "Nhap so luong gameshow:";
		cin >> gameshow;
	}
	void Tinhluong()
	{
		this->luong = 5000000 + 500000 * this->nam + 1200 * this->dia + 500000 * this->buoibieudien+500000*this->gameshow;
	}
	void Xuat()
	{
		Casi::Xuat();
		cout << "So gameshow:" << gameshow << endl;

	}

};
int main()
{
	int n;
	cin >> n;
	Casi** casi = new Casi * [n];
	for (int i = 0; i < n; i++)
	{
		int luachon;
		cin >> luachon;
		for (int i = 0; i < n; i++)
		{
			if (luachon == 1) casi[i] = new Casichua();
			else if (luachon == 2) casi[i] = new Casinoi();
		}
		casi[i]->Nhap();
	}
	for (int i = 0; i < n; i++)
	{
		casi[i]->Tinhluong();
		casi[i]->Xuat();
	}
	return 0;

}
