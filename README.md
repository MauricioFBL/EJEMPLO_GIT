# EJEMPLO_GIT
La idea de este repositorio es entender los fundamentos de git y el trabajo
colaborativo en un repositorio.

si se desea ahondar un poco mas sobre git revisar la presentacion
[presentacion git](https://docs.google.com/presentation/d/1O3kCgxjSReIGI0aW-Y2nlL9Rex2qNHTU/edit?usp=sharing&ouid=107033381423019020472&rtpof=true&sd=true)

El repositorio contara con un archivo .md con algunos de los comandos
basicos de git que sirve como apoyo 
[GIT_BASICO.md](GIT_BASICO.md)


## Ejercicio 

desarrollar codigo para poder ejecutar las operaciones matematicas basicas,
bajo las siguientes consideraciones:

- Clonar el repositorio localmente
    ```
    git clone https:...
    ```

- Situarse en la rama development y hacer ramas a partir de developmnet 
    ```
    git checkout developmnet
    ```

- crear una rama por cada operacion, en caso de tener varias personas en
el equipo asignar las operaciones aleatoriamente 
    ```
    git branch suma
    git branch ....
    ```

- Al finalizar alguna funcion hacer un push sobre la rama y hacer pull
request para fusionar la rama en development 
    ```bash
    git add operaciones.py
    git commit -m "mensaje sobre el cambio realizado en el codigo"
    git push origin mirama
    ```
    una vez pusheados los cambios en el portal de github hacer pull 
    request a development
- Asignar a alguna persona para aprovar los pull request y hacer merge

- al final resetear la rama development usando la rama development_base 
permitiendo que cualquierea pueda hacer el ejercicio

## Forma base de development 

```python
# menu (si hay tiempo)
def algo():
    pass

# suma

# resta

# multiplicacion

# division

# main
if __name__ =='__main__':
    print('hola')
```



