#include <iostream>
#include <cmath>
#include <vector> // libreria para usar vectores
using namespace std;
// Función para calcular el desgaste de los neumáticos en porcentaje
double calcularDesgasteNeumaticos(double velocidadCurvas, double temperaturaPista, double presionNeumaticos) {
    // Supongamos que hay una relación lineal entre la velocidad en las curvas y el desgaste
    // También consideremos la influencia de la temperatura y la presión
    double factorVelocidad = 0.01; // Valor preestablecido de la relacion entre velocidad y desgaste
    double factorTemperatura = 0.005; // Valor preestablecido de la relacion entre la temperatura y el desgaste
    double factorPresion = 0.002; // Valor preestablecido de la relacion entre la presión y desgaste
    // Calcular el desgaste total
    double desgasteTotal = (velocidadCurvas * factorVelocidad + temperaturaPista * factorTemperatura - presionNeumaticos * factorPresion);
    int desgaste = (desgasteTotal / 100.0) * 100;
    return desgaste;
}
int main() {
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
