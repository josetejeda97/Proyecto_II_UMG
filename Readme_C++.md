# Proyecto realizado en C++
**El siguiente proyecto esta basado en el manejo de archivos, en el cual consta de un menu con 3 opciones para la creacion del archivo, lectura del archivo, manipulacion del archuivo**

## Declaracion del MENU del programa
**En el siguiente bloque de codigo se realiza la creacion de un menu, en el cual se obtienen multiples opciones como:Agregar Persona, Ver Personas,Buscar Personas,Modificar Personas**
```c++
int menu(){
	int x;
	system("cls");
	cout << "<<------Bienvenido------->>"<<endl<<endl;
	cout << "1. Agregar Persona" << endl;
	cout << "2. Ver Personas" << endl;
	cout << "3. Buscar Personas" << endl;
	cout << "4. Modificar Personas" << endl;
	cout << "5. Salir " << endl;
	cout << "Opcion ";
	cin >> x;
	return x;
```
**Se declaran las variables: ced, precio, proveedor, existencia, estado, descuento y se leen variables**
```c++
bool verifica(string ced){
	ifstream leer("Personas.txt", ios::in);
	string Nom;
	string Ced;
	float precio;
	string proveedor;
	int existencia;
	char estado;
	float descuento;
	leer >> Nom;
	while (!leer.eof()){
		leer>>Ced;
		leer>>precio;
		leer>>proveedor;
		leer>>existencia;
		leer>>estado;
		leer>>descuento;

```
**Al momento de ingresar un codigo repetido se genera el siguiente codigo:**
`if(Ced == ced){
			cout << "¡¡¡Este codigo ya existe!!!";
			Sleep(1500);
			leer.close();
			return false;
`
**se crea la variable crear para poder ingresar nuevos productos:**
```c++
void agregar (ofstream &es){
	system("cls");
	string Nom;
	string Ced;
	float precio;
	string proveedor;
	int existencia;
	char estado;
	float descuento;
	es.open("personas.txt", ios::out | ios::app);
	cout << "Nombre ";
	cin >> Nom;
	cout << "Codigo ";
	cin >> Ced;
	cout << "Precio ";
	cin >> precio;
	cout << "Proveedor ";
	cin >> proveedor;
	cout << "existencia ";
	cin >> existencia;
	cout << "Estado ";
	cin >> estado;
	cout << "Descuento ";
	cin >> descuento;
	if (verifica(Ced))
	es << Nom << " " << Ced << " " << precio << " " << proveedor << " " << existencia<< " " << estado << " " << descuento<< " " << "\n";
	es.close();
}
```
**Se crea la opcion de ver registros por medio de un While**
```c++
void verRegistros(ifstream &Lec){
	system("cls");
	string nom;
	string ced;
	float precio;
	string proveedor;
	int existencia;
	char estado;
	float descuento;
	Lec.open("Personas.txt", ios::in);
	cout<<"----Personas Registradas----"<< endl<<endl;
	Lec>>nom;
	while(!Lec.eof()){
		Lec>>ced;
		Lec>>precio;
		Lec>>proveedor;
		Lec>>existencia;
		Lec>>estado;
		Lec>>descuento;
		cout<<"Nombre------: "<<nom<<endl;
		cout<<"Codigo----: "<<ced<<endl;
		cout<<"Precio------: "<<precio<<endl;
		cout<<"Proveedor------: "<<proveedor<<endl;
		cout<<"Existencia----: "<<existencia<<endl;
		cout<<"Estado------: "<<estado<<endl;
		cout<<"Descuento------: "<<descuento<<endl;
		cout<<"--------------"<<endl;
		Lec>>nom;
	}
```
**Se crea la opcion de buscqueda en la aplicion el cual realiza la busqueda por medio del codigo**
```c++
void verRegistros(ifstream &Lec){
	system("cls");
	string nom;
	string ced;
	float precio;
	string proveedor;
	int existencia;
	char estado;
	float descuento;
	Lec.open("Personas.txt", ios::in);
	cout<<"----Personas Registradas----"<< endl<<endl;
	Lec>>nom;
	while(!Lec.eof()){
		Lec>>ced;
		Lec>>precio;
		Lec>>proveedor;
		Lec>>existencia;
		Lec>>estado;
		Lec>>descuento;
		cout<<"Nombre------: "<<nom<<endl;
		cout<<"Codigo----: "<<ced<<endl;
		cout<<"Precio------: "<<precio<<endl;
		cout<<"Proveedor------: "<<proveedor<<endl;
		cout<<"Existencia----: "<<existencia<<endl;
		cout<<"Estado------: "<<estado<<endl;
		cout<<"Descuento------: "<<descuento<<endl;
		cout<<"--------------"<<endl;
		Lec>>nom;
	}
```
**En caso no encuentre los datos realizara lo siguiente:**
```c++
cout<<"Dato no encontrado"<<endl;
	system("pause");
```
**Se cuenta con la opcion de modificar el cual modifica el archivo Personas.txt:¨**
```c++
void modificar(ifstream &Lec){
	system("cls");
	string nom;
	string ced;
	float precio;
	string proveedor;
	int existencia;
	char estado;
	float descuento;
	string cedaux;
	string nomaux;
	float precioux;
	string proveedorux;
	int existenciaux;
	char estadoux;
	float descuentoux;
	Lec.open("Personas.txt", ios::in);
	ofstream aux("auxiliar.txt", ios::out);
	if(Lec.is_open()){
		cout<<"Codigo ";
		cin>>cedaux;
		Lec>>nom;
		while(!Lec.eof()){
			Lec>>ced;
			Lec>>precio;
		Lec>>proveedor;
		Lec>>existencia;
		Lec>>estado;
		Lec>>descuento;   
			if(ced == cedaux){
				cout<<"Nuevo nombre ";
				cin>>nomaux;
				cout<<"Nuevo precio ";
				cin>>precioux;
				cout<<"Nuevo proveedor ";
				cin>>proveedorux;
				cout<<"Nueva existencia ";
				cin>>existenciaux;
				cout<<"Nuevo estado ";
				cin>>estadoux;
				cout<<"Nuevo descuento ";
				cin>>descuentoux;
				aux<<nomaux<<" "<<ced<< " " <<precioux << " " << proveedorux << " " <<existenciaux << " " <<estadoux << " " <<descuentoux << "\n";
			}else{
				aux<<nom<<" " <<ced<<"\n";
			}
			Lec>>nom;
			
		}
		Lec.close();
		aux.close();
```
**En dado caso el usaurio coloque un valor malo ejecutara lo siguiente:**
```c++
out<<"Error"<<endl;
	remove("Personas.txt");
	rename("auxiliar.txt", "Personas.txt");

```
##Por ultimo nos da la opcion de volver a regresar al menu o cerrar programa:**
```c++
nt main(){
	ofstream Esc;
	ifstream Lec;
	int op;
	do{
		system("cls");
		op = menu();
		switch(op){
			case 1: 
			    agregar(Esc);
			break;
			case 2:
				verRegistros(Lec);
			break;
			case 3:
				buscarPersona(Lec);
			break;
			case 4:
				modificar(Lec);
			break;
		}	
	} while(op != 4);
	
	return 0;
```