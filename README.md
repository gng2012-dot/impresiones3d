# Foto a 3D para Bambu Lab A1

App local para Windows que convierte la foto de un objeto en un modelo 3D listo para imprimir en una **Bambu Lab A1** (con **AMS lite** para multicolor). Funciona en CPU, sin placa NVIDIA.

Usa [TripoSR](https://github.com/VAST-AI-Research/TripoSR) (licencia MIT) para generar el modelo a partir de una sola imagen.

## Versión web (index.html)

Además de la app de Python, el repo incluye `index.html`: una página que convierte la foto en un **relieve**, una **litofanía** o una **silueta extruida** (llaveros, toppers) y descarga el STL. Todo se calcula en el navegador, sin instalar nada. No genera un modelo 3D completo del objeto: para eso se usa la app de Python.

Para usarla online, activá GitHub Pages en **Settings > Pages**, elegí la rama `main` y la carpeta raíz. La página queda en `https://TU-USUARIO.github.io/foto-a-3d/`.

## Qué genera la app de Python

- `modelo.stl`: un solo color.
- `modelo_color.obj` + `modelo_color.mtl`: hasta 4 colores, para asignarlos a los slots del AMS lite en Bambu Studio.

## Requisitos (Windows, una sola vez)

1. [Python 3.11](https://www.python.org/downloads/) (marcar "Add to PATH")
2. [Git](https://git-scm.com/download/win)
3. [CMake](https://cmake.org/download/) (marcar "Add to PATH")
4. Build Tools de Visual Studio con la carga "Desarrollo para el escritorio con C++" (para compilar `torchmcubes`)

## Instalación y uso

```bat
git clone https://github.com/TU-USUARIO/foto-a-3d.git
cd foto-a-3d
instalar.bat
iniciar.bat
```

- `instalar.bat` crea el entorno, instala PyTorch (CPU) y clona TripoSR. Tarda y descarga varios GB.
- `iniciar.bat` abre la app en el navegador. La primera vez descarga el modelo de IA (~1,7 GB).
- Sin NVIDIA, cada foto tarda varios minutos.

## Consejos para la foto

- Un solo objeto, de frente o apenas desde arriba, buena luz y fondo liso.
- Con una sola foto la IA inventa la parte de atrás: sirve para figuras y objetos simples, no para piezas con medidas exactas.

## Imprimir

- Abrí el STL en Bambu Studio para un solo color.
- Para multicolor, abrí el OBJ (con el `.mtl` en la misma carpeta) y asigná cada color a un slot del AMS lite (máximo 4).
- Los archivos quedan en la carpeta `salidas/`.

## Estado

Proyecto en desarrollo, sin probar en todas las configuraciones. Si algo falla en la instalación, abrí un issue con el mensaje de error.
