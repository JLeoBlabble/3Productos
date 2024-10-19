
    include <iostream>
    include <vector>
    include <string>
    include <algorithm>

    int main() {
        // Preguntar cantidad de objetos en lista de compra:
        float cantidadProductos;
        while (true) {
            std::cout << "¿Cuántos productos deseas comprar? ";
            std::cin >> cantidadProductos;
            if (cantidadProductos > 0) {
                break;
            } else {
                std::cout << "Por favor introduzca el número de productos a comprar" << std::endl;
                continue;
            }
        }
    
    // Crear lista de la compra
    std::vector<std::string> listaCompraProductos;
    std::vector<float> listaCompraPrecios;
    int index = 0;
    
    // Preguntar por los productos y sus precios
    for (int i = 0; i < static_cast<int>(cantidadProductos); ++i) {
        std::string productoAñadido;
        std::cout << "Por favor introduzca el nombre del producto número " << index + 1 << ": ";
        std::cin >> productoAñadido;
        listaCompraProductos.push_back(productoAñadido);

        float precioAñadido;
        std::cout << "Por favor introduzca el precio del producto número " << index + 1 << ": ";
        std::cin >> precioAñadido;
        listaCompraPrecios.push_back(precioAñadido);
        index++;
    }

    // Encontrar el precio más barato
    float precioMasBarato = *std::min_element(listaCompraPrecios.begin(), listaCompraPrecios.end());

    // Crear lista final de compra con los productos que tienen el precio más barato
    std::vector<std::string> listaCompraFinal;
    for (size_t i = 0; i < listaCompraPrecios.size(); ++i) {
        if (listaCompraPrecios[i] == precioMasBarato) {
            listaCompraFinal.push_back(listaCompraProductos[i]);
        }
    }

    // Indicar cuál/es de los productos es/son el/los más barato/s
    std::cout << "Los productos más baratos son los que cuestan " << precioMasBarato << " euros, o sea ";
    for (const auto& producto : listaCompraFinal) {
        std::cout << producto << " ";
    }
    std::cout << std::endl;

    return 0;
}
