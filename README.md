# Estructura del repositorio:

pdf_converter/
│
├── README.md
├── requirements.txt
├── pdf_converter.py
└── .gitignore

# Contenido de requirements.txt:
PyPDF2==3.0.1
pandas==2.0.0
tabula-py==2.9.0

# Contenido de .gitignore:
__pycache__/
*.pyc
*.pdf
*.xlsx
venv/
.env    


# Conversor PDF a Excel

Una aplicación simple para convertir archivos PDF a formato Excel.

## Requisitos previos
- Python 3.7 o superior
- Java Runtime Environment (JRE)

## Instalación

1. Clona el repositorio:
```bash
git clone https://github.com/tu-usuario/pdf-to-excel-converter.git
cd pdf-to-excel-converter
```

2. Crea un entorno virtual (opcional pero recomendado):
```bash
python -m venv venv
# En Windows:
venv\Scripts\activate
# En macOS/Linux:
source venv/bin/activate
```

3. Instala las dependencias:
```bash
pip install -r requirements.txt
```

## Uso

1. Ejecuta el script:
```bash
python pdf_converter.py
```

2. Haz clic en "Select PDF File"
3. Selecciona tu archivo PDF
4. El archivo Excel se guardará en la misma ubicación que el PDF

## Características
- Interfaz gráfica simple
- Soporte para múltiples páginas
- Preserva la estructura de las tablas
- Manejo de errores con retroalimentación al usuario

## Contribuir
Las contribuciones son bienvenidas. Por favor, abre un issue primero para discutir los cambios que te gustaría hacer.
