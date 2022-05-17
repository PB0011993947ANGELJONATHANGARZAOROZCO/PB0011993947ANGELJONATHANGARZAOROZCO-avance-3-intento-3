#include <iostream>
#include <stdio.h>
#include<string.h>
#include <fstream>
#include <stdlib.h>
#include <string>

using namespace std;


struct consultorio {
	string paci;
	char hrs[100];
	string nomtrat;
	int prec;
	int num;
	string desc;
	int catra, total, subtotal;
	int hora, min;
	int subt, iva;
};
void archivo();

consultorio citas[3];
int main()
{
	int opcion, a, i, j;


	do {
		cout << "bienvenido al consultorio de tatalan (Angel Jonathan Garza Orozco)" << endl;
		cout << "1-Agendar cita <3" << endl;
		cout << "2-Modificar cita <3" << endl;
		cout << "3-Eliminar cita <3" << endl;
		cout << "4-Lista de citas vigentes <3" << endl;
		cout << "5-Limpiar pantalla <3" << endl;
		cout << "6-Salir <3" << endl;
		cin >> opcion;


		switch (opcion)
		{
		case 1:

			for (i = 0; i < 3; i++)
			{
				cout << "El numero de cita es:" << endl;
				citas[i].num = i + 1;
				cout << citas[i].num << endl;
				cout << "Ingrese el nombre del paciente" << endl;
				cin >> citas[i].paci;
				cin.ignore();
				getline(cin, citas[i].desc);
				cout << "Ingrese la hora: ";
				cin >> citas[i].hora;
				cout << "Ingrese los minutos: ";
				cin >> citas[i].min;

				if (citas[i].hora < 24 && citas[i].hora >= 0 && citas[i].min < 60 && citas[i].min >= 0) {
					cout << "La hora quedo establecida como: " << citas[i].hora << ":" << citas[i].min << endl;
					system("pause");
				}
				else {
					cout << "La hora es invalida intentelo de nuevo" << endl;
					system("pause");
					system("cls");
					cout << "pulse 1) para volver a iniciar la cita" << endl;
					cin >> a;
					break;
				}
				cout << "Ingrese el nombre del tratamiento" << endl;
				cin >> citas[i].nomtrat;
				cin.ignore();
				getline(cin, citas[i].desc);
				cout << "Ingrese una descripcion" << endl;
				cin.ignore();
				getline(cin, citas[i].desc);
				cout << "Ingrese la cantidad del tratamiento" << endl;
				cin >> citas[i].catra;
				cout << "Ingrese el precio unitario" << endl;
				cin >> citas[i].prec;
				citas[i].total = citas[i].prec * citas[i].catra;
				citas[i].subtotal = citas[i].catra * citas[i].prec;
				citas[i].iva = citas[i].subtotal * 0.16;
				citas[i].total = citas[i].subtotal + (citas[i].subtotal * 0, 16);

				cout << "El total es: $" << citas[i].total << endl;

			}


			cout << "¿¿Desea regresar al menu??" << endl;
			cout << "1-si" << endl;
			cout << "2-no" << endl;
			cin >> a;


			break;
		case 2:
			cout << "Ingrese el numero de cita que desee modificar" << endl;
			cin >> j;
			i = j - 1;
			for (i; i < j; i++)
			{

				cout << "Ingrese el nombre del paciente" << endl;
				cin >> citas[i].paci;
				cout << "Ingrese la hora del tratamiento (favor de ingresarlo en 24 horas)" << endl;
				cin >> citas[i].hrs;
				cout << "Ingrese el nombre del tratamiento" << endl;
				cin >> citas[i].nomtrat;
			}
			break;
		case 3:
		{
			int j;
			cout << "ingrese el  registro a eliminar";
			cin >> j;
			j = j - 1;
			for (int i = j; i == j; i++)
			{
				cout << "Eliminando registro" << j + 1 << endl;

				citas[i].paci = " ";
				citas[i].hora = 0;
				citas[i].min = 0;
				citas[i].nomtrat = " ";
				citas[i].desc = " ";
				citas[i].prec = 0;
				citas[i].catra = 0;
			}
		}

		cout << "¿¿Desea regresar al menu??" << endl;
		cout << "1-si" << endl;
		cout << "2-no" << endl;
		cin >> a;

		break;
		case 4:

			for (i = 0; i < 3; i++)
			{
				cout << "El numero de cita es:  " << citas[i].num << endl;
				cout << "El paciente es: " << citas[i].paci << endl;
				cout << "La hora de la cita es a las: " << citas[i].hora << ":" << citas[i].min << endl;
				cout << "El Tratamiento es: " << citas[i].nomtrat
					<< endl;
				cout << "subtotal de la cita es: " << citas[i].subtotal << endl;
				cout << "iva de la cita es: " << citas[i].iva << endl;

			}
			cout << "¿¿Desea regresar al menu??" << endl;
			cout << "1-si" << endl;
			cout << "2-no" << endl;
			cin >> a;

			break;
		case 5:
			system("cls");
			cout << "!!yey ahora tu pantalla esta limpia!!" << endl;
			cout << "¿¿Desea regresar al menu??" << endl;
			cout << "1-si" << endl;
			cout << "2-no" << endl;
			cin >> a;

			break;
		case 6:
			archivo();

			cout << "Muchas gracias por su visita, que tenga un buen dia" << endl;

			a = 2;

			break;
		default:
			cout << "Ingrese una ocpion valida" << endl;
			a = 1;


		}


	} while (a == 1);

}

void archivo()
{
	ofstream archivo;
	string tex;

	cout << "citas uwu" << endl;
	archivo.open("citas uwu", ios::out);

	if (archivo.fail())
	{
		cout << "error no se creo su archivo :c";
		exit(1);

	}


	archivo << "no.de cita" << "\t";
	archivo << "paciente" << "\t";
	archivo << "hora" << "\t";
	archivo << "tratamiento" << "\t";
	archivo << "descripcion" << "\t";
	archivo << "precio unitario" << "\t";
	archivo << "subtotal" << "\t";
	archivo << "iva" << "\t";
	archivo << "cantidad de tratamiento" << "\t";
	archivo << "total" << "\t" << "\n";

	for (int i = 0; i < 3; i++)
	{

		archivo << i + 1 << ".-" << "\t" << "\t";
		archivo << citas[i].paci << "\t" << "\t";
		archivo << citas[i].hora << ":";
		archivo << citas[i].min << "\t" << "\t";
		archivo << citas[i].nomtrat << "\t" << "\t";
		archivo << citas[i].desc << "\t";
		archivo << citas[i].prec << "\t" << "\t";
		archivo << citas[i].subtotal << "\t" << "\t";
		archivo << citas[i].iva << "\t";
		archivo << citas[i].catra << "\t" << "\t" << "\t";
		archivo << citas[i].total << "\t" << "\t" << "\t" << "\t" << "\n";

	}


	archivo.close();
}
