# ale-g
from data.biblioteca import libros, categorias
from utils.operaciones import mostrar_libros_disponibles, buscar_libros_por_paginas, agregar_categoria

def menu():
    while True:
        print("\n==============================")
        print(" SISTEMA DE BIBLIOTECA")
        print("==============================")
        print("1. Ver todos los libros")
        print("2. Mostrar libros disponibles")
        print("3. Buscar libros por paginas")
        print("4. Agregar nueva categoria")
        print("5. Salir")
        
        opcion = input("Elige una opcion: ")

        if opcion == "1":
            print("\n--- TODOS LOS LIBROS ---")
            for libro in libros:
                estado = "Disponible" if libro["disponible"] else "Prestado"
                print(f"- {libro['titulo']} ({estado})")

        elif opcion == "2":
            mostrar_libros_disponibles(libros)

        elif opcion == "3":
            texto = input("Ingresa el numero maximo de paginas: ")
            if texto.isdigit():
                buscar_libros_por_paginas(libros, int(texto))
            else:
                print("Error: Debes escribir un numero.")

        elif opcion == "4":
            nueva = input("Ingresa la nueva categoria: ")
            agregar_categoria(categorias, nueva)

        elif opcion == "5":
            print("Saliendo...")
            break
        else:
            print("Opcion no valida.")

# Esto hace que funcione
if __name__ == "__main__":
    menu()
