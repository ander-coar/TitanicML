# Hallazgos del Análisis Exploratorio de Datos (EDA) - Titanic

## Fase 1: Comprendiendo el problema y los datos

### 1️⃣ Definiendo el problema: ¿Qué queremos predecir o explicar?

Predecir si un pasajero sobrevivió (Survived) según sus características.

- 🧠 Columna objetivo (target): Survived (1 = sobrevivió, 0 = no sobrevivió)
- Todo el análisis gira en torno a entender qué variables influyen en Survived.

### 📒 Bitacora de variables (matriz de metadatos) o data dictionary:
- PassengerId:
    - Cantidad de datos: 891
    - Valores faltantes: 0
    - Valores únicos (Cardinalidad): 891
    - Tipo de variable: Cuantitativa discreta (Identificador unico) 
    - Tipo de dato: Entero (int64)
    - Descripción: ID único para cada pasajero
    - Rango: 1 a 891
    - Distribución: Uniforme (incremental de 1 en 1)
    - Tipo de dato vacio: Ninguno
    - Clasificación de ausencia (MCAR - MAR - MNAR): Ninguno
    - Outliers: Ninguno
    - Dependencias: Ninguna (No afecta ni es afectada por otras variables)
    - Tipo de relación con el target: Ninguna
    - Tratamiento previsto: Eliminar antes del modelado
    - Relevancia: Nula (No aporta información predictiva)
    - Observaciones: Sin errores, datos limpios
- Survived: 
    - Cantidad de datos: 891
    - Valores faltantes: 0
    - Valores únicos (Cardinalidad): 2 (0 - No sobrevivió, 1 - Sobrevivió)
    - Tipo de variable: Cuantitativa discreta (Binaria)
    - Tipo de dato: Entero (int64)
    - Descripción: Indica si el pasajero sobrevivió o no
    - Rango: 0 a 1
    - Distribución: 
    - Tipo de dato vacio: Ninguno
    - Clasificación de ausencia (MCAR - MAR - MNAR): Ninguno
    - Outliers: Ninguno
    - Dependencias: Analíticamente, depende de otras variables, pero no presenta dependencias estructurales dentro del dataset.
    - Tipo de relación con el target: Ninguna (Es la variable objetivo)
    - Tratamiento previsto: Mantener sin transformaciones
    - Relevancia: Alta (Variable objetivo principal)
    - Observaciones: Sin errores, datos limpios
- Pclass:
    - Cantidad de datos: 891
    - Valores faltantes: 0
    - Valores únicos (Cardinalidad): 3 (1 - Clase 1, 2 - Clase 2, 3 - Clase 3)
    - Tipo de variable: Cuantitativa discreta (Ordinal)
    - Tipo de dato: Entero (int64)
    - Descripción: Indica la clase del billete del pasajero
    - Rango: 1 a 3
    - Distribución: 
    - Tipo de dato vacio: Ninguno
    - Clasificación de ausencia (MCAR - MAR - MNAR): Ninguno
    - Outliers: Ninguno
    - Dependencias: 
    - Tipo de relación con el target: 
    - Tratamiento previsto: 
    - Relevancia: 
    - Observaciones: Sin errores, datos limpios
- Name:
    - Cantidad de datos: 891
    - Valores faltantes: 0
    - Valores únicos (Cardinalidad): 891 (Todos los nombres son únicos)
    - Tipo de variable: Cualitativa nominal (Identificador unico)
    - Tipo de dato: Objeto (object) / String
    - Descripción: Nombre completo del pasajero
    - Rango: N/A
    - Distribución: N/A 
    - Tipo de dato vacio: Ninguno
    - Clasificación de ausencia (MCAR - MAR - MNAR): Ninguno
    - Outliers: Ninguno
    - Dependencias: 
    - Tipo de relación con el target: 
    - Tratamiento previsto: 
    - Relevancia: 
    - Observaciones: 
      - Los nombres contienen la siguiente estructura: 
        - Apellido,  Título. Nombre
          - Título (Mr, Mrs, Miss, Master, etc)
          - Los nombres en parentesis indican que es una mujer casada y contienen su nombre de pila.
        - Es posible extraer títulos y crear una nueva variable categórica (Title) para análisis futuros.
- Sex:
  - Cantidad de datos: 891
    - Valores faltantes: 0
    - Valores únicos (Cardinalidad): 2 (male, female)
    - Tipo de variable: Cualitativa nominal
    - Tipo de dato: objeto (object) / String
    - Descripción: Sexo del pasajero
    - Rango: N/A
    - Distribución: 
    - Tipo de dato vacio: Ninguno
    - Clasificación de ausencia (MCAR - MAR - MNAR): Ninguno
    - Outliers: Ninguno
    - Dependencias: 
    - Tipo de relación con el target: 
    - Tratamiento previsto: 
    - Relevancia: 
    - Observaciones: Sin errores, datos limpios
- Age:
    - Cantidad de datos: 891
    - Valores faltantes: 177
    - Valores únicos (Cardinalidad): 88 
    - Tipo de variable: Cuantitativa continua 
    - Tipo de dato: Flotante (float64)
    - Descripción: Edad del pasajero en años y meses
    - Rango: 0.42 a 80.0
    - Distribución: 
    - Tipo de dato vacio: null 
    - Clasificación de ausencia (MCAR - MAR - MNAR): 
    - Outliers:
    - Dependencias: 
    - Tipo de relación con el target: 
    - Tratamiento previsto: 
    - Relevancia: 
    - Observaciones: 
- SibSp:
    - Cantidad de datos: 891
    - Valores faltantes: 0
    - Valores únicos: 7
    - Tipo de variable: Cuantitativa discreta
    - Tipo de dato: Entero (int64)
    - Descripción: Número de hermanos/cónyuges a bordo (no tiene en cuenta los amantes o prometidos)
    - Relevancia:
- Parch:
    - Cantidad de datos: 891
    - Valores faltantes: 0
    - Valores únicos: 7
    - Tipo de variable: Cuantitativa discreta
    - Tipo de dato: Entero (int64)
    - Descripción: Número de padres/hijos a bordo (no incluye niñeras)
    - Relevancia:
- Ticket:
    - Cantidad de datos: 891
    - Valores faltantes: 0
    - Valores únicos: 681
    - Tipo de variable: Cualitativa nominal
    - Tipo de dato: Objeto (object) / String
    - Descripción: Número de ticket del pasajero
    - Relevancia:
- Fare:
    - Cantidad de datos: 891
    - Valores faltantes: 0
    - Valores únicos: 248
    - Tipo de variable: Cuantitativa continua
    - Tipo de dato: Flotante (float64)
    - Descripción: Tarifa pagada por el pasajero
    - Relevancia:
- Cabin:
    - Cantidad de datos: 204
    - Valores faltantes: 687
    - Valores únicos: 147
    - Tipo de variable: Cualitativa nominal
    - Tipo de dato: Objeto (object) / String
    - Descripción: Número de cabina del pasajero
    - Relevancia:
- Embarked:
    - Cantidad de datos: 889
    - Valores faltantes: 2
    - Valores únicos: 3 (C, Q, S) / Zona o lugar de embarque
    - Tipo de variable: Cualitativa nominal
    - Tipo de dato: Objeto (object) / String
    - Descripción: Puerto de embarque del pasajero (C = Cherburgo, Q = Queenstown, S = Southampton)
    - Relevancia: 

## 📊 HALLAZGOS CLAVE - EDA
### 1. Analizar la columna objetivo y su distribución

### 1. Variable Objetivo (Survived)
- **38% sobrevivió** vs 62% murió
- Dataset ligeramente desbalanceado
- Baseline (modelo dummy): 62%

### 2. Sex vs Survived ⭐ MUY IMPORTANTE
- **Mujeres: 74%** sobrevivieron (233 de 314)
- **Hombres: 19%** sobrevivieron (109 de 577)
- **Diferencia: 55 puntos porcentuales**
- **Conclusión:** Política "mujeres primero" confirmada
- **Predictividad:** ALTA (la variable más importante)

### 3. Pclass vs Survived ⭐ IMPORTANTE
- **1ra clase: 63%** sobrevivieron (136 de 216)
- **2da clase: 47%** sobrevivieron (87 de 184)
- **3ra clase: 24%** sobrevivieron (119 de 491)
- **Conclusión:** A mayor clase social, mayor supervivencia
- **Predictividad:** ALTA (segunda más importante)

### 4. Decisiones Preliminares
**Eliminar:**
- PassengerId (solo ID): Se debe eliminar antes ya que es una variable identificadora única que no aporta información predictiva.
- Cabin (77% missing): Demasiados valores faltantes para imputar confiablemente.

**Mantener y transformar:**
- Sex ✅
- Pclass ✅
- Age (imputar faltantes)
