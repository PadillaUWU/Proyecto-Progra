#include <iostream>
#include <vector> // Necesario para usar vectores
#include <cmath>
using namespace std;

// Función para calcular el desgaste total de los neumáticos en porcentaje
double desgasteTotal(const std::vector<int>& velocidades, double temperaturaPista, double presionNeumaticos) {
    // Supongamos que hay una relación lineal entre la velocidad en las curvas y el desgaste
    // También consideremos la influencia de la temperatura y la presión

    double factorVelocidad = 0.01; // Valor preestablecido de la relación entre velocidad y desgaste
    double factorTemperatura = 0.005; // Valor preestablecido de la relación entre la temperatura y el desgaste
    double factorPresion = 0.002; // Valor preestablecido de la relación entre la presión y el desgaste

    // Calcular la velocidad promedio
    int sumaVelocidades = 0;
    for (int velocidad : velocidades) {
        sumaVelocidades += velocidad;
    }
    double promedioVelocidad = static_cast<double>(sumaVelocidades) / velocidades.size();

    // Calcular el desgaste total
    double desgasteTotal = (promedioVelocidad * factorVelocidad + temperaturaPista * factorTemperatura - presionNeumaticos * factorPresion);

    int desgaste = static_cast<int>((desgasteTotal / 100.0) * 100);

    return desgaste;
}

// Función para calcular el desgaste por vuelta en porcentaje
double desgasteVuelta(double desgasteTotal, int cantidadVueltas) {
    // Supongamos que el desgaste por vuelta es proporcional al desgaste total
    // Consideremos también la cantidad de vueltas

    double factorVueltas = 0.02; // Valor preestablecido de la relación entre vueltas y desgaste

    // Calcular el desgaste por vuelta
    double desgastePorVuelta = desgasteTotal * factorVueltas * cantidadVueltas;

    int desgasteVuelta = static_cast<int>((desgastePorVuelta / 100.0) * 100);

    return desgasteVuelta;
}
int main () {
cout << "Programa para calcular el desgaste en porcentaje de desgaste de los neumáticos en función de la temperatura de la pista, velocidad promedio en curvas y presión de los neumáticos" << endl;
cout << "Ingresa cuantas curvas tiene la pista en la que estas corriendo:" << endl;
int cantidadCurvas;
cin >> cantidadCurvas;
// Función de vector para almacenar las velocidades que va a introcducir el usuario
vector<int> velocidades;
// ciclo para almacenar las velocidades en cada curva
for (int i = 0; i < cantidadCurvas; ++i) {
    int velocidadCurva;
    cout << "Ingresa tu velocidad en la curva " << i + 1 << ": ";
    cin >> velocidadCurva;
    //Función que nos ayuda a agregarle un elemento o valor final a nuestro vector de velocidades
    velocidades.push_back(velocidadCurva);
}
// Calcular la suma total de velocidades
int sumaVelocidades = 0;
for (int velocidad : velocidades) {
    sumaVelocidades += velocidad;
}
// Calcular el promedio
double promedioV = static_cast<double>(sumaVelocidades) / cantidadCurvas;
cout << "El promedio de velocidad en todas las curvas es: " << promedioV << endl;
cout << "Ingresa la temperatura de la pista en grados celcius ";
int temperatura; // Temperatura de la pista (en °C)
cin >> temperatura;
cout << "Ingresa la presion de los neumáticos en bares ";
double presion;// Presión de los neumáticos (en bares)
cin >> presion;
int desgastePorcentaje = calcularDesgasteNeumaticos(velocidadCurva, temperatura, presion);
cout << "El desgaste estimado de los neumáticos en una curva es del " << desgastePorcentaje << "%." << endl;
cout << "Realizando cálculos de desgaste por vueltas..." << endl;
int desgasteVuelta = (desgastePorcentaje * cantidadCurvas);
cout << desgasteVuelta;
return 0;
}
