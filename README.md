# RETO-2-POO
### Soy Jhon Sebastian Rodriguez Ramirez y pertenezco al grupo de "Parchados".



## Caso de estudio: Restaurante
A partir de este caso, fueron modelados los siguientes diagramas de UML

### Relacion Restaurante - cliente
```mermaid
classDiagram
    Restaurante <-- Cliente : entrar() comprar()
    class Restaurante{
      +ubicacion : str
      +nombre : str
      +abrir_restaurante()
      +cerrar_Restaurante()
    }
```
### Relacion Restaurante - Componentes
```mermaid
classDiagram
    Restaurante *-- Cocina
    Restaurante *-- Menu
    Restaurante *-- Personal
    Restaurante *-- Salon
    class Restaurante{
      +ubicacion : str
      +nombre : str
      +abrir_restaurante()
      +cerrar_Restaurante()
    }
    class Menu{
        +platos : list
        +precios : float
        +mostrar_informacion()
        +calcular_total(precios)


    }
    class Personal{
        +contrato : str
        +cargo : str
        +jornada : str
        +uniforme : str
        +salario(cargo)
        +actividad (cargo)

    }
    class Salon{
        +capacidad : int
        +numero_de_sillas : int
        +mesas : list[Mesa]
        +organizar_mesas()
        +calcular_ocupacion() 
        +asignar_mesa()
    }
    class Cocina{
        +area : str
        +preparar_platos ()
        +almacenar_recursos()

    }
    
    
```

### Relacion entre personal
```mermaid
classDiagram
    Personal <|-- Cocinero
    Personal <|-- Mesero
    Personal <|-- Ayudante_De_Cocina
    Personal <|-- Cajero
    
    class Personal{
        +contrato : str
        +cargo : str
        +jornada : str
        +uniforme : str
        +salario(cargo) 
        +actividad(cargo)
    }

    class Mesero{
        +tomar_pedido()
        +entregar_pedido()
        +calcular_total(pedido : list[float]) 
        +limpiar_mesas()
    }

    class Cocinero{
        +preparar_platos(pedidos : list[str])
        +supervisar_inventario()
        +limpiar_area_de_trabajo()
    }

    class Ayudante_De_Cocina{
        +organizar_utensilios()
        +apoyar_preparacion(pedidos : list[str])
        +limpiar_areas()
    }

    class Cajero{
        +cobrar_cuenta(pedido : list[float]) 
        +emitir_factura()
        +gestionar_caja()
    }


```

### Relacion Cocina 
```mermaid
classDiagram
    Cocina *-- Cocinero
    Cocina *-- Utencilios
    Cocina <|-- Ayudante_De_Cocina
    Cocina <|-- Maquinaria
    
    class Cocina{
        +area : str

        +almacenar_inventario(recurso : str, cantidad : int)
        
    }

    class Utencilios{
        +usar()
        +limpiar()
        +guardar() 
        +utencilios : list[str]
    }

    class Cocinero{
        +preparar_platos(pedidos : list[str])
        +supervisar_inventario()
        +limpiar_area_de_trabajo()
    }

    class Ayudante_De_Cocina{
        +organizar_utensilios()
        +apoyar_preparacion(pedidos : list[str])
        +limpiar_areas()
    }

    class Maquinaria{
        +id : int
        +marca : str
        +modelo : str
        +estado : str  // Operativo, En mantenimiento, Fuera de servicio
        +energia : str // Gas, Eléctrica
        +encender()
        +apagar()
        +revisar_estado()
    }

```
### Relacion Maquinaria
```mermaid
classDiagram
    Maquinaria <|-- Estufa
    Maquinaria <|-- Horno
    Maquinaria <|-- Refrigerador
    Maquinaria <|-- Congelador
    
    class Maquinaria{
        +id : int
        +marca : str
        +modelo : str
        +estado : str  // Operativo, En mantenimiento, Fuera de servicio
        +energia : str // Gas, Eléctrica
        +encender()
        +apagar()
        +revisar_estado() 
    }

    class Estufa{
        +quemadores : int
        +tipo : str // Gas, Inducción
        +ajustar_temperatura(quemador : int, temperatura : int)
    }

    class Horno{
        +capacidad : int // en litros
        +ajustar_temperatura(temperatura : int)
        +programar_tiempo(tiempo : int)
    }

    class Refrigerador{
        +capacidad : int // en litros
        +temperatura : float
        +ajustar_temperatura(temperatura : float)
        +consultar_inventario() : dict[str, int]
    }

    class Congelador{
        +capacidad : int // en litros
        +temperatura_minima : float
        +ajustar_temperatura(temperatura : float)
        +consultar_inventario() : dict[str, int]
    }

```
### Relacion Salon
```mermaid
classDiagram
    Salon *-- Mesa
    Mesa *-- Cliente
    Mesa *-- Mesero
    
    class Salon{
        +capacidad : int
        +numero_de_sillas : int
        +mesas : list[Mesa]
        +organizar_mesas()
        +calcular_ocupacion() 
        +asignar_mesa()
    }

    class Mesa{
        +numero : int
        +capacidad : int
        +estado : str  // Disponible, Ocupada, Reservada
        +asignar_cliente(cliente : Cliente)
        +asignar_mesero(mesero : Mesero)
        +liberar_mesa()
    }

    class Cliente{
        +nombre : str
        +pedido : list[str]
        +elegir_mesa(salon : Salon) 
        +realizar_pedido(pedido : list[str])
    }

    class Mesero{
        +nombre : str
        +platos_servidos : list[str]
        +asignar_mesa(mesa : Mesa)
        +tomar_pedido(cliente : Cliente) 
        +entregar_pedido(mesa : Mesa)
    }

```
###
